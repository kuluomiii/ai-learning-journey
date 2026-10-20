# C 部分：uv 虚拟环境实操（W1）

> 示例项目 `projects/hello-uv` 已经建好跑通了。你的任务是**自己从零再走一遍**，
> 然后回答三个理解题。会背命令没用，理解了 W2 之后每天都要用。

## C1 自己动手建一个（照抄执行）

```bash
cd ~/Desktop/ai-learning-journey/projects
uv init my-first-uv        # 建 my-first-uv（和 hello-uv 区分开，是你的练习）
cd my-first-uv
uv add rich                # 装一个终端美化库 rich
```

然后用编辑器把 `main.py` 改成：

```python
from rich import print

print("[bold green]我的第一个 uv 项目跑通了！[/bold green]")
print({"环境管理": "uv", "感受": "比 conda 快多了"})
```

运行：

```bash
uv run main.py
```

看到带颜色的输出就成功了 ✅

## C2 理解三题（答案写在本文件里）

打开 `my-first-uv` 目录看一圈（`ls` 和用编辑器），然后回答：

1. **`uv run` 和直接 `python` 的区别？**
   提示：试试直接 `python main.py` 会发生什么（如果报错/找不到 rich，就说明问题所在）

   你的回答：

2. **`.venv/` 目录是干什么的？为什么它在 .gitignore 里？**
   提示：`ls my-first-uv/.venv` 看看里面有多少东西；想想「这个目录能随便删吗？删了怎么恢复？」

   你的回答：

3. **`pyproject.toml` 和 `uv.lock` 各自记录了什么？**
   提示：用 `cat` 分别看这两个文件的内容，对比差异

   你的回答：

## C3 conda vs uv 速度对比（30秒体验）

```bash
time uv venv /tmp/test-uv          # uv 建环境
rm -rf /tmp/test-uv
time conda create -n test-slow python=3.12   # conda 建环境（等它跑完或 Ctrl+C）
conda env remove -n test-slow      # 清理
```

把两个时间记在这：uv ____ ｜ conda ____
（如果 conda 报 permission denied：用 `/opt/anaconda3/bin/conda` 全路径）

## 完成后

```bash
cd ~/Desktop/ai-learning-journey
git add projects/my-first-uv notes/uv-basics.md 2>/dev/null || git add -A
git commit -m "W1: C部分 uv 练习完成"
git push
```

## C 部分验收（自查）

- [ ] `my-first-uv` 跑出过彩色输出
- [ ] 三道理解题用自己的话答完
- [ ] 能说清：以后新项目第一步为什么是 `uv init` 而不是直接建 py 文件
