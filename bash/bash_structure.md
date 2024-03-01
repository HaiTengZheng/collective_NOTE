# if-then-elif-else
```bash
if command
then
    commands
elif command
then
    commands
else
    commands
fi

# or

if command; then
    commands
elif command; then
    commands
else
    commands
fi
```

# for
```bash
for variable in values
do
	statement
done
```

# while
```bash
while condition; do
	statement
done
```

# until
```bash
until condition
do
	statement
done
```

# case
```bash
case variable in
	patten [ | patten] ...) statements;;
	patten [ | patten] ...) statements;;
	...
esac
```
- remark: 每个模式行都以双分号结尾 ;;
- 模式中小心使用 * 这样的通配符，case 将使用第一个匹配的模式，即使后续的模式有更加精确的匹配。
- 如果最后一个 case 模式是默认模式，那么可以省略最后一个 ;;
- ;;$ 表示即使找到匹配，依然尝试匹配下一个模式，如果发现该模式匹配，则执行与之相关的命令
- ;& 不论模式是否匹配都执行下一组语句

# break

# continue
