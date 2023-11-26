# Usage

To produce a PDF, specify an output file with a .pdf extension
 ([Creating PDF](https://pandoc.org/chunkedhtml-demo/2.4-creating-a-pdf.html))

**Topic**

1. [Margins](#margins)
2. [Newpage](#newpage)
3. [Font](#font)
    1. [Font Size](#size)
4. [Table of Contents](#table-of-contents)

---

## Margins

By default the margins are pretty large. To optionally change the margin.
 `-V geometry:margin=1in`

```bash
pandoc input.md -o output.pdf -V geometry:margin=1in
```

---

## Newpage

Newpage between each markdown files. `\break`

```bash
sed -se '$a\\\break'  *.md | pandoc -o output.pdf -V geometry: margin=1in  --pdf-engine=xelatex
```

---

## Font

Change font to match missing Unicode character. `-V mainfont=`

```bash
 pandoc -o output.pdf -V geometry: margin=1in --pdf-engine=xelatex -V mainfont='DejaVuSerif' *.md
```

### Size

Change font size. `--variable fontsize=`

```bash
```bash
pandoc nov_26.md -o output.pdf -V geometry:margin=1in --variable fontsize=10pt --variable fontfamily=utopia --variable linkcolor=blue --pdf-engine=xelatex -f markdown-implicit_figures -s
```

---

## Table of contents

Include table of contents from heading. `--toc`

```bash
pandoc nov_26.md -o output.pdf --toc -V geometry:margin=1in pdf-engine=xelatex
```
