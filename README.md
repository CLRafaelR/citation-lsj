# The Citation Style Sheet for *Gengo Kenkyu*, Journal of the Linguistic Society of Japan (March 2022)

An unofficial Citation Style Language file for *Gengo Kenkyu*, Journal of the Linguistic Society of Japan, and its minimal working examples

See how the citation style looks like from [here](https://htmlpreview.github.io/?https://github.com/CLRafaelR/citation-lsj/blob/master/doc/test-lsj.html).
You will notice that you can simultaneously present Japanese and English references in their proper citation format.
The CSL file should be useful particularly when you produce Microsoft Word documents (`.docx`) or HTML web pages and slides out of [markdown](https://pandoc.org/MANUAL.html#pandocs-markdown) files (`.md`) using [Pandoc](https://pandoc.org/index.html)
or out of [R Markdown](https://rmarkdown.rstudio.com/) files (`.Rmd`).

# How does the CSL distinguish Japanese and English references?

The CSL detects whether a bib entry in a CSL JSON file (`.json`) has `language` field (i.e. `<if variable="language" match="any">...</if>`).
If the bib entry contains a `language` field,
the CSL processes such an entry so that the entry is presented in Japanese formatting.
Please make sure that
no bib entries for English references contain `language` field and that every bib entry for a Japanese reference has `"language": "ja-JP"`
to make the current implementation of the CSL work properly.

## `<if variable="language" match="any">...</if>` in the process of citation

<https://github.com/CLRafaelR/citation-lsj/blob/master/lsj-gengo-kenkyu.csl#L1485-L1504>

## `<if variable="language" match="any">...</if>` in the process of bibliography

<https://github.com/CLRafaelR/citation-lsj/blob/master/lsj-gengo-kenkyu.csl#L1524-L1564>

# Usage

1. Prepare different bibtex files (`.bib`) for Japanese and English references
1. In `.bib`s for Japanese documents, add `langid = {japanese}` to each reference (***This step is mandatory***)
1. Convert `.bib`s to CSL JSON files (`.json`) by using pandoc: `pandoc bib-file-name.bib -t csljson -o json-file-name.json`
1. Change the bibliography field in the YAML of `.md` file so that pandoc can refer to the .json file when pandoc generates outputs from that `.md` file.

# Disclaimer

This CSL file is ***unofficial***.
Moreover, it is still alpha version, and several notations do not strictly follow the style specified by the Journal of the Linguistic Society of Japan. Not all, but the following are known issues:

- Specific to English references
  - `&` currently concatenates multiple author names, but `and` should be used for that purpose;
  - The type of a thesis written in English is not presented
- Common in Japanese and English references
  - Presentations are ill-formatted
    - Presentation types are wrongly italicised in English references (e.g. \**Invited plenary address at the 81st Annual Meeting of the Linguistic Society of America* -> Invited plenary address at the 81st Annual Meeting of the Linguistic Society of America [**The** upright **type should be used**])
    - Presentations in Japanese are wrongly displayed as if they were proceedings papers (e.g. The event type is surrounded by white corner brackets 二重鉤括弧; \*『日本言語学会第55回大会口頭発表』 -> 日本言語学会第55回大会口頭発表). 

Please refer to [The Style Sheet for *Gengo Kenkyu*, Journal of the Linguistic Society of Japan](https://www.ls-japan.org/modules/documents/LSJpapers/e-gkstyle202207.pdf) or its Japanese version [『言語研究』執筆要項](https://www.ls-japan.org/modules/documents/LSJpapers/j-gkstyle202207.pdf).

Any bib entry that has `language` field is processed as Japanese reference as described in the previous section,
and the current CSL ignores the value of `language` filed (e.g. "ja-JP" and "en-GB").
This means that even a bib entry for British English reference that contains `"language": "en-GB"` is displayed as a Japanese reference.

# Licence

`lsj-gengo-kenkyu.csl` is a derivative of ["Chinese American Psychological Association 6th edition"](https://raw.githubusercontent.com/pulipulichen/blogger/master/project/zotero/apa_zh_pulipuli.csl) by Pudding Chen, used under Creative Commons Attribution-ShareAlike 3.0 License. `lsj-gengo-kenkyu.csl` is, therefore, licensed under Creative Commons Attribution-ShareAlike 3.0 License by Masataka Ogawa.

`test-lsj.Rmd` and `test-lsj.html` are licensed under  Attribution-NonCommercial-ShareAlike 4.0 International.

The other files are licensed under CC0 1.0 Universal.
