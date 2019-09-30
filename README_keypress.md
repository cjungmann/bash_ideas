# Project bash_ideas : keypress

[Main README](README.md)

This script includes a function, *get_keypress*, followed by
some examples of strings that can be used to interpret the
return value of *get_keypress*.  The benefit of this function
is that it can return a multi-character string as the appropriate
representation of a keystroke.

The *get_keypress* function takes advantage of *read* features:

- **-n 1** option reads a single character, without waiting for
  a delimiter (e.g. the ENTER key).

- **-t 0**, through an exit value of 0, indicates that there are
  additional characters in the input buffer.  In *get_keypress*,
  this is used in a loop condition to collect extra characters
  resulting from a keypress.


## Example Recognition Strings

Use [*ANSI-C Quoting*](https://www.gnu.org/software/bash/manual/html_node/ANSI_002dC-Quoting.html\#ANSI_002dC-Quoting)
to include create or recognize control characters.

Control-key characters can be tested with $'\c.':

~~~sh
declare keypress_ctrl_n=$'\cn'   \# control-n
declare keypress_ctrl_p=$'\cp'   \# control-p
~~~

The ESCAPE character may be a prefix to a keystroke
string:

~~~sh
declare keypress_down_array=$'\e[B'
declare keypress_up_array=$'\e[A'
~~~

In EMACS, a developer can use C-q, ESC to enter an escape character.
(see documentation: info emacs -n "Inserting Text")
~~~sh
declare keypress_down_arrow='^[[B'
declare keypress_up_array='^[[A'
~~~


