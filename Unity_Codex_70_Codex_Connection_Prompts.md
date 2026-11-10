# Codex 단계별 Unity MCP 설치·연결 프롬프트 P0~P9

## P0 — 현재 상태 조사 (읽기 전용)
AGENTS.md를 먼저 확인해줘. Unity 프로젝트와 Codex 설정을 **읽기만** 하고, Unity CLI·Editor·Pipeline·MCP의 설치 및 연결 상태를 증거와 함께 보고해줘. 설치/수정/삭제/실행 승인 요청은 하지 말고, 확인 사실/가정/미검증을 구분해줘.

## P1 — 설치 계획 수립
현재 상태를 기준으로 부족한 구성요소만 설치하는 WBS를 만들어줘. 변경 파일, `config.toml` 백업, 되돌리기, 실제 Editor 확인 테스트를 포함하고 계획만 제시해줘.

## P2 — Pipeline 설치 사전 검사
열려 있는 Editor의 프로젝트 경로, Unity 버전, Console 컴파일 에러 상태, `unity pipeline list` 결과를 검사해줘. 이미 설치돼 있으면 재설치하지 말 것. 설치가 필요하면 이유와 변경 범위를 보고하고 사용자 승인을 요청해줘.

## P3 — MCP 설정 미리보기
`unity mcp configure --list`, `unity mcp configure codex --dry-run` 결과를 검토해줘. `config.toml`, 로컬 네트워크/sandbox 정책에서 바뀌는 점과 복구 방법을 설명해줘. 실제 등록은 별도 승인까지 금지.

## P4 — 실제 Editor 읽기 연결 검사
AGENTS.md 규칙을 먼저 확인하고, MCP 도구를 사용하여 실행 중인 Unity Editor의 프로젝트 경로(공유본은 마스킹), Unity 버전, 활성 Scene 이름을 **실제로 조회**해줘. 파일, 씬, 설정을 수정하지 마. 도구 이름·실제 반환 데이터·성공/실패를 구분해 기록해줘. 실행할 수 없다면 NOT RUN이라고 보고해줘.

## P5 — 여러 Editor 인스턴스 검사
Unity Editor가 2개 이상이면 목록을 조회하고 대상 프로젝트 경로가 정확한지 확인해줘. 작업 대상을 특정할 수 없다면 중단하고 이름·경로를 보고해줘. 쓰기 동작은 금지.

## P6 — 제한적 쓰기 실험 (별도 사용자 승인 후)
읽기 연결이 성공했다면 **새 테스트 씬 Day70_MCP_TestScene에서만** `Day70_MCP_Cube` 하나를 생성하는 방법을 제안해줘. 실제 수정은 사용자 승인 후 실행하고, 결과를 Hierarchy와 Git Diff로 확인한 다음 원복 방법을 보고해줘. 기존 Scene은 변경 금지.

## P7 — 안전·권한 감사
Unity MCP 등록에 따른 네트워크 정책·도구 권한·외부 전송 가능성을 점검해줘. 기본은 읽기 전용. 광범위한 승인·네트워크 전면 허용·토큰 노출은 하지 말아줘. 의심 항목은 별도 보고해줘.

## P8 — 실패 원인 분석
Unity MCP 연결 실패 로그를 받은 그대로 분석하고 실패 계층(CLI / Editor / Pipeline / MCP 설정 / Codex 세션 / Sandbox / 승인)을 분류해줘. 처음부터 재설치하지 말고 최소 수정안과 재검증 절차를 제시해줘.

## P9 — QA 보고서
QA01~QA12 각각 PASS/FAIL/NOT RUN, 증거 경로·실제 사용한 명령·수정 파일·잔여 위험을 정리해줘. 실제 Unity Editor 또는 MCP 호출을 못 했다면 성공이라고 쓰지 말아줘. Git commit/push는 하지 말아줘.
