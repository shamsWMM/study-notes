# 1. The Shell
```bash
$ date # prints the date
$ echo Hello\ World
$ echo $PATH
$ which echo # prints the path of the command "echo"
# Example:
    $ which which
    # which: shell built-in command
```
> Paths in linux are separated by forward slashes. Everything lives under the root namespace.\
> In windows they are separated by back slashes. There is one root per partition.
```bash
# Tilde 
    $ echo ~ # same as $ echo $HOME
    # /Users/myUserName
# Dash
    $ cd - # changes directory to previous one
# dash is built into cd as $OLDPWD, but is not interpretted as such by other commands
# therefore `echo -` prints nothing, and isn't predictable
```
> $OLDPWD is not guaranteed by POSIX - Portable Operating System Interface
```bash
$ ls # long listing format more info about the files
    # d = directory
    # owner - group that owns - everyone else
    # permissons for a directory: read determines whether a user can see the drectory content, write determines whether create, rename, or delete files within a directory, and execute determines whether you can access the contents

$ mv # takes old path and new path
$ cp # takes from path and to path
$ rm # takes the path of the file to be removed
    # -r for recursive
$ rmdir # only removes empty directory
$ mkdir

$ man #<command> for command manual
```

> Every program has two primary streams. By default the input stream and the output stream are both the terminal. \
> `< file`  means rewire the input of the program to be the contents of this file \
> `> file` means rewire the output of the program to this file \
> `>> file` means append \
> `<< DELIMITER` is a heredoc syntax to use the upcoming lines as input \
>  `;` ends a command in shell \
> `|` take the output of the left, make it the input of the right

```bash
$ cat < hello.txt >> hello2.txt # example
$ tail -n 5 text.txt # reads last 5 lines

$ sudo su # get a shell as the super user
    # the prompt changes from `$` to `#` to signify super user shell

$ echo 1060 | sudo tee brightnets # `tee` takes its input and writes it to a file
$ tee -a hi.txt < wow.txt # add to hi.txt the content of wow.txt
    # `-a` flag is for append, without it content is overwritten

$ xdg-open hello.txt # just `open` on mac, opens the file with the appropriate program 

$ ls -l file.txt        # mtime
$ ls -lu file.txt       # atime
$ ls -lc file.txt       # ctime

$ sh semester # executes the semester file using the shell interpreter
    # you are executing /bin/sh (which is executable)
    # you are passing semester as a data file (an argument) to sh

$ grep -i last-modified txt.txt 
    # last-modified: Thu, 22 Jan 2026 02:33:05 GMT
```
> `$SHELL` holds shell path

# 2. Editors - Vim
vim modes
- normal -> insert (i) -> normal (press esc)
- replace mode (r)
- selection, visual (v)
- visual-line (&#8679; v) 
- visual-block (^ v)
- command-line mode (:) 

Notation \<C-V> is (^ v)



- :sp :vsp (split)
- ^wj ^wk ^ww ^wp moves between split screens
- :qa (quit all)
- :e {name of file} open file for editing 
- :help {topic} open help
	:help :w opens help for the :w command
	:help w opens help for the w movement
- :s/old/new/g to substitue new for old, no g means only one occurrence in the line, g means all occurrences in the line
	- :#,#s/old/new/g    where #,# are the line numbers of the range of lines where the substitution is to be done.
	- :%s/old/new/g      to change every occurrence in the whole file.
	- :%s/old/new/gc     to find every occurrence in the whole file, with a prompt whether to substitute or not.
- hjkl (move left, down, up, right)
- wbe (move one word forward, back, end of word)$
- 0$^ (move to beginning of the line, end of the line, first non empty character on the line)
- (^ u) (scroll up)
- (^ d) (scroll down)
- ^o ^i go back to where you came from, go forward
- (&#8679; g) (go down the whole buffer)
- gg (go up the whole buffer)
- :{number}<CR> or {number}G (line {number})
- ^g file name and position in the file
- (&#8679; l, m, h) (go to lowest, middle, highest line shown on the screen, respectivley)
- f followed by a some char (find the first some char on the line) 
- (&#8679; F) (find backward)
- t and &#8679; t (for find to forward and backward)
- Find: f{character}, t{character}, F{character}, T{character}
    find/to forward/backward {character} on the current line
    ,; for repeat search opposite direction or same direction respectively

- forward slash /{regex} followed by a string searches for a string, press enter to go there, press n for next and &#8679; N for backward next
	? searches backward 
- oO (new line and get into insert mode below and above)
- d and a movement command deletes, dd cuts line
- u undo, ^r redo
- c and movement changes the char using movement command and puts into insert, cc changes whole line and puts into insert mode
- x cuts char, r replaces char with another char given
- y for copy, p for paste, yy for copy line, yw for copy word
- "+p "*p pastes from clipboard and primary registers respectively
- ~ changes case of selection
- &#8679; j to join two lines separated by line break, &#8679; gJ for no space between the joined lines  

- number followed by command does command number times
- ci \[ change inside the square bracket
- % jump back and forth between matching parentheses 
- da \[ deletes all in parentheses as well as the parentheses
- . repeats previous command

[Advanced Vim Commands](https://vim.fandom.com/wiki/Search_and_replace)

> https://missing.csail.mit.edu/2020/course-shell/
