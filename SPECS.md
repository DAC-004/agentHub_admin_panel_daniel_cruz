# SPECS.md

# AgentHub Admin Panel Prototype Specification

## 1. Objective

Build a polished, browser-ready HTML admin panel prototype for **AgentHub**, a SaaS platform where companies rent AI agents for business workflows. The prototype is for internal product review and future backend handoff.

AgentHub agents are pre-configured AI assistants that can be assigned reusable skills such as web browsing, document reading, invoice parsing, calendar management, report generation, and ticket summarization.

This project is **specification-first**. This `SPECS.md` file must be created and committed before any HTML work begins. Git history will be evaluated.

## 2. Required Deliverables

1. `SPECS.md` at the root of the repository.
2. A separate Git commit for `SPECS.md` before the first HTML file.
3. A fully working admin panel prototype.
4. Preferred implementation: one `index.html` file.
5. Acceptable implementation: multiple linked HTML files, one per major section.
6. All prototype data must be hardcoded.
7. The final prototype must open directly in a browser without installing dependencies.

## 3. Technology Constraints

### Required

- HTML5
- Tailwind CSS via CDN
- Vanilla JavaScript only
- Hardcoded data
- Semantic HTML
- Tailwind `dark:` utilities for dark/light mode

### Prohibited

- React
- Vue
- Angular
- Svelte
- jQuery
- Bootstrap
- Build tools
- Bundlers
- Backend APIs
- Database connections
- External CSS files
- Inline `style` attributes
- Custom CSS files

All styling must be implemented with Tailwind utility classes only.

## 4. Source-of-Truth Requirements

The implementation must satisfy the requirements shown in the reference images at `docs/design-reference/agenthub-admin-panel/` (requirement screenshots only — not app assets):

1. `01-what-you-need-to-do-spec-first.png`
2. `02-what-you-need-to-do-build-dashboard.png`
3. `03-user-agent-skills-requirements.png`
4. `04-contracts-error-log-requirements.png`
5. `05-global-interactions-requirements.png`
6. `06-evaluation-criteria.png`

Required behavior extracted from the images:

- All six admin sections must exist.
- All six sections must be accessible from a persistent sidebar.
- A top-bar dark/light mode toggle must switch the full panel.
- Dark/light mode state must remain while navigating between sections.
- All action rows must have a working `⋮` dropdown.
- Dropdowns must open, close on action click, and close on outside click.
- “View detail” must open a modal in at least four sections.
- Modals must close by close button and backdrop click.
- Agent skill lists must be collapsed by default.
- Agent skill lists must expand/collapse on click with a visible transition.
- Hardcoded agent names must be consistent across Agent Management, Agent Contracts, and Error Log.
- HTML must use semantic tags such as `header`, `nav`, `main`, `section`, `table`, and `button`.
- The layout must be usable on desktop and tablet viewports.

## 5. Application Structure

The admin panel must contain these six sections:

1. Dashboard
2. User Management
3. Agent Management
4. Skills
5. Agent Contracts
6. Error Log

A persistent sidebar must provide navigation to each section.

## 6. Global Layout Specification

### 6.1 App Shell

Use a two-column admin layout:

- Left side: persistent sidebar.
- Right side: main application area.
- Top of main area: header/top bar.
- Below the top bar: active section content.

The shell must support both light and dark color schemes.

### 6.2 Sidebar

The sidebar must include:

- AgentHub brand label.
- Navigation items for all six sections.
- Active state indicator for the selected section.
- Semantic `<nav>` markup.
- Buttons or links that are keyboard-focusable.
- Layout that remains usable on desktop and tablet screens.

Required sidebar labels:

- Dashboard
- User Management
- Agent Management
- Skills
- Agent Contracts
- Error Log

### 6.3 Top Bar

The top bar must include:

- Current section title.
- Dark/light mode toggle.
- Optional short page context or admin label.
- Consistent spacing and alignment.

The dark/light mode toggle must:

- Switch the full interface, not only isolated components.
- Use Tailwind `dark:` classes.
- Preserve the selected mode while switching sections.
- Update its visible state, label, or icon.

### 6.4 Main Content

The main content area must:

