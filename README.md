# Group Pre-Order Homework

This document summarizes the completed static Owner Review screen for the Group Pre-Order homework and lists the files changed.

## What changed

- Added the invitation header using `GROUP_ORDER_PREVIEW.invite`: location address, date, time range, and current guest count.
- Added the Grand Total using `GROUP_ORDER_PREVIEW.sessions.total`.
- Updated the page and participant cards to match the Owner Review design, including the “Created New Pre-Order” label, the Maria notification, owner/guest card actions, quantity controls, item remove buttons, subtotals, and the Submit Pre-Order button.
- Kept semantic page structure: one `<main>`, one `<h1>`, participants in a `<ul>`/`<li>` list, and each card in an `<article>`.
- Kept cart status visible as text (“Submitted” / “Still choosing”).
- Added responsive styles for narrow screens. Both component stylesheets use the shared colors through Sass `@use`.

## Changed files

| File | Changes |
|---|---|
| [`group-order-page.component.ts`](./frontend/restaurant-frontend-app/src/app/pages/group-order-page/group-order-page.component.ts) | Exposes preview invite, participant, total, and owner-session data as signals; imports the `date` and `currency` pipes and page stylesheet. |
| [`group-order-page.component.html`](./frontend/restaurant-frontend-app/src/app/pages/group-order-page/group-order-page.component.html) | Renders the header, invitation details, notification, participant list, Grand Total, and submit button. |
| [`group-order-page.component.scss`](./frontend/restaurant-frontend-app/src/app/pages/group-order-page/group-order-page.component.scss) | Adds the page layout, design styling, shared palette, and mobile layout. |
| [`participant-card.component.ts`](./frontend/restaurant-frontend-app/src/app/components/group-orders/participant-card/participant-card.component.ts) | Adds owner-card presentation input and selects the card heading. |
| [`participant-card.component.html`](./frontend/restaurant-frontend-app/src/app/components/group-orders/participant-card/participant-card.component.html) | Renders the cart status, owner/guest action labels, dish rows, quantity controls, remove buttons, and subtotal. |
| [`participant-card.component.scss`](./frontend/restaurant-frontend-app/src/app/components/group-orders/participant-card/participant-card.component.scss) | Adds card and dish-row styling, shared palette, and responsive layout. |

## Design reference and data

- Design: [`homework-design/01-owner-review.png`](./homework-design/01-owner-review.png)
- Preview data: `GROUP_ORDER_PREVIEW` from `frontend/restaurant-frontend-app/src/app/shared/mocks/group-orders/group-order.preview.ts`
- The date and time use Angular’s `date` pipe; monetary values use Angular’s `currency` pipe.

## Run locally

Use a Node.js version supported by the Angular app, then run:

```bash
cd frontend/restaurant-frontend-app
npm start
```

Open the demo route:

```text
http://localhost:4200/reservations/demo-reservation/group-order?demo
```

## Verification

From `frontend/restaurant-frontend-app`:

```bash
npm run test:hw
npx tsc -p tsconfig.app.json --noEmit
```

Both checks passed during implementation; `npm run test:hw` reported 34 successful tests.

## Scope note

This is the static homework screen backed by `GROUP_ORDER_PREVIEW`. The Edit, Remove, quantity, close, and submit controls are visual elements only; their actions are not implemented at this level.
