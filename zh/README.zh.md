<div align="center">
    <img src="./media/logo_large.webp" alt="Spec Kit 徽标" width="200" height="200"/>
    <h1>🌱 Spec Kit</h1>
    <h3><em>更快构建高质量软件。</em></h3>
</div>

<p align="center">
    <strong>一个开源工具包，让你专注于产品场景和可预测结果，而不是从零开始对每一部分都进行 vibe coding。</strong>
</p>

<p align="center">
    <a href="https://github.com/github/spec-kit/releases/latest"><img src="https://img.shields.io/github/v/release/github/spec-kit" alt="Latest Release"/></a>
    <a href="https://github.com/github/spec-kit/stargazers"><img src="https://img.shields.io/github/stars/github/spec-kit?style=social" alt="GitHub stars"/></a>
    <a href="https://github.com/github/spec-kit/blob/main/LICENSE"><img src="https://img.shields.io/github/license/github/spec-kit" alt="License"/></a>
    <a href="https://github.github.io/spec-kit/"><img src="https://img.shields.io/badge/docs-GitHub_Pages-blue" alt="Documentation"/></a>
</p>

---

## 目录

- [🤔 什么是 Spec-Driven Development？](#-什么是-spec-driven-development)
- [⚡ 快速开始](#-快速开始)
- [📽️ 视频概览](#️-视频概览)
- [🧩 社区扩展](#-社区扩展)
- [🎨 社区预设](#-社区预设)
- [🚶 社区演练](#-社区演练)
- [🛠️ 社区伙伴项目](#️-社区伙伴项目)
- [🤖 支持的 AI 编码代理集成](#-支持的-ai-编码代理集成)
- [🔧 Specify CLI 参考](#-specify-cli-参考)
- [🧩 打造你的 Spec Kit：扩展与预设](#-打造你的-spec-kit扩展与预设)
- [📚 核心理念](#-核心理念)
- [🌟 开发阶段](#-开发阶段)
- [🎯 实验目标](#-实验目标)
- [🔧 前置条件](#-前置条件)
- [📖 进一步学习](#-进一步学习)
- [📋 详细流程](#-详细流程)
- [🔍 故障排查](#-故障排查)
- [💬 支持](#-支持)
- [🙏 致谢](#-致谢)
- [📄 许可证](#-许可证)

## 🤔 什么是 Spec-Driven Development？

Spec-Driven Development **颠覆了**传统软件开发方式。几十年来，代码一直是核心——规格说明只是脚手架，一旦“真正的编码工作”开始就会被丢弃。Spec-Driven Development 改变了这一点：**规格本身可执行**，可以直接生成可运行实现，而不只是提供指导。

## ⚡ 快速开始

### 1. 安装 Specify CLI

选择你偏好的安装方式：

> **重要：** Spec Kit 唯一官方且持续维护的包都发布在这个 GitHub 仓库中。PyPI 上任何同名包都**不**隶属于本项目，也不由 Spec Kit 维护者维护。请始终按下方方式直接从 GitHub 安装。

#### 选项 1：持久安装（推荐）

安装一次，处处可用。为稳定性建议固定到某个发布标签（最新版本见 [Releases](https://github.com/github/spec-kit/releases)）：

```bash
# Install a specific stable release (recommended — replace vX.Y.Z with the latest tag)
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git@vX.Y.Z

# Or install latest from main (may include unreleased changes)
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git

# Alternative: using pipx (also works)
pipx install git+https://github.com/github/spec-kit.git@vX.Y.Z
pipx install git+https://github.com/github/spec-kit.git
```

然后验证已安装正确版本：

```bash
specify version
```

并直接使用工具：

```bash
# Create new project
specify init <PROJECT_NAME>

# Or initialize in existing project
specify init . --integration copilot
# or
specify init --here --integration copilot

# Check installed tools
specify check
```

如需升级 Specify，请查看[升级指南](./docs/upgrade.md)获取详细说明。快速升级如下：

```bash
uv tool install specify-cli --force --from git+https://github.com/github/spec-kit.git@vX.Y.Z
# pipx users: pipx install --force git+https://github.com/github/spec-kit.git@vX.Y.Z
```

#### 选项 2：一次性使用

无需安装，直接运行：

```bash
# Create new project (pinned to a stable release — replace vX.Y.Z with the latest tag)
uvx --from git+https://github.com/github/spec-kit.git@vX.Y.Z specify init <PROJECT_NAME>

# Or initialize in existing project
uvx --from git+https://github.com/github/spec-kit.git@vX.Y.Z specify init . --integration copilot
# or
uvx --from git+https://github.com/github/spec-kit.git@vX.Y.Z specify init --here --integration copilot
```

**持久安装的优势：**

- 工具会保留安装并在 PATH 中可用
- 不需要创建 shell alias
- 可通过 `uv tool list`、`uv tool upgrade`、`uv tool uninstall` 更好地管理工具
- shell 配置更简洁

#### 选项 3：企业 / Air-Gapped 安装

如果你的环境无法访问 PyPI 或 GitHub，请查看 [Enterprise / Air-Gapped Installation](./docs/installation.md#enterprise--air-gapped-installation) 指南，了解如何在联网机器上使用 `pip download` 创建可移植、按操作系统区分的 wheel 包。

### 2. 建立项目原则

在项目目录中启动你的编码代理。多数代理将 spec-kit 暴露为 `/speckit.*` slash commands；Codex CLI 的 skills 模式则使用 `$speckit-*`。

使用 **`/speckit.constitution`** 命令创建项目治理原则与开发指南，指导后续所有开发。

```bash
/speckit.constitution Create principles focused on code quality, testing standards, user experience consistency, and performance requirements
```

### 3. 创建规格

使用 **`/speckit.specify`** 命令描述你要构建什么。关注 **what** 和 **why**，而不是技术栈。

```bash
/speckit.specify Build an application that can help me organize my photos in separate photo albums. Albums are grouped by date and can be re-organized by dragging and dropping on the main page. Albums are never in other nested albums. Within each album, photos are previewed in a tile-like interface.
```

### 4. 创建技术实现计划

使用 **`/speckit.plan`** 命令提供你的技术栈和架构选择。

```bash
/speckit.plan The application uses Vite with minimal number of libraries. Use vanilla HTML, CSS, and JavaScript as much as possible. Images are not uploaded anywhere and metadata is stored in a local SQLite database.
```

### 5. 拆解为任务

使用 **`/speckit.tasks`** 从实现计划生成可执行任务清单。

```bash
/speckit.tasks
```

### 6. 执行实现

使用 **`/speckit.implement`** 执行全部任务，并按计划构建功能。

```bash
/speckit.implement
```

详细分步说明见我们的[完整指南](./spec-driven.md)。

## 📽️ 视频概览

想看 Spec Kit 实际运行效果？观看我们的[视频概览](https://www.youtube.com/watch?v=a9eR1xsfvHg&pp=0gcJCckJAYcqIYzv)！

[![Spec Kit video header](/media/spec-kit-video-header.jpg)](https://www.youtube.com/watch?v=a9eR1xsfvHg&pp=0gcJCckJAYcqIYzv)

## 🧩 社区扩展

> [!NOTE]
> 社区扩展由各自作者独立创建和维护。GitHub 与 Spec Kit 维护者可能会审核将条目添加到社区目录的 pull request（主要针对格式、目录结构或策略合规），但他们**不会审核、审计、背书或支持扩展代码本身**。社区扩展网站同样是第三方资源。安装前请审阅扩展源码，并自行判断是否使用。

🔍 **在[Community Extensions website](https://speckit-community.github.io/extensions/) 浏览和搜索社区扩展。**

以下社区贡献扩展可见于 [`catalog.community.json`](extensions/catalog.community.json)：

**分类：**

- `docs` — 读取、校验或生成规格工件
- `code` — 评审、校验或修改源码
- `process` — 编排跨阶段工作流
- `integration` — 与外部平台同步
- `visibility` — 报告项目健康度或进展

**影响：**

- `Read-only` — 仅生成报告，不修改文件
- `Read+Write` — 修改文件、创建工件或更新规格

| Extension | Purpose | Category | Effect | URL |
|-----------|---------|----------|--------|-----|
| Agent Assign | Assign specialized Claude Code agents to spec-kit tasks for targeted execution | `process` | Read+Write | [spec-kit-agent-assign](https://github.com/xymelon/spec-kit-agent-assign) |
| AI-Driven Engineering (AIDE) | A structured 7-step workflow for building new projects from scratch with AI assistants — from vision through implementation | `process` | Read+Write | [aide](https://github.com/mnriem/spec-kit-extensions/tree/main/aide) |
| Architect Impact Previewer | Predicts architectural impact, complexity, and risks of proposed changes before implementation. | `visibility` | Read-only | [spec-kit-architect-preview](https://github.com/UmmeHabiba1312/spec-kit-architect-preview) |
| Archive Extension | Archive merged features into main project memory. | `docs` | Read+Write | [spec-kit-archive](https://github.com/stn1slv/spec-kit-archive) |
| Azure DevOps Integration | Sync user stories and tasks to Azure DevOps work items using OAuth authentication | `integration` | Read+Write | [spec-kit-azure-devops](https://github.com/pragya247/spec-kit-azure-devops) |
| Blueprint | Stay code-literate in AI-driven development: review a complete code blueprint for every task from spec artifacts before /speckit.implement runs | `docs` | Read+Write | [spec-kit-blueprint](https://github.com/chordpli/spec-kit-blueprint) |
| Branch Convention | Configurable branch and folder naming conventions for /specify with presets and custom patterns | `process` | Read+Write | [spec-kit-branch-convention](https://github.com/Quratulain-bilal/spec-kit-branch-convention) |
| Brownfield Bootstrap | Bootstrap spec-kit for existing codebases — auto-discover architecture and adopt SDD incrementally | `process` | Read+Write | [spec-kit-brownfield](https://github.com/Quratulain-bilal/spec-kit-brownfield) |
| Bugfix Workflow | Structured bugfix workflow — capture bugs, trace to spec artifacts, and patch specs surgically | `process` | Read+Write | [spec-kit-bugfix](https://github.com/Quratulain-bilal/spec-kit-bugfix) |
| Canon | Adds canon-driven (baseline-driven) workflows: spec-first, code-first, spec-drift. Requires Canon Core preset installation. | `process` | Read+Write | [spec-kit-canon](https://github.com/maximiliamus/spec-kit-canon/tree/master/extension) |
| Catalog CI | Automated validation for spec-kit community catalog entries — structure, URLs, diffs, and linting | `process` | Read-only | [spec-kit-catalog-ci](https://github.com/Quratulain-bilal/spec-kit-catalog-ci) |
| CI Guard | Spec compliance gates for CI/CD — verify specs exist, check drift, and block merges on gaps | `process` | Read-only | [spec-kit-ci-guard](https://github.com/Quratulain-bilal/spec-kit-ci-guard) |
| Checkpoint Extension | Commit the changes made during the middle of the implementation, so you don't end up with just one very large commit at the end | `code` | Read+Write | [spec-kit-checkpoint](https://github.com/aaronrsun/spec-kit-checkpoint) |
| Cleanup Extension | Post-implementation quality gate that reviews changes, fixes small issues (scout rule), creates tasks for medium issues, and generates analysis for large issues | `code` | Read+Write | [spec-kit-cleanup](https://github.com/dsrednicki/spec-kit-cleanup) |
| Conduct Extension | Orchestrates spec-kit phases via sub-agent delegation to reduce context pollution. | `process` | Read+Write | [spec-kit-conduct-ext](https://github.com/twbrandon7/spec-kit-conduct-ext) |
| Confluence Extension | Create a doc in Confluence summarizing the specifications and planning files | `integration` | Read+Write | [spec-kit-confluence](https://github.com/aaronrsun/spec-kit-confluence) |
| DocGuard — CDD Enforcement | Canonical-Driven Development enforcement. Validates, scores, and traces project documentation with automated checks, AI-driven workflows, and spec-kit hooks. Zero NPM runtime dependencies. | `docs` | Read+Write | [spec-kit-docguard](https://github.com/raccioly/docguard) |
| Extensify | Create and validate extensions and extension catalogs | `process` | Read+Write | [extensify](https://github.com/mnriem/spec-kit-extensions/tree/main/extensify) |
| Fix Findings | Automated analyze-fix-reanalyze loop that resolves spec findings until clean | `code` | Read+Write | [spec-kit-fix-findings](https://github.com/Quratulain-bilal/spec-kit-fix-findings) |
| FixIt Extension | Spec-aware bug fixing — maps bugs to spec artifacts, proposes a plan, applies minimal changes | `code` | Read+Write | [spec-kit-fixit](https://github.com/speckit-community/spec-kit-fixit) |
| Fleet Orchestrator | Orchestrate a full feature lifecycle with human-in-the-loop gates across all SpecKit phases | `process` | Read+Write | [spec-kit-fleet](https://github.com/sharathsatish/spec-kit-fleet) |
| GitHub Issues Integration 1 | Generate spec artifacts from GitHub Issues - import issues, sync updates, and maintain bidirectional traceability | `integration` | Read+Write | [spec-kit-github-issues](https://github.com/Fatima367/spec-kit-github-issues) |
| GitHub Issues Integration 2 | Creates and syncs local specs from an existing GitHub issue | `integration` | Read+Write | [spec-kit-issue](https://github.com/aaronrsun/spec-kit-issue) |
| Iterate | Iterate on spec documents with a two-phase define-and-apply workflow — refine specs mid-implementation and go straight back to building | `docs` | Read+Write | [spec-kit-iterate](https://github.com/imviancagrace/spec-kit-iterate) |
| Jira Integration | Create Jira Epics, Stories, and Issues from spec-kit specifications and task breakdowns with configurable hierarchy and custom field support | `integration` | Read+Write | [spec-kit-jira](https://github.com/mbachorik/spec-kit-jira) |
| Learning Extension | Generate educational guides from implementations and enhance clarifications with mentoring context | `docs` | Read+Write | [spec-kit-learn](https://github.com/imviancagrace/spec-kit-learn) |
| MAQA — Multi-Agent & Quality Assurance | Coordinator → feature → QA agent workflow with parallel worktree-based implementation. Language-agnostic. Auto-detects installed board plugins. Optional CI gate. | `process` | Read+Write | [spec-kit-maqa-ext](https://github.com/GenieRobot/spec-kit-maqa-ext) |
| MAQA Azure DevOps Integration | Azure DevOps Boards integration for MAQA — syncs User Stories and Task children as features progress | `integration` | Read+Write | [spec-kit-maqa-azure-devops](https://github.com/GenieRobot/spec-kit-maqa-azure-devops) |
| MAQA CI/CD Gate | Auto-detects GitHub Actions, CircleCI, GitLab CI, and Bitbucket Pipelines. Blocks QA handoff until pipeline is green. | `process` | Read+Write | [spec-kit-maqa-ci](https://github.com/GenieRobot/spec-kit-maqa-ci) |
| MAQA GitHub Projects Integration | GitHub Projects v2 integration for MAQA — syncs draft issues and Status columns as features progress | `integration` | Read+Write | [spec-kit-maqa-github-projects](https://github.com/GenieRobot/spec-kit-maqa-github-projects) |
| MAQA Jira Integration | Jira integration for MAQA — syncs Stories and Subtasks as features progress through the board | `integration` | Read+Write | [spec-kit-maqa-jira](https://github.com/GenieRobot/spec-kit-maqa-jira) |
| MAQA Linear Integration | Linear integration for MAQA — syncs issues and sub-issues across workflow states as features progress | `integration` | Read+Write | [spec-kit-maqa-linear](https://github.com/GenieRobot/spec-kit-maqa-linear) |
| MAQA Trello Integration | Trello board integration for MAQA — populates board from specs, moves cards, real-time checklist ticking | `integration` | Read+Write | [spec-kit-maqa-trello](https://github.com/GenieRobot/spec-kit-maqa-trello) |
| MarkItDown Document Converter | Convert documents (PDF, Word, PowerPoint, Excel, and more) to Markdown for use as spec reference material | `docs` | Read+Write | [spec-kit-markitdown](https://github.com/BenBtg/spec-kit-markitdown) |
| Memory Loader | Loads .specify/memory/ files before lifecycle commands so LLM agents have project governance context | `docs` | Read-only | [spec-kit-memory-loader](https://github.com/KevinBrown5280/spec-kit-memory-loader) |
| Memory MD | Repository-native durable memory for Spec Kit projects | `docs` | Read+Write | [spec-kit-memory-hub](https://github.com/DyanGalih/spec-kit-memory-hub) |
| MemoryLint | Agent memory governance tool: Automatically audits and fixes boundary conflicts between AGENTS.md and the constitution. | `process` | Read+Write | [memorylint](https://github.com/RbBtSn0w/spec-kit-extensions/tree/main/memorylint) |
| Microsoft 365 Integration | Fetch Teams messages, meeting transcripts, and SharePoint/OneDrive files as local Markdown for spec generation | `integration` | Read+Write | [spec-kit-m365](https://github.com/BenBtg/spec-kit-m365) |
| Onboard | Contextual onboarding and progressive growth for developers new to spec-kit projects. Explains specs, maps dependencies, validates understanding, and guides the next step | `process` | Read+Write | [spec-kit-onboard](https://github.com/dmux/spec-kit-onboard) |
| Optimize | Audit and optimize AI governance for context efficiency — token budgets, rule health, interpretability, compression, coherence, and echo detection | `process` | Read+Write | [spec-kit-optimize](https://github.com/sakitA/spec-kit-optimize) |
| OWASP LLM Threat Model | OWASP Top 10 for LLM Applications 2025 threat analysis on agent artifacts | `code` | Read-only | [spec-kit-threatmodel](https://github.com/NaviaSamal/spec-kit-threatmodel) |
| Plan Review Gate | Require spec.md and plan.md to be merged via MR/PR before allowing task generation | `process` | Read-only | [spec-kit-plan-review-gate](https://github.com/luno/spec-kit-plan-review-gate) |
| PR Bridge | Auto-generate pull request descriptions, checklists, and summaries from spec artifacts | `process` | Read-only | [spec-kit-pr-bridge-](https://github.com/Quratulain-bilal/spec-kit-pr-bridge-) |
| Presetify | Create and validate presets and preset catalogs | `process` | Read+Write | [presetify](https://github.com/mnriem/spec-kit-extensions/tree/main/presetify) |
| Product Forge | Full product lifecycle from research to release — portfolio, lite mode, monorepo, optional V-Model | `process` | Read+Write | [speckit-product-forge](https://github.com/VaiYav/speckit-product-forge) |
| Project Health Check | Diagnose a Spec Kit project and report health issues across structure, agents, features, scripts, extensions, and git | `visibility` | Read-only | [spec-kit-doctor](https://github.com/KhawarHabibKhan/spec-kit-doctor) |
| Project Status | Show current SDD workflow progress — active feature, artifact status, task completion, workflow phase, and extensions summary | `visibility` | Read-only | [spec-kit-status](https://github.com/KhawarHabibKhan/spec-kit-status) |
| QA Testing Extension | Systematic QA testing with browser-driven or CLI-based validation of acceptance criteria from spec | `code` | Read-only | [spec-kit-qa](https://github.com/arunt14/spec-kit-qa) |
| Ralph Loop | Autonomous implementation loop using AI agent CLI | `code` | Read+Write | [spec-kit-ralph](https://github.com/Rubiss/spec-kit-ralph) |
| Reconcile Extension | Reconcile implementation drift by surgically updating feature artifacts. | `docs` | Read+Write | [spec-kit-reconcile](https://github.com/stn1slv/spec-kit-reconcile) |
| Red Team | Adversarial review of specs before /speckit.plan — parallel lens agents surface risks that clarify/analyze structurally can't (prompt injection, integrity gaps, cross-spec drift, silent failures). Produces a structured findings report; no auto-edits to specs. | `docs` | Read+Write | [spec-kit-red-team](https://github.com/ashbrener/spec-kit-red-team) |
| Repository Index | Generate index for existing repo for overview, architecture and module level. | `docs` | Read-only | [spec-kit-repoindex](https://github.com/liuyiyu/spec-kit-repoindex) |
| Retro Extension | Sprint retrospective analysis with metrics, spec accuracy assessment, and improvement suggestions | `process` | Read+Write | [spec-kit-retro](https://github.com/arunt14/spec-kit-retro) |
| Retrospective Extension | Post-implementation retrospective with spec adherence scoring, drift analysis, and human-gated spec updates | `docs` | Read+Write | [spec-kit-retrospective](https://github.com/emi-dm/spec-kit-retrospective) |
| Review Extension | Post-implementation comprehensive code review with specialized agents for code quality, comments, tests, error handling, type design, and simplification | `code` | Read-only | [spec-kit-review](https://github.com/ismaelJimenez/spec-kit-review) |
| Ripple | Detect side effects that tests can't catch after implementation — delta-anchored analysis across 9 domain-agnostic categories | `code` | Read+Write | [spec-kit-ripple](https://github.com/chordpli/spec-kit-ripple) |
| SDD Utilities | Resume interrupted workflows, validate project health, and verify spec-to-task traceability | `process` | Read+Write | [speckit-utils](https://github.com/mvanhorn/speckit-utils) |
| Security Review | Comprehensive security audit of codebases using AI-powered DevSecOps analysis | `code` | Read-only | [spec-kit-security-review](https://github.com/DyanGalih/spec-kit-security-review) |
| SFSpeckit | Enterprise Salesforce SDLC with 18 commands for the full SDD lifecycle. | `process` | Read+Write | [spec-kit-sf](https://github.com/ysumanth06/spec-kit-sf) |
| Ship Release Extension | Automates release pipeline: pre-flight checks, branch sync, changelog generation, CI verification, and PR creation | `process` | Read+Write | [spec-kit-ship](https://github.com/arunt14/spec-kit-ship) |
| Spec Reference Loader | Reads the ## References section from the feature spec and loads only the listed docs into context | `docs` | Read-only | [spec-kit-spec-reference-loader](https://github.com/KevinBrown5280/spec-kit-spec-reference-loader) |
| Spec Critique Extension | Dual-lens critical review of spec and plan from product strategy and engineering risk perspectives | `docs` | Read-only | [spec-kit-critique](https://github.com/arunt14/spec-kit-critique) |
| Spec Diagram | Auto-generate Mermaid diagrams of SDD workflow state, feature progress, and task dependencies | `visibility` | Read-only | [spec-kit-diagram-](https://github.com/Quratulain-bilal/spec-kit-diagram-) |
| Spec Orchestrator | Cross-feature orchestration — track state, select tasks, and detect conflicts across parallel specs | `process` | Read-only | [spec-kit-orchestrator](https://github.com/Quratulain-bilal/spec-kit-orchestrator) |
| Spec Refine | Update specs in-place, propagate changes to plan and tasks, and diff impact across artifacts | `process` | Read+Write | [spec-kit-refine](https://github.com/Quratulain-bilal/spec-kit-refine) |
| Spec Scope | Effort estimation and scope tracking — estimate work, detect creep, and budget time per phase | `process` | Read-only | [spec-kit-scope-](https://github.com/Quratulain-bilal/spec-kit-scope-) |
| Spec Sync | Detect and resolve drift between specs and implementation. AI-assisted resolution with human approval | `docs` | Read+Write | [spec-kit-sync](https://github.com/bgervin/spec-kit-sync) |
| Spec Validate | Comprehension validation, review gating, and approval state for spec-kit artifacts — staged quizzes, peer review SLA, and a hard gate before /speckit.implement | `process` | Read+Write | [spec-kit-spec-validate](https://github.com/aeltayeb/spec-kit-spec-validate) |
| SpecTest | Auto-generate test scaffolds from spec criteria, map coverage, and find untested requirements | `code` | Read+Write | [spec-kit-spectest](https://github.com/Quratulain-bilal/spec-kit-spectest) |
| Staff Review Extension | Staff-engineer-level code review that validates implementation against spec, checks security, performance, and test coverage | `code` | Read-only | [spec-kit-staff-review](https://github.com/arunt14/spec-kit-staff-review) |
| Status Report | Project status, feature progress, and next-action recommendations for spec-driven workflows | `visibility` | Read-only | [Open-Agent-Tools/spec-kit-status](https://github.com/Open-Agent-Tools/spec-kit-status) |
| Superpowers Bridge | Orchestrates obra/superpowers skills within the spec-kit SDD workflow across the full lifecycle (clarification, TDD, review, verification, critique, debugging, branch completion) | `process` | Read+Write | [superpowers-bridge](https://github.com/RbBtSn0w/spec-kit-extensions/tree/main/superpowers-bridge) |
| Superpowers Bridge (WangX0111) | Bridges spec-kit with obra/superpowers (brainstorming, TDD, subagent, code-review) into a unified, resumable workflow with graceful degradation and session progress tracking | `process` | Read+Write | [superspec](https://github.com/WangX0111/superspec) |
| TinySpec | Lightweight single-file workflow for small tasks — skip the heavy multi-step SDD process | `process` | Read+Write | [spec-kit-tinyspec](https://github.com/Quratulain-bilal/spec-kit-tinyspec) |
| V-Model Extension Pack | Enforces V-Model paired generation of development specs and test specs with full traceability | `docs` | Read+Write | [spec-kit-v-model](https://github.com/leocamello/spec-kit-v-model) |
| Verify Extension | Post-implementation quality gate that validates implemented code against specification artifacts | `code` | Read-only | [spec-kit-verify](https://github.com/ismaelJimenez/spec-kit-verify) |
| Verify Tasks Extension | Detect phantom completions: tasks marked [X] in tasks.md with no real implementation | `code` | Read-only | [spec-kit-verify-tasks](https://github.com/datastone-inc/spec-kit-verify-tasks) |
| Version Guard | Verify tech stack versions against live npm registries before planning and implementation | `process` | Read-only | [spec-kit-version-guard](https://github.com/KevinBrown5280/spec-kit-version-guard) |
| What-if Analysis | Preview the downstream impact (complexity, effort, tasks, risks) of requirement changes before committing to them | `visibility` | Read-only | [spec-kit-whatif](https://github.com/DevAbdullah90/spec-kit-whatif) |
| Wireframe Visual Feedback Loop | SVG wireframe generation, review, and sign-off for spec-driven development. Approved wireframes become spec constraints honored by /speckit.plan, /speckit.tasks, and /speckit.implement | `visibility` | Read+Write | [spec-kit-extension-wireframe](https://github.com/TortoiseWolfe/spec-kit-extension-wireframe) |
| Worktree Isolation | Spawn isolated git worktrees for parallel feature development without checkout switching | `process` | Read+Write | [spec-kit-worktree](https://github.com/Quratulain-bilal/spec-kit-worktree) |
| Worktrees | Default-on worktree isolation for parallel agents — sibling or nested layout | `process` | Read+Write | [spec-kit-worktree-parallel](https://github.com/dango85/spec-kit-worktree-parallel) |

要提交你自己的扩展，请参阅 [Extension Publishing Guide](extensions/EXTENSION-PUBLISHING-GUIDE.md)。

## 🎨 社区预设

社区贡献的 presets 可自定义 Spec Kit 行为——覆盖模板、命令和术语，而无需修改任何工具。完整列表见 [Community Presets](https://github.github.io/spec-kit/community/presets.html) 页面。

> [!NOTE]
> 社区 presets 为第三方贡献，并非由 Spec Kit 团队维护。使用前请仔细审阅，并参见上方文档页中的完整免责声明。

要提交你自己的 preset，请参阅 [Presets Publishing Guide](presets/PUBLISHING.md)。

## 🚶 社区演练

通过社区贡献的 walkthroughs 了解 Spec-Driven Development 在不同场景中的实际应用；完整列表见 [Community Walkthroughs](https://github.github.io/spec-kit/community/walkthroughs.html) 页面。

## 🛠️ 社区伙伴项目

这些社区项目对 Spec Kit 进行扩展、可视化或构建在其之上。完整列表见 [Community Friends](https://github.github.io/spec-kit/community/friends.html) 页面。

## 🤖 支持的 AI 编码代理集成

Spec Kit 支持 30+ AI 编码代理——包括 CLI 工具和 IDE 助手。完整列表、说明与用法细节见 [Supported AI Coding Agent Integrations](https://github.github.io/spec-kit/reference/integrations.html) 指南。

运行 `specify integration list` 查看你当前安装版本中的所有可用集成。

## 可用 Slash Commands

运行 `specify init` 后，你的 AI 编码代理将可使用以下 slash commands 进行结构化开发。对于支持 skills 模式的集成，传入 `--integration <agent> --integration-options="--skills"` 会安装 agent skills，而不是 slash-command prompt files。

#### 核心命令

Spec-Driven Development 工作流的关键命令：

| Command                  | Agent Skill            | Description                                                                |
| ------------------------ | ---------------------- | -------------------------------------------------------------------------- |
| `/speckit.constitution`  | `speckit-constitution` | 创建或更新项目治理原则与开发指南 |
| `/speckit.specify`       | `speckit-specify`      | 定义你要构建的内容（需求和用户故事） |
| `/speckit.plan`          | `speckit-plan`         | 使用你选定的技术栈创建技术实现计划 |
| `/speckit.tasks`         | `speckit-tasks`        | 生成可执行的实现任务清单 |
| `/speckit.taskstoissues` | `speckit-taskstoissues`| 将生成的任务清单转换为 GitHub issues 以便跟踪和执行 |
| `/speckit.implement`     | `speckit-implement`    | 按计划执行所有任务并构建功能 |

#### 可选命令

用于增强质量与验证的附加命令：

| Command              | Agent Skill            | Description                                                                                                                          |
| -------------------- | ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| `/speckit.clarify`   | `speckit-clarify`      | 澄清定义不足的区域（建议在 `/speckit.plan` 前执行；原名 `/quizme`） |
| `/speckit.analyze`   | `speckit-analyze`      | 跨工件一致性与覆盖率分析（在 `/speckit.tasks` 后、`/speckit.implement` 前运行） |
| `/speckit.checklist` | `speckit-checklist`    | 生成自定义质量检查清单，用于验证需求完整性、清晰度和一致性（类似“针对英文的单元测试”） |

## 🔧 Specify CLI 参考

完整命令详情、参数与示例，请参阅 [CLI Reference](https://github.github.io/spec-kit/reference/overview.html)。

## 🧩 打造你的 Spec Kit：扩展与预设

Spec Kit 可通过两套互补系统按需定制——**extensions** 与 **presets**——再加上项目本地覆盖，满足一次性调整：

| Priority | Component Type                                    | Location                         |
| -------: | ------------------------------------------------- | -------------------------------- |
|      ⬆ 1 | Project-Local Overrides                           | `.specify/templates/overrides/`  |
|        2 | Presets — Customize core & extensions             | `.specify/presets/templates/`    |
|        3 | Extensions — Add new capabilities                 | `.specify/extensions/templates/` |
|      ⬇ 4 | Spec Kit Core — Built-in SDD commands & templates | `.specify/templates/`            |

- **Templates** 在**运行时**解析——Spec Kit 会自上而下遍历栈并使用第一个匹配项。
- 项目本地覆盖（`.specify/templates/overrides/`）让你无需创建完整 preset 也能做一次性定制。
- **Extension/preset commands** 在**安装时**应用——当你运行 `specify extension add` 或 `specify preset add` 时，命令文件会写入代理目录（如 `.claude/commands/`）。
- 若多个 preset 或 extension 提供同一命令，优先级最高者生效；移除后会自动恢复到下一优先级版本。
- 若不存在任何覆盖或定制，Spec Kit 使用核心默认配置。

### Extensions — 增加新能力

当你需要超出 Spec Kit 核心能力的功能时，使用 **extensions**。扩展会引入新命令和模板——例如添加内置 SDD 命令未覆盖的领域工作流、集成外部工具，或增加全新开发阶段。它们扩展的是 *Spec Kit 能做什么*。

```bash
# Search available extensions
specify extension search

# Install an extension
specify extension add <extension-name>
```

例如，扩展可以增加 Jira 集成、实现后代码评审、V-Model 测试可追溯性或项目健康诊断。

完整命令指南见 [Extensions reference](https://github.github.io/spec-kit/reference/extensions.html)。可在上方 [community extensions](#-community-extensions) 中浏览可用项。

### Presets — 自定义现有工作流

当你想改变 Spec Kit 的工作方式、但不增加新能力时，使用 **presets**。preset 会覆盖核心及已安装扩展附带的模板与命令——例如强制合规导向的规格格式、使用领域术语，或将组织标准应用到计划与任务。它们定制的是 Spec Kit 及其扩展产出的工件与指令。

```bash
# Search available presets
specify preset search

# Install a preset
specify preset add <preset-name>
```

例如，preset 可以重构规格模板以满足监管追溯、将流程适配你的方法论（如 Agile、Kanban、Waterfall、jobs-to-be-done 或 domain-driven design）、在计划中加入强制安全评审门禁、强制测试优先任务顺序，或将整个流程本地化为其他语言。[pirate-speak demo](https://github.com/mnriem/spec-kit-pirate-speak-preset-demo) 展示了定制深度。多个 preset 可按优先级叠加。

完整命令指南（含解析顺序与优先级叠加）见 [Presets reference](https://github.github.io/spec-kit/reference/presets.html)。

### 何时使用哪一个

| Goal | Use |
| --- | --- |
| 增加全新命令或工作流 | Extension |
| 自定义规格、计划或任务的格式 | Preset |
| 集成外部工具或服务 | Extension |
| 强制组织或监管标准 | Preset |
| 交付可复用的领域模板 | 两者皆可——模板覆盖用 presets，随新命令打包模板用 extensions |

## 📚 核心理念

Spec-Driven Development 是一种结构化流程，强调：

- **意图驱动开发**：先定义“*what*”，再定义“*how*”
- 使用约束护栏与组织原则进行**高质量规格创建**
- **多步骤迭代细化**，而非一次性 prompt 出代码
- **高度依赖**先进 AI 模型对规格的理解能力

## 🌟 开发阶段

| Phase                                    | Focus                    | Key Activities                                                                                                                                                     |
| ---------------------------------------- | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **0-to-1 Development** ("Greenfield")    | Generate from scratch    | <ul><li>Start with high-level requirements</li><li>Generate specifications</li><li>Plan implementation steps</li><li>Build production-ready applications</li></ul> |
| **Creative Exploration**                 | Parallel implementations | <ul><li>Explore diverse solutions</li><li>Support multiple technology stacks & architectures</li><li>Experiment with UX patterns</li></ul>                         |
| **Iterative Enhancement** ("Brownfield") | Brownfield modernization | <ul><li>Add features iteratively</li><li>Modernize legacy systems</li><li>Adapt processes</li></ul>                                                                |

## 🎯 实验目标

我们的研究与实验聚焦于：

### 技术独立性

- 使用多样技术栈构建应用
- 验证 Spec-Driven Development 是与特定技术、编程语言或框架无绑定的流程这一假设

### 企业约束

- 证明关键任务应用开发能力
- 纳入组织约束（云提供商、技术栈、工程实践）
- 支持企业设计系统与合规要求

### 以用户为中心的开发

- 面向不同用户群体与偏好构建应用
- 支持多种开发方式（从 vibe-coding 到 AI-native development）

### 创意与迭代流程

- 验证并行实现探索的概念
- 提供稳健的迭代式功能开发工作流
- 将流程扩展到升级与现代化任务

## 🔧 前置条件

- **Linux/macOS/Windows**
- [支持的](#-支持的-ai-编码代理集成) AI 编码代理
- 用于包管理的 [uv](https://docs.astral.sh/uv/)（推荐）或用于持久安装的 [pipx](https://pypa.github.io/pipx/)
- [Python 3.11+](https://www.python.org/downloads/)
- [Git](https://git-scm.com/downloads)

如果你在某个代理上遇到问题，请提交 issue，帮助我们改进集成。

## 📖 进一步学习

- **[完整 Spec-Driven Development 方法论](./spec-driven.md)** - 深入了解全流程
- **[详细演练](#-详细流程)** - 分步实现指南

---

## 📋 详细流程

<details>
<summary>点击展开详细分步演练</summary>

你可以使用 Specify CLI 启动项目，它会在你的环境中引入所需工件。运行：

```bash
specify init <project_name>
```

或者在当前目录初始化：

```bash
specify init .
# or use the --here flag
specify init --here
# Skip confirmation when the directory already has files
specify init . --force
# or
specify init --here --force
```

![Specify CLI bootstrapping a new project in the terminal](./media/specify_cli.gif)

系统会提示你选择正在使用的编码代理集成。你也可以直接在终端中提前指定：

```bash
specify init <project_name> --integration copilot
specify init <project_name> --integration gemini
specify init <project_name> --integration codex

# Or in current directory:
specify init . --integration copilot
specify init . --integration codex --integration-options="--skills"

# or use --here flag
specify init --here --integration copilot
specify init --here --integration codex --integration-options="--skills"

# Force merge into a non-empty current directory
specify init . --force --integration copilot

# or
specify init --here --force --integration copilot
```

CLI 会检查你是否安装了 Claude Code、Gemini CLI、Cursor CLI、Qwen CLI、opencode、Codex CLI、Qoder CLI、Tabnine CLI、Kiro CLI、Pi、Forge、Goose 或 Mistral Vibe。若未安装，或你希望不做工具检查直接获取模板，可在命令中使用 `--ignore-agent-tools`：

```bash
specify init <project_name> --integration copilot --ignore-agent-tools
```

### **STEP 1:** 建立项目原则

进入项目目录并运行你的编码代理。在本示例中，我们使用 `claude`。

![Bootstrapping Claude Code environment](./media/bootstrap-claude-code.gif)

如果你能看到 `/speckit.constitution`、`/speckit.specify`、`/speckit.plan`、`/speckit.tasks` 和 `/speckit.implement` 命令，说明配置正确。

第一步应使用 `/speckit.constitution` 命令建立项目治理原则，确保后续所有开发阶段决策一致：

```text
/speckit.constitution Create principles focused on code quality, testing standards, user experience consistency, and performance requirements. Include governance for how these principles should guide technical decisions and implementation choices.
```

这一步会创建或更新 `.specify/memory/constitution.md` 文件，写入项目基础指南，供编码代理在规格、规划和实现阶段参考。

### **STEP 2:** 创建项目规格

建立好项目原则后，即可开始创建功能规格。使用 `/speckit.specify` 命令，然后提供你要开发项目的具体需求。

> [!IMPORTANT]
> 尽可能明确说明你要构建的 *what* 和 *why*。**此时不要关注技术栈**。

示例提示词：

```text
Develop Taskify, a team productivity platform. It should allow users to create projects, add team members,
assign tasks, comment and move tasks between boards in Kanban style. In this initial phase for this feature,
let's call it "Create Taskify," let's have multiple users but the users will be declared ahead of time, predefined.
I want five users in two different categories, one product manager and four engineers. Let's create three
different sample projects. Let's have the standard Kanban columns for the status of each task, such as "To Do,"
"In Progress," "In Review," and "Done." There will be no login for this application as this is just the very
first testing thing to ensure that our basic features are set up. For each task in the UI for a task card,
you should be able to change the current status of the task between the different columns in the Kanban work board.
You should be able to leave an unlimited number of comments for a particular card. You should be able to, from that task
card, assign one of the valid users. When you first launch Taskify, it's going to give you a list of the five users to pick
from. There will be no password required. When you click on a user, you go into the main view, which displays the list of
projects. When you click on a project, you open the Kanban board for that project. You're going to see the columns.
You'll be able to drag and drop cards back and forth between different columns. You will see any cards that are
assigned to you, the currently logged in user, in a different color from all the other ones, so you can quickly
see yours. You can edit any comments that you make, but you can't edit comments that other people made. You can
delete any comments that you made, but you can't delete comments anybody else made.
```

输入该提示后，你应会看到 Claude Code 启动规划与规格草拟流程。Claude Code 还会触发一些内置脚本来初始化仓库。

此步骤完成后，应会创建一个新分支（例如 `001-create-taskify`），并在 `specs/001-create-taskify` 目录下生成新的规格。

生成的规格应包含模板定义的用户故事与功能需求集合。

此时项目目录结构应类似：

```text
└── .specify
    ├── memory
    │  └── constitution.md
    ├── scripts
    │  ├── check-prerequisites.sh
    │  ├── common.sh
    │  ├── create-new-feature.sh
    │  ├── setup-plan.sh
    │  └── update-claude-md.sh
    ├── specs
    │  └── 001-create-taskify
    │      └── spec.md
    └── templates
        ├── plan-template.md
        ├── spec-template.md
        └── tasks-template.md
```

### **STEP 3:** 功能规格澄清（规划前必需）

有了基础规格后，你可以继续澄清首次生成时未准确捕获的需求。

建议在创建技术计划**之前**运行结构化澄清流程，以减少后续返工。

推荐顺序：

1. 使用 `/speckit.clarify`（结构化）——顺序式、基于覆盖率的问题流程，并将回答记录到 Clarifications 区域。
2. 如仍有模糊之处，可选地再做自由形式补充澄清。

如果你有意跳过澄清（例如 spike 或探索性原型），请明确说明，以免代理因缺少澄清而阻塞。

示例自由形式补充提示（如 `/speckit.clarify` 后仍需）：

```text
For each sample project or project that you create there should be a variable number of tasks between 5 and 15
tasks for each one randomly distributed into different states of completion. Make sure that there's at least
one task in each stage of completion.
```

你还应要求 Claude Code 校验 **Review & Acceptance Checklist**，满足要求的项打勾，不满足的保持未勾选。可使用下列提示：

```text
Read the review and acceptance checklist, and check off each item in the checklist if the feature spec meets the criteria. Leave it empty if it does not.
```

务必将与 Claude Code 的交互当作澄清规格、提问求证的机会——**不要把它第一次输出当最终结果**。

### **STEP 4:** 生成计划

现在可以明确技术栈和其他技术要求。使用项目模板内置的 `/speckit.plan` 命令，并给出类似如下提示：

```text
We are going to generate this using .NET Aspire, using Postgres as the database. The frontend should use
Blazor server with drag-and-drop task boards, real-time updates. There should be a REST API created with a projects API,
tasks API, and a notifications API.
```

此步骤输出将包含多个实现细节文档，目录树类似：

```text
.
├── CLAUDE.md
├── memory
│  └── constitution.md
├── scripts
│  ├── check-prerequisites.sh
│  ├── common.sh
│  ├── create-new-feature.sh
│  ├── setup-plan.sh
│  └── update-claude-md.sh
├── specs
│  └── 001-create-taskify
│      ├── contracts
│      │  ├── api-spec.json
│      │  └── signalr-spec.md
│      ├── data-model.md
│      ├── plan.md
│      ├── quickstart.md
│      ├── research.md
│      └── spec.md
└── templates
    ├── CLAUDE-template.md
    ├── plan-template.md
    ├── spec-template.md
    └── tasks-template.md
```

检查 `research.md`，确认技术栈符合你的要求。如有不合适之处，可让 Claude Code 继续优化，或让它检查本地安装的平台/框架版本（如 .NET）。

此外，若所选技术栈变化快（如 .NET Aspire、JS 框架），你可能希望让 Claude Code 做更深入研究，可用如下提示：

```text
I want you to go through the implementation plan and implementation details, looking for areas that could
benefit from additional research as .NET Aspire is a rapidly changing library. For those areas that you identify that
require further research, I want you to update the research document with additional details about the specific
versions that we are going to be using in this Taskify application and spawn parallel research tasks to clarify
any details using research from the web.
```

在这个过程中，你可能会发现 Claude Code 在错误方向上研究太久——你可以用如下提示引导它：

```text
I think we need to break this down into a series of steps. First, identify a list of tasks
that you would need to do during implementation that you're not sure of or would benefit
from further research. Write down a list of those tasks. And then for each one of these tasks,
I want you to spin up a separate research task so that the net results is we are researching
all of those very specific tasks in parallel. What I saw you doing was it looks like you were
researching .NET Aspire in general and I don't think that's gonna do much for us in this case.
That's way too untargeted research. The research needs to help you solve a specific targeted question.
```

> [!NOTE]
> Claude Code 可能会过于积极，添加你未要求的组件。请它澄清变更理由和来源。

### **STEP 5:** 让 Claude Code 校验计划

计划完成后，应让 Claude Code 过一遍，确保没有遗漏。可使用如下提示：

```text
Now I want you to go and audit the implementation plan and the implementation detail files.
Read through it with an eye on determining whether or not there is a sequence of tasks that you need
to be doing that are obvious from reading this. Because I don't know if there's enough here. For example,
when I look at the core implementation, it would be useful to reference the appropriate places in the implementation
details where it can find the information as it walks through each step in the core implementation or in the refinement.
```

这有助于细化实现计划，并避免 Claude Code 在规划周期中遗漏盲点。初步细化完成后，请再让 Claude Code 过一次 checklist，然后再进入实现阶段。

如果你安装了 [GitHub CLI](https://docs.github.com/en/github-cli/github-cli)，也可以让 Claude Code 直接从当前分支向 `main` 创建带详细描述的 pull request，以确保工作可追踪。

> [!NOTE]
> 在让代理开始实现前，也值得提示 Claude Code 进行交叉检查，确认是否有过度设计（记住：它可能过于积极）。若存在过度设计组件或决策，可让 Claude Code 进行收敛。确保 Claude Code 遵循 [constitution](base/memory/constitution.md) 作为建立计划时必须遵守的基础。

### **STEP 6:** 使用 /speckit.tasks 生成任务拆分

实现计划校验完成后，即可将计划拆分为可按顺序执行的具体任务。使用 `/speckit.tasks` 命令从实现计划自动生成详细任务拆分：

```text
/speckit.tasks
```

此步骤会在你的功能规格目录中创建 `tasks.md`，其中包含：

- **按用户故事组织的任务拆分** - 每个用户故事成为独立实现阶段，并包含对应任务
- **依赖管理** - 任务顺序遵循组件依赖（如 models 在 services 前，services 在 endpoints 前）
- **并行执行标记** - 可并行任务会标记为 `[P]`，优化开发流程
- **文件路径说明** - 每个任务都包含具体实施文件路径
- **测试驱动开发结构** - 如果要求测试，会包含测试任务并排在实现之前
- **检查点校验** - 每个用户故事阶段包含可独立验证功能的检查点

生成的 tasks.md 为 `/speckit.implement` 提供清晰路线图，确保系统化实现、保持代码质量，并支持用户故事的增量交付。

### **STEP 7:** 实现

准备就绪后，使用 `/speckit.implement` 执行实现计划：

```text
/speckit.implement
```

`/speckit.implement` 命令将会：

- 校验所有前置条件是否完备（constitution、spec、plan 和 tasks）
- 解析 `tasks.md` 中的任务拆分
- 按正确顺序执行任务，遵循依赖与并行标记
- 遵循任务计划中定义的 TDD 方法
- 提供进度更新并妥善处理错误

> [!IMPORTANT]
> 编码代理会执行本地 CLI 命令（如 `dotnet`、`npm` 等）——请确保你的机器已安装所需工具。

实现完成后，请测试应用并处理 CLI 日志中不易看到的运行时错误（如浏览器控制台错误）。你可以将这些错误复制粘贴回编码代理让其修复。

</details>

---

## 🔍 故障排查

### Linux 上的 Git Credential Manager

如果你在 Linux 上遇到 Git 认证问题，可以安装 Git Credential Manager：

```bash
#!/usr/bin/env bash
set -e
echo "Downloading Git Credential Manager v2.6.1..."
wget https://github.com/git-ecosystem/git-credential-manager/releases/download/v2.6.1/gcm-linux_amd64.2.6.1.deb
echo "Installing Git Credential Manager..."
sudo dpkg -i gcm-linux_amd64.2.6.1.deb
echo "Configuring Git to use GCM..."
git config --global credential.helper manager
echo "Cleaning up..."
rm gcm-linux_amd64.2.6.1.deb
```

## 💬 支持

如需支持，请提交 [GitHub issue](https://github.com/github/spec-kit/issues/new)。我们欢迎 bug 报告、功能请求以及关于 Spec-Driven Development 使用方面的问题。

## 🙏 致谢

本项目深受 [John Lam](https://github.com/jflam) 的工作与研究影响，并以其成果为基础构建。

## 📄 许可证

本项目基于 MIT 开源许可证条款授权。完整条款请参阅 [LICENSE](./LICENSE) 文件。
