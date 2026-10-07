---
name: session-task-benchmark
description: Reviews up to 20 recent accessible conversation sessions, identifies recurring patterns of small workflow tasks, and writes one fictional task prompt in that style for comparing AI models. Use when the user wants a representative small task based on their work history.
license: Apache-2.0
---

# Session Task Benchmark

Create one fictional, self-contained task prompt that resembles the user's recurring small tasks. The user will decide whether the prompt is representative and may ask for another. Do not carry out the generated task or edit the project while this skill is running.

## Review session history

1. Use the current host's supported session-history or conversation-search tools to find up to 20 recent prior sessions. Include archived sessions when the tool supports it. Review fewer if fewer are available.
2. Read enough of each session to understand the user's requested work. Track how many sessions were listed, how many had readable conversations, and how many were actually reviewed. Do not treat repeated messages in one session as separate sessions.
3. If available, use a supported VS Code session-history or Chronicle command/tool to find recent chats missing from the host's session list or transcript results. Chronicle may be experimental or disabled; use it only when the current host exposes it. Never inspect VS Code's internal databases or files directly.
4. If history is incomplete, report exactly what was accessible. If a supported Chronicle/history feature is available but disabled, explain how the user can enable or run it and provide a query they can use to produce a concise summary. Otherwise, ask for session exports or summaries. Do not imply access to hidden history or invent evidence.
5. Extract only generalized task patterns. Do not reproduce private code, project or customer names, credentials, personal data, or distinctive content from past sessions in the generated prompt.

## Choose a representative task pattern

- Group tasks by their underlying operation and scope, not exact wording. Examples include replacing or renaming a small set of variables, extracting repeated code into a helper, or making a localized UI color or position adjustment.
- Let the evidence guide whether tasks are meaningfully similar and recurring; do not require identical requests. Prefer the clearest repeated pattern, and do not claim a pattern is common if the history does not support it.
- If a task is explicitly estimated or shown by session history to take more than 10 minutes, exclude it. If duration is unavailable, judge from the scope: prefer a localized, low-risk change with one clear outcome. Exclude broad feature work, architectural changes, and tasks with substantial cross-cutting dependencies.
- If no defensible recurring pattern of small tasks is present, explain that and ask the user for more history or direction rather than manufacturing one.

## Write the fictional prompt

- Invent neutral names and details; preserve the pattern of work, not the original task or its project context.
- Make the task plausible and specific enough that different models could attempt the same work. Keep it small and focused; it does not need to advance a real product feature.
- Output exactly one candidate prompt. Do not execute it, solve it, or make changes in the workspace.
- If the user says the candidate is a miss and asks for another, choose the next-best supported pattern and write a different prompt. Do not repeat the same candidate with superficial wording changes.

## Present the result

Show:

1. **Pattern identified** — a brief, generalized description and how many distinct sessions support it, if that count is available.
2. **Candidate prompt** — one clearly delimited prompt the user can copy into another model.
3. **Coverage** — how many prior sessions were actually reviewed, up to 20; note any history-access limitation.

Keep the rationale short and free of identifying details. Invite the user to confirm whether the candidate fits or request another. For an initial run, suggest a lightweight, lower-cost model such as Luna or Haiku if available; if the pattern or prompt is not representative, suggest trying a more capable model.