- Use a semantic `<main>` element.
- Use a semantic `<section>` for each admin section.
- Show one active section at a time if implemented as a single-page prototype.
- Use consistent spacing, borders, cards, badges, tables, and controls.
- Avoid cramped, outdated, or low-density layout decisions.

## 7. Hardcoded Data Contract

All prototype data must be hardcoded and internally consistent.

### 7.1 Shared Agent Names

The same agent names must appear exactly across Agent Management, Agent Contracts, and Error Log:

- Atlas Support Agent
- Ledger Reconciliation Agent
- Calendar Dispatch Agent
- Insight Report Agent

### 7.2 Shared Client / Owner Names

Use these client and owner names consistently:

- Northstar Property Group
- Beacon Health Partners
- UrbanBuild Contractors
- Meridian Legal Services

### 7.3 Shared Skill Names

Skill names must be reused consistently across Agent Management, Skills, and Agent Contracts:

- Web Browsing
- Document Reader
- Ticket Summarizer
- Invoice Parser
- Report Generator
- Calendar Manager
- Email Drafting
- Risk Scanner

## 8. Reusable Component Inventory

The implementation should treat these as reusable UI patterns, even if coded in one HTML file:

1. **App Shell**
   - Sidebar, top bar, and main content frame.

2. **Sidebar Navigation Item**
   - Reusable navigation control with active and inactive states.

3. **Section Header**
   - Page title, optional description, and optional supporting actions.

4. **Metric Card**
   - Dashboard summary card with icon, label, value, and accent treatment.

5. **Data Table**
   - Structured table pattern for users, contracts, and optionally errors.

6. **Status Badge**
   - Visual label for user status, agent status, contract status, and error type.

7. **Action Dropdown**
   - `⋮` trigger with contextual row actions.

8. **Modal**
   - Reusable overlay pattern for detail and configuration views.

9. **Collapsible Skill List**
   - Expandable/collapsible skill display used in Agent Management.

10. **Chart Placeholder**
    - Non-functional visual placeholder for weekly activity.

11. **Textarea Configuration Field**
    - Editable system prompt field used in the agent configuration modal.

## 9. Section Specifications

---

## 9.1 Dashboard

### Purpose

The Dashboard gives admins a quick operational and financial overview of the platform.

### Required Components

- Four metric cards.
- Weekly activity chart placeholder.

### Specifications

1. Display four metric cards in a responsive grid.
   - Desktop: four cards in one row when space allows.
   - Tablet: cards wrap into a two-column layout.

2. Include these metric cards:
   - `Total Revenue This Month`: `$84,250`
   - `Discount & Coupon Losses`: `$6,430`
   - `Active Agents`: `128`
   - `Failing Agents`: `7`

3. Each metric card must include:
   - Icon or visual marker.
   - Label.
   - Hardcoded value.
   - Distinct accent treatment.
   - Rounded card container.
   - Light and dark mode styling.

4. Add a full-width weekly activity chart placeholder below the cards.
   - Use a bordered or dashed container.
   - Include centered text: `Weekly Activity Chart Placeholder`.
   - The placeholder must not use a charting library.

---

## 9.2 User Management

### Purpose

User Management lets admins inspect registered users and access user-level actions.

### Required Components

- User table.
- Status badges.
- Row action dropdowns.
- User detail modal.

### Required Columns

- Name
- Email
- Plan
- Status
- Actions

### Required Data

| Name         | Email                                                                 | Plan       | Status    | Company                  | Joined     | Last Login       |
| ------------ | --------------------------------------------------------------------- | ---------- | --------- | ------------------------ | ---------- | ---------------- |
| Maya Chen    | [maya.chen@northstar.example](mailto:maya.chen@northstar.example)     | Enterprise | Active    | Northstar Property Group | 2026-01-12 | 2026-06-22 14:35 |
| Luis Ramirez | [luis.ramirez@beacon.example](mailto:luis.ramirez@beacon.example)     | Pro        | Trial     | Beacon Health Partners   | 2026-06-01 | 2026-06-23 09:20 |
| Priya Shah   | [priya.shah@urbanbuild.example](mailto:priya.shah@urbanbuild.example) | Enterprise | Active    | UrbanBuild Contractors   | 2026-02-18 | 2026-06-21 17:10 |
| Evan Brooks  | [evan.brooks@meridian.example](mailto:evan.brooks@meridian.example)   | Standard   | Past Due  | Meridian Legal Services  | 2026-03-05 | 2026-06-18 11:42 |
| Aisha Grant  | [aisha.grant@clearline.example](mailto:aisha.grant@clearline.example) | Pro        | Suspended | Clearline Logistics      | 2026-04-09 | 2026-06-10 08:55 |

