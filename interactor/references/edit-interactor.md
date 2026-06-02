# Interactor Editing Flow

Use this reference when you need to edit an existing Interactor.

Follow these steps strictly:

1. Ensure you understand what Interactor you must edit. If it's not clear, list the Interactors and ask the user.
2. Read the patch Interactor schema to understand what possible configuration exists.
3. Read the current Interactor state before preparing any patch.
4. Understand the user request and align with current Interactor state, possible configuration and Interactor design best practices.
5. Confirm before destructive or meaningfully irreversible changes.

6. Pause and discuss when:

- The request would delete or replace meaningful content.
- The request changes how customer conversations flow.
- The owner asks for behavior that conflicts with existing modules.
- The request could cause customers to receive wrong pricing, availability, legal, medical, financial, or safety information.
- The schema or current state shows that the proposed edit does not fit the current Interactor design.
- When pausing, explain the concern, trade-off, and smallest proposed adjustment.

7. Prepare the patch carefully. Read `references/patching-behavior.md` before writing or sending any patch.
8. Read the updated Interactor back and show the overview to the user.

## Unsupported features

If the user asks to do something that the patch schema doesn't expose (e.g. connect external services), load the full Interactor schema and see if there is any way to do what's requested.

If you can't find a way, instruct the owner to explore Interactor admin UI.

## References

- `references/interactor-design.md`: how to design the Interactor.
- `references/cli.md`: how to work with platform API.
- `references/patching-behavior.md`: how patch payloads merge objects and replace/upsert arrays.
