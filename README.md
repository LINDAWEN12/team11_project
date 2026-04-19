# My AI Project
# 开发环境配置说明

## 前置要求

- **Java Development Kit (JDK) 17** 或更高版本
- **Maven** 3.8+ （用于后端构建）
- **Node.js** 20.x 和 **npm** 10.x （用于前端构建）
- **MySQL** 8.0+
- **Git**

## 后端启动步骤

1. 进入后端目录：
   ```bash
   cd backend

# Git 协作流程说明
## 分支约定
- **main**：稳定发布分支，禁止直接提交
- **dev**：日常集成分支，所有功能最终先合入 dev
- **feature/任务名**：功能开发分支，例如 feature/login-api
- **fix/问题名**：缺陷修复分支，例如 fix/order-status
## 开发流程
1. 同步远程代码
   ```bash
   git fetch origin #获取远程仓库代码
   git switch dev #切换到 dev 分支
   git pull origin dev #拉取最新 dev 代码
   ```

1. 从 dev 切出个人任务分支
   ```bash
   git switch -c feature/任务名 #创建并切换到新分支
   ```

1. 开发并提交
   ```bash
   git add .
   git commit -m "feat: 描述本次改动"
   ```

1. 推送分支到远程
   ```bash
   git push -u origin feature/任务名
   ```

1. 发起 Pull Request
   - 在 GitHub 上创建 PR
   - base 选择 dev
   - compare 选择 feature/任务名
   - 填写改动说明、测试说明、影响范围
   - 提交 PR

## 评审与合并规则
- 至少 1 名成员评审通过后才可合并
- CI 或测试检查必须通过
- 禁止未评审直接合并到 dev 或 main

## 冲突处理规则
- 若 PR 评审期间 dev 有新变更，PR 作者需先同步最新 dev 到自己分支
- 在功能分支解决冲突并重新推送
- 冲突解决后重新执行测试，再继续评审
### 常用命令：
   ```bash
   git switch feature/任务名
   git merge origin/dev
   #（解决冲突后）
   git add .
   git commit -m "chore: resolve merge conflicts with dev"
   git push
   ```

## 合并后清理
- 合并完成后删除远程功能分支
- 本地也删除已合并分支并清理远程引用
### 常用命令：
   ```bash
   - git branch -d feature/任务名 #删除本地分支
   - git push origin --delete feature/任务名 #删除远程分支
   - git fetch -p #清理远程已删除分支的引用
   ```