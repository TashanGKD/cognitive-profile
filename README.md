# cognitive-profile

用于在持续对话中形成一份可修正的用户画像，让 Codex 在后续任务里更稳定地沿用用户的表达偏好、判断习惯、边界要求和需要校准的地方。

这个 skill 不追求给用户贴标签，也不记录无关隐私。它只处理会影响后续回答质量的偏好、纠错、长期习惯和明确的记忆边界。

## 适用场景

- 用户说“记住”“以后默认”“按我之前习惯”“别再这样”
- 用户纠正“这不像我”“太官方”“理解错了”
- 用户要求查看、删除、恢复或校准画像
- 普通任务中需要沿用已知偏好，但不应重新猜测用户

## 安装

把本仓库克隆到本地后，将整个目录复制到 Codex skills 目录：

```bash
git clone https://github.com/TashanGKD/cognitive-profile.git
cp -R cognitive-profile ~/.codex/skills/
```

Windows PowerShell 示例：

```powershell
git clone https://github.com/TashanGKD/cognitive-profile.git
Copy-Item -Recurse -Force .\cognitive-profile $env:USERPROFILE\.codex\skills\
```

## 目录结构

```text
SKILL.md
references/
  采集证据.md
  形成画像.md
  召回问答.md
  校准整理.md
```

## 使用方式

安装后，Codex 会根据 `SKILL.md` 的 frontmatter 和触发规则自动选择这个 skill。主要流程分为四类：

- 采集证据：从用户真实表达中提取可复用偏好。
- 形成画像：把零散线索整理成薄而准的画像。
- 召回问答：在普通任务里只召回最相关、最稳的部分。
- 校准整理：根据用户纠正更新、删除或降级画像内容。

## 维护原则

- 少写，写准，不凭空推断。
- 用户明确说“不要记录”时，优先处理边界。
- 画像服务后续回答质量，不服务人格判断。
- 材料少时画像要薄，不能为了完整而放大猜测。
