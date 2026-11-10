# Codex 리팩토링 실습 프롬프트 P0~P7

## P0 — 읽기·계획만
Unity 6.3 프로젝트의 `AGENTS.md`와 관련 규칙 문서를 확인해줘. 현재 Git 상태와 몬스터 전투 코드를 읽고 Health·Cooldown·Combat 책임을 구분해줘. **코드는 수정하지 말고** 기존 외부 동작 계약, 호출부, 직렬화 필드, 이벤트 수명, 리스크, 단계별 수정 계획(T01~T04)을 제시해줘. 각 단계에 검증 기준을 포함해줘.

## P1 — T01 Health 분리
승인된 범위에서 HP·사망 이벤트 계산만 `Day68HealthState`로 추출해줘. 기존 `ReceiveDamage`, `CurrentHp`, `OnDied`, `Reset`의 관찰 가능한 결과는 유지해줘. 수정할 파일 목록을 먼저 밝히고, 다른 기능·Prefab·Scene을 바꾸지 마. 변경 후 git diff와 검증 결과 PASS/FAIL/NOT RUN을 보고해줘. 커밋·푸시는 하지 마.

## P2 — T02 Cooldown 분리
공격 시간 비교를 `Day68CooldownGate`로 추출해줘. `TryAttack(float now)`의 유효·무효 시각, 동일 시각 재호출, Reset 동작을 변경하지 마. 외부 시계(Time.time)를 내부에서 새로 읽지 말고 now를 주입받도록 해줘. 차이를 git diff로 검토하고 조건별 테스트 결과를 보고해줘.

## P3 — T03 Combat 조합
`Day68RefactoredMonsterLogic`이 Health와 Cooldown을 조합하도록 수정해줘. 기존 공개 생성자·메서드·이벤트·프로퍼티의 관찰 가능한 계약을 유지해줘. 사망 이후 공격 금지, 중복 이벤트 금지를 확인해줘. 관련 없는 리네이밍은 하지 마.

## P4 — Unity Facade 연결
`Day68CombatFacade`가 순수 로직을 관리하도록 연결해줘. Scene/Prefab 직렬화 참조와 `Awake`, `OnEnable`, `OnDisable`, `OnDestroy`의 실행 순서를 조사하고 보상 이벤트 구독/해제의 대칭을 확인해줘. Scene·Prefab 변경이 필요하면 먼저 변경 목록과 영향·승인을 요청해줘.

## P5 — Git Diff 셀프 리뷰
`git status`, `git diff --stat`, `git diff --check`, 승인 대상 파일의 상세 diff를 읽기 전용으로 검토해줘. 기능 변경, 누락된 이벤트 해제, Reset 누락, Inspector 참조 변경을 중점 확인해줘. 발견 사항은 파일:줄, 조건, 실제 영향, 우선순위, 최소 수정안을 포함해 보고해줘. 수정하지 마.

## P6 — 동등성/회귀 검증
Legacy/Refactored 양쪽에 같은 입력 시퀀스를 실행하는 테스트를 점검해줘. 12개 모델 시퀀스, OnEnable 반복, 이벤트 보상 1회, Prefab 참조, git diff 범위까지 QA01~QA12로 정리해줘. 실행한 테스트와 미실행 테스트를 구분하고, 각 결과를 PASS/FAIL/NOT RUN + 로그 근거로 보고해줘.

## P7 — 최종 인계
수정 전 문제·변경 계획·작업별 diff·행동 계약·자동/수동 테스트 결과·남은 위험·수정하지 않은 항목을 리팩토링 보고서로 작성해줘. 승인받지 않은 Git commit/push, Scene/Prefab 변경은 하지 마. 검증이 불가능한 것은 반드시 NOT RUN으로 표시해줘.
