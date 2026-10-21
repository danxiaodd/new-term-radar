# 免费中文云端采集

此 Fork 使用 GitHub Actions 自动采集，仅访问 Hugging Face 公共 API、GitHub API 和 config.json 中的公开站点地图。

- 北京时间每天 08:17、16:17、次日 00:17：Hugging Face Models / Spaces。
- 北京时间每天 09:47：完整免费日报（包含 Hugging Face、GitHub 新仓库及站点地图）。
- GitHub 定时任务可能排队延迟。
- 手动运行：Actions → New-term radar (free, 中文) → Run workflow，选择 daily 或 sources。
- 也会在本工作流或 config.json 提交到 main 时生成日报，供配置验证。
- 首次 HF 和站点地图只建立基线；GitHub 爆发仓库可在首日出现。
- 中文为报告标题、栏目与状态文字；原始项目名和项目介绍保留来源语言。

## 费用与密钥

不启用 X/AIsa、GoAnyAPI、TrustMRR、LLM 判词、搜索量、Google Trends 复盘、教程分析、邮件或付费功能。工作流不读取任何仓库 Secrets；只注入 GitHub 自动签发的临时 GITHUB_TOKEN，权限为 contents:read。config.json 不包含密钥，不要在此文件添加凭据。

## 报告与状态

每次运行的 Summary 显示报告；Artifacts 保留 Markdown、JSON（daily）、run.log 和完整 state 目录 14 天。缓存用于跨次比较与去重；缓存丢失时会重新建立基线。需要长期保存时下载完整 artifact。

## 开启与暂停

工作流默认启用；Fork 首次使用时仍需在 GitHub Actions 页面开启仓库工作流。设置仓库 Actions Variable RADAR_ENABLED=false 可暂停采集，删除该变量或改为 true 可恢复。

免费采集直接执行上游 Python 标准库代码，不安装邮件或 MCP 依赖，也不启用任何付费模式开关。
