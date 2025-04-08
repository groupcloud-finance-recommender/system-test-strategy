# 📘 TERMINOLOGY

이 문서는 테스트 전략 및 인프라 설계에서 자주 등장하는 핵심 용어들을 정리한 것입니다.  
특히 고가용성(HA), 장애 허용(FT) 등 인프라와 밀접한 개념에 대해 명확히 이해하고 사용하기 위한 기준을 제공합니다.

---

## ✅ 핵심 개념 정의

| 용어 | 정의 | 특징 |
|------|------|------|
| HA (High Availability) | 고가용성: 시스템이 최대한 **장애 없이 지속적으로 운영**될 수 있도록 구성 | 복구 중심, 장애 발생 시 자동 전환 (Failover), 몇 초 내 회복 |
| FT (Fault Tolerance) | 장애 허용: 시스템 일부에 장애가 발생해도 **서비스가 중단 없이 동작** | 무중단 중심, 동시 이중화 구조, 비용 높음 |
| Failover | 장애 발생 시 자동으로 대체 시스템으로 **전환**되는 기능 | RDS Multi-AZ, EC2 Auto Recovery 등 |
| RPO (Recovery Point Objective) | 복구 지점 목표: 장애 발생 시 **데이터를 얼마만큼 잃어도 허용 가능한가** | ex) RPO = 5분 → 최대 5분 데이터 손실 가능 |
| RTO (Recovery Time Objective) | 복구 시간 목표: 장애 발생 후 **얼마나 빨리 복구해야 하는가** | ex) RTO = 1분 → 1분 이내 복구 필수 |
| Chaos Engineering | 의도적으로 시스템에 장애를 발생시켜 **복원력과 자동 복구 능력을 검증**하는 방식 | Netflix의 Chaos Monkey가 대표적 |
| Load Testing | 시스템에 일정 수준의 부하를 주어 **성능과 안정성을 검증**하는 테스트 | ex) 500명 동시 접속 시 API 응답 확인 |
| Smoke Testing | 배포 직후 최소한의 기능이 정상인지 빠르게 확인하는 테스트 | 예: `/health`, `/version` API 확인 |
| Regression Testing | 기능 추가나 코드 변경 후 **기존 기능이 정상 작동하는지 확인**하는 테스트 | 변경 사항에 대한 영향 분석 포함 |

---

## 📌 참고 사항

- HA ≠ FT: 고가용성과 장애 허용은 유사하지만 목적과 구성 방식이 다름
- 실제 환경에서는 **HA를 기본으로 구성**하고, 일부 핵심 시스템만 FT 구조로 설계
- RPO/RTO는 백업/복구 전략에서 반드시 기준으로 설정되어야 함

---

## 📦 연관 문서
- [`TEST_PLAN.md`](./TEST_PLAN.md): 테스트 전략 문서
- [`database.md`](../scenarios/database.md): DB 복구 및 HA 시나리오
- [`infra.md`](../scenarios/infra.md): Chaos, 부하, 확장성 테스트 시나리오
