# 67일차 Codex 코드 리뷰 프롬프트 · P0~P6

## P0 — Scope / Git Status
```text
현재 저장소 AGENTS.md와 관련 하위 규칙을 읽고 git status --short, git diff --stat,
git diff --name-status, git diff --cached --stat를 확인해줘.
수정된 파일 범위와 Unstaged/Staged/Untracked 구분만 보고하고 파일은 수정하지 마.
```

## P1 — Read-Only Review
```text
현재 승인된 T03 기능의 Git Diff만 읽기 전용으로 리뷰해줘.
변경된 줄·관련 호출부와 AGENTS.md의 Code Review Rules를 확인해.
데이터 손실, 이벤트 해제, Pool 중복 반환, JSON 상태 손상, 기존 기능 회귀에 집중.
각 Finding은 [P1/P2/P3] 제목, 정확한 파일:줄, 트리거, 기대/실제, 원인,
최소 수정 제안, 확인할 테스트를 적어줘. 추측은 Finding으로 확정하지 마.
실행하지 못한 검사는 NOT RUN. 코드·Prefab·Scene·Git 상태를 변경하지 마.
```

## P2 — Codex Built-in /review 비교
```text
VS Code Codex 입력창에서 /review를 실행하고 Review uncommitted changes를 선택해줘.
(도구가 제공하지 않으면 위 P1 텍스트 요청으로 대체.)
결과를 보고서에 붙인 다음 사람이 찾은 F01~F04와 누락·거짓 양성을 비교해줘.
```

## P3 — Verify Findings
```text
각 Finding의 정확한 변경 줄과 전체 호출 경로를 확인해줘.
변경 전에도 존재한 문제인지, 이번 변경으로 도입된 회귀인지 구분해줘.
Unity Editor Play Mode 실행이 불가능하면 정적 리뷰로 표기하고 NOT RUN을 유지해.
```

## P4 — Minimal Fix Proposal (NO CODE CHANGE)
```text
확정한 Finding만 대상으로 허용 파일별 1~2단계 최소 수정 계획을 제안해줘.
기존 프로젝트 변경 보존, .meta와 씬 보존, 다른 기능 확장 금지.
승인 전에는 코드 수정·git add/commit/push하지 마.
```

## P5 — Approved Fix / Re-Review
```text
내가 승인한 Finding만 최소 diff로 수정해줘.
수정 전·후 git diff를 비교하고 QA07~QA10 재현 조건을 다시 검증해줘.
PASS/FAIL/BLOCKED/NOT RUN과 실제 로그·미해결 위험을 보고해.
```

## P6 — Final Handoff
```text
최종 Finding 상태 OPEN/FIXED/NOT REPRODUCED를 기록해줘.
변경 파일, 검증 근거, 회귀 테스트 결과, 남은 문제, 다음 작업의 선행 조건을
정리하되 승인 없이 commit/push하지 마.
```
