# ⚙️ Backend Test Scenarios

이 문서는 Spring Boot 기반 백엔드 애플리케이션에서 수행할 테스트 시나리오를 정리한 문서입니다.  
테스트는 단위(Unit), 통합(Integration), API 테스트 단계로 구성됩니다.

---

## ✅ 단위 테스트 (Unit Test)

| 항목 | 설명 |
|------|------|
| Service 로직 검증 | 각 서비스 메서드가 비즈니스 로직대로 동작하는지 확인 |
| Repository Mock 테스트 | DB 없이 Repository 메서드 동작을 mock으로 테스트 |
| 예외 처리 검증 | 잘못된 입력에 대해 적절한 예외가 발생하는지 확인 |

📌 사용 도구: JUnit 5, Mockito

---

## ✅ 통합 테스트 (Integration Test)

| 항목 | 설명 |
|------|------|
| DB 연동 검증 | 실제 MySQL과 연동해 Entity 저장 및 조회 테스트 |
| 트랜잭션 롤백 | 예외 발생 시 데이터가 롤백되는지 확인 |
| 구성 요소 연동 | Controller → Service → Repository 흐름 확인 |

📌 사용 도구: SpringBootTest, TestContainers

---

## ✅ API 테스트 (REST API)

| 시나리오 | 절차 |
|----------|------|
| 회원가입 API | `POST /api/users` 요청 → 상태 코드 201 응답 확인 |
| 로그인 API | `POST /api/login` → JWT 토큰 응답 확인 |
| 인증/인가 테스트 | 유효하지 않은 토큰 → 401/403 응답 확인 |
| 예외 처리 테스트 | 필수 파라미터 누락 → 400 Bad Request 응답 확인 |

📌 사용 도구: Postman, RestAssured

---

## 📦 기타 고려사항

- Spring REST Docs 또는 Swagger를 활용한 API 문서 자동화 고려
- TestContainers로 실제 환경과 유사한 DB 테스트 환경 구성
- MockMvc 또는 WebTestClient로 HTTP 테스트도 가능함
