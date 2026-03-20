## Correcting EXFOR data in C4, C5, X5, X4Pro
_by V.Zerkin, 2011-2026_

### Introduction
A lot of experimental data presented in EXFOR were measured as ratio to a monitor, but presented in absolute values.
EXFOR files often include either monitor data or reference to monitor data published by authors.
This information (together with decay data used for calculations) may change if experiment was performed years ago.
Official EXFOR Library contains data exaclly as published by authors,
but evaluators may need to re-calculate data accroding to modern standards,
or introduce their corrections to the data values and/or uncetrainties.
The systems implementing various data modifications are known as "Correction Systems".

### EXFOR data corrections
The IAEA-NDS EXFOR data correction system (V.Zerkin, 2011-2023) is presented in several EXFOR tools:
- **[C4](C4/)/[C5](C5/)** - EXFOR data translated to computational form.<br>
  EXFOR Web-retrieval system offers predefined automatic, expert 
  corrections in analytical form as well as possibility for user 
  to edit proposed corrections and introduce own corrections,
  processing data on the fly, checking mode presenting data 
  uncertainties before and after modification, plotting data, 
  visualization of old and new monitor data, etc. 
  The tool working with C4 is more interactive, while the corrected 
  C5 data are intended to be imported into local software systems
- **[X5](X5/)** - comprehensive EXFOR in JSON.<br>
  Files presenting EXFOR + relevant information from Dictionaries +
  data in original and computational form +
  data needed for renormalization.
- **[X4Pro](X4Pro/)** - universal, fully relational EXFOR database. Professional edition.<br>
  Presents EXFOR as relational database (SQLite), which also includes
  C5 and X5 data. Delivered with examples of codes in SQL, Fortran 
  and Python implementing simple and complex operations on EXFOR and ENDF data.
- **[SG54](SG54/)** - project with WPEC Subgroup SG54 *(under development, since 2025)*.<br>
  Presents EXFOR file as an object in Python/JavaScript program alowing
  various data re-calculations, to add/modify meta-data, to store it
  as EXFOR and/or JSON file, etc.
  > **_NOTE:_** 
  SG54 project is ongoing and data examples presented here are for discussion
  
| Feature                           | C4/Web                 | C5/Web                 | X5-JSON                | X4Pro-db               |
|:----------------------------------|:-----------------------|:-----------------------|:-----------------------|:-----------------------|
| Metadata in the file              | :x: No                 | :white_check_mark: Yes | :white_check_mark: Yes | :white_check_mark: Yes |
| Interactive (via Web-forms)       | :white_check_mark: Yes | :x: No                 | :x: No                 | :x: No                 |
| Automatic-corrections             | :white_check_mark: Yes | :white_check_mark: Yes | :white_check_mark: Yes | :white_check_mark: Yes |
| Expert/User-corrections           | :white_check_mark: Yes | :x: No                 | :x: No                 | :white_check_mark: Yes |
| Checking-mode (for every point)   | :white_check_mark: Yes | :x: No                 | :x: No                 | :white_check_mark: Yes |
| Plotting data                     | :white_check_mark: Yes | :x: No                 | :white_check_mark: Yes | :white_check_mark: Yes |
| Plotting monitors                 | :white_check_mark: Yes | :x: No                 | :x: No                 | :x: No                 |
| Includes monitor data to the file | :x: No                 | :white_check_mark: Yes | :white_check_mark: Yes | :white_check_mark: Yes |
| Correction-algorithm in the file  | :x: No                 | :white_check_mark: Yes | :white_check_mark: Yes | :white_check_mark: Yes |
| Exampes of codes                  | :x: No                 | :x: No                 | :white_check_mark: Yes | :white_check_mark: Yes |

### Examples of data files

