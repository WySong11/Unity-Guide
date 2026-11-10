# Codex 단계별 작업 프롬프트 (복사/편집용)

`AGENTS.md`는 지속적인 규칙, 아래 P0~P7은 **이번 과제에 대한 일회성 요청**이다.

## P0 · 기존 프로젝트 조사 — READ ONLY
```text
Unity 6.3 프로젝트의 AGENTS.md 및 해당 작업에 적용되는 규칙을 먼저 확인해줘.
현재 코드·에셋은 수정하지 마. git status와 관련 파일 구조를 확인한 뒤
아이템 획득/인벤토리/JSON Save 구현에 필요한 기존 시스템, 재사용 지점,
요구 누락, 위험, 미결정 항목을 표로 정리해줘.
찾지 못한 파일은 존재한다고 추측하지 마. 예상 변경 파일과 영향도를 보고해줘.
```

## P1 · WBS 및 계획 수립 — PLAN ONLY
```text
PROJECT_BRIEF.md의 R01~R04, AGENTS.md 규칙을 기준으로 WBS를 설계해줘.
각 Task에 ID, 목적, 선행 Task, 수정 대상 경로(미확인 시 미정), AC,
테스트 방법, 완료 조건, 위험 및 사람 승인 Gate를 명시해줘.
계획 문서 초안만 제안하고 C#/Prefab/Scene 구현은 시작하지 마.
선행 관계의 순환과 과도하게 큰 Task가 없는지 자체 검토해줘.
```

## P2 · 승인된 T02만 구현 — EXECUTE ONE TASK
```text
내가 승인한 TASKS/T02.md만 구현해줘. AGENTS.md와 git status를 먼저 확인해.
현재 프로젝트에서 확정된 Data 폴더 내 ItemData/Catalog 및 ID 검사만 수정할 것.
Player/Enemy/Scene/Packages/저장 시스템은 변경하지 마.
기존 사용자 변경을 유지하면서 최소 diff로 작성하고, 다음 T03는 실행하지 마.
변경 파일과 정적 리뷰 및 가능할 경우 Unity 컴파일 기록을 제출해줘.
```

## P3 · 완료 기준 검증 — VERIFY
```text
T02의 AC와 TEST_MATRIX를 점검해줘. 실행한 검사만 PASS라고 보고해.
정적 검토, Unity 컴파일, Play Mode를 분리하고 불가능한 검사는 NOT RUN으로 표시.
git diff --check, 변경 파일 범위, Item ID 중복/빈 ID 검사 결과를 기록해줘.
문제가 있으면 정확한 재현 조건과 최소 수정 방안을 제시해줘.
```

## P4 · 작업 종료 보고 — HANDOFF
```text
승인된 T02 작업을 인계 문서로 정리해줘.
완료/차단/취소 상태, 수정 파일, AC별 검사 증거, 미실행 항목,
미해결 위험, 다음 Task T03 선행 조건을 작성해줘.
PLANS.md와 BUILD_LOG.md의 실제 상태만 갱신해줘.
명시적 요청 없이는 git commit/push 또는 다음 Task 구현을 하지 마.
```

## P5 · 코드 리뷰 / 최소 개선 — REVIEW
```text
T02 변경분만 리뷰해줘. Scope creep, 공개 필드, ID 중복, Unity 직렬화,
에셋 참조·.meta 위험, 기존 시스템 회귀 가능성을 점검해줘.
우선순위와 증거를 남기고 이번 Task 범위를 벗어나는 개선은 제안으로만 기록해줘.
```

## P6 · 요구 변경 영향 분석 — CHANGE CONTROL
```text
추가 요청 '장비 아이템 지원'은 기존 범위를 벗어나.
지금은 수정하지 말고 R01~R04/WBS/T02~T05에 미치는 영향,
새 Task, 수정/테스트 범위, 위험, 승인 Gate를 문서로만 제안해줘.
```

## P7 · 회귀 검증 — REGRESSION
```text
승인된 Task 완료 후 기존 Player 이동, 전투, Enemy AI, UI 동작에 영향이 없는지
기존 테스트 목록과 가능한 Unity 테스트를 대조해줘.
실제 실행한 로그만 PASS로, 환경 부족은 NOT RUN으로 보고하고
새로 확인된 문제와 관련 Task ID를 연결해줘.
```
