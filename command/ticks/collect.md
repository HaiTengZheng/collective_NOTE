# clear a file quickly
```bash
> file.txt
```

# create delays in pipes
```bash
cat somefile.txt | (sleep 0.1; tee somefile.txt)
```

# clear the sudo cache
```bash
sudo -K
```
