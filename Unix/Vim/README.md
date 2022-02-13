# Vim

<a id="toc"></a>
## Table of contents

1. [Contribution guidelines](#contri_guidelines)

<a id="contri_guidelines"></a>
## Contribution guidelines [^](#toc)

1. Fork -> Clone the project.
2. Make change.
3. Raise pull request & merge.

<a id="version"></a>
### Version [^](#toc)
Use commands vim -v / vim --version
<details>
    <summary>Sample output: </summary>

```text
vim -v

    VIM - Vi Improved                                                     
    version 8.1.2269
    by Bram Moolenaar et al.
    .
    .
    . 
use :q! to close the vim window

vim --version

    VIM - Vi IMproved 8.1 (2018 May 18, compiled Nov 08 2021 14:21:34)
    Included patches: 1-2269
    Modified by team+vim@tracker.debian.org
    .
    .
    .

```

</details>

<a id="modes"></a>
### Modes [^](#toc)
Vim has following modes which help with different kind of features vim has to offer.
These modes help in faster file editing with vim.
`Normal` `Insert` `Visual` `Command Line`

<a id="help"></a>
### Help [^](#toc)
vim help / list of vim options can be launched outside of vim using `vim -h` / `vim --help`. When inside a file using vim, vim help can be launched by `:h` / `:help`.

<a id="launch"></a>
### Launch Vim [^](#toc)
Vim can be launched via
<details>
<summary>Vim Launch </summary>

```text
vim <file_name>
vim <files>  // In case operating with multiple files
vim -u NONE -N <file_name> // Use this command not to souce any vim customization due to vimrc. -u NONE : Not to use vim rc & -N avoid vim falling back to vi compatible mode.
```
</details>

<a id="navigation"></a>
### Navigation [^](#toc)
If Insert mode is active, use [Esc] first to come out of edit mode to execute following commands.
<details>
<summary>Commands </summary>

```text
Line numbers can be shown for each line using `:set nu`.
Go to a line using `:<line_number>`
Go to starting of file `gg`, end of file `Shift + g`.
Starting of line `0`, end of line `$`.
Move forward by a word `w`, backward by a word `b`
Move forward by a character `l`, backward by a char `h`, downward by a char `j`, upward by a char `k`

Few shortcuts below

        `j`   Down one real line
        `gj`  Down one display line
        `k`   Up one real line
        `gk`  Up one display line
        `0`   To first character of real line
        `g0`  To first character of display line
        `^`   To first nonblank character of real line
        `g^`  To first nonblank character of display line
        `$`   To end of real line
        `g$`  To end of display line
        `w`   Forward to start of next word
        `b`   Backward to start of current/previous word
        `e`   Forward to end of current/next word
        `%`   Jump between opening and closing sets of parentheses
        ``    Position before the last jump within current file
        `.    Location of last change

```
</details>

<a id="prompt"></a>
### Prompts [^](#toc)
Prompts such as `:` has meaning in vim.
<details>
<summary>Prompts </summary>

```text
`$` Enter command line in external shell
`:` Activate execute mode and execute command inside vim
`/` Forward search
`?` Bacward search

```
</details>

<a id="search"></a>
### Search [^](#toc)
If Insert mode is active, use [Esc] first to come out of edit mode to execute following commands.
<details>
<summary>Commands </summary>

```text
Search a character 
    Forward `Type f followed by character i.e. f[char]`
    Backward `Use F instead of f above`
    To repeat search action of above commands use 
        repeat search forward `;`
        repeat search backward `,`
Search a word 
    Forward use `*` when over a word
        repeat search forward `n`
        repeat search backward `N`
Search character / word / regular expression:
    forward `/[expression]`
    backward `?[backward]`
Use grep command:
    `:grep <grep options> "<expression>" *`  // * means search entire file. Quotes on expression is optional.

```
</details>

<a id="edit"></a>
## Edit [^](#toc)
A file can be edited using vim via in any mode.

<a id="delete"></a>
### Delete [^](#toc)
<details>
<summary>Commands </summary>

```text
Delete current character `x`
Word delete
    Single word `dw`
    Multiple words `d[count]w` / `[cound]dw` e.g. `d5w` / `5dw`
    Delete backwards `db`
Line delete `dd`
Use `.` to repeat last action more than one time e.g. `.` after `d2w` will keep deleting 2 words.

```
</details>

<a id="substitute"></a>
### Substitute / replace / append [^](#toc)
<details>
<summary>Commands </summary>

```text
Modes: `normal`, `visual`
Move to the character and then type for
    Substitute 
        `s`  // This will delete the character on the cursor and open the 
    `Insert` mode of vim
        `S` // This will delete the entire line and open the `Insert` mode
    Append 
        `a` // This will move the cursor to the next character and open the `Insert` mode of vim
        `A` // This will move the cursor to the end of line and open the `Insert` mode
    Change 
        `cw` / `c3w` // This will delete the number of words and open vim in `Insert` mode
        `c0` // Change from the word to the begining of the line
        `c$` // Change from the word to the end of the line
    Insert
        `i` // In normal mode pressing key `i` will open the `insert mode`
    Replace
        `r` // In normal mode pressing key `r` followed by character will cause the character under cursor to get replaced with new character. In visual mode pressing `r` key followed by character will cause the entire selected text to be replaced with new character

//------- Interesting combinations ---------//
1. Use `A` to move to end of line, append any character say `.` / `:`, use movement keys j, h and use `.` command to repeat action.
2. Use `f[char]` to search for a character, substitute char by `s[chars]`, perform futher forward / backward search using `;` / `,` and use command `.` to repeat substitution.

```
</details>

<a id="indentation"></a>
### Indentation [^](#toc)
<details>
<summary>Commands </summary>

```text
Modes: `normal`, `visual`
Move the cursor to the required position and do 
    right indentation `>` / `[n]>` followed by enter key press. Operation can be repeated with `.`
    left indentation `<` / `[n]<` followed by enter key press. Operation can be repeated with `.`

```
</details>

<a id="commandline_commands"></a>
### Commandline commands [^](#toc)
<details>
<summary>Commands </summary>

```text
Enter: enter by using `:`
Go to line `:[n]` `:1` `:$` where n is line number, 1 for the first line $ for the last line
Print line content 
                    `:[n]p` where n is line number, just `:p` to print content of current line
                    `[a,b]p` to print content between line number a, b
                    `.,2p` . stands for current line, $ stands for last line
                    `%p`   % stands for all lines
                    `:/<html>/,/<\/html>/p` pattern print between <html> & </html>
                    `:/<html>/+1,/<\/html>/-1p` +1 line from `from` pattern to -1 `to` pattern
Delete line content 
                    all of above commands can be used, just replace `p` with `d`
Execute any normal command
                    `:normal [normal mode command]` e.g. `:normal A;` will append ; to end for current line
                    `:%normal A;` add ; to end of all lines
                    `1,4normal A;` will put ; to end for first 4 lines as specified by range
Loop through executed command line commands / go through command history
                    In command line mode use up / down arrow keys
                    use `q:` this will open history of commands executed in command line mode
Loop through all commands / options in comamndline mode
                    after typing few letters use [tab] for looping though options 1 by 1 / use [ctrl+d] to see list of options
Combine multiple commands
                    execute multiple commands in one go using | operator after one command e.g. ` command 1 | command 2 | command 3`
                    Commands from history can be combined together by using `q:` go the first command then use `A | ` and then paste another command from history

```
</details>

<a id="vim_background_foreground"></a>
### Vim to background then to foreground [^](#toc)
<details>
<summary>Commands </summary>

```text
Send to background `ctrl+z`
Bring to foreground `type fg on shell`

```
</details>

<a id="commandline_command_bang"></a>
### Commandline commands using bang [^](#toc)
<details>
<summary>Commands </summary>

```text
Enter: enter by using `:`
Execute command on shell from inside vim
                `:! <command>`  \\ this will cause the command to execute on shell, leaving the vim. Press `enter` do `ctrl+c` / type `exit` to go back to vim
Excute command on content of file using external command
                `:<range>!<command>`  \\ e.g. command `:1,$!sort -t',' -k2` will cause sorting of content in vim on second content after separator `,`

```
</details>

<a id="working_with_multiple_files"></a>
### Working with multiple files [^](#toc)
<details>
<summary>Details </summary>

```text
Open multiple files at a time with vim using `vi <files>`.

List all files
                `:ls` \ `:args`
navigate between files
                `:bnext`, `:bprevious`,`:bfirst`,`:blast` and other commands. Press `tab` after `:b` for autocompletion.
Creating multiple windows
                Horizontal split: `<C-w>s`  \\ type `ctrl+w` then followed by `s` for horizontal split. Current file will be split.
                Vertical split: `<C-w>v`  \\ type `ctrl+w` then followed by `v` for vertical split. Current file will be split.
                Cyle between open windows:     \\ `<c-w>w`
                Load new file: `:split <file>`, `vsplit <file>`  \\ load file in horizontal \ vertical window.
                Close:  `:close`
                Leave open current file and close others:   `:only`
Working with tabbed windows
                Load new file in tab:   `:tabedit <file>`, close tab  `:tabclose`, close all tab excep the current one `:tabonly`
                Navigate to a tab: {n}gt, where n is number
                Move a tab to a position:   `:tabmove {N}`
                
```
</details>

<a id="see_changes"></a>
### See changes (changelist) done in a file [^](#toc)
<details>
<summary>Details </summary>

```text
            `:changes`      \\ show list of changes done, use `g;` & `g,` to move forward / backward
                
```
</details>

<a id="using_marks"></a>
### Using marks [^](#toc)
<details>
<summary>Details </summary>

```text
        `ma` 	    set mark `a` at current cursor location. Lowercase letters create marks that are local to a buffer, whereas uppercase letters create global marks (can be used to navigate between files). You can set up to twenty-six global marks
        `'a` 	    jump to line of mark a (first non-blank character in line)
        ``a` 	    jump to position (line and column) of mark a
        `d'a` 	    delete from current line to line of mark a
        `d`a` 	    delete from current cursor position to position of mark a
        `c'a` 	    change text from current line to line of mark a
        `y`a` 	    yank text to unnamed buffer from cursor to position of mark a
        `:marks` 	list all the current marks 
                
```
</details>

<a id="working_with_macros"></a>
### Working with macros [^](#toc)
<details>
<summary>Details </summary>

Create macro using sequence of steps and repeat.
```text
    How to use:
            The q key acts both as the “record” button and the “stop” button. Begin recording keystrokes by typing q{register}, giving the address of the register where to save the macro.
            Inspect the content of register as
    Inspect macro:
            `:reg {register}`
    How to apply:
            Go to the line where you would like to apply macro and use 
                `@{register}`  // apply the macro once
                `[number]@{register}`   // apply macro n number of times
    How to edit existing macro:
            When you have a document open, press `Shift+G` to go to end of document and 
            use `:put {register}`, this will paste the content of macro after the current line in doc.
            Edit macro. To save the content of macro use command `"add`
                
```
</details>

<a id="search_replace_execute_global_commands"></a>
### Search, replace & execute global comamnds [^](#toc)
<details>
<summary>Details </summary>

```text
Search:
    set ignore case:
            Set ignore case globally. `:set ignorecase`
            `\c` causes the search pattern to ignore case, `\C` item forces case sensitivity.
    python / perl like regex:
            Use \v before pattern e.g.
            /\v#([0-9a-fA-F]{6}|[0-9a-fA-F]{3})     // Matches color pattern
                                                        body { color: #3c3c3c; }
                                                        a { color: #0000EE; }
                                                        strong { color: #000; }
            Different between normal regex (POSIX) vs using `/v` on vim:

            #\([0-9a-fA-F]\{6}\|[0-9a-fA-F]\{3}\)   // normal
            \v#([0-9a-fA-F]{6}|[0-9a-fA-F]{3})      // equivalent of above using `\v`
            :g/TODO/yank A      // search each line which have TODO and append the result to register `a`
                                :reg a
                                ❮ "a // TODO: Cache this regexp for certain depths.
                                // TODO: No matching end code found - warn!
Substitution:
        :[range]s[ubstitute]/{pattern}/{string}/[flags]

        :%s/<search pattern>/<replace text>/g    // Global edit:  E.g. :%s/\v'(([^']|'\w)+)'/“\1”/g  ,  `%` help with vertical axis, `g` helps with horizontal axis
        :%s/<search pattern>/<replace text>     // First match, single line edit
        :%s/content/copy/gc     // The c flag causes Vim to show us each match and ask “Replace with copy?”. Use `y` to perform the change or `n` to skip it.

        E.gs.

        :%s/\n/,        //  joins every line of a file by replacing newlines with commas
        :%s//<C-r>0/g   //  use the content of register `0` for substitution. Similarly content of register can work for search pattern as well
        /\v\<\/?h\zs\d     // The `\zs` allows to zoom in on part of the match. `h\zs\d` would match the letter h followed
                            by any digit (e.g. h1, h2). The placement of \`zs` indicates that the h itself would be excluded from the match
        Creating dictionary in vim:
                            :let swapper={"up":"down","down":"up"}
                            :echo swapper["up"]
                            ❮ down
                            :echo swapper["down"]
                            ❮ up
Execute global commands:
        :g/{pattern}/[cmd]
        :g/{pattern}/[range][cmd]
```
</details>


<a id="autocompletion"></a>
### Autocompletion [^](#toc)
<details>
<summary>Details </summary>

Autocompletion can be triggered in insert mode.
```text

Commands:
            <C-n> Generic keywords      // <C-n> : next, <C-p> : previous
            <C-x><C-n> Current buffer keywords
            <C-x><C-i> Included file keywords
            <C-x><C-]> tags file keywords
            <C-x><C-k> Dictionary lookup
            <C-x><C-l> Whole line completion
            <C-x><C-f> Filename completion
            <C-x><C-o> Omni-completion
```
</details>

<a id="spell_checker"></a>
### Spell checker [^](#toc)
<details>
<summary>Details </summary>

Find and correct spelling mistakes.
```text

Commands:
            `:set spell`        // Highlight a word mispelled
            `:set nospell`      // Disable spell check
            `:set spelllang=en_us`  // Set up regional language for spell check
            `]s`                // Jump to next spelling error
            `[s`                // Jump to previous spelling error
            `z=`                // Suggest corrections for current word
            `1z=`               // Fix the word with suggestion
            `zg`                // Add current word to spell file
            `zw`                // Remove current word from spell file
            `zug`               // Revert zg or zw command for current word
```
</details>

<a id="ctags"></a>
### Ctags [^](#toc)
<details>
<summary>Details </summary>

ctags is an external program that scans through a codebase and generates an index of keywords. This allows us to navigate around a codebase by quickly jumping to definitions of functions and classes. Output from ctags can be used to generate a word list for autocompletion.
```text

Commands:
            `Ctrl + ]`	        // Go to definition
            `Ctrl + T`	        // Jump back from the definition
            `Ctrl + W Ctrl + ]`	// Open the definition in a horizontal split
            `:ts <tag_name>`	// List the tags that match <tag_name>
            `:tn`	            // Jump to the next matching tag
            `:tp`	            // Jump to the previous matching tag
```
</details>