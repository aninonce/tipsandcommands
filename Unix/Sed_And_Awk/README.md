# SED (“Non-interactive” stream-oriented editor) & AWK (Pattern matching programming language)

<a id="toc"></a>
## Table of contents

1. [Version](#version)

<a id="version"></a>
### Version [^](#toc)
Use commands    sed --version
                awk --version
<details>
    <summary>Sample output: </summary>

```text
sed --version

    Written by Jay Fenlason, Tom Lord, Ken Pizzini,
    Paolo Bonzini, Jim Meyering, and Assaf Gordon.
    GNU sed home page: <https://www.gnu.org/software/sed/>.
    .
    .

awk --version

    GNU Awk 5.0.1, API: 2.0 (GNU MPFR 4.0.2, GNU MP 6.2.0)
    Copyright (C) 1989, 1991-2019 Free Software Foundation.
```
</details>

<a id="understanding"></a>
### Understanding [^](#toc)

<details>
    <summary>Information: </summary>

```text
    In sed and awk, each instruction has two parts: a pattern and a procedure. The pattern is a regular expression delimited with slashes (/). 
    A procedure specifies one or more actions to be performed.
    `sed` does not modify the input, it excute the command and redirect the ouput..mainly on std out if nothing is specified in output.
    While using `sed`, do not redirect the output to the file you are editing or you will clobber it.
```
</details>

<a id="sed_how_it_works"></a>
### Sed how it works [^](#toc)

When running multiple sed commands via command line / file

• All editing commands in a script are applied in order to each line of input.

• Commands are applied to all lines (globally) unless line addressing restricts
the lines affected by editing commands.

• The original input file is unchanged; the editing commands modify a copy of
original input line and the copy is sent to standard output.

A sed command can specify zero, one, or two addresses. An address can be a regular
expression describing a pattern, a line number, or a line addressing symbol.

• If address is not specified, then the command is applied to each line.

• If there is only one address, the command is applied to any line matching the address.

• If two comma-separated addresses are specified, the command is performed
on the first line matching the first address and all succeeding lines up to and
including a line matching the second address.

• If an address is followed by an exclamation mark (!), the command is applied
to all lines that do not match the address.

<details>
    <summary>Commands: </summary>

```text
    d, 1d $d       // Deletes all lines, delete first line, delete last line
    /ˆ$/d          // Deletes only blank line
    50,$d          // Deletes from line 50 to the last line in the file
    1,/ˆ$/d        // This example deletes from the first line up to the first blank line
                    Braces ({}) are used in sed to nest one address inside another or to apply multiple
                    commands at the same address.
    /ˆ\.TS/,/ˆ\.TE/{
    /ˆ$/d
    }               The opening curly brace must end a line and the closing curly brace must be on a
                    line by itself. Be sure ther e ar e no spaces after the braces.
```
</details>

<a id="sed_multiple_commands"></a>
### Sed multiple commands [^](#toc)

<details>
    <summary>Details: </summary>

4 ways
```text
    Separate instructions with `;` :
            sed ’{instruction 1}; {instruction 2}’ {file to operate on}
    Use `-e` before each instruction:       // In general as a practice use `-e` before every command (except while using scriptfile)
            sed -e ’{instruction 1}’ -e ’{instruction 2}’ {file to operate on}
    Instructions on multiple lines:
            $ sed ’
            > {instruction 1}
            > {instruction 2}’ {file to operate on}
    Using instructions in a file as input:      // One instruction per line
            sed -f {scriptfile} {file to operate on}

```
</details>

<a id="sed_awk_multiple_commands"></a>
### Sed / Awk multiple commands [^](#toc)

<details>
    <summary>Details: </summary>

4 ways
```text
    Separate instructions with `;` :
            sed ’{instruction 1}; {instruction 2}’ {file to operate on}
    Use `-e` before each instruction:       // In general as a practice use `-e` before every command (except while using scriptfile)
            sed -e ’{instruction 1}’ -e ’{instruction 2}’ {file to operate on}
    Instructions on multiple lines:
            $ sed ’
            > {instruction 1}
            > {instruction 2}’ {file to operate on}
    Using instructions in a file as input:      // One instruction per line
            sed -f {scriptfile} {file to operate on}

    Similarly for awk, just replace sed with awk

```
</details>

<a id="suppressing_automatic_display_input_lines"></a>
### Suppressing of automatic display of input lines [^](#toc)

By default sed prints every input line
<details>
    <summary>Details: </summary>

```text
    sed -n -e ’{instruction}’ {file to operate on}

    Other options:
        `-e` Editing instruction follows
        `-f` Filename of script follows
        `-n` Suppress automatic output of input lines

```
</details>

<a id="awk_how_it_works"></a>
### Awk how it works [^](#toc)

Awk, in the usual case, interprets each input line as a record and each word on
that line, delimited by spaces or tabs, as a field.
Awk variables are initialized to the empty string.

Awk allows two special routines that can be executed before any input is read and after all input is read. These are the procedures associated with the BEGIN and END rules, respectively.

<details>
    <summary>Commands: </summary>

```text
    awk ’{ print $1 }’ {input file}:
        “$1” refers to the value of the first field on each input line.
    awk -F<seperator> ’/<search pattern>/ { print $1 }’ {input file}:
        Searches for <search pattern> on each line of {input file}, then using the <separator> print the first word
        E.g. of above using multiple operations: awk -F<separator> ’{ print $1; print $2; print $3 }’ {input file}
    /ˆ$/ { print "This is a blank" }:
        If the input line is blank, then print “This is a blank”
    /MA/ { print $1 ", " $6 }:
        Matches the line having keyword `MA` and prints first and sixth word
    $5 ˜ /MA/ { print $1 ", " $6 }:
        Prints the first and sixth word of the line where the 5th word have `MA`
    $5 !˜ /MA/ { print $1 ", " $6 }:
        Prints the first and sixth word of the line where the 5th word does not have `MA`

```
</details>

<a id="awk_reserved_keywords"></a>
### Awk reserved keywords [^](#toc)

<details>
    <summary>Details: </summary>

```text
    BEGIN   // Execute instruction before any line is processed by awk
    END     // Execute instruction after last line is processed by awk
    NR      // After the last line of input is read, NR contains the number of input records (lines)
    print   // Print the statement / variable
    printf  // Print using formatting options. Check for formatting options for printf.
    $n      // E.g. $1, $2 denotes the first and second field on matching line
    NF      // Which is set to the number of fields for the current record, $NF denotes the last field on current record
    FS      // Field separator
    RS      // Record separator, as a newline.
    OFS     // Output field separator
    ORS     // Output record separator

```
</details>

<a id="awk_special_symbols_operators_functions"></a>
### Awk special symbols, operators & functions [^](#toc)

<details>
    <summary>Details: </summary>

```text
    \a      Alert character, usually ASCII BEL character
    \b      Backspace
    \f      Formfeed
    \n      Newline
    \r      Carriage retur n
    \t      Horizontal tab
    \v      Vertical tab
    \ddd    Character repr esented as 1 to 3 digit octal value
    \xhex   Character repr esented as hexadecimal value

    +       Addition
    -       Subtraction
    *       Multiplication
    /       Division
    %       Modulo
    ˆ       Exponentiation

    <       Less than
    >       Greater than
    <=      Less than or equal to
    >=      Greater than or equal to
    ==      Equal to
    !=      Not equal to
    ˜       Matches
    !˜      Does not match

    ||      Logical OR
    &&      Logical AND
    !       Logical NOT

    ++      Add 1 to variable
    --      Subtract 1 from variable
    +=      Assign result of addition
    -=      Assign result of subtraction

    Other operators similar to above are applicable

    cos(x)      Returns cosine of x (x is in radians).
    exp(x)      Returns e to the power x.
    int(x)      Returns truncated value of x.
    log(x)      Returns natural logarithm (base-e) of x.
    sin(x)      Returns sine of x (x is in radians).
    sqr t(x)    Returns squar e root of x.
    atan2(y,x)  Returns arctangent of y/x in the range -π to π.
    rand( )     Returns pseudo-random number r, wher e 0 <= r < 1.
    srand(x)    Establishes new seed for rand( ). If no seed is specified,  uses time of day. Returns the old seed.


    gsub(r,s,t)     Globally substitutes s for each match of the regular expression r in
    the string t. Returns the number of substitutions. If t is not supplied,
    defaults to $0.
    index(s,t)      Returns position of substring t in string s or zero if not present.
    length(s)       Returns length of string s or length of $0 if no string is supplied.
    match(s,r)      Returns either the position in s wher e the regular expression r
    begins, or 0 if no occurrences are found. Sets the values of RSTART
    and RLENGTH.
    split(s,a,sep)  Parses string s into elements of array a using field separator sep;
    returns number of elements. If sep is not supplied, FS is used. Array
    splitting works the same way as field splitting.
    spr intf(“fmt ”,expr)   Uses printf for mat specification for expr.
    sub(r,s,t)      Substitutes s for first match of the regular expressions in the string t.
    Returns 1 if successful; 0 otherwise. If t is not supplied, defaults to $0.
    substr(s,p,n)   Returns substring of string s at beginning position p up to a
    maximum length of n. If n is not supplied, the rest of the string from p is used.
    tolower(s)      Translates all uppercase characters in string to lowercase and
    returns the new string.
    toupper(s)      Translates all lowercase characters in string to uppercase and
    returns the new string.

    Awk support self declared functions:
        function (arguments){
            // Expressions
            // Optional return statement
        }

```
</details>

<a id="awk_conditional_operators_iteration_array"></a>
### Awk conditional operators, iteration & array [^](#toc)

<details>
    <summary>Details: </summary>

```text
    Supported conditional operators:
        if, ifelse, else
    Iteration:
        For loop, while, do while
    Arrays:
        Supported. Awk support associative arrays. What makes an associative array unique is
that its index can be a string or a number. All array indices in awk are strings. Even with number as an index, awk automatically converts it to a string first.
    Arrays support `in` operator.
        item in array
        if ( "BASIC" in acro )
    
    delete array[subscript]
    split(string, array, separator)

```
</details>

<a id="awk_commands"></a>
### Awk commands [^](#toc)

<details>
    <summary>Commands: </summary>

```text

    /ˆ$/ {
        print x += 1
        }       //  Count blank lines

    /ˆ$/ {
        ++x
        }
        END {
        print x
        }       // Count blank lines

    `john 85 92 78 94 88
    andrea 89 90 75 90 86
    jasper 84 88 80 92 84`

    # average five grades
    { total = $2 + $3 + $4 + $5 + $6
    avg = total / 5
    print $1, avg }     //  john 87.4

    `John Robinson
    Koren Inc.
    978 Commonwealth Ave.
    Boston
    MA 01760
    696-0987`

    BEGIN { FS = "\n"; RS = "" }
    { print $1, $NF }       //  John Robinson 696-0987

```
</details>

<a id="pass_variables_to_awk"></a>
### Pass variables to awk [^](#toc)

<details>
    <summary>Details: </summary>

```text
    awk -f scriptfile high=100 low=60 datafile

    Inside the script, these two variables are available and can be accessed as any awk
    variable. If you were to put this script in a shell script wrapper, then you could
    pass the shell’s command-line arguments as values. (The shell makes available
    command-line arguments in the positional variables—$1 for the first parameter, $2
    for the second, and so on.)* For instance, look at the shell script version of the
    pr evious command:
    awk -f scriptfile "high=$1" "low=$2" file_name
    If this shell script were named awket, it could be invoked as:
    $ awket 100 60

```
</details>

<a id="awk_limitations"></a>
### Awk limitations [^](#toc)

<details>
    <summary>Limitations: </summary>

```text

    Number of fields per record     100
    Characters per input record     3000
    Characters per output record    3000
    Characters per field            1024
    Characters per printf string    3000
    Characters in literal string    400
    Characters in character class   400
    Files open                      15
    Pipes open                      1

```
</details>

<a id="sed_examples"></a>
### SED Examples [^](#toc)

<details>
    <summary>Examples: </summary>

```text

Print:
    sed -n 'p' <file>     // Print all lines from the given file
    sed -n '2 p' <file>   // Print 2nd line from the given file
    sed -n '1,4 p' <file> // Print all the lines from 1 to 4 from the given file
    sed -n '2,$ p' <file> // Pint all the lines from 2 to end from the given file
    sed -n '2,+3 p' <file> // Pint the 2nd line and next 3 lines from the given file. Another e.g. sed -n '2,-3 p' <file>
    1~2 matches 1,3,5,7 etc.    2~3 matches 2,5,8,11, etc.
    sed -n '/pattern/,4 p' <file>     // Print lines starting with matching pattern till line 4 from the given file
    sed -n '/pattern1/,/pattern2/ p' <file>    // Print lines starting with line matching pattern1 through the lines matching the pattern2 from the given file. This is the generic range for sed pattern can be replaced by line absolute / relative number, file end symbol etc. `p` represents the command.
    sed -n '/pattern1\|pattern2/ p' <file>      // Print the line containing either pattern1 or pattern2
    sed can use any regular expression
    `p` can be replaced with any applicable command e.g. 
Delete:
    sed -n '/pattern1/,/pattern2/ d' <file>   // Delete all the lines starting with the line matching with pattern1 upto the lines matching pattern2 from the input line
Write:
    sed -n '/pattern1/,/pattern2/ w <output file>' <file>  // Writes all the line starting with the line matching pattern1 to first line matching pattern2 to output file
Replace:
    sed '[address-range|pattern-range] s/pattern/replacement-string/[substitute-flags]' <file>
    substitute-flags:
            g       // Global: substitute all matches on the given line. `g` is like horizontal matching on the line
            2       // replace the second occurance of pattern on each matching line
Execute command:
    sed substitution can be used to execute command e.g.
    sed 's/^/ls -l /e' <file>      // This command will add `ls -l ` before each line and then those will get executed
Combining multiple flags:
    sed -n '[address-range|pattern-range] s/pattern/replacement-string/' <file>
Modify file:
    sed -i 'command' <file>     // -i flag modifies the file
    sed -ibak 'command' <file>  // modify the file and save and save backup of original file
    sed '[address] c the-line-to-insert' <file>     // Change the content of file at `address`
Show hidden characters:
    sed -n l <file>
Working with multipel input files:
    Most of the sed commands can take multiple input files as: <file1>  <file2>

```
</details>

<a id="awk_examples"></a>
### AWK Examples [^](#toc)

<details>
    <summary>Examples: </summary>

```text

Print:
    awk -Fs '/pattern/ {action}' <file1> <file2>     // `F` file separator `s` is separator
    awk -f <script file> 'BEGIN { awk command} \/pattern/ {action} \END { awk command }' <file>
    Use printf function instead of print to format the print
    Built in numeric functions:
        See section `awk_special_symbols_operators_functions`
    Built in environment variables:
        ENVIRON     // E.g. ENVIRON["PATH"]
        IGNORECASE  // Default value =0 which means do not ignore case E.g. awk 'BEGIN{IGNORECASE=1} /pattern/ {print}' <file>
        ERRNO       // Contains the error message while doing I/O operation
    User defined function:
        function fn-name(parameters)
            {
            function-body
            }

```
</details>