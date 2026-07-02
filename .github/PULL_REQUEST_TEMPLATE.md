<!--
For Chinese contributors: 请直接用中文填写。
For English contributors: please fill in English. All fields marked (EN) accept English.
-->

## PR Type

- [ ] fix
- [ ] feat
- [ ] refactor
- [ ] docs
- [ ] chore
- [ ] test

## Background And Problem

请描述当前问题、影响范围与触发场景。  
*(EN) Describe the problem, its impact, and what triggers it.*

## Scope Of Change

请列出本 PR 修改的模块和文件范围。  
*(EN) List the modules and files changed in this PR.*

> 注意：请按实际 `git diff` 全量列出文件范围（建议注明文件总数），避免遗漏文档/后端/API/前端文件导致描述不一致。

> 若本 PR 修改了 `.github/PULL_REQUEST_TEMPLATE.md`、`.github/copilot-instructions.md`、`AGENTS.md`、`.github/instructions/*` 或 `.claude/skills/**` 等协作与治理文件，请补充“变更原因 + 影响面 + 回滚方式（默认 revert）”到 Summary / Compatibility / Rollback，避免 Scope 与描述不一致。

> 建议先执行并粘贴以下命令输出，避免与实际 diff 不一致：

```bash
BASE_REF=$(git merge-base HEAD origin/main)
git diff --stat "$BASE_REF"..HEAD
git diff --name-only "$BASE_REF"..HEAD
```

- 文件总数 / 变更行数（建议粘贴 `git diff --stat "$BASE_REF"..HEAD`）：
- 文件清单（按实际 diff 全量，逐项列出）：
- 文档更新文件（`docs/*`）：

## Issue Link

必须填写以下之一 / Fill in one of:
- `Fixes #<issue_number>`
- `Refs #<issue_number>`
- 无 Issue 时说明原因与验收标准 / If no issue, explain the motivation and acceptance criteria

## Verification Commands And Results

请填写你实际执行过的命令和关键结果（不要只写"已测试"）。  
*(EN) Paste the commands you actually ran and their key output (don't just write "tested"):*

```bash
# example
./scripts/ci_gate.sh
python -m pytest -m "not network"
```

> `Full-suite note` 必须与当次 PR 的当前 Head CI 结果保持一致；若本地复现存在环境相关失败，请明确标注“本地环境差异”并给出 GitHub CI 的结论与链接。  
> 请避免保留与本 PR 无关的历史失败措辞，按本次实际结果填报。
> 如历史描述中仍保留 `./scripts/ci_gate.sh` 失败记录，请先改为当前 Head CI 状态或说明与 Head CI 的差异来源。
> 若 `Full-suite note` 与当前 Head CI 不一致，PR 文本不完整，请先更新 PR 描述后再提交。

- 请在下面按实际结果填写并与 `Full-suite note` 保持一致（任一未填视为信息缺失）：
  - ai-governance：`pass` / `fail`，附链接
  - backend-gate：`pass` / `fail`，附链接
  - docker-build：`pass` / `fail`，附链接
  - web-gate：`pass` / `fail`，附链接
  - 若本 PR 修改 `.github/PULL_REQUEST_TEMPLATE.md` 等流程模板协作文件，请先说明变更必要性、影响边界，并明确回滚方式（默认 `revert this PR`）；否则请在下一版中拆为单独 chore PR。

关键输出/结论 / Key output & conclusion:

- 【必填】当前 Head CI：`ai-governance:pass / backend-gate:pass / docker-build:pass / web-gate:pass`（按实际结果替换）并附对应链接。  
- 若需保留本地失败现象，请在同段写明“本地环境差异 + 当前 CI 通过/失败结果 + CI 链接”。  
- 若全部通过，需补充一句：`当前状态：全部通过（pass）`，并明确 Head CI 全部为 pass。  

- 建议将本行直接粘贴到 PR 描述正文首段：`当前 Head CI：ai-governance:pass / backend-gate:pass / docker-build:pass / web-gate:pass`（仅示例，按实际结果替换）。

> 若上述核验项与 PR 文本冲突，建议先更新 PR 描述再提交，避免审查因状态不一致被阻塞。

## Visual Evidence (if applicable)

【必填】若本 PR 修改报告格式、报告渲染效果或 Web UI 界面，请在此处附受影响报告 / 页面截图；涉及前后差异时，优先附前后对比。Issue / PR 过程截图、审查截图、一次性验收截图和临时可视证据请放在 PR 描述、PR 评论、GitHub 附件、Actions artifact 或外部可访问链接中，不要作为仓库文件合入。
*(EN) If this PR changes report formatting, report rendering, or Web UI, attach screenshots of the affected report/page here; before/after screenshots are preferred when relevant. Issue/PR process screenshots, review screenshots, one-off acceptance screenshots, and temporary visual evidence should be linked from the PR body/comments, GitHub attachments, Actions artifacts, or external accessible evidence; do not commit them as repository files.)*

> 如截图无法获取，请在“原因”中明确写明替代证据（如 Playwright/e2e 产物路径、审查链接）及其可追溯命令，不得留空。涉及 Web 设置/报告渲染变更时，需确保截图或替代证据明确指向变更项。
>
> 若本 PR 修改 Web UI，建议至少补一条可复现路径，例如（优先 settings page）：
>
> - Playwright 截图产物：`apps/dsa-web/e2e/smoke.spec.ts`（`cd apps/dsa-web && npx playwright test e2e/smoke.spec.ts --grep "settings page renders title and save actions after login"`）
> - 审查证据链接：可直接使用 Actions 产物、GitHub 评论附件或外部可访问链接。

> 替代证据模板（设置页变更建议）：
> - 命令：`cd apps/dsa-web && npx playwright test e2e/smoke.spec.ts --grep "settings page"`
> - 产物路径：`apps/dsa-web/test-results/**/smoke-setting