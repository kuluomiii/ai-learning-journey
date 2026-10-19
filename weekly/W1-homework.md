# W1 实操作业（10/12–10/18）

> 规则：所有作业在 `~/Desktop/ai-learning-journey` 里完成，**每完成一项就 commit 一次**。
> commit 历史本身就是 W1 的成绩单。

## ✅ 已由 AI 代办（你只需确认 + 理解）

- [x] 环境检查：git 2.51 / Python 3.13 / conda 24.11（`/opt/anaconda3`）/ Cursor + VS Code 均已安装
- [x] 新装：uv（Python 环境管理，比 conda 轻快，本项目主力）+ gh（GitHub CLI）
- [x] `code` 命令行已链接（终端输 `code .` 可用 VS Code 打开当前目录）
- [x] Git 身份已配置（whl / 1430721439@qq.com）
- [x] SSH key 已存在且已连通 GitHub（账号 **kuluomiii**）
- [x] 学习仓 `~/Desktop/ai-learning-journey` 已创建（README/weekly/notes/prompt-experiments/projects），已首次 commit

## 🫵 需要你亲手做的 2 件事（10分钟）

### 1. 在 GitHub 上创建远程仓库（二选一）

- **网页版**：打开 <https://github.com/new> → 仓库名 `ai-learning-journey` → 选 **Private**（以后想公开随时可公开）→ **不要**勾选任何初始化选项 → Create
- **或 CLI 版**：在你自己的终端里运行 `gh auth login`（按提示走浏览器授权），然后告诉我，我帮你建

建好后回来跑：
```bash
cd ~/Desktop/ai-learning-journey
git push -u origin main
```
刷新 GitHub 页面看到 README 就成功了。

### 2. VS Code 打开学习仓，逛一遍

```bash
code ~/Desktop/ai-learning-journey
```
装两个扩展（VS Code 内扩展面板搜索）：**Python**（ms-python.python）、**GitLens**（看每行代码是谁什么时候写的）。

## 📝 核心作业（本周完成，预计 6–8h）

### A. Git 完整工作流（约 3h）— 在学习仓里直接练

边做边看：廖雪峰 Git 教程 <https://www.liaoxuefeng.com/wiki/896043488029600>

- [ ] A1 在 `notes/git-basics.md` 用自己的话写下：add / commit / push 三步各自干了什么
- [ ] A2 建分支练完整流程：
  ```bash
  git switch -c practice          # 建并切换到新分支
  echo "branch practice" >> notes/practice.md
  git add . && git commit -m "practice: 分支练习"
  git switch main                  # 切回主分支
  git merge practice               # 合并
  git branch -d practice           # 删分支
  ```
- [ ] A3 制造并解决一次冲突：在两个分支里改 `notes/conflict.md` 的同一行，merge 时观察冲突标记，手动改完 `git add` + `git commit`
- [ ] A4 学会看历史：`git log --oneline --graph --all`（建议把这个设成别名）
- [ ] A5 把上面每一步的命令和你的理解追加到 `notes/git-basics.md`，commit

### B. 命令行基础（约 1.5h）

- [ ] B1 在 `notes/cli-basics.md` 记录以下命令各自的作用（逐个跑一遍）：
  `pwd` `ls -la` `cd` `mkdir` `cp` `mv` `rm` `cat` `head` `grep` `|` 管道
- [ ] B2 组合拳练习：在项目目录里执行
  ```bash
  grep -r "TODO" . --include="*.md" | head -5
  ```
  把输出贴进笔记，解释这条命令发生了什么
- [ ] B3 了解环境变量：`echo $PATH`、`export MY_VAR=hello`、`echo $MY_VAR`

### C. uv 虚拟环境（约 1.5h）— 这是你之后每个项目都会用的

- [ ] C1 建第一个 uv 项目（在仓库的 projects 下练手，练完可删）：
  ```bash
  cd ~/Desktop/ai-learning-journey/projects
  uv init hello-uv
  cd hello-uv
  uv add requests
  uv run python -c "import requests; print(requests.__version__)"
  ```
- [ ] C2 回答并记进 `notes/uv-basics.md`：
  - `uv run` 和直接 `python` 的区别是什么？
  - `.venv/` 目录是干什么的？为什么它在 .gitignore 里？
  - `pyproject.toml` 和 `uv.lock` 各自记录了什么？
- [ ] C3 对比体验（理解为什么计划里选 uv）：conda 建环境要等很久，uv 秒级完成——`time conda create -n test python=3.12` vs `time uv venv`（不用真等 conda 跑完，看到速度差异即可 Ctrl+C）

### D. AI 辅助编码环境（约 0.5h）

- [ ] D1 打开 Cursor，打开学习仓，用 Cmd+L 对话让它解释 A3 里的冲突标记每一行含义
- [ ] D2 在 `notes/ai-coding.md` 写下你的第一条心得：什么任务适合交给 AI、什么必须自己搞懂（这条 W2 之后每周回看）

## 🏁 W1 验收标准（周日自查）

1. `git push` 能成功，GitHub 上能看到 ≥8 个 commit
2. 不看笔记能说出：建分支→开发→合并 的完整命令序列
3. 能独立用 uv 从零建一个带依赖的 Python 项目
4. `notes/` 里有 4 篇笔记（git / cli / uv / ai-coding）
5. 在 `weekly/2026-W42.md` 写第一份周复盘（模板在计划文档 §9）

## 常见问题

- **conda 报 permission denied**：直接用全路径 `/opt/anaconda3/bin/conda`，或重开一个终端窗口（新 shell 会重新初始化）
- **push 被拒**：确认仓库建在 kuluomiii 账号下、名字完全一致是 `ai-learning-journey`
- **卡住超过 30 分钟**：直接问 Cursor / 问 AI，把报错原文贴给它——这也是本计划要练的核心能力
