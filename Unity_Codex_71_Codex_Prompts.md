# 71일차 Codex 단계별 프롬프트 P0~P10

> 각 프롬프트를 독립된 단계로 실행한다. 실제 제공된 도구 명과 스키마에 맞게 인수를 작성한다. **쓰기 시작 전 사용자/강사 승인**을 받는다.

## P0 — 사전 환경 및 규칙 조사 (읽기만)
```text
작업 폴더의 AGENTS.md와 Unity 관련 규칙을 확인해줘. 현재 Unity 프로젝트 경로, Git 변경 상태, Unity CLI/Pipeline/Codex MCP 연결 상태를 읽기 전용으로 조사해. 설정이나 Scene을 수정하지 말고 실행한 명령과 실제 결과만 표로 보고해.
```

## P1 — MCP 도구 인벤토리 (읽기만)
```text
지금 활성화된 Unity MCP 도구의 실제 식별자·설명·필수 인수 스키마를 확인해줘. Scene 조회, Hierarchy 조회, GameObject 생성, Transform 수정, Component 연결, 저장, Console 조회에 해당하는 도구를 구분해. 없는 도구는 “제공되지 않음”으로 보고하고 이름을 추측하지 마. 프로젝트 변경 금지.
```

## P2 — Editor 실조회 (읽기만)
```text
Unity MCP로 현재 Editor 프로젝트 경로, Unity 버전, 활성 Scene 이름·경로, Root GameObject 목록, 선택된 객체 Transform, Console Error/Warning 상태를 조회해줘. 도구명/입력/실제 응답과 Inspector 비교 결과를 표로 남겨줘. 실행 못한 항목은 NOT RUN.
```

## P3 — 신규 Scene 생성 (승인 후 쓰기)
```text
승인 범위는 Assets/Day71_EditorToolLab/ 내 새로운 Scene 한 개야. Scene 이름은 Day71_MCP_EditorLab. 기존 Scene의 미저장 변경과 동일 파일 존재 여부를 먼저 확인해. 충돌하면 중단. 새로운 Scene 생성 도구를 실제 스키마에 맞게 호출하고 생성 경로를 재조회해. 기존 Scene·ProjectSettings·Packages 수정 금지.
```

## P4 — Cube 생성 (승인 후 쓰기)
```text
Day71_MCP_EditorLab Scene에 Day71_MCP_Cube가 없다면 딱 한 개만 생성해줘. 같은 이름이 이미 있으면 생성하지 말고 기존 객체를 확인해. 실행한 Unity 도구의 실명·인수와 Hierarchy의 객체 수를 보고해.
```

## P5 — Transform 지정 (승인 후 쓰기)
```text
Day71_MCP_Cube의 Position=(0,1,0), Euler=(0,0,0), Scale=(1,1,1)을 지정해줘. Local/World 기준을 명확히 해. 변경 후 다시 Transform 값을 실제 조회해서 Before/After 표를 만들어줘.
```

## P6 — 컴포넌트 연결 (승인 후 쓰기)
```text
제공된 Day71SpinCube 스크립트 존재와 컴파일 Error=0을 먼저 확인해줘. Day71_MCP_Cube에 Day71SpinCube가 없다면 1회만 추가하고, SpeedDegreesPerSecond=45를 Inspector에서 재조회해. 컴파일 오류나 도구 부재가 있으면 중단하고 추측하지 마.
```

## P7 — Scene Save (승인 후 쓰기)
```text
활성 Scene이 Day71_MCP_EditorLab인지 확인하고 그 Scene만 저장해줘. 저장 후 Scene path, dirty 상태, Cube transform, 컴포넌트 수를 다시 조회하고 git status·git diff --stat도 확인해. 다른 파일 변경이 있으면 목록과 원인을 보고해.
```

## P8 — Play Mode 테스트 (승인 후 실행)
```text
Console에 컴파일 오류가 없는지 확인한 다음 허가된 Day71 실습 Scene에서만 Play Mode를 실행해줘. Cube가 초당 45도 속도로 Y축 회전하는지 Game/Scene 뷰에서 검사하고 종료해. 실행 증거가 없으면 PASS를 표시하지 마.
```

## P9 — 재현·회귀 테스트 (읽기 / 승인된 제한적 쓰기)
```text
QA_MATRIX.csv의 QA01~QA12를 순서대로 검증해줘. 실제 도구 호출 로그, Editor 값, 파일 경로, Git 변경 사항을 증거로 PASS/FAIL/NOT RUN으로 구분해. 도구 응답 또는 스크린샷 없는 항목을 PASS로 만들지 마.
```

## P10 — 리뷰 보고 / 원복 방안 (읽기만)
```text
변경한 파일 목록과 각 변경의 목적, 수행된 Unity MCP 도구 목록과 결과, Console Error 수, QA 합격/실패/미실행 수를 보고해줘. 승인하지 않은 삭제·커밋·푸시 금지. 실습 Scene을 제거하려면 먼저 삭제 대상을 보여주고 승인을 요청해.
```
