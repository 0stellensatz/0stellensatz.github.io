---
title: "Git: 메인 브랜치 이름 변경하기"
date: 2022-11-29T01:45:18+09:00
draft: false
tags: ["git", "linux", "github"]
categories: ["Git"]
showToc: true
TocOpen: false
---

변경 전 브랜치의 이름을 `master`, 변경 후 브랜치의 이름을 `main` 으로 둔다. `master` 의 커밋을 모두 포함하는 새 브랜치 `main` 을 먼저 생성한다.

```bash
git branch -m master main
```

`main` 브랜치를 원격 저장소에 푸시한다.

```bash
git push -u origin main
```

HEAD가 `main` 브랜치를 향하도록 설정한다.

```bash
git symbolic-ref refs/remotes/origin/HEAD refs/remotes/origin/main
```

설정을 완료했다면, `git branch -a`로 HEAD를 확인한다. GitHub 저장소의 경우, 저장소 설정에서 메인 브랜치를 업데이트한다.

작업을 마친 후에는 원격 저장소에서 `master` 브랜치를 제거해도 된다.

```bash
git push origin --delete master
git branch -a
```