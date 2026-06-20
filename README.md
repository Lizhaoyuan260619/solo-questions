# Solo Questions 统一题目仓库

> 本仓库是所有 Solo Coder 题目的唯一真相源（Single Source of Truth）。
> 所有电脑在出题前必须先 `git pull` 同步，出题后必须 `git push` 推送。

## 目录结构

```
solo-questions/
├── batches/              # 批次文档目录（存放 solo0-1_第X批.md）
│   └── NEXT_ID          # 下一个可用编号（例如：00021）
├── projects/            # 项目目录（每题一个文件夹，格式：lzy-00XXX）
└── README.md
```

## 出题流程

1. `git pull origin main` — 同步其他电脑最新题目
2. 读取 `batches/NEXT_ID` 获取起始编号
3. 出题并写入对应文件
4. 更新 `batches/NEXT_ID`
5. `git add` + `git commit` + `git push`

## 配置变量

- GITHUB_OWNER = Lizhaoyuan260619
- AUTHOR_NAME = 李昭原
- NAME_PREFIX = lzy
- PYTHON_CMD = python
