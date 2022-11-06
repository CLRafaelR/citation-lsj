# The Citation Style Language (CSL) for *Gengo Kenkyu*, Journal of the Linguistic Society of Japan (March 2022)

An unofficial Citation Style Language file for *Gengo Kenkyu*, Journal of the Linguistic Society of Japan, and its minimal working examples

![](https://github.com/CLRafaelR/citation-lsj/blob/master/doc/output-example.png)

See how the citation style looks like from [here](https://htmlpreview.github.io/?https://github.com/CLRafaelR/citation-lsj/blob/master/doc/test-lsj.html).
You will notice that you can simultaneously present Japanese and English references in their proper citation format.
For instance, the names of multiple authors of a Japanese reference are delimited by `・` and those for an English reference are dilimited by `, ` in a same document that you produce using this CSL.
The CSL file is useful when you produce Microsoft Word documents (`.docx`), HTML web pages and slides, and even PDF documents using LaTeX (including `beamer` slides).
You may write your manuscripts in [markdown](https://pandoc.org/MANUAL.html#pandocs-markdown) files (`.md`) or [R Markdown](https://rmarkdown.rstudio.com/) files (`.Rmd`)
and process them using [Pandoc](https://pandoc.org/index.html) to enjoy the beautiful bibliographic typesetting that the CSL offers.

# How does the CSL distinguish Japanese and English references?

The CSL detects whether a bib entry in a CSL JSON file (`.json`) has `language` field (i.e. `<if variable="language" match="any">...</if>`).
If the bib entry contains a `language` field,
the CSL processes such an entry so that the entry is presented in Japanese formatting.
Please make sure that
no bib entries for English references contain `language` field and that every bib entry for a Japanese reference has `"language": "ja-JP"`
to make the current implementation of the CSL work properly.

## `<if variable="language" match="any">...</if>` in the process of citation

https://github.com/CLRafaelR/citation-lsj/blob/master/lsj-gengo-kenkyu.csl#L1485-L1504

## `<if variable="language" match="any">...</if>` in the process of bibliography

https://github.com/CLRafaelR/citation-lsj/blob/master/lsj-gengo-kenkyu.csl#L1524-L1564

# Usage

1. Make sure that you have installed [Pandoc](https://pandoc.org/installing.html)
2. Prepare different bibtex files (`.bib`) for Japanese and English references
    - See how `.bib` files look like from [the `.bib` files in this repository](https://github.com/CLRafaelR/citation-lsj/tree/master/bib)
3. Add `langid = {japanese}` to each reference in `.bib`s for Japanese documents (***This step is mandatory***)
    - See [`lsj-ja.bib` in this repository](https://github.com/CLRafaelR/citation-lsj/blob/master/bib/lsj-ja.bib) for the details
4. Convert `.bib`s to CSL JSON files (`.json`) by using Pandoc by typing `Pandoc bib-file-name.bib -t csljson -o json-file-name.json` in the command line (e.g. Windows [PowerShell](https://learn.microsoft.com/ja-jp/powershell/scripting/discover-powershell) or Mac [Terminal](https://support.apple.com/ja-jp/guide/terminal/welcome/mac))
    - See [`json` folder in this repository](https://github.com/CLRafaelR/citation-lsj/tree/master/json) to know how CSL JSON files look like
5. Write manuscripts in `.md` (or `.Rmd`) files
    - **Markdown is much easier to understand than any other mark-up languages such as HTML and LaTeX**.
    - See [the documentation](https://pandoc.org/MANUAL.html#pandocs-markdown) to familiarise yourself with Pandoc's markdown notation
    - e.g.
      - [citing references](https://pandoc.org/MANUAL.html#citation-syntax); just like `@mention`!
      - [marking section headers](https://pandoc.org/MANUAL.html#atx-style-headings)
      - [*italicising/emphasising* and/or **boldfacing** texts](https://pandoc.org/MANUAL.html#emphasis)
      - commenting out a part of texts using an HTML comment (`<!-- -->`)
6. Add `bibliography` field in the YAML of `.md` file (i.e. the area surrounded by `---`; see [this line of `test-lsj.Rmd`](https://github.com/CLRafaelR/citation-lsj/blob/e1b95ab32f0870de32b9f8db96bfc73c2358d623/doc/test-lsj.Rmd#L14) for instance) so that Pandoc can refer to .json files when Pandoc generates outputs from that `.md` file
7. Generate the output from your manuscripts using Pandoc
    - e.g. if you write `.md` files to render them into a Word file (`.docx`), type `pandoc manuscript.md -t docx -o output.docx` in the command line
    - e.g. if you write `.Rmd` files, just *knit* your `.Rmd` files to render them into what you want to get! (See [`doc` folder in this repository](https://rmarkdown.rstudio.com/docs/))

You can also test how the CSL works by *knitting* [`test-lsj.Rmd` in this repository](https://github.com/CLRafaelR/citation-lsj/blob/master/doc/test-lsj.Rmd).

# Disclaimer

This CSL file is ***unofficial***.
Moreover, several notations do not strictly follow the style specified by the Journal of the Linguistic Society of Japan. Not all, but the following are known issues:

- Common in Japanese and English references
  - Presentations are ill-formatted
    - Presentation types are incorrectly italicised in English references (e.g. \**Invited plenary address at the 81st Annual Meeting of the Linguistic Society of America* -> Invited plenary address at the 81st Annual Meeting of the Linguistic Society of America [**The** upright **type should be used**])
    - Presentations in Japanese are incorrectly displayed as if they were proceedings papers (e.g. The event type is surrounded by white corner brackets 二重鉤括弧; \*『日本言語学会第55回大会口頭発表』 -> 日本言語学会第55回大会口頭発表).

Please refer to [The Style Sheet for *Gengo Kenkyu*, Journal of the Linguistic Society of Japan](https://www.ls-japan.org/modules/documents/LSJpapers/e-gkstyle202207.pdf) or its Japanese version [『言語研究』執筆要項](https://www.ls-japan.org/modules/documents/LSJpapers/j-gkstyle202207.pdf).

Any bib entry that has `language` field is processed as Japanese reference as described in the previous section,
and the current CSL ignores the value of `language` filed (e.g. "ja-JP" and "en-GB").
This means that even a bib entry for British English reference that contains `"language": "en-GB"` is displayed in the format for Japanese references.

# Licence

`lsj-gengo-kenkyu.csl` is a derivative of ["Chinese American Psychological Association 6th edition"](https://raw.githubusercontent.com/pulipulichen/blogger/master/project/zotero/apa_zh_pulipuli.csl) by Pudding Chen, used under Creative Commons Attribution-ShareAlike 3.0 License. `lsj-gengo-kenkyu.csl` is, therefore, licensed under Creative Commons Attribution-ShareAlike 3.0 License by Masataka Ogawa.

`test-lsj.Rmd`, `test-lsj.docx`, `test-lsj.html`, and `test-lsj.pdf` are licensed under  Attribution-NonCommercial-ShareAlike 4.0 International.

The other files are licensed under CC0 1.0 Universal.
