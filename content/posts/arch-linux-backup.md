---
title: "Arch Linux Backup"
date: 2022-11-12T07:24:46+09:00
draft: false
tags: ["korean", "arch linux", "linux"]
categories: ["Linux"]
showToc: true
TocOpen: false
---

다음과 같은 방법으로 Arch Linux 시스템을 주기적으로 백업한다.

- pacman 데이터베이스를 백업한다.
- pacman 패키지 목록을 백업한다.
- 암호화된 디스크에 rsync를 이용하여 홈 디렉토리를 차분 백업한다.

## pacman 데이터베이스, pacman 패키지 목록 백업

시스템에 설치된 패키지의 목록을 텍스트 파일로 저장하려면:

```
pacman -Qqe > pkglist-$(date +%F).txt
```

주어진 패키지 목록으로부터 저장소에서 동기화 가능한 패키지를 선별하여 설치하려면:

```
pacman -S --needed $(comm -12 <(pacman -Slq | sort) <(sort pkglist.txt))
```

저장소 외부로부터 설치된 패키지의 목록을 텍스트 파일로 저장하려면:

```
pacman -Qqem > pkglist-foreign-$(date +%F).txt
```

pacman의 데이터베이스를 백업하려면:

```
tar -cjvf pacman_database-$(date +%F).tar.bz2 /var/lib/pacman/local
```

이를 복원하려면, `pacman_database.tar.bz2` 파일을 `/` 으로 옮긴 뒤, 다음을 실행한다.

```
tar -xjvf pacman_database.tar.bz2
```

## rsync를 이용한 홈 디렉토리의 백업

미리 지정해 둔 리스트 `/path/to/.rsync-exclusion` 에 포함된 디렉토리를 제외하여, 홈 디렉토리를 현재 디렉토리로 rsync 하려면:

```
rsync -aAHXvh --exclude-from=/path/to/.rsync-exclusion $HOME . --delete-after
```

'dry run' 을 원한다면 `-n` 옵션을 추가하면 된다.

```
rsync -aAHXvnh --exclude-from=/path/to/.rsync-exclusion $HOME . --delete-after
```

제외 리스트 `/path/to/.rsync-exclusion` 의 예시:

```
.thumbnails/*
.cache/mozilla/*
.cache/chromium/*
```

복원할 때에는 위 명령에서 원본과 목적지의 경로를 반대로 하여 실행하면 된다.
