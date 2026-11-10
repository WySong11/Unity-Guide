# Windows PowerShell 명령 모음

## 0. 현황만 조사 (설정 변경 없음)
```powershell
Get-Command unity -ErrorAction SilentlyContinue
Get-Command codex -ErrorAction SilentlyContinue
unity --help
unity status
unity editors running
unity pipeline list
unity command
unity mcp configure --list
codex mcp list
```
CLI가 없다면 나머지 명령은 실패하는 것이 정상입니다. 해당 환경에서 NOT RUN으로 기록합니다.

## 1. 설치가 필요한 경우 (사용자 승인 후)
```powershell
unity auth login
unity pipeline install
unity pipeline list
```
이미 패키지가 있으면 재설치하지 않습니다. 프로젝트가 여러 개라면 설치 대상 경로를 먼저 확인하세요.

## 2. MCP 구성 (사용자 승인 후)
```powershell
unity mcp configure codex --dry-run
# 출력 확인 + 기존 설정 별도 백업 + 권한 승인
unity mcp configure codex
codex mcp list
```
`unity mcp configure codex`는 Codex의 config.toml뿐 아니라 localhost 접근을 위한 샌드박스 네트워크 정책을 변경할 수 있습니다. 원래 설정과 Diff를 검토합니다.

## 3. 연결 검증 (쓰기 금지)
```powershell
unity command
# 둘 이상 Editor가 열려 있을 때
unity command --project-path="D:\Projects\MyUnityGame"
```
`D:\Projects\MyUnityGame`은 본인 환경의 실제 프로젝트 경로로 교체합니다.

## 4. 선택 과제: Unity 공식 스킬 플러그인 (MCP 설정과 별개)
```powershell
codex plugin marketplace add Unity-Technologies/unity-agent-plugin
codex plugin add unity@unity-agent-plugin
codex plugin list
```

## 보안
Codex 설정 파일을 새 내용으로 전면 덮어쓰지 말 것. 쓰기·삭제·씬 변경 작업을 승인 없이 실행하지 말 것. 서버 등록 성공과 실제 Editor 응답은 다른 증거입니다.
