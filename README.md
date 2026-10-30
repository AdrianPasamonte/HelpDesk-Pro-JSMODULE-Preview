# HelpDesk Pro — JavaScript Module Preview

A preview of HelpDesk Pro organized into separate HTML, CSS, and JavaScript modules. The original application remains at https://adrianpasamonte.github.io/Campus-Help-Desk/app.html.

A campus help desk and ticketing system built as a group class project. Students can find answers, submit concerns, and follow up with the appropriate support team.

The current scope uses student concerns at STI Ortigas-Cainta as its reference. This is a class project prototype, not an official school service. HelpDesk Pro remains the project name while the team reviews its branding and scope.

**[Open the website](https://adrianpasamonte.github.io/HelpDesk-Pro-JSMODULE-Preview/app.html)**

## User roles

| Role | Access |
| --- | --- |
| Student | Read FAQs, submit tickets, view their own requests, reply, and confirm or reopen a resolution. |
| Staff | View their department's tickets and handle unassigned requests or requests assigned to them. |
| Admin | Oversee all tickets, manage assignments and departments, create staff accounts, publish FAQs, and review reports. |

Public registration creates Student accounts only. Admins create Staff/Admin accounts. Students cannot be promoted; existing staff can be promoted to Admin.

## Support scope

Ticket creation starts with a general topic, then asks for a specific concern and the relevant details.

| Topic | Examples | Routed to |
| --- | --- | --- |
| Account access | Forgotten school password, Authenticator problems, unavailable registered phone, verification-code issues | IT |
| eLMS & SIMS | Website errors, unavailable handouts, failed assignment uploads, missing page content | IT |
| Computer lab | Computers not starting, faulty peripherals, application issues, lab computer internet problems | IT |
| Student records & enrollment | Document requests, enrollment questions, incorrect student records | Registrar |
| Fees & payments | Unrecorded payments, fee or balance questions | Finance / Cashier |
| Something else / Not sure | Concerns that do not fit the available choices | Admin review |

The system records and routes requests. It does not directly reset school Microsoft accounts, change grades, process payments, or issue school documents. Office procedures and response schedules still need to be confirmed by the team.

## Main features

- **Student Help Center:** searchable FAQs, topic filters, and visible Create Ticket buttons.
- **Guided ticket creation:** topic, concern, and questions specific to the problem.
- **Department queues:** automatic routing and access restrictions for staff.
- **Ticket conversations:** student and staff replies, with a Staff label on support replies.
- **Screenshots:** attachments on tickets and replies, with validation and upload retry.
- **Resolution confirmation:** students confirm a solution or reopen the request.
- **Notifications:** unread badges for replies and ticket changes, with updates checked every 20 seconds while the app is visible.
- **Account tools:** saved display names, confirmed email changes, password visibility, password confirmation, and email-based password recovery.
- **FAQ management:** admins can draft, publish, unpublish, archive, and restore articles.
- **Student ticket view:** a centered layout, separate problem and solution, expandable details, and a scrollable conversation.

Screenshots support PNG, JPG, and WebP, with up to 3 files per submission and a maximum of 5 MB per file.

## Ticket workflow

1. The student checks the Help Center or creates a ticket.
2. The selected topic determines its department.
3. Staff or an admin assigns and handles the request.
4. The student and support team exchange replies and screenshots.
5. Support marks the ticket **Resolved** with a required resolution note.
6. The student selects **Yes, it's fixed** to close it, or **Not fixed** to reopen it.

Active tickets appear oldest first. Students do not select a priority. Staff cannot directly close tickets, and resolved/closed conversations are read-only. Students can delete their own Open tickets submitted by mistake.

## Dashboard and Reports

**Dashboard** supports daily work. It shows active, open, in-progress, and unassigned requests, plus the oldest requests needing attention.

**Reports** helps admins review patterns through a request-volume graph, department bars, and the five most reported concerns. Review periods include 7, 30, or 90 days, or all time.

Report periods use the ticket submission date. Charts display actual records and show an empty state when no requests fall within the selected period.

## Technology

- HTML, CSS, and JavaScript for the web interface.
- Supabase for authentication, database records, access policies, private screenshot storage, and staff account creation.
- GitHub for source control and GitHub Pages for frontend hosting.
- Trello for team task coordination.

## Run the app

### Hosted version

Open [HelpDesk Pro](https://adrianpasamonte.github.io/HelpDesk-Pro-JSMODULE-Preview/app.html). Use the full `app.html` address.

### Local development

1. Clone or download this repository and install Node.js 22 or newer.
2. Run `npm start`, or double-click `Start-HelpDesk.cmd` on Windows.
3. Open `http://127.0.0.1:5504/app.html` and keep the server running.

There is no frontend build step. The app needs an internet connection to reach Supabase and load its client library.

### Backend configuration

This repository contains the frontend connected to the project's existing Supabase backend. Cloning the repository does not recreate that backend.

For a different Supabase project, the team must configure its database, access policies, screenshot storage, and staff-creation function, then update the connection settings in `js/core/client.js`.

This preview uses the same existing Supabase project as the original. Normal app actions save real records there. Backend settings are unchanged. Password recovery on this separate domain requires its recovery return URL to be included in the project's Auth redirect allowlist; email delivery and preview redirects are not newly verified.

## Repository files

| File | Purpose |
| --- | --- |
| `app.html` | Pages, forms, dialogs, and interface structure |
| `js/main.js` | Startup and feature wiring |
| `js/core/` | Shared client, session, state, navigation, permissions and updates |
| `js/features/` | Account, ticket, knowledge, notification, user and report workflows |
| `js/ui/` | Shared display and dialog helpers |
| `css/` | Shared and feature styles, including responsive views |
| `tools/` | Local preview, launcher and syntax checking |
| `tests/` | Small local permission, preview and startup tests |
| `.gitignore` | Excludes local development files and secrets |

The public repository contains the app source and documentation. Database scripts and Supabase deployment helpers are maintained separately. The included small Node tests can be run with `npm test`; use `npm run check` for syntax checks. These local tests do not certify live backend authorization or email delivery.

## Testing and feedback

Test with separate Student, Staff, and Admin accounts. Staff testing should cover more than one department.

- Register, sign in, sign out, recover a password, and save profile changes.
- Search FAQs and test every ticket topic and its required questions.
- Check ticket routing, assignment, transfers, and access restrictions.
- Send replies, switch tickets quickly, and try repeated submission clicks.
- Upload screenshots and test rejected files and failed-upload retries.
- Resolve, confirm, reopen, and delete tickets under the allowed conditions.
- Check notifications and automatic updates without losing a typed reply.
- Test staff management and FAQ publishing permissions.
- Compare dashboard counts and report graphs with the actual tickets.
- Review readability, navigation, scrolling, and layouts on desktop and mobile.

For each issue, record the account role, steps, expected result, actual result, and a screenshot. Also flag confusing wording, missing concerns, and unnecessary steps.
