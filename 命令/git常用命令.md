### **1. 配置相关**


```bash
# 设置全局用户名和邮箱
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# 查看当前配置
git config --list
```
---

### **2. 仓库初始化与克隆**

```bash
# 初始化新仓库
git init

# 克隆远程仓库
git clone <远程仓库URL>
```
---

### **3. 基本操作**

```bash
# 查看仓库状态（修改/未跟踪的文件）
git status

# 添加文件到暂存区
git add <文件名>       # 添加指定文件
git add .             # 添加所有修改和新文件

# 提交更改到本地仓库
git commit -m "提交说明"

# 查看提交历史
git log               # 详细历史
git log --oneline     # 简洁单行显示
git log --graph       # 图形化分支历史
```
---

### **4. 分支管理**

```bash
# 查看分支
git branch            # 本地分支
git branch -a         # 查看所有分支（包括远程）

# 创建分支
git branch <分支名>

# 切换分支
git checkout <分支名>
git switch <分支名>    # Git 2.23+ 推荐方式

# 创建并切换分支
git checkout -b <新分支名>
git switch -c <新分支名>

# 合并分支（将指定分支合并到当前分支）
git merge <分支名>

# 删除分支
git branch -d <分支名>  # 安全删除（已合并）
git branch -D <分支名>  # 强制删除（未合并）
```

---

### **5. 远程仓库操作**

```bash
# 关联远程仓库
git remote add origin <远程仓库URL>

# 推送本地分支到远程
git push -u origin <分支名>   # 首次推送需 -u
git push origin main         # 后续推送

# 拉取远程分支更新
git pull origin <分支名>      # 拉取并合并
git fetch origin            # 仅获取远程更新（不自动合并）

# 查看远程仓库信息
git remote -v

# 删除远程分支
git push origin --delete <分支名>
```

---

### **6. 撤销与恢复**

```bash
# 撤销工作区的修改（未添加到暂存区）
git restore <文件名>       # Git 2.23+ 推荐方式
git checkout -- <文件名>   # 旧版本写法

# 撤销暂存区的修改（已 add 但未 commit）
git restore --staged <文件名>

# 回退到某个提交（谨慎操作）
git reset --hard <commit_id>   # 彻底回退
git reset --soft <commit_id>   # 保留修改到工作区

# 撤销某次提交（生成新提交）
git revert <commit_id>
```

---

### **7. 暂存更改（Stash）**

```bash
# 临时保存工作区修改
git stash

# 查看暂存列表
git stash list

# 恢复最近暂存的修改
git stash pop

# 删除暂存记录
git stash drop
```

---

### **8. 标签管理**

```bash
# 创建标签
git tag <标签名>          # 轻量标签
git tag -a <标签名> -m "说明"  # 附注标签

# 推送标签到远程
git push origin --tags

# 删除标签
git tag -d <标签名>
git push origin :refs/tags/<标签名>  # 删除远程标签
```

---

### **9. 比较差异**

```bash
# 比较工作区与暂存区
git diff

# 比较暂存区与最新提交
git diff --staged

# 比较两个提交之间的差异
git diff <commit_id1> <commit_id2>
```
---

### **10. 其他实用命令**

```bash
# 查看文件修改历史
git blame <文件名>

# 强制拉取远程覆盖本地（谨慎！）
git fetch --all
git reset --hard origin/main

# 交互式变基（修改提交历史）
git rebase -i <commit_id>
```

