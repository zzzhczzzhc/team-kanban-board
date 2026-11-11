# team-kanban-board 团队任务看板

一个新团队用于管理项目进度的「团队任务看板」应用。本项目采用业界标准的 **Fork + Pull Request** 工作流协作开发，技术栈刻意保持简单：**HTML5 + CSS3 + 原生 JavaScript（Vanilla JS）**，不使用任何框架，数据存储在浏览器 `localStorage` 中，无后端数据库。

## 功能列表

| 功能 | 说明 | 负责人 |
|------|------|--------|
| 创建任务 | 输入标题、选择优先级，新任务进入「待办」列 | 前端开发者 B |
| 删除任务 | 每张卡片提供删除按钮，可移除任务 | 前端开发者 B |
| 看板 UI 布局与卡片展示 | 三列看板（待办 / 进行中 / 已完成），卡片含标题、优先级标签、时间 | 前端开发者 A |
| 拖拽移动任务 | 拖拽卡片到其他列即可更新任务状态 | 前端开发者 C |

## 本地运行

直接用浏览器打开 `index.html` 即可，无需安装任何依赖：

```bash
# 或启动一个简单的静态服务
python3 -m http.server 8080
# 然后访问 http://localhost:8080
```

## Git 协作工作流（本团队约定）

1. **中央仓库**：由项目负责人创建 `team-kanban-board` 公开仓库，并为 `main` 分支启用保护规则（所有 PR 必须经至少一人审查后才能合并）。
2. **Fork**：每位开发者 Fork 中央仓库到自己账户，拥有独立副本。
3. **克隆与配置远程**：

   ```bash
   git clone https://github.com/YOUR_USERNAME/team-kanban-board.git
   cd team-kanban-board
   git remote add upstream https://github.com/PROJECT_OWNER_USERNAME/team-kanban-board.git
   git remote -v   # 应能看到 origin（你的 fork）和 upstream（原始仓库）
   ```

4. **功能开发分支**：开发前先同步 upstream/main，再建功能分支，命名清晰（如 `feature/ui-layout`）：

   ```bash
   git pull upstream main
   git checkout -b feature/ui-layout
   ```

5. **提交与推送**：提交信息必须清晰、有意义（遵循 Conventional Commits 风格）：

   ```bash
   git add .
   git commit -m "feat: add basic kanban board columns and header"
   git push origin feature/ui-layout
   ```

6. **创建 PR**：从自己的功能分支向原始仓库 `main` 创建 Pull Request，标题简明，描述详尽（改了什么、为什么、如何测试、附截图）。
7. **代码审查**：除 PR 作者外所有成员都参与审查，评论保持专业与建设性；作者根据意见 push 新提交，PR 自动更新。
8. **合并**：PR 获得 Approve 后由项目负责人以 **Squash and merge** 方式合并，随后删除已合并的功能分支。
9. **保持同步**：合并后其他开发者执行：

   ```bash
   git checkout main
   git pull upstream main
   git checkout feature/your-feature
   git merge main   # 将 main 最新代码合入自己的功能分支，避免未来冲突
   ```

## 分支命名规范

- `feature/<功能名>`：新功能，如 `feature/ui-layout`、`feature/task-create-delete`、`feature/drag-and-drop`
- `fix/<问题名>`：缺陷修复
- `docs/<主题>`：文档更新
