# 줄바꿈(CRLF) 경고 메시지

Windows에서 Git이 "LF will be replaced by CRLF" 같은 줄바꿈 경고를 띄울 때 대처 방법입니다.

## 상황

줄바꿈 문자 차이(LF vs CRLF) 때문에 Git이 경고를 보여주거나, 커밋 시마다 불필요한 변경으로 보일 때 설정으로 정리할 수 있습니다.

## 명령어

```bash
git config --global core.autocrlf true
```

- Windows에서는 보통 `true`로 두면, 커밋 시 LF로 저장하고 체크아웃 시 CRLF로 변환합니다.

## 참고

- **Windows 사용자**: 위 설정으로 대부분의 경고가 사라집니다. 팀이 Windows·Mac 혼용이면 저장소 규칙(예: `.gitattributes`에서 `* text=auto`)과 맞춰 두는 것이 좋습니다.
