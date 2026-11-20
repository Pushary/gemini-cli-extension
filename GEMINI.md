# Pushary

The `pushary` MCP server reaches the user on their phone or Mac.

- Use `ask_user` only for a decision you cannot make yourself. Fold several decisions into one question. Wait for the answer with `wait_for_answer` and the same correlation ID. Silence is never consent.
- Use `send_notification` when a long task finishes, or fails in a way you cannot fix. Do not send more than three per task unless the user asks for more.
- Follow the `pushary` skill for the full rules.