### Specifications

1. Render at least five hardcoded user rows in a semantic table using:
   - `<table>`
   - `<thead>`
   - `<tbody>`
   - `<tr>`
   - `<th>`
   - `<td>`

2. Each row must display:
   - User name.
   - Email.
   - Plan.
   - Status badge.
   - `⋮` action dropdown.

3. Status badges must be visually distinct:
   - Active: success treatment.
   - Trial: informational treatment.
   - Past Due: warning treatment.
   - Suspended: error/disabled treatment.

4. Each row dropdown must include:
   - `View detail`
   - `Delete`

5. `View detail` must open a modal with the full user record:
   - Name
   - Email
   - Plan
   - Status
   - Company
   - Joined date
   - Last login

6. `Delete` may show a non-persistent prototype response.
   - It must not call an API.
   - It must not reload the page.
   - It must not break the table layout.

---

## 9.3 Agent Management

### Purpose

Agent Management lets admins review agents, ownership, operational status, assigned skills, and configuration prompts.

### Required Components

- Agent listing.
- Status badges.
- Collapsible skill lists.
- Row/card action dropdowns.
- Configure modal with editable system prompt.

### Required Data

| Agent Name                  | Owner                    | Status   | Skills                                            |
| --------------------------- | ------------------------ | -------- | ------------------------------------------------- |
| Atlas Support Agent         | Northstar Property Group | Active   | Web Browsing, Document Reader, Ticket Summarizer  |
| Ledger Reconciliation Agent | Beacon Health Partners   | Failing  | Document Reader, Invoice Parser, Report Generator |
| Calendar Dispatch Agent     | UrbanBuild Contractors   | Active   | Calendar Manager, Email Drafting, Web Browsing    |
| Insight Report Agent        | Meridian Legal Services  | Inactive | Report Generator, Document Reader, Risk Scanner   |

### Required System Prompts

- Atlas Support Agent:
  - `You are Atlas Support Agent, an internal support assistant for Northstar Property Group. Summarize tenant requests, identify urgency, and prepare clear escalation notes for staff review.`

- Ledger Reconciliation Agent:
  - `You are Ledger Reconciliation Agent for Beacon Health Partners. Extract invoice details, compare them against approved records, identify mismatches, and produce concise reconciliation findings.`

- Calendar Dispatch Agent:
  - `You are Calendar Dispatch Agent for UrbanBuild Contractors. Review scheduling requests, identify availability conflicts, and prepare calendar actions for human approval.`

- Insight Report Agent:
  - `You are Insight Report Agent for Meridian Legal Services. Review source documents, identify risks, and generate structured operational summaries with clear supporting notes.`

### Specifications

1. Render at least four hardcoded agent records.

2. Each agent record must show:
   - Agent name.
   - Owner.
   - Status badge.
   - Collapsed skill list control.
   - `⋮` action dropdown.

3. Status badges must support:
   - Active
   - Inactive
   - Failing

4. Skill lists must be collapsed by default.

5. Each agent must include an expand/collapse control.
   - First click expands skills.
   - Second click collapses skills.
   - The transition must be visible and smooth.
   - The control must visually communicate expanded/collapsed state.

6. Each agent dropdown must include:
   - `Configure`
   - `Delete`

7. `Configure` must open a modal showing:
   - Agent name.
   - Owner.
   - Status.
   - Assigned skills.
   - Editable `<textarea>` containing the agent system prompt.

8. `Delete` may show a non-persistent prototype response.
   - It must not call an API.
   - It must not reload the page.

---

## 9.4 Skills

### Purpose

The Skills section explains and catalogs reusable capabilities that can be attached to AgentHub agents.

### Required Components

- In-panel explanation.
- Skill catalog.
- Usage count indicator.
- Action dropdowns.
- Skill detail modal.

### Required Explanation

