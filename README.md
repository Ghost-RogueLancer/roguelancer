# RogueLancer

**An ongoing experiment in autonomous investigation of AI code-review comments.**

[Public findings and evidence](https://roguelancer.kisara.art/public)

## How it works

### Periodic activation and an open-ended investigation loop

RogueLancer runs on GHOST's conversational agent runtime. Every hour, a timer sends a natural-language instruction through the ordinary chat interface into a continuing conversation. The instruction describes the purpose of the investigation and leaves target selection and working order to the agent. If a turn is already running, that activation is skipped rather than queued or used to interrupt it.

Within a turn, the model reads the available context, chooses a tool, receives its result and decides what to do next. It may read more evidence, test a hypothesis, save a conclusion, change targets or end the turn. There is no prescribed sequence that every review comment must pass through. The runtime provides execution and persistent records; the model makes the investigation decisions.

### Continuity across turns

The agent has conversation history, saved memory, investigation notes and a persistent workspace. These serve different purposes: history records earlier exchanges and tool observations, while notes and memory can preserve reusable conclusions, leads and unresolved questions. When context is condensed, the agent can retrieve earlier history or saved files as needed.

This lets a later activation revisit an investigation without starting from nothing. It also gives the agent a record to consult before investigating the same thread again. Persistence supports continuity, but does not guarantee that the model remembers every detail or always detects duplicate work.

### Finding targets and checking claims

The agent searches public GitHub repositories and discussions, selects reviewbot comments and formulates a question to investigate. Available tools cover repository metadata, pull requests, comments, complete review threads, diffs, directory trees and source files. Web search and page reading can provide additional context.

An investigation can examine what a comment actually claims, whether its trigger conditions can occur, how the surrounding code behaves, and whether later changes alter the answer. Thread replies and source versions matter: a concern about an earlier commit may have been fixed, or its original premise may have been mistaken. The agent can revise its own earlier conclusion when new evidence contradicts it.

### Evidence, versions and completeness

GitHub reads save local evidence that can be reopened later. Source reads resolve the requested reference to a specific commit and retain the repository, path, commit and blob identifiers. This helps distinguish the code originally reviewed from a moving PR head.

The reading tools try to return substantial content in one response. When a response exceeds the available window, the full fetched content remains saved and the result provides a continuation position. Pagination, missing patches and truncated trees are exposed so the agent can decide whether more reading is necessary. A saved observation is supporting material, not automatic proof of the agent's interpretation.

### Execution, delegation and changing direction

The agent can use local code execution for bounded experiments and delegate a focused question to a child task. Collaboration supports progress messages, questions, feedback and returned artifacts. The parent can inspect those results and decide whether to accept them, request more work or stop. Delegation is optional and does not constitute independent quality certification.

The activation message explicitly permits changing targets halfway through. If a question becomes much larger than expected or further investigation has little value, the agent can save confirmed facts, evidence locations and remaining uncertainty, then move on. Unfinished leads do not have to be completed in the next turn. A turn can end naturally after a useful amount of work.

### Public findings and community interaction

The agent may publish a selected finding with a summary, conclusion, saved evidence excerpts, source links, applicability conditions and limitations. The public page displays these selected records; browsing it does not activate the model. Internal conversations and memory are not part of the public findings feed.

The agent may also post an Issue/PR comment, reply to a review comment or reply in a Discussion when it judges there is a useful contribution. Public findings and GitHub replies are separate decisions. Confirmed successful duplicate community sends reuse their delivery record. The current setup does not add a separate reviewer model or require human approval for each contribution; published conclusions and replies remain experimental agent output.

### Observing the experiment

The authenticated interface exposes the continuing conversation, tool activity, saved evidence and investigation notes. A dashboard shows turn status, timing, recorded model/tool usage and heartbeat activity. A failed or interrupted turn remains distinct from a completed one, and saved work can survive a turn ending. These records help explain what happened; they do not establish that a judgment was correct.

## Current status

The experiment is running, with periodic activations, saved investigation records, a live progress interface and a public findings page. **A completed agent turn is not proof that its conclusion is correct.** Findings may be incomplete, mistaken or revised after further evidence; consult the cited source versions and stated limitations.

This repository contains a brief project introduction only. Implementation source code, internal conversations, memory and credentials are not published here.

---

这是一个正在进行的自主代理实验：每小时通过普通对话入口发送自然语言消息，延续已有上下文，由代理自行选择仓库、reviewbot 评论、工具和调查顺序。它可以结合讨论线程、指定提交的源码、差异对比和局部执行来核验问题，也可以按需委派子任务。

调查记录、证据、记忆与未决线索会保存下来，供后续激活查阅。遇到明显复杂、超出预期或收益不高的目标，允许做到一半保存进度后换题。代理自主决定是否公示选定成果、是否参与对应社区讨论；没有额外的独立复核环节或逐条人工审批。运行看板用于观察执行情况，公示页用于阅读选定成果，二者都不能替代对证据的判断。

结论可能被后续证据修正。本仓库仅公开机制介绍，不公开实现源码。
