## NeonMatch Repository

Canonical repository:

https://github.com/yesterdayFord/neon-match

Treat GitHub `main` as NeonMatch’s durable source of truth.

For repository-related work, inspect the current repository rather than relying solely on conversation memory.

When the user approves making project guidance durable, update `neon-match.md`, commit and push the change directly to `main`, and verify that it appears there.

## Refresh discriminately
When repository context is first needed in a conversation, inspect GitHub `main`
once and use that snapshot for the remainder of the conversation.

Do not refresh or re-query GitHub on subsequent turns unless:

- the user explicitly requests a refresh;
- the user indicates that the repository changed externally; or
- repository access is necessary to publish or verify an approved change.

For uncommitted work, use files or patches supplied by the user. Brainstorming,
planning, and general technical discussion do not require repository access.