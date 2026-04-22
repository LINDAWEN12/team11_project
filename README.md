# My AI Project
项目简介：
一款校园互助平台

开发人员：陈陆源，刘扬，林天问，苗子轩

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

## 获取项目

1. 克隆仓库到本地
   ```bash
   # 使用 HTTPS 克隆
   git clone https://github.com/LINDAWEN12/team11_project.git
   # 或者使用 SSH 克隆（需要配置 SSH 密钥）
   git clone git@github.com:LINDAWEN12/team11_project.git
   ```
2. 查看所有远程分支
   ```bash
   git branch -r
   ```
3. 克隆并追踪需要的分支
   ```bash
   #创建并切换到本地分支，同时追踪对应的远程分支
   git switch -c <本地分支名> --track origin/<远程分支名> 
   ```

## 开发流程
1. 同步远程代码
   ```bash
   git fetch origin #获取远程仓库代码
   git switch <本地分支名> #切换到某本地分支
   git pull origin <远程分支名> #拉取远程分支的最新代码
   ```

2. 从 dev 切出个人任务分支
   ```bash
   git switch -c <本地分支名> #创建并切换到新分支
   ```

3. 开发并提交
   ```bash
   git add .
   git commit -m "feat: 描述本次改动"
   ```

4. 推送分支到远程
   ```bash
   #远程分支不存在时会自动创建，-u 参数会将本地分支与远程分支关联
   git push -u origin <远程分支名> 
   ```

5. 发起 Pull Request 到 dev 分支
   - 确保本地的 dev 分支是最新的
   - 在本地确认分支能够成功合并 dev，否则先解决所有冲突
   - 在 GitHub 上创建 PR
   - base 选择 dev
   - compare 选择对应的功能分支
   - 填写改动说明、测试说明、影响范围
   - 提交 PR

6. 发起 Pull Request 到 main 分支
   - 仅当 dev 分支的功能稳定且经过充分测试后才发起 PR 到 main
   - base 选择 main
   - compare 选择 dev
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
   git switch <本地分支名>
   git fetch origin
   git merge origin/dev
   #（解决冲突后）
   git add .
   git commit -m "<提交信息>"
   git push
   ```

## 合并后清理
- 合并完成后删除远程功能分支
- 本地也删除已合并分支并清理远程引用
### 常用命令：
   ```bash
   - git branch -d <本地分支名> #删除本地分支
   - git push origin --delete <远程分支名> #删除远程分支
   - git fetch -p #清理远程已删除分支的引用
   ```