A skill is a reusable capability that can be attached to an AI agent so the agent can perform a specific category of work, such as browsing the web, reading documents, parsing invoices, managing calendars, or generating reports.

### Required Data

| Skill Name        | Description                                                                      | Agents Enabled | Associated Agents                                                      |
| ----------------- | -------------------------------------------------------------------------------- | -------------: | ---------------------------------------------------------------------- |
| Web Browsing      | Allows an agent to retrieve and summarize public web information.                |              2 | Atlas Support Agent, Calendar Dispatch Agent                           |
| Document Reader   | Allows an agent to read uploaded documents and extract structured details.       |              3 | Atlas Support Agent, Ledger Reconciliation Agent, Insight Report Agent |
| Ticket Summarizer | Allows an agent to condense support tickets into actionable summaries.           |              1 | Atlas Support Agent                                                    |
| Invoice Parser    | Allows an agent to extract totals, vendors, dates, and line items from invoices. |              1 | Ledger Reconciliation Agent                                            |
| Report Generator  | Allows an agent to produce structured operational reports.                       |              2 | Ledger Reconciliation Agent, Insight Report Agent                      |
| Calendar Manager  | Allows an agent to inspect schedules and prepare calendar actions.               |              1 | Calendar Dispatch Agent                                                |
| Email Drafting    | Allows an agent to prepare email responses or dispatch messages for review.      |              1 | Calendar Dispatch Agent                                                |
| Risk Scanner      | Allows an agent to identify possible operational, legal, or compliance risks.    |              1 | Insight Report Agent                                                   |

### Specifications

1. Display the required in-panel explanation near the top of the section.

2. Display at least four skills.
   - Preferred: display all eight skills listed above.

3. Each skill record must show:
   - Skill name.
   - Description.
   - Number of agents enabled.
   - `⋮` action dropdown.

4. Agents enabled counts must align with the Agent Management records.

5. Each skill dropdown must include:
   - `View detail`
   - `Delete`

6. `View detail` must open a modal showing:
   - Skill name.
   - Description.
   - Agents enabled count.
   - Associated agents.
   - Example use case.

7. `Delete` may show a non-persistent prototype response.
   - It must not remove required hardcoded data permanently.
   - It must not reload the page.

---

## 9.5 Agent Contracts

### Purpose

Agent Contracts lets admins review active and historical rental contracts, including rented agents, contracted skills, contract windows, and payment totals.

### Required Components

- Contracts table.
- Contract status badge.
- Row action dropdowns.
- Contract detail modal with itemized skill pricing.

### Required Columns

- Client
- Agent
- Contracted Skills
- Start Date
- End Date
- Amount Paid
- Actions

### Required Data

| Client                   | Agent                       | Skills                                            | Start Date | End Date   | Status      | Amount Paid |
| ------------------------ | --------------------------- | ------------------------------------------------- | ---------- | ---------- | ----------- | ----------: |
| Northstar Property Group | Atlas Support Agent         | Web Browsing, Document Reader, Ticket Summarizer  | 2026-06-01 | 2026-06-30 | Active      |     $12,800 |
| Beacon Health Partners   | Ledger Reconciliation Agent | Document Reader, Invoice Parser, Report Generator | 2026-05-15 | 2026-06-15 | Renewal Due |     $18,400 |
| UrbanBuild Contractors   | Calendar Dispatch Agent     | Calendar Manager, Email Drafting, Web Browsing    | 2026-06-10 | 2026-07-10 | Active      |      $9,750 |
| Meridian Legal Services  | Insight Report Agent        | Report Generator, Document Reader, Risk Scanner   | 2026-04-01 | 2026-06-01 | Expired     |     $14,200 |

### Itemized Skill Pricing

| Contract                                             | Itemized Skills                                                           |
| ---------------------------------------------------- | ------------------------------------------------------------------------- |
| Northstar Property Group / Atlas Support Agent       | Web Browsing: $4,200; Document Reader: $5,100; Ticket Summarizer: $3,500  |
| Beacon Health Partners / Ledger Reconciliation Agent | Document Reader: $5,400; Invoice Parser: $6,200; Report Generator: $6,800 |
| UrbanBuild Contractors / Calendar Dispatch Agent     | Calendar Manager: $3,600; Email Drafting: $2,650; Web Browsing: $3,500    |
| Meridian Legal Services / Insight Report Agent       | Report Generator: $5,900; Document Reader: $4,800; Risk Scanner: $3,500   |

