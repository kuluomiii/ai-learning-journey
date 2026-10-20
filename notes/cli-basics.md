# B 部分：命令行基础实操（W1）

> 用法：在终端里逐条跑下面的命令（在任意目录都行，建议在学习仓里），
> 跑完把「✍️ 填空」补上，然后 commit。
> 卡住就把报错贴给 Cursor（Cmd+L）或 AI。

## B1 逐个认识这些命令

在终端依次执行，观察输出：

```bash
pwd                # 我现在在哪个目录？（print working directory）
ls -la             # 列出当前目录所有文件（-a 含隐藏文件，-l 详细信息）
cd ~/Desktop       # 切换目录（~ = 你的家目录 /Users/karen）
mkdir cli-test     # 新建目录
cd cli-test
touch hello.txt    # 新建空文件
echo "hello cli" > hello.txt   # 把文字写进文件（> 是覆盖写）
echo "line2" >> hello.txt      # 追加写（>> 不会覆盖）
cat hello.txt      # 打印整个文件内容
head -1 hello.txt  # 只看第一行
cp hello.txt copy.txt   # 复制
mv copy.txt moved.txt   # 移动/重命名
rm moved.txt            # 删除文件（⚠️ rm 没有回收站，删了就没了）
cd .. && rm -rf cli-test   # 删目录（-r 递归 -f 强制，⚠️ 慎用）
```

### ✍️ 填空（用自己的话，一句话即可）

- `>` 和 `>>` 的区别：>是覆盖写，>>是追加写
- `rm` 和 `rm -rf` 的区别，哪个更危险：后者更危险，会递归删除目录
- `cd ..` 是什么意思：切换到上一级目录

## B2 grep 与管道（最重要的组合）

```bash
cd ~/Desktop/ai-learning-journey

# 1. 在所有 md 文件里找包含 "commit" 的行，显示行号
grep -rn "commit" . --include="*.md"

# 2. 只列出哪些文件包含 "W1"（-l = 只显示文件名）
grep -rl "W1" . --include="*.md"

# 3. 管道：把前一个命令的输出交给后一个命令处理
grep -rn "uv" . --include="*.md" | wc -l        # 统计出现次数
grep -rn "git" . --include="*.md" | head -5     # 只看前5条
```

### ✍️ 填空

- 用自己的话解释 `|`（管道）：把前一个命令的输出交给后一个命令来处理
- 跑上面第 3 条，把「出现次数」的数字写在这：__35__
- 组合拳：统计你仓库里有多少个 md 文件（提示：`ls` + `grep` 或 `find`）：
  ```bash
  # 你的命令：
  ls | grep "\.md" | wc -l
  ```

## B3 环境变量

```bash
echo $PATH          # 系统去哪些目录找可执行程序（用 : 分隔）
echo $SHELL         # 你正在用的 shell
export MY_VAR=hello # 定义环境变量（只对当前终端有效）
echo $MY_VAR
printenv | head -10 # 看所有环境变量前十行
```

### ✍️ 填空

- 为什么在终端输 `code .` 能打开 VS Code？（提示：想想 PATH 和 ~/bin）：因为 ~/bin 目录在 PATH 中，所以 code 命令能被找到
- `export` 定义的变量关掉终端就没了，想永久生效应该写进哪个文件？：~/.bashrc

## 完成后

```bash
cd ~/Desktop/ai-learning-journey
git add notes/cli-basics.md
git commit -m "notes: B 命令行基础笔记"
git push
```

## B 部分验收（自查）

- [x] 三组填空全部用自己的话填完（不是复制网上定义）
- [x] B2 的组合拳命令真的跑出过结果
- [x] 已 commit + push
