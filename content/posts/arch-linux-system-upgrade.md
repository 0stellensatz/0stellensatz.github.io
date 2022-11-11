---
title: "Arch Linux: 시스템 업그레이드"
date: 2022-11-12T06:26:54+09:00
draft: false
tags: ["korean", "arch linux", "linux"]
categories: ["Linux"]
showToc: true
TocOpen: false
---

[ArchWiki](https://wiki.archlinux.org/index.php/System_maintenance#Upgrading_the_system) 내용의 요약:

1. [시스템 백업](/posts/arch-linux-backup): 우선 시스템을 백업한다.
2. 공지사항 확인: 업그레이드 내용과 관련한 공지사항과 포럼 게시물 등을 확인한다. 알려진 문제점이 있는지 미리 확인한다.
3. 업그레이드: `pacman -Syu` 혹은 `yay -Syu` 을 실행한다.
4. 추가 조치: `pacman` 이 출력한 메시지를 확인하고, 이에 따라 필요한 추가 조치를 취한다. 업데이트 도중 오류가 발생했다면, 우선 `/var/log/pacman.log`를 확인한다.

`pacman -Qtd` 를 실행하여 'orphaned' 로 표시된 패키지를 확인할 수 있다. 저장소에 더 이상 존재하지 않는 패키지는 `pacman -Qm` 을 실행하여 확인할 수 있다.

`yay`를 사용하는 경우, `yay -Yc` 를 실행하여 더 이상 필요하지 않은 의존성 패키지를 제거할 수 있다. `yay -Sc` 를 이용하여 pacman과 yay의 캐시 파일을 삭제할 수 있다.

## 참고 문헌

- [ArchWiki: System maintenance](https://wiki.archlinux.org/index.php/System_maintenance)
- [ArchWiki: Pacman#Upgrading_packages](https://wiki.archlinux.org/title/Pacman#Upgrading_packages)
