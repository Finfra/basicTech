# Visual Studio Code

## 개요

Visual Studio Code(VS Code)는 Microsoft에서 개발한 무료 오픈소스 코드 에디터입니다.
가볍고 빠르며, 다양한 프로그래밍 언어를 지원하고 풍부한 확장 기능을 제공합니다.

## 주요 개념

### 설치 및 시작
- VS Code 다운로드 및 설치
- 기본 인터페이스 이해
- 작업 공간(Workspace) 개념

### 핵심 기능
- 파일 탐색기
- 통합 터미널
- 소스 제어(Git 통합)
- 디버깅
- 확장 기능(Extensions)

### 자주 사용하는 단축키
- `Ctrl/Cmd + P`: 파일 빠르게 열기
- `Ctrl/Cmd + Shift + P`: 명령 팔레트
- `Ctrl/Cmd + B`: 사이드바 토글
- `Ctrl/Cmd + /`: 주석 토글

## 실습 예제

### VS Code에서 프로젝트 열기
```bash
# 터미널에서 VS Code로 현재 디렉토리 열기
code .

# 특정 폴더 열기
code /path/to/project
```

### 추천 확장 기능 설치
- **Korean Language Pack**: 한국어 인터페이스
- **Prettier**: 코드 포맷터
- **GitLens**: Git 기능 강화
- **Docker**: Docker 파일 지원
- **Python**: Python 개발 지원

### settings.json 기본 설정
```json
{
  "editor.fontSize": 14,
  "editor.tabSize": 2,
  "editor.formatOnSave": true,
  "files.autoSave": "afterDelay"
}
```

## 참고 자료

- [VS Code 공식 문서](https://code.visualstudio.com/docs)
- [VS Code 단축키 치트시트](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)
- [VS Code 확장 마켓플레이스](https://marketplace.visualstudio.com/vscode)
