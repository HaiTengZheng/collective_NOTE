# create multi dirs
enclose in curly brackets `{}`, seprate with comma `,`
e.g.
> mkdir -pv dir_first/{dir1_1, dir1_2}/{dir2_1, dir2_2}
make below
```
dir_first
|-- dir1_1
|   |-- dir2_1
|   |-- dir2_2
|-- dir2_1
|   |-- dir2_1
|   |-- dir2_2
```