### Specifications

1. Render at least four hardcoded contract rows in a semantic table.

2. Each contract row must show:
   - Client.
   - Rented agent.
   - Contracted skills.
   - Start date.
   - End date.
   - Amount paid.
   - `⋮` action dropdown.

3. Each contract should include a status badge:
   - Active
   - Renewal Due
   - Expired

4. Each contract dropdown must include:
   - `View detail`

5. `View detail` must open a modal with:
   - Client.
   - Agent.
   - Contract dates.
   - Status.
   - Amount paid.
   - Itemized skills.
   - Individual skill prices.

6. Itemized skill prices must logically sum to the contract amount paid.

7. Contract agent names must exactly match Agent Management agent names.

8. Contract skill names must match Skills catalog names.

---

## 9.6 Error Log

### Purpose

The Error Log gives admins visibility into agent execution failures and operational exceptions.

### Required Components

- Error log table or list.
- Error type badges.
- Row action dropdowns.
- Error detail modal.
- Mark as resolved prototype action.

### Required Data

| Timestamp        | Agent Name                  | Error Type   | Severity | Short Description                                  |
| ---------------- | --------------------------- | ------------ | -------- | -------------------------------------------------- |
| 2026-06-23 09:14 | Ledger Reconciliation Agent | Parsing      | High     | Failed to extract invoice total from uploaded PDF. |
| 2026-06-23 10:02 | Atlas Support Agent         | API Timeout  | Medium   | Web lookup exceeded response threshold.            |
| 2026-06-23 10:47 | Calendar Dispatch Agent     | Permission   | High     | Calendar scope unavailable for requested action.   |
| 2026-06-23 11:18 | Ledger Reconciliation Agent | Validation   | High     | Reconciliation output failed confidence rules.     |
| 2026-06-23 12:05 | Insight Report Agent        | Tool Failure | Medium   | Report generator returned incomplete section data. |
| 2026-06-23 13:22 | Atlas Support Agent         | Rate Limit   | Low      | External search provider limit reached.            |

### Required Trace Examples

Each error detail modal must include a full trace field. Example trace format:

```text
ExecutionTrace:
agent_id: ledger-reconciliation-agent
step: invoice_parse
tool: document_reader
result: failed
message: Unable to identify invoice total with required confidence threshold.
```

### Specifications

1. Render at least six hardcoded error entries.

2. Each error entry must show:
   - Timestamp.
   - Agent name.
   - Error type badge.
   - Short description.
   - `⋮` action dropdown.

3. Error type badges must be color-coded by type or severity.

4. Each error dropdown must include:
   - `View detail`
   - `Mark as resolved`

5. `View detail` must open a modal showing:
   - Timestamp.
   - Agent name.
   - Error type.
   - Severity.
   - Short description.
   - Full trace.

6. `Mark as resolved` must provide a visible prototype response.
   - Acceptable behavior: change row status to `Resolved`, dim the row, or show a temporary confirmation.
   - It must not reload the page.
   - It must not call an API.

7. Error agent names must exactly match Agent Management agent names.

## 10. Global Interaction Requirements

### 10.1 Navigation

- Sidebar navigation must switch between sections.
- Active navigation state must update immediately.
- Section title in the top bar must update with the active section.
- Theme state must remain unchanged while navigating.

### 10.2 Action Dropdowns

Every required row or card action menu must use the same behavior:

- Triggered by a `⋮` button.
- Opens on click.
- Closes when clicking the trigger again.
- Closes when selecting an action.
- Closes when clicking outside the dropdown.
- Only one dropdown may be open at a time.
- Trigger must be keyboard-focusable.
- Trigger must include an accessible label.
- Menu must not be clipped by parent containers.

Sections requiring dropdowns:

- User Management
- Agent Management
- Skills
- Agent Contracts
- Error Log

### 10.3 Modals

All modals must follow one consistent overlay pattern:

