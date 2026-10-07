# MSqwq的 ACM 模板

这是一个面向算法竞赛的个人模板，整理了常见的数据结构、图论、字符串、数学、动态规划和其他竞赛技巧。项目使用 XeLaTeX 编译成一份便于打印、查阅和携带的 PDF 讲义。

模板内容仍在持续完善，难免存在错误或排版问题。如果发现问题，欢迎提交 Issue 或 Pull Request。

## 项目特点

- 按专题整理竞赛中常用的算法和数据结构；
- 使用 `minted` 显示 C++、Python 等代码，便于阅读；
- 支持生成带目录、页码和章节结构的 PDF；
- 提供 `Makefile`，可以一条命令完成编译和清理。

## 环境要求

### Windows

- Windows 10/11；
- TeX Live，并且能够在命令行中使用 `xelatex`；
- Python 3；
- Python 包 `pygments`；
- GNU Make（推荐使用 Git Bash、MSYS2 或其他提供 `make` 的环境）。

### Linux

需要安装 XeLaTeX、Python 3、`pygments` 和 GNU Make。Linux 下 `Makefile` 中的清理命令使用的是 Windows 的 `del` 和 `rmdir`，如果直接执行失败，请将它们改为 Linux 命令 `rm`。

## 快速开始

先进入项目根目录：

```bash
cd
python -m pip install pygments
make
```

编译成功后，会在项目根目录生成 `template.pdf`。由于目录和交叉引用需要多次编译，`make` 会自动执行两次 XeLaTeX。

如果系统中没有 `make`，也可以手动执行：

```bash
xelatex -shell-escape template.tex
xelatex -shell-escape template.tex
```

`-shell-escape` 是 `minted` 调用 Pygments 所必需的参数。

## 常用命令

```bash
make          # 检查内容并生成完整 PDF
make update   # 重新编译 PDF，不执行额外检查
make check    # 运行 check.py，检查模板中的内容问题
make clean    # 删除 LaTeX 编译产生的临时文件
```

如果编译时出现 `I can't write on file`，通常是 `.log` 或 `.pdf` 正被编辑器、PDF 阅读器或另一个 LaTeX 进程占用。关闭相关程序后重新编译即可。

## 目录结构

```text
template.tex       # 主 LaTeX 文件，负责组织整份讲义
chapters/          # 各专题章节
images/            # 封面和其他图片
check.py           # 内容检查脚本
Makefile           # 编译、检查和清理命令
README.md          # 项目说明
```

章节目录通常按照以下形式组织：

```text
chapters/
├── ch1-data-structure/
├── ch2-graph-theory/
├── ch3-network-flow-and-match/
├── ch4-string/
├── ch5-math/
├── ch6-dynamic-programming/
└── ch7-uncategorized/
```

## 修改和添加内容

1. 在对应章节目录下编辑 `.tex` 文件；
2. 如果新增了文件，在对应章节的 `index.tex` 中加入 `\input{文件路径}`；
3. 如果新增了章节，还需要在根目录的 `template.tex` 中加入对应的 `\input`；
4. 执行 `make` 检查并生成 PDF。

项目中部分 `.md` 文件是为了方便整理和阅读而保留的草稿或笔记，最终排版内容请以对应的 `.tex` 文件为准。



## 反馈与贡献

如果发现公式、代码、目录或排版错误，可以在 GitHub 提交 Issue，或修改后提交 Pull Request。欢迎补充新的算法模板、证明、复杂度分析和易错点。
