# here document
```bash
cat <<EOF > file.sh
echo 'printing pwd'
echo "\$(pwd)" 
ls -a
find '*.txt'
EOF
```
$ is escaped because we do not want it to be expanded by the current shell

or
```bash
cat <<'EOF' > file.sh
commands
...
EOF
```
the closing `EOF` should be at the beginning of the line(NO whitespace before)

## <<-
allow indentation
```bash
if cond; then
    cat <<- EOF
    hello
    there
    EOF
fi
```
it is customary to indent the lines within code blocks as in if statement, for
    better readability

# here string
```bash
awk '{print $2}' <<< "hello world - how are you?"
```
