# f
- ; next
- , prev

# *
查找当前光标下的单词

# J
join two line together

# gO
get the tables

# help
> :help Ctrl-A
## insert mode with i_
> :help i_Ctrl-A
## error
> :help E37
## normal mode
no prefix
## visula mode v_
> :help v_o
## command line c_
> :help c_%
## Ex commands 
start with `:`
> :help :s


# ^
moves to the first nonblock character

# t and T
The "tx" command works like the "fx" command, except it stops one character
before the searched character.

# 50%
move halfway through the file

# move to lines visible
- H (Home)
- M (Middle)
- L (Last)

# move half screen
- Ctrl-U
- Ctrl-D

# scroll one line
- Ctrl-E (scroll up)
- Ctrl-Y (scroll down)

# z
- zt
- zz
- zb

# ``
go back where you from

# mark
> ms
> `s
## special markers
-   '	The cursor position before doing a jump
-   "	The cursor position when last editing the file
-   [	Start of the last change
-   ]	End of the last change
## get a list of markers
> markers

# search 
> /^the
> /the$
> /^the$
## search special character
> /the\.

# fold
open fold
- zo
close fold
- zc

# diff
> vim -d file1.md file1~.md
or in vim (only one patch)
> :vertical diffpatch main.c.diff

# ZZ
save and quit

# ZQ
quit without save
