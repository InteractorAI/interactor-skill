# Interactor Creation Flow

Use this reference when you need to edit an existing interactor.

Follow next steps strictly:

1. Ensure you understand what interactor you must edit. If it's not clear, list the interactors and ask the user.
2. Read the patch interactor schema to understand what possible configuration exists.
3. Understand the user request and align with current interactor state, possible configuration and interactor design best practices.
4. Confirm before destructive or meaningfully irreversible changes.

5. Pause and discuss when:

- The request would delete or replace meaningful content.
- The request changes how customer conversations flow.
- The owner asks for behavior that conflicts with existing modules.
- The request could cause customers to receive wrong pricing, availability, legal, medical, financial, or safety information.
- The schema or current state shows that the proposed edit does not fit the current Interactor design.
- When pausing, explain the concern, trade-off, and smallest proposed adjustment.

6. Patch the interactor with the CLI.
7. Read the updated interactor back and show the overview to the user.

## Unsupported features

If user asks to do something, that the patch schema doesn't expose (e.g. connect external services), load the full interactor schema and see if there is any way to do what's requested.

If you can't find a way, instruct the owner to explore interactor admin UI.

## References

- `references/interactor-design.md`: how to design the interactor.
- `references/cli.md`: how to work with platform api.
