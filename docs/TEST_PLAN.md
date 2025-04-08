# 🧪 TEST PLAN

이 문서는 시스템 전반에 대한 테스트 전략을 계층별로 정리한 문서입니다.  
각 테스트는 기능, 성능, 안정성, 보안, 복구 관점에서 구성되며,  
Frontend, Backend, Database, Infrastructure 등 각 계층에서 사용될 도구와 테스트 종류를 구분하여 설계합니다.

---

## ✅ 계층별 테스트 항목

| 계층 | 테스트 종류 | 도구 | 설명 |
| --- | --- | --- | --- |
| 🖼 Frontend | 단위 테스트 | Jest, React Testing Library | 버튼, 텍스트 렌더링 확인 |
| 〃 | 통합 테스트 | Cypress (with mock API) | 로그인 → 리디렉션 → 홈 이동 |
| 〃 | E2E 테스트 | Cypress | 실제 API와 통신, 회원가입 → 로그인 |
| ⚙️ Backend | 단위 테스트 | JUnit, Mockito | Service, Repository 단위 검증 |
| 〃 | 통합 테스트 | SpringBootTest, TestContainers | 실제 DB(MySQL) 연동 테스트 |
| 〃 | API 테스트 | Postman / RestAssured | REST API 상태코드, 응답 구조 |
| 🛢 Database | HA 테스트 | RDS Multi-AZ Failover 시나리오 | 강제 failover 후 서비스 복원 확인 |
| 〃 | 무결성 테스트 | S3, RDS snapshot | 데이터 무결성 확인 |
| ☁ Infra | 인프라 헬스체크 | EC2 헬스체크, ALB 상태 | 인스턴스 죽었을 때 자동 교체 여부 |
| 〃 | 부하 테스트 | k6, JMeter, stress, ab | 500명 동시 접속, DB 응답 시간 측정 |
| 〃 | 고가용성 테스트 | Chaos Mesh / AWS Fault Injection Simulator | 노드 다운, 네트워크 단절 시나리오 |
| 〃 | 보안 테스트 | AWS Inspector, WAF 테스트 | 포트/보안그룹/인증 우회 점검 |
| 〃 | 정적 분석 | SonarQube, ESLint, SpotBugs | 코드 품질 자동 검출 |
| 〃 | 확장성 테스트 | CloudWatch, Prometheus, Grafana | 트래픽 급증 시 오토스케일링 여부 테스트 |
| 〃 | CI/CD 테스트 | Jenkins, GitHub Actions, GitLab CI | CI/CD 파이프라인 신뢰성 검증 |
| 〃 | 백업 & 복구 테스트 | cron + mysqldump + shell | 정기 백업 수행 및 장애 발생 시 복구 자동화 검증 |

---

## 📎 연관 문서
- [`TEST_TYPES.md`](./TEST_TYPES.md): 테스트 분류별 정의
- [`scenarios/README.md`](../scenarios/README.md): 테스트 시나리오 디렉토리 안내
