# Interactor Creation Flow

Use this reference when you need to create a new Interactor.

Follow these steps:

1. Read the full Interactor schema to understand what possible configuration exists.
2. Gather the business context needed for a useful first version: name, business type, audience, service area or location, key offers, contact preferences, and primary customer goals. If user didn't provide all the information in the initial request, pause and ask.
3. Read `references/interactor-design.md` for best practices.
4. Build a complete initial Interactor with useful modules rather than a thin shell. The final configuration must accurately reflect the business area or user's request.
5. Omit `agentBehaviorInstructions` at this step. Platform generates initial behavior automatically for new Interactors.
6. Create the Interactor with the CLI.
7. Read the created Interactor back and show the overview to the user.

## References

- `references/interactor-design.md`: how to design the Interactor.
- `references/cli.md`: how to work with platform API.
