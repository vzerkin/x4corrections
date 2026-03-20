## SG54. Examples of files for discussion
_by V.Zerkin, 2026-03-20_

> **_NOTE:_** 
Files under this directory present one of possible options of final result of the WPEC Subgroup SG54.<br>
SG54 project is ongoing and data presented here are examples for discussion.


### Procedure
The selected EXFOR file is translated into an object in Python code, 
which will perform various data calculations, add/modify metadata, 
and save it as an EXFOR and/or JSON file.<br>
:warning: _Unlike other correction methods that modify data but store it in different formats, 
the approach presented here assumes the possibility of storing modified data in EXFOR format.
Since this can be confusing and even dangerous, this solution should be considered a proto-type._


### Characteristics of test cases selected from EXFOR

| &darr; Corrections : : : : : : : : : EXFOR &rarr;     | 13597002               | 21741005               | 30581004                 |
|:------------------------------------------------------|:-----------------------|:-----------------------|:-------------------------|
| :clapper: Year, 1st Author, exp.points                | 1995, S.K.Ghorai, #4   | 1966, A.Paulsen, #24   | 1980, E.Zupranska, #10   |
| :a: Automatic correction /V.Zerkin 2026/              | :white_check_mark: Yes | :x: No                 | :white_check_mark: Yes   |
| :floppy_disk: Expert's correction /K.Zolotarev 2011/  | :white_check_mark: Yes | :white_check_mark: Yes | :x: No                   |
| Corr-type: Monitor reaction data: CS(EN)              | :white_check_mark: Yes | :x: No                 | :white_check_mark: Yes   |
| Corr-type: Decay data (DECAY-DATA) for reaction       | :white_check_mark: Yes | :x: No                 | :x: No                   |
| Corr-type: Decay data (DECAY-MON) for monitor         | :white_check_mark: Yes | :x: No                 | :x: No                   |
| Corr-type: Integral of CS in energy interval          | :white_check_mark: Yes | :white_check_mark: Yes | :x: No                   |
| Recalculated: data values                             | :white_check_mark: Yes | :white_check_mark: Yes | :white_check_mark: Yes   |
| Recalculated: absolute total uncertainties            | :white_check_mark: Yes | :white_check_mark: Yes | :white_check_mark: Yes   |
| Recalculated: relative total uncertainties            | :white_check_mark: Yes | :white_check_mark: Yes | :x: No                   |
| EXFOR: Modification in BIB section                    | :white_check_mark: Yes | :white_check_mark: Yes | :white_check_mark: Yes   |
| EXFOR: Modification in DATA section                   | :white_check_mark: Yes | :white_check_mark: Yes | :white_check_mark: Yes   |
| EXFOR: Modification in COMMON section                 | :x: No                 | :white_check_mark: Yes | :x: No                   |


### Files, objects, operations, naming convention:
```
Procedure of Automatic correction for EXFOR 13597002:
  #) Input        Operation          Output               #Comment on output
  1) 13597002.x4  (parse)            [x4py]               #object in Python code "x4modif5.py"
  2) [x4py]       (reconstruct)      13597002.x4.x4       #object --> list and save as EXFOR file
  3) [x4py]       (save as JSON)     13597002.x4.json     #object --> dict and saved to JSON file
  4) [x4py]       (a1-calculations)  [x4py]               #modified object
  5) [x4py]       (update BIB-info)  [x4py]               #modified object
  6) [x4py]       (reconstruct)      13597002.x4.a1.x4    #object --> list and save as EXFOR file
  7) [x4py]       (save as JSON)     13597002.x4.a1.json  #object --> dict and saved to JSON file
Notes: 
  - the same procedure was done for Expert's correction of 13597002
  - the same procedures were done for EXFOR 21741005 and 30581004
Legend: 
  *.x4   - EXFOR file
  *.json - JSON file
  *.a1.* - file with automatic correction applied
  *.e1.* - file with expert's corrections applied
```

### Data files

| Content                 | 13597002                  | 21741005                | 30581004               |
|:------------------------|:-------------------------:|:-----------------------:|:----------------------:|
| EXFOR                   | [`x4`](13597002/13597002.x4)    | [`x4`](21741005/21741005.x4)  | [`x4`](30581004/30581004.x4) |
| Reconstructed           | [`x4`](13597002/13597002.x4.x4) : [`json`](13597002/13597002.x4.json) | [`x4`](21741005/21741005.x4.x4) : [`json`](21741005/21741005.x4.json) | [`x4`](30581004/30581004.x4.x4) : [`json`](30581004/30581004.x4.json) |
| Automatically-corrected | [`a1.x4`](13597002/13597002.x4.a1.x4) : [`a1.json`](13597002/13597002.x4.a1.json) | :no_entry: | [`a1.x4`](30581004/30581004.x4.a1.x4) : [`a1.json`](30581004/30581004.x4.a1.json) |
| Expert-corrected        | [`e1.x4`](13597002/13597002.x4.e1.x4) : [`e1.json`](13597002/13597002.x4.e1.json) | [`e1.x4`](21741005/21741005.x4.e1.x4) : [`e1.json`](21741005/21741005.x4.e1.json) | :no_entry: |

> **_NOTE:_** 
On Git files include History of Commits allowing be compare with previous one without last operations.<br>
To use this, click on [file] and click on [History] and select [Commit] from the history.<br>
For example, reconstructed EXFOR can be compared with original EXFOR file: [`13597002.x4.x4`](13597002/13597002.x4.x4),<br>
automatically-corrected EXFOR can be compared with reconstructed file: [`13597002.x4.a1.x4`](13597002/13597002.x4.a1.x4), etc.