- Centered modal panel.
- Full-screen backdrop.
- Visible close button.
- Close on close button click.
- Close on backdrop click.
- Do not close when clicking inside the modal panel.
- Include `role="dialog"` and `aria-modal="true"` if not using native `<dialog>`.
- Include a clear heading.
- Preserve readable layout in light and dark mode.

Required modal triggers:

- User Management: `View detail`
- Agent Management: `Configure`
- Skills: `View detail`
- Agent Contracts: `View detail`
- Error Log: `View detail`

### 10.4 Collapsible Skill Lists

- Agent skill lists must start collapsed.
- Expand/collapse must be controlled independently per agent.
- The transition must be visible.
- The control must indicate current state.
- Collapsing one agent must not break another agent’s state.

### 10.5 Dark/Light Mode

- Toggle must switch the entire panel.
- Use Tailwind `dark:` utilities.
- Apply the dark mode class to a top-level wrapper or document root.
- Maintain theme state during section navigation.
- Both modes must style sidebar, top bar, cards, tables, dropdowns, modals, badges, and chart placeholder.

## 11. Accessibility Requirements

- Use semantic HTML controls for all interactions.
- Use `<button>` for dropdown triggers, modal close buttons, expand/collapse controls, and toggle controls.
- Use accessible labels on icon-only buttons.
- Use readable visible text for badge meaning; do not rely on color alone.
- Preserve text contrast in light and dark mode.
- Ensure all controls are keyboard-focusable.
- Ensure modal content has a heading.
- Ensure modal close buttons have `aria-label="Close modal"`.
- Ensure dropdown triggers have context-specific labels, such as `aria-label="Open actions for Atlas Support Agent"`.

## 12. Responsive Requirements

The prototype must be usable on:

- Desktop viewports.
- Tablet viewports.

Responsive behavior:

- Sidebar remains accessible.
- Main content does not overlap the sidebar.
- Metric cards wrap cleanly.
- Tables use readable spacing or horizontal overflow containers.
- Dropdowns remain clickable.
- Modals fit within viewport width and height.
- Content spacing remains professional at tablet widths.

A mobile hamburger navigation is not required.

## 13. Visual Design Requirements

The interface should feel like a modern SaaS admin console.

Required visual qualities:

- Clean hierarchy.
- Professional spacing.
- Consistent card radius.
- Consistent badge styling.
- Clear active navigation state.
- Clear hover and focus states.
- Distinct but restrained accent colors.
- Polished light mode.
- Polished dark mode.
- No unfinished browser-default controls except where intentionally acceptable, such as a textarea inside a modal.

## 14. Implementation Guidance

Recommended implementation approach:

1. Define hardcoded data arrays for users, agents, skills, contracts, and errors.
2. Render repeatable rows/cards from data where practical.
3. Use `data-*` attributes for section IDs, record IDs, and action types.
4. Use event delegation for dropdown and modal actions.
5. Track the active dropdown so only one menu opens at a time.
6. Use a single reusable modal container and populate it dynamically.
7. Use a top-level class toggle for dark mode.
8. Avoid duplicating modal and dropdown logic per section.
9. Keep JavaScript readable and grouped by responsibility:
   - data
   - rendering
   - navigation
   - theme
   - dropdowns
   - modals
   - collapsibles
   - prototype actions

## 15. Manual QA Checklist

Before final submission, verify:

- `SPECS.md` exists at repository root.
- `SPECS.md` was committed before HTML work.
- All six sections are reachable from the sidebar.
- Active sidebar state updates.
- Top bar title updates.
- Dark/light mode affects the entire panel.
- Theme state remains while navigating.
- Dashboard has four metric cards.
- Dashboard has weekly chart placeholder.
- User Management has at least five rows.
- Agent Management has at least four agents.
- Skills has at least four skills.
- Agent Contracts has at least four contracts.
- Error Log has at least six entries.
- Every required row/card has a working `⋮` dropdown.
- Dropdowns close on outside click.
- Dropdowns close after choosing an option.
- Only one dropdown opens at a time.
- Required modals open correctly.
- Modals close by close button.
- Modals close by backdrop click.
- Clicking inside modal content does not close the modal.
- Agent skill lists are collapsed by default.
- Agent skill lists expand/collapse with a visible transition.
- Shared agent names match exactly across required sections.
- No framework is used.
- No external CSS file is used.
- No inline styles exist.
- Tailwind is loaded by CDN.
- HTML uses semantic tags.
- Desktop layout is usable.
- Tablet layout is usable.

