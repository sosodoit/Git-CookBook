# 대용량 파일(Git LFS) 사용할 때

CSV, 영상, 대용량 바이너리 등 큰 파일을 저장소에서 Git LFS로 관리하려고 할 때 사용합니다.

## 상황

- `.csv`, `.zip`, `.psd`, `.mp4` 같은 **대용량 파일**을 Git으로 버전 관리하고 싶을 때
- Git LFS를 쓰면 저장소에는 **파일 포인터**만 남기고, 실제 파일은 LFS 서버에서 관리해 저장소 크기와 클론 속도를 줄일 수 있습니다.

## 사전 준비

[Git LFS](https://git-lfs.com/) 클라이언트를 설치해야 합니다. 설치 후 아래 명령어를 사용합니다.

## 저장소에 Git LFS 초기화

해당 저장소에서 LFS를 **처음 쓸 때** 한 번 실행합니다.

```bash
git lfs install
```

- **출력 예:** `Updated Git hooks.` / `Git LFS initialized.`
- Git 훅이 갱신되고, 이 저장소에서 커밋·푸시 시 LFS가 동작하도록 설정됩니다.

## 특정 확장자(또는 패턴) LFS로 추적하기

어떤 종류의 파일을 LFS로 관리할지 지정합니다.

```bash
git lfs track ".csv"
```

- **출력 예:** `Tracking ".csv"`
- `.gitattributes`에 `*.csv filter=lfs diff=lfs merge=lfs -text` 같은 줄이 추가됩니다.
- 여러 확장자를 쓰려면 예: `git lfs track "*.zip"`, `git lfs track "*.psd"` 처럼 반복 실행하면 됩니다.

## 설정 반영하기

`.gitattributes`가 바뀌었으므로 이 변경을 커밋해야 LFS 설정이 저장소에 적용됩니다.

```bash
git add .gitattributes
git commit -m "chore: Git LFS 추적 설정 (.csv 등)"
git push origin main
```

- 이미 해당 확장자 파일이 저장소에 있다면, 그 파일들도 LFS로 옮긴 뒤 한 번 더 커밋·푸시하는 것이 좋습니다. (필요 시 `git lfs migrate` 등 문서를 참고하세요.)

## 참고

- LFS로 추적된 파일은 저장소에는 **포인터**만 들어가고, 실제 내용은 Git LFS 서버(GitHub 등 호스트의 LFS 스토리지)에 올라갑니다.
- GitHub에서는 저장소별·계정별 LFS 용량 제한이 있으므로, 공식 문서를 확인하는 것이 좋습니다.
- 추적 중인 패턴 확인: `git lfs track`
