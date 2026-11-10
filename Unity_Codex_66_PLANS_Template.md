# PLANS | Inventory & Save

> **참고:** 본 문서는 66일차 교육용 계획 템플릿입니다. 프로젝트의 AGENTS.md보다 우선하지 않습니다.
> 모든 Task는 예시이며 실제 저장소 조사 후 수정해야 합니다.

## Goal
아이템 획득에서 UI 갱신 및 JSON 저장·로드까지 검증 가능하게 구현한다.

## Constraints / Non-goals
- Player/Enemy 이동·전투·AI 코드를 사전 승인 없이 수정하지 않는다.
- 사용자 변경과 `.meta`를 보존한다. 패키지 변경·Git commit/push는 별도 승인.
- 서버/상점/장비 기능은 범위 밖이다.

## Work Breakdown & Dependencies
| Task | Phase | Depends On | Deliverable | Status |
|---|---|---|---|---|
| T01 | 0. Survey | - | 현행 구조·요구/미정 목록 | NOT STARTED |
| T02 | 1. Data | T01 | ItemData + Catalog + ID 검사 | NOT STARTED |
| T03 | 2. Domain | T02 | Inventory add/remove + stack 검사 | NOT STARTED |
| T04 | 2. Integration | T03 | Pickup + UI event 연결 | NOT STARTED |
| T05 | 3. Persistence | T03,T04 | JSON Save/Load + 손상 데이터 검사 | NOT STARTED |

## Phase Gates
- G0: 분석 결과 및 변경 범위 승인 — T02 구현 전
- G1: T02 데이터/ID 정적 검사 및 Unity 컴파일 상태 보고 — T03 전
- G2: T03 스택 경계/아이템 손실 방지 검증 — T04 전
- G3: T04 UI 이벤트·픽업 재현 기록 — T05 전
- G4: T05 Save/Load·회귀 결과 제출 후 수락

## Validation
각 Task는 `TASKS/Txx.md`의 AC와 `TEST_MATRIX.csv`를 따른다. 실제 Unity Editor가 없으면 `NOT RUN` 표시한다.

## Status Semantics
- NOT STARTED: 진행 전
- IN PROGRESS: 승인되어 진행 중
- DONE: 범위 내 구현과 계획된 검증 완료(미실행 항목은 명시)
- BLOCKED: 필요한 환경/권한/결정 부족
- CANCELLED: 취소 이유 기록

## Recovery / Change Control
실패 시 다음 Task로 넘어가지 않는다. 변경 요청은 `CHANGE_REQUEST_TEMPLATE.md`에 영향도를 기록하고 WBS/AC 승인 후 재개한다.
