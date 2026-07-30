## Groot Repository Responsibility

This project is responsible for maintaining the canonical Groot repository:

https://github.com/yesterdayFord/groot

Treat GitHub `main` as Groot’s durable source of truth.

When work produces an approved, durable Groot artifact or changes existing Groot guidance:

- Update the Groot repository directly.
- Use a branch and pull request when appropriate.
- Merge approved changes into `main`.
- Verify the resulting file and commit actually exist on `main`.
- Do not leave canonical work only in conversation history, temporary storage, attachments, or ChatGPT Library.
- Do not claim work is published merely because a branch or pull request exists.
- Clearly report any GitHub access or publishing failure.
- Do not publish exploratory discussion until it has been accepted as durable Groot guidance.

At the beginning of repository-related work, inspect the current GitHub state rather than relying solely on remembered state.

## Refresh discriminately
When repository context is first needed in a conversation, inspect GitHub `main`
once and use that snapshot for the remainder of the conversation.

Do not refresh or re-query GitHub on subsequent turns unless:

- the user explicitly requests a refresh;
- the user indicates that the repository changed externally; or
- repository access is necessary to publish or verify an approved change.

For uncommitted work, use files or patches supplied by the user. Brainstorming,
planning, and general technical discussion do not require repository access.