## 16. Acceptance Criteria

1. `SPECS.md` exists at the repository root.
2. Git history shows `SPECS.md` was committed before any HTML file.
3. The prototype contains Dashboard, User Management, Agent Management, Skills, Agent Contracts, and Error Log.
4. All six sections are accessible from a persistent sidebar.
5. Sidebar active state updates when navigation changes.
6. Top bar title updates when navigation changes.
7. Dark/light mode toggle switches the entire interface.
8. Dark/light mode uses Tailwind `dark:` utilities.
9. Theme state persists while navigating between sections.
10. Tailwind CSS is loaded through CDN only.
11. The implementation uses vanilla JavaScript only.
12. No prohibited framework, library, bundler, external CSS file, or inline style attribute is used.
13. Dashboard displays four required metric cards.
14. Dashboard displays a weekly activity chart placeholder.
15. User Management displays at least five hardcoded users.
16. User Management rows include name, email, plan, status badge, and action dropdown.
17. User Management `View detail` opens a full user detail modal.
18. Agent Management displays at least four hardcoded agents.
19. Agent Management rows/cards include agent name, owner, status badge, collapsed skill list, and action dropdown.
20. Agent skill lists are collapsed by default.
21. Agent skill lists expand/collapse with a visible transition.
22. Agent Management `Configure` opens a modal with an editable system prompt `<textarea>`.
23. Skills displays a platform-specific explanation of skills.
24. Skills displays at least four hardcoded skills.
25. Skill records include name, description, agents-enabled count, and action dropdown.
26. Skills `View detail` opens a full skill detail modal.
27. Agent Contracts displays at least four hardcoded contracts.
28. Contract rows include client, agent, contracted skills, dates, amount paid, and action dropdown.
29. Agent Contracts `View detail` opens a full contract breakdown modal.
30. Contract breakdown includes itemized skill pricing.
31. Error Log displays at least six hardcoded errors.
32. Error rows include timestamp, agent name, error type badge, short description, and action dropdown.
33. Error badges are visually categorized by type or severity.
34. Error Log `View detail` opens a full error trace modal.
35. Error Log `Mark as resolved` provides a visible non-persistent prototype response.
36. All required dropdowns open on click.
37. All dropdowns close when clicking the trigger again.
38. All dropdowns close when clicking outside the menu.
39. All dropdowns close after selecting an action.
40. Only one dropdown is open at a time.
41. All modals close with a close button.
42. All modals close by backdrop click.
43. Clicking inside modal content does not close the modal.
44. “View detail” opens a modal in at least four different sections.
45. Agent names are consistent across Agent Management, Agent Contracts, and Error Log.
46. Skill names are consistent across Agent Management, Skills, and Agent Contracts.
47. Semantic HTML tags are used correctly.
48. All icon-only controls have accessible labels.
49. Status and error badges include visible text.
50. Layout is usable on desktop viewports.
51. Layout is usable on tablet viewports.
52. The prototype opens directly in a browser with no install step.
53. All data is hardcoded and visible without API calls.
54. The final result is polished enough for product review and backend handoff.

## 17. Out of Scope

Do not implement:

- Authentication
- Backend services
- Database persistence
- Real API calls
- Real charting library
- Production delete behavior
- User creation workflows
- Agent creation workflows
- Billing processor integration
- Real-time logs
- Export/download functionality
- Mobile hamburger navigation unless added voluntarily without compromising tablet/desktop requirements

## 18. Final Handoff Report

After implementation, provide a concise report containing:

1. Files created or changed.
2. Confirmation that `SPECS.md` was committed before HTML work.
3. Confirmation that Tailwind is loaded via CDN.
4. Confirmation that vanilla JavaScript only was used.
5. Confirmation that no external CSS or inline styles were used.
6. Confirmation that all six sections are present.
7. Confirmation that dropdowns were manually tested.
8. Confirmation that modals were manually tested.
9. Confirmation that collapsible skill lists were manually tested.
10. Confirmation that dark/light mode was manually tested.
11. Known limitations, if any.
