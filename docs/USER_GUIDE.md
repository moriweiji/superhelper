# SuperHelper 用户指南 v2.0

## 5秒上手

SuperHelper基于专家级咨询机制，帮你获得准确的SuperClaude命令推荐。

### 系统要求

**必需工具**：
- ✅ Claude Code已安装
- ✅ deepwiki MCP工具已配置（核心依赖）
- ✅ 网络连接正常

**可选工具**：
- sequential-thinking MCP工具（需求分析）
- graphiti-memory MCP工具（用户偏好记忆）

### 安装

**方式1: 复制文件（推荐）**
```bash
# 在superhelper项目目录
cp .claude/commands/superh.md ~/.claude/commands/
```

**方式2: 开发模式**
```bash
# 在superhelper项目目录，直接测试
claude-code
@superh "你的需求"
```

### 验证安装

```bash
# 测试SuperHelper是否正常工作
@superh "测试"
```

如果提示需要deepwiki，请确保MCP工具正确配置。

## 使用指南

### 基本语法

```bash
@superh "需求描述"
```

**重要**：描述越具体，推荐越准确！

### 优质需求描述示例

```bash
# ✅ 好的描述
@superh "分析React项目的性能瓶颈"
@superh "设计微服务架构的用户认证系统"
@superh "部署Node.js应用到生产环境"

# ❌ 模糊的描述
@superh "优化"
@superh "分析"
@superh "帮我"
```

## 使用示例

### 单命令推荐

```bash
@superh "React项目代码审查"

✅ deepwiki专家推荐结果 - 质量审核通过！

/analyze --code --react --persona-frontend --think "
🎯 任务：React项目代码质量分析
📋 目标：识别问题和改进建议
➡️ 下一步：/improve --quality
"

📝 参数解释（deepwiki专业分析）
- --code: 代码质量分析，检查结构和可维护性
- --react: React特定分析模式
- --persona-frontend: 前端开发专家视角
- --think: 多文件分析，消耗~4K tokens

💯 推荐理由（基于deepwiki专业分析）
1. 为什么选择analyze命令: 代码审查需要先分析现状
2. 为什么这些参数组合: React项目需要前端专家视角
3. 预期效果: 获得专业的代码质量报告

➡️ 后续建议
/improve --react --quality "基于分析结果优化代码"
```

### 工作流推荐

```bash
@superh "构建全栈电商应用"

✅ deepwiki专家推荐结果 - 质量审核通过！

🚀 **全栈电商应用开发工作流**

**步骤 1/5: 需求分析和架构设计**
/design --fullstack --ecommerce --think-hard "
🎯 项目：电商应用系统架构设计
📋 当前阶段：需求分析和技术选型
🔗 依赖输入：业务需求、用户故事、技术约束
📤 期望输出：架构图、技术栈选择、API设计
➡️ 完成后执行：/build --frontend --react
"

**步骤 2/5: 前端开发**
[完整工作流继续...]
```

### 模糊需求处理

```bash
@superh "优化项目"

SuperHelper Think Harder引擎启动...

🤔 需求不够明确，我已向deepwiki咨询多种优化场景：

1. **代码质量优化**: /analyze --code --think
2. **性能优化**: /analyze --performance --profile  
3. **架构优化**: /analyze --architecture --think-hard

请选择你的具体需求，或提供更多细节信息。
```

## 错误处理

### deepwiki不可用

```bash
❌ SuperHelper需要deepwiki支持才能提供准确的SuperClaude命令推荐。

🔧 解决方案：
1. 检查网络连接
2. 确认deepwiki MCP工具已安装
3. 确认deepwiki服务正常运行

💡 为什么需要deepwiki？
- 确保推荐的命令和参数是最新的
- 避免过时或错误的信息
- 提供专业级的SuperClaude使用建议

请解决deepwiki问题后再次尝试。
```

### 推荐质量不满意

SuperHelper会自动迭代优化：

```bash
第1次推荐不满意 → 向deepwiki追问更详细信息
第2次推荐不满意 → 重新分析需求并查询
第3次推荐不满意 → 告知限制，建议澄清需求
```

## 高级用法

### 需求优化技巧

```bash
# 包含技术栈信息
@superh "优化React + TypeScript项目的打包性能"

# 指定环境和约束
@superh "部署Node.js API到AWS Lambda，要求冷启动时间<2秒"

# 明确目标和成功标准
@superh "重构遗留PHP代码，目标是提升50%的响应速度"
```

### 上下文利用

SuperHelper会智能利用项目上下文：

```bash
# 在React项目中
@superh "添加用户认证"
→ 自动推荐React相关的认证方案

# 在Python项目中  
@superh "添加用户认证"
→ 自动推荐Python/Django/Flask认证方案
```

## 常见问题

### Q: 推荐不准确怎么办？
A: 
1. 提供更具体的需求描述
2. 包含技术栈、环境、约束等信息
3. SuperHelper会自动迭代直到满意

### Q: deepwiki查询失败？
A: 
1. 检查网络连接
2. 确认MCP工具配置正确
3. 重启Claude Code

### Q: 响应速度慢？
A: deepwiki查询需要2-5秒，这是为了确保信息准确性。

### Q: 想要不同的推荐风格？
A: 在需求中指定：
- "简单方案" → 更直接的命令
- "详细方案" → 完整工作流
- "学习导向" → 更多解释和教学

## 故障排除

### 检查配置

```bash
# 检查superh.md是否存在
ls ~/.claude/commands/superh.md

# 检查MCP工具
# 在Claude Code中测试
@deepwiki "test"
```

### 重新安装

```bash
# 删除旧版本
rm ~/.claude/commands/superh.md

# 重新复制最新版本
cp .claude/commands/superh.md ~/.claude/commands/
```

## 卸载

```bash
rm ~/.claude/commands/superh.md
```

---

**记住**: SuperHelper v2.0追求的是**准确的专家级推荐**，而非快速的"凑合答案"。给一点时间让专家为你提供最佳建议！