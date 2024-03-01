# Aliasing
```bash
# alias word='command'
# alias word='command --with --options'
alias ls='ls --color=auto'
# include multiple commands in the same alias
alias print_tings='echo "foo" && echo "bar" && echo "baz"'
# remove an existing alias
unalias {alias_name}
```

# BASH_ALIASES is an internal bash associative array
```bash
#!/bin/bash -li
# -l makes this behave like a login shell
# -i makes it behave like an interacive shell
#
# shopt -s expand_aliases will not work in most cases

echo Tere are ${#BASH_ALIASES[*]} aliased defined.

for ali in "${BASH_ALIASES[@]}"; do
    printf "alias: %-10s triggers: %s\n" "$ali" "${BASH_ALIASES[$ali]}"
done
```

# expand alias
> Ctrl + alt + e

# list all alias
> alias -p