| Content                | 13597002                  | 21741005                | 30581004               |
|:-----------------------|:--------------------------|:------------------------|:-----------------------|
| **EXFOR**              | [`x4`](C4/13597002.x4)    | [`x4`](C4/21741005.x4)  | [`x4`](C4/30581004.x4) |
| **C4-data**            | [`c4`](C4/13597002.c4)    | [`c4`](C4/21741005.c4)  | [`c4`](C4/30581004.c4) |
| **C5-data**            | [`c5`](C5/13597002.c5)    | [`c5`](C5/21741005.c5)  | [`c5`](C5/30581004.c5) |
| **X5-JSON**            | [`x5`](X5/13597002.x5)    | [`x5`](X5/21741005.x5)  | [`x5`](X5/30581004.x5) |
| Automatic-corrections  | [`auto1.corr`](C4/13597002.auto1.corr)           | :no_entry:             | [`auto1.corr`](C4/30581004.auto1.corr) |
| Expert's-corrections   | [`expert1.corr`](C4/13597002.expert1.corr)       | [`expert1.corr`](C4/21741005.expert1.corr) | :no_entry:         |
| C4-Calculation details | [`auto1.datamod`](C4/13597002.auto1.datamod)     | :no_entry:             | [`auto1.datamod`](C4/30581004.auto1.datamod) |
| C4-data corrected      | [`auto1.c4`](C4/13597002.auto1.c4)               | :no_entry:             | [`auto1.c4`](C4/30581004.auto1.c4)   |
| C4-Calculation details | [`expert1.datamod`](C4/13597002.expert1.datamod) | [`expert1.datamod`](C4/21741005.expert1.datamod) | :no_entry: |
| C4-corrected           | [`expert1.c4`](C4/13597002.expert1.c4)           | [`expert1.c4`](C4/21741005.expert1.c4) | :no_entry:           |
| C5-data corrected      | [`auto1.c5`](C5/13597002.auto1.c5)               | :no_entry:     | [`auto1.c5`](C5/30581004.auto.c5)            |
| X4Pro-retrieved        | [`x4pro.json`](X4Pro/expert1-orig.json)          | :no_entry:     | [`x4pro.json`](X4Pro/auto1-orig.json)        |
| X4Pro-corrected        | [`expert1.x4pro`](X4Pro/expert1-corr.json) : [`png`](X4Pro/expert1.png) | :no_entry: | [`auto1.x4pro`](X4Pro/auto1-corr.json) : [`png`](X4Pro/auto1.png) |
| **SG54** | [`x4`](SG54/13597002/13597002.x4.x4) [`json`](SG54/13597002/13597002.x4.json) | [`x4`](SG54/21741005/21741005.x4.x4) [`json`](SG54/21741005/21741005.x4.json) | [`x4`](SG54/30581004/30581004.x4.x4) [`json`](SG54/30581004/30581004.x4.json) |
| SG54-auto-corrected   | [`a1.x4`](SG54/13597002/13597002.x4.a1.x4) :: [`a1.json`](SG54/13597002/13597002.x4.a1.json) | :no_entry: | [`a1.x4`](SG54/30581004/30581004.x4.a1.x4) :: [`a1.json`](SG54/30581004/30581004.x4.a1.json) |
| SG54-expert-corrected | [`e1.x4`](SG54/13597002/13597002.x4.e1.x4) :: [`e1.json`](SG54/13597002/13597002.x4.e1.json) | [`e1.x4`](SG54/21741005/21741005.x4.e1.x4) :: [`e1.json`](SG54/21741005/21741005.x4.e1.json) | :no_entry: |
### Links

* [NRDC](https://nds.iaea.org/nrdc/) International Network of Nuclear Reaction Data Centres 
* [IAEA-NDS](https://nds.iaea.org/) International Atomic Energy Agency, Nuclear Data Service 
* [EXFOR](https://nds.iaea.org/exfor/) IAEA-NDS Web-Retrieval System 
* [X4Pro-mini](https://github.com/vzerkin/x4pro) - X4Pro on GitHub (with mini-database)
* [X4Pro](https://nds.iaea.org/cdroms/#x4pro1) - download previous version of X4Pro from IAEA-NDS site
* X4Pro [reference paper](https://doi.org/10.1051/epjconf/202328414015),
  Nuclear-Data Conference ND2022: [presentation](https://indico.frib.msu.edu/event/52/contributions/875/attachments/487/2289/nd2022-zerkin1.pdf)
* Automatic renormalization in X4Pro [presentation](https://nds.iaea.org/nrdc/wksp_2022/present/zerkin5.pdf) on EXFOR-Workshop-2022
* :red_circle: Youtube [Video](https://www.youtube.com/watch?v=n9P1Z134WYM)-2013:
  Automatic re-normalization of EXFOR data under Web retrieval system
* Program [X4TOC4](https://nds.iaea.org/nrdc/nrdc_doc/iaea-nds-0080-200103.pdf), D.E.Cullen, A.Trkov, 2001
* Program [x4toc5](https://doi.org/10.61092/iaea.gxra-p855), V.Zerkin, 2024
* General-purpose EXFOR-driver, V.Zerkin, [presentation](https://nds.iaea.org/nrdc/nrdc_2025/present/zerkin1.pdf) on NRDC-2025 Meeting
