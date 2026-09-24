# 摄影作品集选片助手

一个用于摄影选片与作品集策展的 Agent Skill。它会根据素材状态选择合适的判断模式，而不是用同一套评分标准处理原片、成片和主题作品集。

## 能做什么

- 原片初选：从大量原片和连拍中找出值得后期的照片
- 成片精选：从已修照片中挑选真正适合展示的作品
- 作品集策展：围绕主题、节奏和组合贡献组织作品集
- 相似照片去重：给出组内最佳、备选及具体取舍理由
- 默认只读：不会擅自移动、修改或删除原图

## 安装到 Codex

将仓库克隆到 Codex 的 Skills 目录：

```powershell
git clone https://github.com/mixiuan21-HLF/photo-portfolio-curator.git "$env:USERPROFILE\.codex\skills\photo-portfolio-curator"
```

重新打开 Codex 后，可以直接说：

```text
使用 $photo-portfolio-curator，帮我审阅 D:\Photos 里的照片，做成片精选。
```

也可以不显式点名。安装后，Agent 可根据任务描述自动调用该 Skill。

## 安装到其他智能体

如果平台支持以 `SKILL.md` 为入口的 Agent Skill，可导入整个仓库或把仓库放进该平台的 Skills 目录。不同平台的目录名称和导入方式可能不同，但请保留以下结构：

```text
photo-portfolio-curator/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── shoot-culling.md
    ├── edited-selection.md
    └── portfolio-curation.md
```

如果平台不支持这种 Skill 结构，可以把 `SKILL.md` 作为系统提示词使用，并确保它能够读取 `references/` 中对应模式的规则。

## 使用方式

### 原片初选

```text
帮我初选这个文件夹里的拍摄原片，找出值得后期的照片，并对连拍去重。
```

### 成片精选

```text
这些照片都已经修完，不限定主题。帮我挑出真正适合公开展示的作品。
```

### 作品集策展

```text
以“城市夜行”为主题，从这个文件夹中挑选 12 张，并给出作品集顺序和每张的作用。
```

## 设计原则

技术完美不等于好照片，好照片也不一定适合当前作品集。这个 Skill 会分别判断单张是否成立、是否为相似组最佳版本，以及它是否对当前作品集有贡献。

## 隐私与文件安全

Skill 默认只读。复制、移动、改名、覆盖、编辑或删除文件前，必须取得用户明确授权。仓库本身不包含任何示例照片、个人作品或本地路径。

## 许可证

本项目采用 [MIT License](LICENSE)。
