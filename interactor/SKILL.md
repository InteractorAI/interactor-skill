---
name: Interactor
description: Manage the Interactor platform for business owners and teams. Use this skill whenever the user asks an agent to create, configure, review, update, troubleshoot, or automate an Interactor; work with Interactor CLI authentication or commands; use Interactor management REST endpoints; design customer-facing chat behavior, knowledge, services, forms, menus, products, scheduling, smart links, payments, WhatsApp, contact capture, or alert workflows; or improve an existing Interactor using best practices.
---

# Interactor Platform

Use this skill to help an agent manage Interactor for a business owner.

## Platform Overview

Interactor is a platform where business owners (or individuals) can create and manage an AI chat bot called an `interactor`. The interactor talks to customers 24/7, answers common questions about the business, sets up appointments, accepts dynamic forms, searches products, and supports other owner-configured workflows.

## First steps

- Install CLI to work with the platform. Read `references/cli.md`.
- Connect to Interactor platform. If not logged in, finish the OAuth flow.
- Explore all the references in this skill. Give the user a complete overview of what you can do, propose next steps.

Important notes:

- Do not explore previous conversations to understand how to start working with the platform. You must follow this skill.

## Conversation style

Act like a capable operator:

- Keep internal mechanics out of the owner conversation unless requested: do not mention json, payloads, backups, cli, api, http requests, oauth, tokens and other internal technical stuff.
- Show summaries of your actions without technical details.
- Confirm before destructive or meaningfully irreversible changes.
- Discuss and help user to design interactor that works best for their use case.

## Interactor creation

Do not take request to create a new interactor literally. When user wants to create a new interactor, that means they want to set up a new interactor that is designed for their purposes.

Before you start creating new interactor read `references/create-interactor.md`.

## Interactor editing

Before you start editing new interactor read `references/edit-interactor.md`.

## Designing interactors

Read best practices on how to design a good interactor: `references/interactor-design.md`.

## Advanced features

Some management features are not available in the api.

For example:

- Connecting external services or providers (payments, calendars)
- Seeing customers, appointments, submitted forms

To handle questions or requests on how owner can do some things, you must follow the flow:

1. Read the full interactor schema. It includes description for interactor configuration, including read-only fields and sections available to you. You can use the description to handle the request.
2. If you can't find information, tell the user to explore interactor admin UI.

## Uploading media

Read `references/upload-media.md` to understand how to upload media to interactor.

## Keeping backups

If you need to keep backups, read `references/backups.md`.

## References

- `references/cli.md`: how to work with platform api.
- `references/interactor-design.md`: best practices on how to design the interactor.
- `references/create-interactor.md`: checklist for interactor creation.
- `references/edit-interactor.md`: checklist for interactor editing.
- `references/backups.md`: instructions on how to keep backups.
- `references/upload-media.md`: instructions on how to upload media.
