# 如何使用本个人 AI 档案（周晨旭 / 19999321-bao）

> 一份档案，多个 AI 共用。仓库公开只读；写入需你的 GitHub Token。

目标仓库（推送后）：https://github.com/19999321-bao/personal-ai-archive  
原始读取基址：https://raw.githubusercontent.com/19999321-bao/personal-ai-archive/main/

---

## 一、把「接入指令」粘贴到 ChatGPT / Claude / Gemini / Grok

打开任意能联网的大模型对话，把下面整段粘贴为第一条消息（或系统提示）：

```
你已接入我的个人AI档案仓库（GitHub 公开仓库）：
  仓库：https://github.com/19999321-bao/personal-ai-archive
  原始读取基址：https://raw.githubusercontent.com/19999321-bao/personal-ai-archive/main/
请先读取 ai-integration.md 了解权限与写入规则，再按需读取 identity/ 与 workflow/ 作为长期上下文。
完成任务后，按「自动写入规则」把可复用的经验/偏好追加到对应文件。
我是周晨旭；正式材料用高标准公文写法；中文交流；歧义先问；发现判断有误须主动质疑。
```

### 各平台注意点

| 平台 | 怎么用 |
|------|--------|
| **ChatGPT** | 开启联网/浏览后粘贴上述指令；也可把 `identity/profile.md` 与 `workflow/communication-style.md` 内容贴进自定义 GPT 说明 |
| **Claude** | 粘贴指令并让其打开 raw URL；或把核心 md 上传到 Claude Projects 知识库 |
| **Gemini** | 粘贴指令并开启联网，让其抓取 raw URL |
| **Grok / Grok Bot** | 粘贴指令；若本机已 clone，可直接读本地仓库路径 |

仓库推送完成前，可先把本地 `identity/`、`workflow/` 文件内容直接粘贴给 AI 作为临时上下文。

---

## 二、如何更新 identity（只读区，须人工确认）

1. 只改 `identity/` 与 `workflow/` 中的稳定事实（姓名、岗位、沟通规则等）。
2. AI **不得擅自改写** READONLY 文件；若 AI 建议修改，须你确认后再提交。
3. 本地修改后：

```bash
cd personal-ai-archive
git add identity/ workflow/
git commit -m "identity: 更新某某字段"
git push
```

4. 公开仓库禁止写入：密码、密钥、内部研发费用/利润、未公开手机号/邮箱等。

---

## 三、AI 如何向 memory 追加（读写区）

- **可追加**：`memory/`、`skills/`、`archive/`（以及 `workflow/tools.md` 底部「AI 建议区」）。
- **规则**：只追加、不覆盖；按 `ai-integration.md` 第 4 节标准条目格式，插到「自动写入区」顶部。
- **提交说明示例**：`memory: preferences - 某某偏好`
- 无 PAT / 无写入权限时：让 AI 产出待追加 Markdown 文本，由你本地粘贴并 `git commit` + `git push`。
- 误写：用 `git revert` 或 GitHub 网页 History 回退（见 `BRANCH-PROTECTION.md`）。

标准条目格式：

```markdown
### YYYY-MM-DD HH:MM | 简短标题
- 来源：ChatGPT/Claude/Gemini/Grok/人工
- 情境：一句话背景
- 结论/偏好/产出：可复用的结论
- 关联：相关 identity/goals.md 或其它文件
```

---

## 四、首次推送到 GitHub（公开仓库）

若父流程已创建空仓库 `19999321-bao/personal-ai-archive`，在含本档案的目录执行：

```bash
cd personal-ai-archive
git remote remove origin 2>/dev/null || true
git remote add origin https://github.com/19999321-bao/personal-ai-archive.git
git branch -M main
git push -u origin main
```

或配置 Token 后使用仓库自带脚本：

```bash
export GITHUB_USERNAME=19999321-bao
export GH_TOKEN=你的PersonalAccessToken   # 需 repo 权限；勿把 Token 写进仓库文件
bash push-to-github.sh
```

推送成功后，把第一节的接入指令发给各 AI 即可。

---

## 五、公开仓库安全须知（必读）

1. 本仓库设计为 **Public**，互联网上任何人与任何 AI 都可读。
2. **严禁**写入：密码、Token、密钥、银行卡、内部金额、未公开手机/邮箱、公司内部未脱敏材料。
3. 知识产权只写已确认公开口径（例如专利 5、软著 3）；不写具体研发费用或利润。
4. 读开放、写受控：写入需要你的 GitHub PAT；建议开启 main 分支保护（见 `BRANCH-PROTECTION.md`）。
5. 公司文件仍放在本机 `D:\工作` 等本地路径，**不要**整目录提交到本公开仓库。

---

## 六、目录权限速查

| 目录 | AI 权限 | 说明 |
|------|---------|------|
| `identity/` | READONLY | 身份·职业·目标，仅人工改 |
| `workflow/` | READONLY（tools 建议区可追加） | 习惯·工具·沟通·优先级 |
| `memory/` | READWRITE 追加 | 经验·决策·偏好 |
| `skills/` | READWRITE 追加 | 技能·学习·待提升 |
| `archive/` | READWRITE 追加 | 项目·已完成任务 |

更多细节见 `ai-integration.md`。
