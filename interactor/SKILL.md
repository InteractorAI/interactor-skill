---
name: Interactor
description: Create, configure, review, troubleshoot, and improve individual Interactors for business owners and teams. Use for an Interactor's configuration, customer-facing conversation behavior, and supported workflows, or for Interactor management CLI/API operations. Do not use for developing, debugging, or fixing the Interactor platform itself, including its application source code; general sales writing; or unrelated website development, payments, WhatsApp, forms, or scheduling tasks.
---

# Interactor Platform

Use this skill to help an agent manage Interactor for a business owner.

## Platform Overview

Interactor is a platform where business owners (or individuals) can create and manage an AI chat bot called an Interactor. The Interactor talks to customers 24/7, answers common questions about the business, sets up appointments, accepts dynamic forms, searches products, and supports other owner-configured workflows.

## Brand And Naming

- Always write `Interactor` as a capitalized proper noun in prose, including when referring to one configured instance. Use `Interactors` for the plural.
- Keep literal command names, package names, URLs, schema IDs, JSON fields, file names, and quoted owner text exactly as written.

## First steps

### Website installation and integration handoff

For adding, configuring, troubleshooting, or removing the Interactor widget on a
website, use the [Interactor Embed skill](https://add.interactor.ai/skill.md).
It owns website scripts, browser initialization, launch buttons, website form
handoffs, page-to-chat messages, and browser verification of the integration.
For website-only requests, follow that skill without performing the management
setup below.

When a request includes both Interactor configuration and website integration,
use this skill for the requested configuration, then pass the confirmed public
Interactor ID or alias to the embed skill for the website work. Use this skill
again only if the integration requires further requested configuration changes.
Neither skill covers developing or fixing the Interactor platform itself.

### Platform management setup

- Install CLI to work with the platform. Read `references/cli.md`.
- Prefer the newest CLI version.
- Connect to Interactor platform. If not logged in, finish the OAuth flow.
- Explore all the references in this skill. Give the user a complete overview of what you can do, propose next steps.

Important notes:

- Do not explore previous conversations to understand how to start working with the platform. You must follow this skill.

## Conversation style

Act like a capable operator:

- Keep internal mechanics out of the owner conversation unless requested: do not mention JSON, payloads, backups, CLI, API, HTTP requests, OAuth, tokens, and other internal technical details.
- Show summaries of your actions without technical details.
- Confirm before destructive or meaningfully irreversible changes.
- Discuss and help user to design an Interactor that works best for their use case.

## Interactor creation

Do not take a request to create a new Interactor literally. When the user wants to create a new Interactor, that means they want to set up a new Interactor that is designed for their purposes.

Before you start creating a new Interactor, read `references/create-interactor.md`.

## Interactor editing

Before you start editing an Interactor, read `references/edit-interactor.md`.

For changes to individual module items, use the item resource commands described
in `references/item-resources.md`. They are the recommended way to create, edit,
delete, or reorder items without replacing the complete list.

## Designing Interactors

Read best practices on how to design a good Interactor: `references/interactor-design.md`.

## Advanced features

Some management features are not available in the API.

For example:

- Connecting external services or providers (payments, calendars)
- Seeing customers, appointments, submitted forms

To handle questions or requests on how the owner can do certain things, you must follow the flow:

1. Read the full Interactor schema. It includes description for Interactor configuration, including read-only fields and sections available to you. You can use the description to handle the request.
2. If you can't find information, tell the user to trying using Interactor directly.

## Uploading media

Read `references/upload-media.md` to understand how to upload media to Interactor.

## Keeping backups

If you need to keep backups, read `references/backups.md`.

## References

- `references/cli.md`: how to work with platform api.
- `references/interactor-design.md`: best practices on how to design the Interactor.
- `references/create-interactor.md`: checklist for Interactor creation.
- `references/edit-interactor.md`: checklist for Interactor editing.
- `references/item-resources.md`: recommended item-level API and CLI workflows, supported modules, and older-CLI fallback.
- `references/patching-behavior.md`: rules for how patch payloads merge objects, replace/upsert arrays, preserve ids, and avoid accidental deletions.
- `references/backups.md`: instructions on how to keep backups.
- `references/upload-media.md`: instructions on how to upload media.
