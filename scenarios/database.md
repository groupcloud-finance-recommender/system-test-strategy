# 🛢 Database Test Scenarios

이 문서는 MySQL 및 AWS RDS를 사용하는 데이터베이스 계층의 테스트 시나리오를 정리한 문서입니다.  
테스트는 고가용성(HA), 무결성, 백업 및 복구 관점으로 구성됩니다.

---

## ✅ 고가용성 테스트 (High Availability)

| 항목 | 설명 |
|------|------|
| RDS Failover | RDS의 Master 인스턴스를 강제로 Failover → 애플리케이션 연결 복구 확인 |
| Multi-AZ 장애 대응 | Multi-AZ 환경에서 장애 발생 시 자동 전환 확인 |
| 커넥션 풀 재연결 | DB 장애 후 커넥션 풀에서 자동 복구 여부 확인 |

📌 사용 도구: AWS Console, CLI, CloudWatch

---

## ✅ 무결성 테스트 (Data Integrity)

| 항목 | 설명 |
|------|------|
| 스냅샷 기반 복구 | RDS snapshot으로 복원 후 데이터 손실 여부 확인 |
| 테이블 제약조건 검증 | FK, NOT NULL, UNIQUE 등 제약조건 위반 시 에러 발생 여부 |
| 동시성 테스트 | 동일 자원에 대한 동시 쓰기 요청 시 일관성 보장 여부 확인 |

📌 사용 도구: SQL 스크립트, S3, 데이터 검증 쿼리

---

## ✅ 백업 및 복구 테스트

| 시나리오 | 절차 |
|----------|------|
| 정기 백업 수행 | cron 기반으로 mysqldump 자동 실행 및 S3 업로드 확인 |
| 복구 스크립트 실행 | `restore.sh` 실행 → DB 재생성 및 데이터 복원 확인 |
| 장애 복구 시나리오 | 운영 DB 장애 시 복구 시나리오 수행 시간 측정 및 검증 |

📌 사용 도구: cron, shell, mysqldump, S3, restore.sh

---

## 📦 기타 고려사항

- TestContainers를 활용한 로컬 테스트 환경에서도 RDS 시나리오 일부 재현 가능
- S3 → RDS 복구 자동화 파이프라인 구성 고려
- 장애 복구 시간(RTO), 데이터 손실 허용 범위(RPO) 기준 수립 필요
