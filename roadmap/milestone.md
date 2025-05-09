# 🚀 Test Strategy Milestone Plan (최종 프로젝트 기반)

이 문서는 최종 프로젝트를 위한 테스트 전략 수립 및 반영 로드맵을 정리한 문서입니다.  
단계적으로 테스트 시나리오를 구성하고, 프로젝트 흐름에 맞게 반영 및 고찰하는 과정을 기록합니다.

---

## ✅ 1차 테스트 시나리오 구성

**목표**: 테스트 전략의 초기 구성 및 기록 체계 마련

- 각 계층(Frontend, Backend, Database, Infra)에 맞는 테스트 항목 도출
- 테스트 종류 정의 및 용어 정리 (`TEST_TYPES.md`, `TERMINOLOGY.md`)
- Git 레포 초기화 및 디렉토리 구조 설정
- 테스트 시나리오 문서 템플릿 작성 (`test-case-template.md`, `test-report-template.md`)
- `docs/`, `scenarios/` 중심 문서 정리 및 커밋

---

## ✅ 2차 테스트 시나리오 구체화 (설계 기반 연구)

**목표**: 실현 가능한 테스트 시나리오 구체화 및 구현 계획 도출

- 실제 테스트 가능 항목 구분 (자동화 vs 수동)
- 사용 도구 구체화 (예: JUnit, Cypress, k6, Chaos Mesh)
- 각 테스트 문서에 절차/기대결과/실행도구 추가
- 테스트 실행 가능 스크립트화 연구
- 부하 테스트, 보안 테스트 실현 범위 검토

---

## ✅ 3차 프로젝트 진행 중 반영

**목표**: 실 프로젝트와 테스트 전략의 연동

- 코드 작성 시 테스트 작성 병행
- GitHub Actions 또는 Jenkins를 통한 테스트 자동화 시작
- 실제 데이터베이스(RDS), 배포 환경에 맞춘 테스트 시나리오 수정
- Chaos 실험 구성 → 스테이징 환경에서 검증

---

## ✅ N차 반영 및 고찰

**목표**: 테스트 전략의 회고 및 개선

- 테스트 커버리지 평가 및 누락 항목 보완
- 실제 장애 대응 시나리오 검토 및 적용 여부 점검
- 테스트 보고서 정리 및 자동화된 결과 시각화 도입
- 프로젝트 종료 후 테스트 전략 문서화 및 최종 정리

---

## 📌 기대 효과

- 개발과 테스트의 동시 진행을 위한 체계 확립
- 실무 수준의 테스트 구성 → 포트폴리오 활용 가능
- 운영 환경에서도 활용 가능한 시나리오 확보

---

## 📦 연관 문서
- [`TEST_PLAN.md`](../docs/TEST_PLAN.md)
- [`frontend.md`](../scenarios/frontend.md)
- [`infra.md`](../scenarios/infra.md)
