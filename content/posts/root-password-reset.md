---
title: "Linux: root 패스워드 초기화"
date: 2022-11-12T06:13:14+09:00
draft: false
tags: ["korean", "grub", "linux"]
categories: ["Linux"]
showToc: true
TocOpen: false
---

우선, 다음 내용을 GRUB의 kernel 라인, 혹은 GRUB2의 linux 라인에 추가한 뒤, 재부팅한다.

```
init=/bin/bash
```

재부팅 후, 파일시스템을 다시 마운트한 뒤, `passwd`를 이용하여 root 패스워드를 초기화한다.

```
mount -o remount,rw /
passwd
```

## 참고 문헌

- [Why is resetting the root password allowed?](https://unix.stackexchange.com/questions/355053/why-is-resetting-the-root-password-allowed)
