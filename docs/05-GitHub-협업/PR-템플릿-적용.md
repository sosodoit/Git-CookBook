# PR 템플릿 적용하기

**Pull Request** 생성 시 본문에 기본 양식이 채워지게 하는 방법입니다.

## 상황

- PR마다 "뭘 적지?" 없이 **변경 요약·관련 이슈·체크리스트**가 나오게 하고 싶을 때
- 팀 규칙으로 PR에 꼭 넣을 항목을 통일하고 싶을 때

## 꼭 필요한 것

- 파일 하나: `.github/PULL_REQUEST_TEMPLATE.md`
- 항목: **변경 사항**, **관련 이슈**, **체크리스트** (3가지만 있으면 충분)

## 템플릿 예시 (필수 항목만)

파일: `.github/PULL_REQUEST_TEMPLATE.md`

```markdown
## 변경 사항
- 

## 관련 이슈
- closes #

## 체크리스트
- [ ] 동작 확인함
- [ ] 문서/주석 필요 시 반영함
```

- `closes #123`처럼 이슈 번호를 넣으면 PR 병합 시 해당 이슈가 자동으로 닫힙니다.

**반영**

```bash
git add .github/PULL_REQUEST_TEMPLATE.md
git commit -m "docs: PR 템플릿 추가"
git push origin main
```

이후 **New pull request** 시 본문에 위 내용이 기본으로 채워집니다.

## 언제 수정하면 좋을지

| 상황 | 수정 예시 |
|------|------------|
| 리뷰 전 체크리스트가 생김 | 체크리스트에 "자기 리뷰 완료", "테스트 추가 여부" 등 항목 추가 |
| 관련 이슈를 안 쓸 때가 많음 | "관련 이슈"를 "(없으면 비우기)" 등으로 안내 문구 추가 |
| 팀에서 스크린샷/영상 필수로 함 | "## 스크린샷 또는 동작 영상" 섹션 추가 |
| 여러 PR 유형(기능/버그/문서)을 나누고 싶음 | `.github/PULL_REQUEST_TEMPLATE/` 폴더에 `default.md`, `bugfix.md` 등 분리 (고급) |

## 참고

- `closes #n`, `fixes #n` 모두 PR 병합 시 이슈를 자동 close 합니다.
- [GitHub: Pull request templates](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/creating-a-pull-request-template-for-your-repository)
