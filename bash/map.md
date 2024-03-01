# map
a collection in which elements of the collection a key value

# declare
> declare -A <map_name>
`-A` indicate the variable represents an associative array which is the same as a map
```bash
declare -A score
score[alex]="1"
score[edson]="2"
```

# show all the keys in the map named score
use `!` and `@`
```bash
echo ${!score[@]}
```

# unset
delete the element identified by the key from the map variable
```bash
unset score[alex] # delete alex entry
```


## get a count of the number of elements in the map variable
use `#` and `@`
```bash
echo ${#score[@]}
```
