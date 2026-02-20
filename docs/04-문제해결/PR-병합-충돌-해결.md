# PR 병합 충돌 해결

Pull Request 병합 시 충돌(merge conflict)이 났을 때 참고할 수 있는 안내입니다.

## 상황

같은 파일의 같은 부분을 여러 브랜치에서 수정했을 때, 병합 시 Git이 자동으로 합치지 못하고 충돌로 표시합니다.

## 기본 흐름

1. GitHub(또는 사용 중인 플랫폼)에서 충돌이 난 PR을 확인합니다.
2. 로컬에서 대상 브랜치(예: `main`)를 최신으로 가져옵니다.
   ```bash
   git checkout main
   git pull origin main
   ```
3. 작업 브랜치로 돌아가 main을 merge합니다.
   ```bash
   git checkout 내브랜치
   git merge main
   ```
4. 충돌이 난 파일을 열어 `<<<<<<<`, `=======`, `>>>>>>>` 표시를 제거하고, 원하는 내용으로 수정합니다.
5. 수정한 파일을 스테이징 후 커밋·푸시합니다.
   ```bash
   git add .
   git commit -m "resolve merge conflict"
   git push origin 내브랜치
   ```

## 참고

- [충돌 발생 시 상세 예시](https://chaeyoung2.tistory.com/61) (외부 링크)
