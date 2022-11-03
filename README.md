# The Citation Style Sheet for *Gengo Kenkyu*, Journal of the Linguistic Society of Japan (March 2022)

A Citation Style Language file for *Gengo Kenkyu*, Journal of the Linguistic Society of Japan, and its minimal working examples

# Usage

1. Prepare different bibtex files (`.bib`) for Japanese and English references
1. In `.bib`s for Japanese documents, add `langid = {japanese}` to each reference
1. Convert `.bib`s to CSL JSON files (`.json`) by using pandoc: `pandoc bib-file-name.bib -t csljson -o json-file-name.json`
1. Change the bibliography field in the YAML of `.md` file so that pandoc can refer to the .json file when pandoc generates outputs from that `.md` file.

# Licence

`lsj-gengo-kenkyu.csl` is a derivative of "Chinese American Psychological Association 6th edition" by Pudding Chen, used under Creative Commons Attribution-ShareAlike 3.0 License. `lsj-gengo-kenkyu.csl` is licensed under Creative Commons Attribution-ShareAlike 3.0 License by Masataka Ogawa.

`test-lsj.Rmd` and `test-lsj.html` are licensed under  Attribution-NonCommercial-ShareAlike 4.0 International.

The other files are licensed under CC0 1.0 Universal.
