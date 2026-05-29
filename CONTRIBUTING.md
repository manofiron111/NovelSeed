# 贡献指南

感谢关注 NovelSeed！

## 环境搭建

```bash
git clone https://github.com/manofiron111/NovelSeed.git
cd NovelSeed
```

NovelSeed 是一个 Agent Skills 仓库，不需要编译或安装依赖。你只需要一个支持 Agent Skills 格式的 AI 编码助手（Claude Code、Cursor、Hermes 等）。

## 贡献方式

### 新增类型模板

在 `skills/novelseed/references/genres/` 下创建新文件。模板必须包含：
- 世界观默认值
- 核心爽点设计
- 读者预期
- 常见陷阱/避坑

### 改进方法论

编辑 `skills/novelseed/SKILL.md` 或相应 reference 文件。保持：
- 第三人称
- 通用化（不引用具体作品）
- 提供"为什么"而不仅仅是"做什么"

## 绝对不要提交

- 真实小说内容（使用通用示例代替）
- 任何平台的发布细节
- API 密钥、Token、密码
- 个人信息
