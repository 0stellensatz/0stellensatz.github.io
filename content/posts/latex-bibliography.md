---
title: "LaTeX: 참고 문헌 리스트 작성하기"
date: 2022-11-12T07:40:41+09:00
draft: false
tags: ["korean", "latex", "bibtex"]
categories: ["LaTeX"]
showToc: true
TocOpen: false
---

BiBTeX을 사용하지 않는 경우에는 `enumerate` 환경과 유사한 `thebibliography`환경을 사용하여 참고 문헌 리스트를 작성할 수 있다.

```latex
\begin{thebibliography}{9}
    \bibitem{cite1}
    ...
    \bibitem{cite2}
    ...
\end{thebibliography}
```

BiBTeX을 사용하는 경우에는, 참고 문헌 리스트를 삽입하고 싶은 위치에, 원하는 BiBTeX 파일의 경로와 함께 다음을 입력하면 된다.

```latex
\bibliographystyle{plain}
\bibliography{path/to/file.bib}
```
