# Interactor Design Best Practices

Use this reference when designing the Interactor.

## Customer-Facing Goal

The customer-facing assistant should feel like the business is helping the customer directly. It should be smooth, predictable, concise, and useful.

Design for customers who may be in a hurry:

- Use short, clear, engaging text.
- Ask one question at a time in workflows and forms.
- Make labels easy to scan.
- Use emojis in labels or titles when they improve clarity or warmth and fit the brand.
- Refer to the business as "we" when speaking on behalf of the business.
- Give concrete next steps.

## Voice And Perspective

Write as the business:

- Prefer "we" over "the company."
- Use the business name where it sounds more natural than "we."
- Preserve owner-provided terminology and service names.

## Menus And Labels

Menu items, also called customer shortcuts, should be short and action-oriented.

Labels must be short, action-oriented, and include emojis relevant to the action and business area unless the owner asks for something else. The shortcut messages under each item must be short and written the way real customers would phrase them.

Examples:

- 🏷️ Pricing | What's the pricing
- ☎️ Book a Call | I'd like to book a call
- 🌿 Our Services | What are your services

Avoid long labels that read like explanations. Put detail in the destination flow or response, not in the menu label.

## Workflows

Customer workflows should avoid overwhelming the customer.

Best practices:

- Ask one question per step.
- Keep workflow steps clear for the customer-facing agent to ensure strict ordering.
- Keep workflow instructions separate from each other. The customer-facing agent should not mix them.

## Forms

Select lists overview:

- Options are not dropdowns. They are always visible.
- A single list allows selecting only one option at a time and does not allow unselecting.
- A multi list allows multiple choices.

Date time pickers overview:

- Date picker looks like a calendar. It cannot be connected to the owner's calendar.
- Time picker looks like a grid of slots, for example 10 AM, 11 AM, and 12 PM. It cannot be connected to the owner's calendar.
- Date-time picker combines date and time in a single component. It can be connected to the owner's calendar. Days unavailable for bookings are disabled. Unavailable time slots are omitted from the grid.

Step design best practices:

- Design for mobile view.
- Use discrete steps.
- Keep max 3 small fields per step.
- Keep large fields in separate steps, such as date/time pickers or select lists with multiple options.

Labels best practices:

- Use placeholders as labels: "Your name", "Details".
- For large fields, use the step title as label.
- Only provide the actual `label` field for select lists if you keep them with other fields in a single step.

## Knowledge

Use knowledge for stable business facts and policies.

Focused sections work better than broad mixed sections:

- About us
- Service area
- Hours and contact
- Pricing and payment
- Policies
- Preparation or requirements
- Parking, access, or location details

Write facts customers can act on. Avoid vague claims unless the owner supplied concrete support.

## Services

Services should help customers understand what they can request.

Each service should include:

- Clear name
- Specific description
- Who it is for, when relevant
- Duration or process, when relevant
- Customer next step
- Relevant images when available

## Products

Products should feel like a useful catalog.

Include:

- Name
- Specific description
- Stock status
- Price and currency when known
- Image URLs when available
- Clear next action

## FAQ

FAQs should answer real customer questions. Prefer 5-10 strong, business-specific FAQs over many generic ones.

Good FAQ topics:

- Service area
- Pricing or estimates
- Availability
- Cancellation or rescheduling
- What to prepare
- Payment methods
- Warranty or follow-up policy

## Greeting

Greeting messages should quickly orient customers.

Good greetings:

- Say what the business can help with.
- Offer common next steps.
- Keep the message short.
- Match the business tone.

Avoid long introductions, generic claims, or internal descriptions of modules.

## Scheduling

Scheduling should make booking easy and predictable.

Configure:

- Appointment types customers understand.
- Availability windows.
- Minimum notice.
- Auto-accept behavior when appropriate.
- Clear customer instructions for preparation or location.

If external calendar setup is missing, the owner must complete that setup in owner mode.

## Smart Links

Smart links should route customers into a specific context or workflow. Names should be clear to the owner and the resulting customer flow should make the context obvious.

## Payments

Use payments when customers need to pay for bookings or products. The owner must set them up in owner mode.

## WhatsApp

The owner must set it up in owner mode.

## Alerts

Alerts should describe owner-notification conditions in business language.

Good alert conditions:

- Customer asks for emergency service.
- Customer requests a quote above a specific amount.
- Customer reports a safety issue.
- Customer asks to speak with a person.

## Customer Experience Checklist

Before finishing customer-facing configuration:

- Text speaks as the business.
- Labels are short and scannable.
- Workflows ask one thing at a time and are reliable.
- Knowledge sections are focused.
- Services, products, and FAQs are specific.
- Greeting gives useful next steps.
- The experience avoids internal platform/tool language.
