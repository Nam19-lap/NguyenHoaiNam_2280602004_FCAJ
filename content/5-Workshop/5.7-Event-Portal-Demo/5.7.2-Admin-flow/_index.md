---
title : "Admin Flow"
date : 2026-07-12
weight : 2
chapter : false
pre : " <b> 5.7.2. </b> "
---

#### Admin flow objective

The Admin flow demonstrates the operator role in Event Portal. Admin can manage events, monitor registrations, view event members, and handle check-in/check-out at the event gate.

Admin accounts are prepared separately and are not created from the public registration form.

#### 1. Log in as Admin

Admin logs in from the same login page as users, using the prepared admin account. After login, the navigation displays admin-only sections.

![Login page](/images/5-Workshop/event-portal-demo/00-login-page.png)

Admin can access:

- **Admin**: dashboard and event management.
- **Check-in**: QR operation screen for check-in/check-out.
- **Profile**: current account information.

#### 2. Admin dashboard

The dashboard summarizes total events, total registrations, and average fill rate.

![Admin dashboard](/images/5-Workshop/event-portal-demo/04-admin-dashboard.png)

Main areas:

1. Metric cards for event and registration statistics.
2. Event table with image, title, category, date, location, and booked tickets.
3. Member button to view registered users.
4. Edit button to update event details.
5. Delete button to remove an event.
6. QR Check-in button to open the gate operation screen.

#### 3. Create or edit events

Admin can open the create event modal and enter event title, category, seats, date, location, cover image URL, and description.

![Create event modal](/images/5-Workshop/event-portal-demo/06-admin-create-event-modal.png)

The frontend validates required fields, sends the request to the backend, and refreshes the event list after success.

#### 4. View event members

From the dashboard, Admin can open the registered member list of each event.

![Member list](/images/5-Workshop/event-portal-demo/05-admin-members.png)

This helps Admin verify registered users, compare ticket codes, and prepare for check-in/check-out operations.

#### 5. QR Check-in and Check-out

The **QR Check-in** screen is used to operate attendance status at the event gate. The updated screen includes a **Check-in / Check-out** mode switch so Admin can choose the action before scanning QR or entering a ticket code.

![Admin QR Check-in và Check-out](/images/5-Workshop/event-portal-demo/09-admin-qr-checkin-checkout-mode.png)



Updated components:

1. Event dropdown.
2. Scan mode: **Check-in** or **Check-out**.
3. Camera/QR area for real ticket scanning.
4. Ticket code / QR payload input for manual fallback.
5. Attendee ticket list for the selected event.
6. Ticket status: not checked in, checked in waiting for check-out, or checked out.
7. Session activity list for recent admin actions.

#### 6. Admin flow summary

```text
Admin login -> Open dashboard -> Manage events -> View members -> Choose Check-in/Check-out mode -> Scan QR or enter ticket code -> Update attendance status
```

This proves the system supports key event operations: monitoring data, managing events, checking registered users, confirming entry, and confirming exit.

