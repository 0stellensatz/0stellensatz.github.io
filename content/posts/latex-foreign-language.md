---
title: "LaTeX: 외국어 입력시 주의 사항"
date: 2022-11-12T07:43:50+09:00
draft: false
tags: ["korean", "russian", "latex", "greek", "babel", "platex", "uplatex"]
categories: ["LaTeX"]
showToc: true
TocOpen: false
---

## `babel` 패키지 이용하기

예를 들어, 러시아어를 입력하고자 하는 경우, `babel` 패키지를 다음과 같이 불러오면, 러시아어에 적합한 설정을 얻을 수 있다.

```latex
\usepackage[russian]{babel}
```

두 개 이상의 언어를 한 문서 안에서 사용하고 싶은 경우, 다음과 같은 방법이 있다.

- `otherlanguage` 환경을 이용하는 방법.
- `\selectlanguage{}` 명령을 이용하는 방법.
- `\foreignlanguage{}{}` 명령을 이용하는 방법.

```latex
\begin{otherlanguage}{russian}
    ...
\end{otherlanguage}
```

`\selectlanguage{}` 명령을 호출한 뒤, 원하는 언어를 입력하면 된다. 원래 사용하던 언어를 입력할 때에는 다시 `\selectlanguage{}` 를 호출하여 원래의 언어를 사용하도록 설정하면 된다.

```latex
\selectlanguage{russian}
```

`\foreignlanguage{}{}` 명령은 문장의 일부분을 다른 언어로 입력하고 싶은 경우에 유용하다.

```latex
\foreignlanguage{russian}{Колмогоров}
```

## 문제 해결

### pLaTeX, upLaTeX 사용 시, 키릴 문자 혹은 그리스 문자가 전각으로 표시되는 경우

pLaTeX는 기본적으로 라틴 알파벳 이외의 문자는 '欧文'이 아닌 '和文'으로 처리한다. 키릴 문자 혹은 그리스 문자 역시 '和文'으로 처리되어 전각 표시가 기본으로 설정된다. `uplatex` 에서 `prefercjkvar` 패키지를 이용하여, 'Latin 1' 보조블럭의 처리를 '欧文'으로 처리되도록 되돌림으로서 문제를 해결할 수 있다.

```latex
\usepackage[russian,japanese]{babel}
\usepackage[prefercjkvar]{pxcjkcat}
\cjkcategory{latn1}{noncjk}
```

## 참고 문헌

- [upLaTeXでキリル文字/ギリシャ文字をまともに出力する方法](https://zenn.dev/fabon/articles/83e7ead73adace)
- [Babel によるロシア語のキリル文字フォントの概要](http://a011w.broada.jp/wbaefznh35st/latex/sample_babel_russian.pdf)
- [TeX ロシア語ハイフネーションと文字入力について](http://yasuda.homeip.net/tex/hyphen.html)
- [LaTeXでロシア語と日本語を共存させてノートがとりたい(キリル文字直打ち)](https://bobbyquine.hatenablog.com/entry/2018/10/07/200436)
