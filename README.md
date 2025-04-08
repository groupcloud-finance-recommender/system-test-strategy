# ⚠️ System Test Strategy

이 레포는 **최종 프로젝트를 위한 시스템 테스트 전략**을 정리하고 자동화 기반 테스트로 확장하기 위한 목적으로 구성되었습니다.  
Frontend, Backend, Database, Infrastructure 계층에서의 다양한 테스트 유형과 시나리오를 문서화하며,  
고가용성(HA), 장애 허용(FT), 보안, 성능, 복구 전략을 포함한 **실무 수준의 테스트 설계**를 목표로 합니다.

---

## ✅ 목적

- 테스트 시나리오를 계층별/도구별로 구조화
- 실제 프로젝트 진행 중 테스트 자동화 및 검증 기반 마련
- 운영 환경에서도 사용할 수 있는 안정성 검증 시나리오 확보
- Chaos Engineering 및 Recovery Plan까지 통합

---

## 🧩 구성
``` bash
📦 system-test-strategy/
├── README.md                    ✅ 레포 소개 및 목적
├── docs/
│   ├── TEST_PLAN.md            ✅ 계층별 테스트 항목 (Spring, React, JPA, MySQL, AWS 포함)
│   ├── TEST_TYPES.md           ✅ 개발에서 사용하는 테스트 종류 설명
│   ├── TEST_EXAMPLES.md        ✅ 실무 기준 테스트 조합 예시
│   ├── TEST_PYRAMID.md         ✅ 테스트 피라미드 설명
│   └── TERMINOLOGY.md          ✅ HA, FT 등 개념 정리 (선택)
├── scenarios/
│   ├── frontend.md             ✅ 프론트엔드 시나리오 (Jest, Cypress)
│   ├── backend.md              ✅ 백엔드 시나리오 (JUnit, Postman)
│   ├── database.md             ✅ DB 무결성, RDS HA 시나리오
│   └── infra.md                ✅ AWS + 고가용성 + 보안 + 오토스케일링 시나리오
├── templates/
│   ├── test-case-template.md   ✅ 공통 테스트 시나리오 작성 양식
│   └── test-report-template.md ✅ 테스트 리포트 양식
└── roadmap/
    └── milestone.md            ✅ 향후 계획 (자동화 도입, 모니터링 연동 등)
```

---

## 🔍 포함 내용 요약

- `docs/TEST_PLAN.md`: 계층별 테스트 항목 정리
- `docs/TEST_PYRAMID.md`: 테스트 피라미드 설명
- `docs/TEST_TYPES.md`: 다양한 테스트 종류 설명
- `docs/TERMINOLOGY.md`: HA, FT, RTO/RPO 등 용어 정리
- `scenarios/`: 실제 시나리오 문서 (frontend, backend, db, infra)
- `roadmap/milestone.md`: 단계별 테스트 계획 및 고찰

---

## 🛠 사용 도구 예시

- **Frontend**: Jest, React Testing Library, Cypress
- **Backend**: JUnit, Mockito, SpringBootTest, TestContainers
- **Infra**: k6, Chaos Mesh, AWS FIS, CloudWatch, Grafana
- **CI/CD**: GitHub Actions, Jenkins, GitLab CI
- **보안/분석**: WAF, Inspector, SonarQube, ESLint

---

## 📌 활용 예시

- 개발 중 테스트 케이스 문서화 → 자동화 코드 연동
- 테스트 결과 리포트 작성 → `templates/test-report-template.md` 활용
- CI/CD 파이프라인 연동 → 배포 전/후 품질 확인
- Chaos 테스트 → 운영 전 복구 시나리오 검증

---

## 📦 작성 및 유지 관리

- **작성자**: 이성빈
- **프로젝트 기간**: 2024.04.08 ~ 2024.06.17
- 테스트 전략 문서는 **프로젝트 흐름과 함께 계속 발전**됩니다.