# SuperHelper - SuperClaude命令智能推荐器

> 🚀 **一个专业的SuperClaude命令推荐引擎，基于deepwiki专家咨询机制，为用户提供精准的命令建议**


## 📖 项目简介

SuperHelper是一个为[SuperClaude](https://github.com/NomenAK/SuperClaude)用户设计的智能命令推荐器。它通过deepwiki专家咨询机制，分析用户需求并推荐最合适的SuperClaude命令组合，而不执行具体任务。

### 🎯 核心价值

- **🔬 专家级推荐**: 基于deepwiki的SuperClaude专业知识提供精准建议
- **✅ 零妥协准确性**: 宁可失败也不给错误建议，追求准确性第一
- **🔄 质量保证机制**: 双重验证确保推荐的命令有效性和合理性
- **🎨 用户体验优先**: 清晰的错误处理和明确的系统限制说明

## 🏗️ 项目架构

### 极简设计理念

```
用户需求 → 直接问deepwiki推荐 → 质量审核 → 不满意就再问 → 输出准确推荐
                                   ↓
                        deepwiki不可用 → 告诉用户安装deepwiki
```

### 核心组件

- **🧠 deepwiki专家顾问**: SuperClaude专业知识来源（主要工作者）
- **🔍 SuperHelper质量审核**: 验证推荐准确性（质量把关）
- **💭 sequential-thinking**: 智能需求分析和优化引擎


### 文件结构

```
superhelper/
├── .claude/
│   ├── settings.local.json         # Claude Code配置文件
│   └── commands/
│       └── superh.md              # 核心命令推荐逻辑
├── docs/
│   ├── ARCHITECTURE.md            # 详细架构说明
│   ├── PLAN.md                    # 开发计划
│   └── USER_GUIDE.md              # 用户使用指南
├── backup/
│   └── superh_new.md              # 架构演进备份
├── CLAUDE.md                      # 项目指令文档
└── README.md                      # 本文件
```

## 🚀 快速开始

### 系统要求

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI工具
- **必需**: [SuperClaude](https://github.com/NomenAK/SuperClaude)
- **必需**: [deepwiki MCP工具](https://docs.devin.ai/work-with-devin/deepwiki-mcp) - 核心依赖
- **推荐**: sequential-thinking MCP工具 - 用于复杂需求分析
- **可选**: graphiti-memory MCP工具 - 用于记忆用户偏好

### 安装使用

1. **克隆项目**
   ```bash
   git clone https://github.com/moriweiji/superhelper
   cd superhelper
   将`.claude/commands/superh.md`文件复制到`~/.claude/commands/`目录下或者你项目的`.claude/commands/`目录下
   ```

2. **配置MCP工具**（重要）
   确保已安装deepwiki MCP工具，这是SuperHelper的核心依赖
   # 添加sequential-thinking
    claude mcp add --scope user sequential-thinking npx @modelcontextprotocol/server-sequential-thinking
   # deepwiki
    claude mcp add --transport sse --scope user deepwiki https://mcp.deepwiki.com/sse

3. **开始使用**
   ```bash
   # 在Claude Code中使用
   /superh "项目分析"
   /superh "构建全栈应用"
   /superh "优化代码性能"
   ```

4. **注意事项**
   - 使用了`/superh`命令，获取到的推荐命令后，要么使用/clear，要么重新开启新的终端，由于上下文的存在，会污染命令执行的效果，严重的会导致进入到superh的死循环中。


## 💡 使用示例

### 基本用法

```bash
# 单命令推荐
/superh "项目分析"

# 复杂场景工作流推荐
/superh "构建React + Node.js全栈应用"

# 模糊需求自动优化
/superh "让代码跑得更快"
```

### 典型场景

- **📊 项目分析**: 代码结构分析、依赖关系梳理
- **🏗️ 功能开发**: 新功能实现、模块构建
- **⚡ 性能优化**: 代码优化、构建优化
- **🧪 质量保证**: 测试编写、代码审查
- **📚 文档生成**: API文档、使用指南

### 推荐输出格式

```bash
/analyze --persona-architect --think-hard "
🎯 任务：深度分析项目架构和依赖关系
📋 目标：识别潜在问题并提供优化建议
➡️ 下一步：/refactor --pattern-modern
"

📝 **参数解释**
- **--persona-architect**: 激活架构师人格，专注系统设计分析
- **--think-hard**: 启用深度思考模式，进行全面分析

💯 **推荐理由**
1. **analyze命令**: 最适合项目结构和代码质量分析
2. **architect人格**: 提供系统化的架构视角
3. **think-hard模式**: 确保分析的深度和完整性
```

## 🔧 工作原理

### 智能推荐流程

1. **需求分析**: 解析用户输入，识别核心需求
2. **专家咨询**: 直接询问deepwiki获取SuperClaude专业建议
3. **质量审核**: 验证命令有效性、参数合理性、解释完整性
4. **迭代优化**: 不满意就继续问deepwiki直到获得满意结果
5. **格式化输出**: 按标准格式提供推荐、解释和后续建议

### 质量保证机制

```yaml
审核标准:
  命令有效性:
    - 命令是否存在于SuperClaude中？
    - 参数组合是否合理？
    - 语法是否正确？
  
  推荐完整性:
    - 是否充分解释了选择理由？
    - 是否提供了预期效果？
    - 是否有后续步骤建议？
  
  用户体验:
    - 推荐是否匹配用户需求？
    - 复杂度是否适中？
    - 是否有必要的安全提示？
```

## 📚 文档

- [📐 架构说明](docs/ARCHITECTURE.md) - 详细的系统架构和设计理念
- [📋 开发计划](docs/PLAN.md) - 项目路线图和开发计划
- [📖 用户指南](docs/USER_GUIDE.md) - 详细的使用说明和最佳实践

## 🛠️ 技术特点

### 核心优势

- **🎯 极简架构**: 专注核心功能，避免不必要的复杂度
- **🔬 专家级咨询**: 基于deepwiki的SuperClaude专业知识
- **✅ 质量保证**: 双重验证确保推荐准确性
- **🔄 迭代改进**: 不满意就继续优化直到获得满意结果
- **🚫 零妥协准确性**: 宁可失败也不给错误建议

### 性能指标

- **准确性**: 基于最新SuperClaude项目信息
- **响应速度**: 取决于deepwiki查询（通常2-5秒）
- **资源占用**: 基本为零（纯Markdown + MCP工具）
- **维护成本**: 极低（主要依赖deepwiki专业知识）

## ⚠️ 重要说明

### 系统限制

- **仅推荐，不执行**: SuperHelper只推荐命令，不执行具体任务
- **依赖deepwiki**: 核心功能依赖deepwiki MCP工具的可用性
- **准确性第一**: 追求准确性，不接受"凑合的备选方案"

### 错误处理

```yaml
错误处理策略:
  deepwiki不可用:
    - 明确告知用户安装deepwiki要求
    - 不提供"凑合的备选方案"
    - 提供具体的解决步骤

  推荐质量不达标:
    - 最多尝试3次deepwiki查询
    - 持续迭代直到满意
    - 如仍不满意，告知限制并建议用户澄清需求
```

## 🤝 贡献

欢迎贡献代码、报告问题或提出改进建议！

### 开发指南

1. Fork项目
2. 创建特性分支
3. 提交更改
4. 推送到分支
5. 创建Pull Request

### 改进方向

- **专家咨询优化**: 改进向deepwiki提问的模板和策略
- **质量标准提升**: 根据用户反馈完善审核标准
- **用户体验**: 优化推荐格式、错误处理、说明文档
- **Think Harder引擎**: 改进模糊需求的处理逻辑

## 📄 许可证

本项目采用MIT许可证 - 查看 [LICENSE](LICENSE) 文件了解详情

## 🔗 相关链接

- [SuperClaude项目](https://github.com/NomenAK/SuperClaude) - 主项目
- [Claude Code文档](https://docs.anthropic.com/en/docs/claude-code) - 官方文档
- [deepwiki MCP工具](https://docs.devin.ai/work-with-devin/deepwiki-mcp) - 核心依赖

---

<div align="center">

**🚀 SuperHelper v2.0 - 专注、直接、有效的SuperClaude命令推荐器**

Made with ❤️ for SuperClaude community

</div>