# LectureNotes

이 문서는 `main` 브랜치를 기준으로, `worktree`를 이용해 독립 작업 브랜치를 만들고 병합하는 기본 실습 절차를 정리한 가이드입니다.

## 0) 핵심 개념

- 브랜치(branch): 커밋 이력의 작업 줄기
- 워크트리(worktree): 실제 파일 작업 폴더
- 한 저장소에서 여러 브랜치를 동시에 작업하려면 `worktree`를 사용

## 1) main 최신화

아래 명령은 메인 작업 폴더(`LectureNotes`)에서 실행:

```bash
cd ~/project_claude/LectureNotes
git checkout main
git pull origin main
git status -sb
```

설명:
- `main` 브랜치로 이동
- 원격 `origin/main` 최신 변경 반영
- 현재 상태 확인

## 2) 새 worktree + 새 브랜치 생성

```bash
git worktree add ../notion_branch -b notion_notes
git worktree list
```

설명:
- `../notion_branch` 폴더 생성
- `notion_notes` 브랜치 생성
- 새 폴더를 `notion_notes` 브랜치에 연결

## 3) 새 worktree에서 작업 및 커밋

```bash
cd ../notion_branch
git status -sb

# 파일 수정 (예: README.md)
nano README.md

git add .
git commit -m "Add notion notes draft"
```

설명:
- `notion_branch`에서는 `notion_notes` 브랜치 커밋이 쌓임
- `main`에는 아직 반영되지 않음

## 4) 원격 브랜치로 push

```bash
git push -u origin notion_notes
```

설명:
- 원격에 `origin/notion_notes` 생성 또는 업데이트
- `-u`는 upstream 설정 (다음부터 `git push`, `git pull`만으로 동기화 가능)

참고:
- SSH timeout이 나면 원격 URL을 HTTPS로 변경

```bash
git remote set-url origin https://github.com/Sehyeogkim/LectureNotes.git
git push -u origin notion_notes
```

## 5) main으로 병합 (로컬 merge 실습)

메인 작업 폴더로 돌아가서 실행:

```bash
cd ~/project_claude/LectureNotes
git checkout main
git pull origin main
git merge --no-ff notion_notes
```

설명:
- `notion_notes`의 변경을 `main`에 병합
- `--no-ff`는 merge commit을 명시적으로 남겨 이력을 학습하기 좋게 만듦

## 6) 충돌(conflict) 발생 시 해결

충돌이 나면:

```bash
git status
nano README.md
```

파일에서 아래 마커를 정리:

- `<<<<<<< HEAD`
- `=======`
- `>>>>>>> notion_notes`

원하는 최종 내용만 남긴 뒤:

```bash
git add README.md
git commit -m "Resolve merge conflict in README"
```

## 7) main 반영 완료

```bash
git push origin main
git log --oneline --decorate --graph -n 10
```

설명:
- 병합 결과를 원격 `main`에 반영
- 그래프로 브랜치 분기/병합 구조 확인

## 8) 실습 후 정리 (선택)

더 이상 `notion_notes` worktree가 필요 없으면:

```bash
git worktree remove ../notion_branch
```

브랜치까지 정리하려면:

```bash
git branch -d notion_notes
git push origin --delete notion_notes
```
