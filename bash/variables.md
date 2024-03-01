# variable
a variable is a parameters denoted by a name
a name is a word containing only letters, numbers, or underscores and beginning
    either a letter or an underscore
> name=Value

# `^`
convert the first character in a string to uppercase
```bash
MSG="aBcDeFg"
echo ${MSG^}
# return : ABcDeFg
```

# `^^` 
turns all lowercase characters in variable to uppercase
```bash
MSG="aBcDeFg"
echo ${MSG^^}
# return : ABCDEFG
```

# `,`
convert the first character in a string to lowercase
```bash
MSG="ABcDeFg"
echo ${MSG,}
# return : aBcDeFg
```

# `,,` 
turns all uppercase characters in variable to lowercase
```bash
MSG="aBcDeFg"
echo ${MSG,,}
# return : abcdefg
```

# word replacement
```bash
MSG="Say hi to Chris and Sidney"
echo ${MSG//Chris/Billy}
# return : Say hi to Billy and Sidney
# //.../... replace every one find in origin word

MSG="I need 10"
echo ${MSG//[a-zA-Z]/X}
# return : X XXXX 10
```

# extracting substrings 
## symbol `:`
```bash
MSG="The Rolling Stones"
echo ${MSG:4}   # get the substring of all the characters after starting at 
                #   position 4
# return : Rolling Stones
echo ${MSG:4:7} # get the substring that has 7 characters at position 4
# return : Rolling
```
## symbol `#`
```bash
MSG="The Rolling Stones"
echo ${MSG#The} # get the substring after the characters `The` starting from
                #   the left of the string
# return : Rolling Stones
```

## symbol `%`
```bash
MSG="The Rolling Stones"
echo ${MSG%Rolling Stones}  # get the substring before the `Rolling Stones`
                            #   starting the right side of the string
# return : The
```


