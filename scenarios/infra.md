# ☁️ Infrastructure Test Scenarios

이 문서는 AWS 기반 인프라 계층에서 수행할 테스트 시나리오를 정리한 문서입니다.  
테스트는 헬스체크, 부하, 보안, 확장성, CI/CD, 고가용성(Chaos 포함) 관점으로 구성됩니다.

---

## ✅ 인프라 헬스체크

| 항목 | 설명 |
|------|------|
| EC2 인스턴스 상태 | 인스턴스 종료/비정상 상태 시 ALB가 자동으로 트래픽을 다른 인스턴스로 전달하는지 확인 |
| ALB 헬스체크 동작 | 비정상 포트/응답 미반환 시 인스턴스가 비정상 처리되는지 검증 |

📌 사용 도구: AWS Console, CloudWatch, ALB 설정

---

## ✅ 부하 테스트 (Performance Test)

| 항목 | 설명 |
|------|------|
| API 동시 요청 | 500명 동시 요청 시 응답 시간 및 에러율 측정 |
| DB 부하 시나리오 | 다중 쓰기/읽기 시 데이터 일관성 및 처리 시간 측정 |

📌 사용 도구: k6, JMeter, stress, ab

---

## ✅ 보안 테스트

| 항목 | 설명 |
|------|------|
| 보안 그룹 설정 검토 | 불필요한 포트가 열려 있는지 확인 |
| 인증 우회 시도 | 토큰 없이 민감 정보 접근 시 차단 확인 |
| WAF 룰 검증 | SQL Injection, XSS 패턴 차단 여부 테스트 |

📌 사용 도구: AWS Inspector, WAF, 수동 테스트

---

## ✅ 확장성 테스트 (Scalability)

| 항목 | 설명 |
|------|------|
| Auto Scaling | CPU 부하 증가 시 EC2 인스턴스가 자동으로 확장되는지 확인 |
| Kubernetes HPA | 트래픽 증가 시 pod가 자동으로 scale-out 되는지 확인 |

📌 사용 도구: CloudWatch, Prometheus, Grafana

---

## ✅ CI/CD 테스트

| 항목 | 설명 |
|------|------|
| 빌드 성공 여부 | PR → Build → Test → Deploy 파이프라인 정상 작동 여부 확인 |
| 실패 핸들링 | 빌드 실패 시 알림 전송 및 배포 중단 여부 확인 |
| 배포 후 Smoke Test | `/health`, `/version` 등 API 응답 확인하여 정상 여부 판별 |

📌 사용 도구: GitHub Actions, Jenkins, GitLab CI

---

## ✅ 고가용성 테스트 (Chaos Test 포함)

| 항목 | 설명 |
|------|------|
| 노드 장애 | EC2 또는 K8s 노드 강제 중단 → 서비스 무중단 유지 여부 확인 |
| 네트워크 분리 | Chaos Mesh 또는 AWS FIS로 네트워크 지연/단절 시나리오 실행 |
| Pod 종료 | 서비스 중인 Pod 강제 종료 → 재시작 및 트래픽 분산 여부 확인 |

📌 사용 도구: Chaos Mesh, AWS Fault Injection Simulator, kubectl, shell scripts

---

## 📦 기타 고려사항

- Chaos 시나리오는 staging 환경에서 사전 테스트 후 운영 적용
- Grafana 대시보드를 통해 테스트 중 지표 실시간 모니터링 가능
- 테스트 결과는 `test-report-template.md`에 따라 문서화
