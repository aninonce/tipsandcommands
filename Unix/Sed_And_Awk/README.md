# Cut

<a id="toc"></a>
## Table of contents

1. [Version](#version)

<a id="version"></a>
### Version [^](#toc)
Use commands    cut --version

<details>
    <summary>Sample output: </summary>

```text
cut --version

    cut (GNU coreutils) 8.30
    Copyright (C) 2018 Free Software Foundation, Inc.
    License GPLv3+: GNU GPL version 3 or later <https://gnu.org/licenses/gpl.html>.
    This is free software: you are free to change and redistribute it.
    There is NO WARRANTY, to the extent permitted by law.

    Written by David M. Ihnat, David MacKenzie, and Jim Meyering.
```
</details>

<a id="cut_examples"></a>
### CUT Examples [^](#toc)

<details>
    <summary>Examples: </summary>

```text

    cut -b <position> / <range>  <file>   // E.g. cut -b 1; cut -b 1,3,4; cut -b 1-5 
    cut -c <position> / <range>  <file>   // E.g. cut -c 1; cut -c 1,3,4; cut -c 1-5 ;; Is mostly preferred over `cut by byte` a character can have more than 1 byte
    cut -d '<delimiter>' -f <position> / <range>  <file>      // use any delimiter. E.g. cut -d ',' -f 1,5 <file>
    cut -d '<delimiter>' -f <position> / <range>  <file> --output-delimiter='<delimiter>'       // E.g.  cut -d ';' -f 1,3,7 --output-delimiter=' ' <file>
    cut --complement -c <position> / <range>  <file>    // first do the cut operation and then do the complement of the same and write that to ouput
    
```
</details>