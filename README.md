# 작업 방법

## 브랜치 구조

기본적으로 Gitflow 규칙을 따른다.

- `main` — 배포/제출 브랜치. **직접 건드리지 않음.** develop이 머지되면 자동으로 반영됨.
- `develop` — 통합 브랜치. 모든 작업이 여기로 모임.
- `feature/*` — 각자 기능 작업 브랜치.

## 작업 순서
```bash
# 1. 최신 develop에서 작업 브랜치 생성
git checkout develop
git pull
git checkout -b feature/기능이름

# 2. 작업 후 커밋 & push
git add .
git commit -m "feat: 설명"
git push -u origin feature/기능이름

# 3. GitHub에서 feature/기능이름 → develop 로 PR 생성
```

## PR 규칙
PR을 올리면 두 가지 검사가 자동으로 돌고, **둘 다 통과해야 머지 가능**:
- **Verify PR Checklist** : PR 본문의 체크박스(`- [ ]`)를 전부 `- [x]`로 체크해야 통과.

    Reviewer에게 확인를 요청하는 내용들을 적는 부분이다. Reviewer는 해당 포인트들 위주로 코드를 검토한다.

- **Run Tests** : `python tests/test.py` 실행. (테스트 코드를 채우면 자동으로 검증됨)

## Merge
- PR이 `develop`에 머지되면 → `main`이 자동으로 같은 커밋으로 업데이트됨.
- `main`에는 아무도 직접 커밋하지 않음. (직접 커밋하면 자동 반영이 깨짐)
