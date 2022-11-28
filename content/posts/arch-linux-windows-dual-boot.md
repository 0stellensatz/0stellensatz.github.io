---
title: "Arch Linux: Windows 듀얼 부팅 시의 주의 사항"
date: 2022-11-29T01:53:24+09:00
draft: false
tags: ["windows", "linux"]
categories: ["Linux"]
showToc: true
TocOpen: false
---

## Fast Startup 관련

Linux 와 Windows 를 같은 디스크에 설치하여 듀얼 부팅하는 경우, Windows 8, 10, 11 의 Fast Startup 기능은 EFI 파티션의 손상을 일으켜, 다시 Windows 로 부팅할 수 없거나, Windows 업데이트를 완료할 수 없는 문제를 유발할 수 있다. 특히, Fast Startup 을 비활성화 한 경우에도, Windows 업데이트 후 Fast Startup 이 다시 활성화된 사례가 보고되는 만큼 각별한 주의가 필요하다.

## 시계 관련

Windows 와 Linux 양측 모두 localtime 대신 UTC 를 사용하도록 설정한다. Windows 의 경우, 다음과 같이 레지스트리를 설정한다. (관리자 권한 필요.)

```cmd
reg add "HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation" /v RealTimeIsUniversal /d 1 /t REG_DWORD /f
```

Arch Linux 의 경우, `timedatectl` 을 실행한다.

```shell
timedatectl set-local-rtc 0
```

## 참고 문헌

- [Turn On or Off Fast Startup in Windows 11](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)
- [Warning When Multi-booting a UEFI System with Windows 10 (Fast Startup): when in doubt, reboot…](https://tedstechshack.com/2017/07/03/warning-multi-booting-uefi-system-windows-10-fast-startup-doubt-reboot/)
