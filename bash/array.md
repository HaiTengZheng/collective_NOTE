# array
a collection in which elements of the collection are accessed according to a
number
```bash
# define a array
# use () enbraced the variables in array, and separate with space
my_array=('Alex' 'Ada' 'Alexandra')
# use key=value, explicit indices
my_array=([1]='Alex' [2]='Ada' [3]='Alexandra')
array[0]='first element'
array[1]='second element'
# declare
declare -A my_array
```
# ${array[@]} 
生成数组所有元素的列表

# ${!array[@]} 
生成数组所有索引的列表

# `+=`
add an element with the value to the array
```bash
my_array+=('Soto')
```

# unset
remove the element from the array at index `[]`
```bash
unset my_array[3]
```

# view data in an array
```bash
echo ${my_array[0]}
```
## `@` or `*`
view all elements
```bash
echo ${my_array[@]}
```
## get the number of elements in an array
use `#` and `@`
```bash
echo ${#my_array[@]}
```

# replacement
```bash
array=(one two three four five)
echo ${array[@]:1:3}
# return : two three four
```

# sub array
```bash
array=(one two three four five)
echo ${array[@]/one/two}
# return : two two three four five
```

# dynamic assignment
```bash
array=($(seq 1 10))
