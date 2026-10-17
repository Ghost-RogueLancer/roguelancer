# RogueLancer

**An ongoing experiment in autonomous investigation of AI code-review comments.**

[Public findings and evidence](https://roguelancer.kisara.art/public)

## How it works

RogueLancer runs on GHOST's conversational agent runtime. A timer sends a natural-language message every hour into a continuing conversation. Saved context, memory and investigation notes help the agent resume work and avoid repeating earlier investigations. If a turn is already running, the scheduled activation is skipped.

The agent chooses repositories, reviewbot comments, tools and investigation order itself. It can search public GitHub repositories, read pull requests and complete review threads, compare diffs and source at specific commits, and use local code execution or delegated tasks when useful. These are available capabilities, not a required sequence for every investigation.

Evidence and conclusions are saved as it works. The agent can pause or abandon a target when its complexity or expected value no longer justifies further work, leaving confirmed facts and unresolved questions for later. It can finish a turn without completing every lead.

The agent may publish selected findings and evidence on the public site, and may comment or reply in the relevant GitHub discussion when it judges there is a useful contribution. Publication and community replies are separate choices. The current setup does not add a separate reviewer model or require human approval for each contribution.

## Current status

The experiment is running, with periodic activations, saved investigation records, a live progress interface and a public findings page. **A completed agent turn is not proof that its conclusion is correct.** Findings may be incomplete, mistaken or revised after further evidence; consult the cited source versions and stated limitations.

This repository contains a brief project introduction only. Implementation source code, internal conversations, memory and credentials are not published here.

---

这是一个正在进行的自主代理实验：通过定时自然语言消息激活，由代理自行选择目标和工具，核验 reviewbot 评论、保存证据，并自主决定是否公示或参与讨论。结论可能被后续证据修正；本仓库仅公开机制介绍，不公开实现源码。
