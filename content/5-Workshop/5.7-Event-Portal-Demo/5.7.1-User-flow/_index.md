---
title : "User Flow"
date : 2026-07-12
weight : 1
chapter : false
pre : " <b> 5.7.1. </b> "
---

#### User flow objective

The User flow demonstrates the attendee experience in Event Portal. A user starts from registration or login, browses events, opens event details, registers for a ticket, and then tracks attendance status after Admin check-in/check-out.

#### 1. Register or log in

A new attendee can choose **Register now** to create a user account. The registration form requires name, email, and password. After creating the account, the user can log in and use event registration features.

![Register page](/images/5-Workshop/event-portal-demo/00-register-page.png)

Existing users can log in from the login screen.

![Login page](/images/5-Workshop/event-portal-demo/00-login-page.png)

After login, the navigation bar shows **My Tickets** and **Profile**, confirming that the user session is active.

#### 2. Browse events

The home page displays events returned by the backend. Each event card contains the cover image, category, date, event title, location, short description, and available seats.

![Event list](/images/5-Workshop/event-portal-demo/01-homepage-events.png)

Main actions:

1. Search events by title or description.
2. Filter events by category.
3. Open event details from an event card.
4. Check seat availability before registering.

#### 3. View details and register ticket

When the user opens an event, the detail page shows date, location, description, and seat status.

![Event detail and ticket](/images/5-Workshop/event-portal-demo/02-user-event-detail-ticket.png)

If the user has not registered yet, the right side displays the **Register Ticket** button. The frontend calls the registration API, and the backend creates a registration record with a ticket code.

After successful registration, the user sees a ticket card. This ticket code can be scanned or entered manually by Admin during check-in/check-out.

#### 4. Review registered tickets

The user can open **My Tickets** to review owned tickets.

![My tickets](/images/5-Workshop/event-portal-demo/03-user-my-tickets.png)

This screen helps the user confirm registration, view ticket codes, return to event details, and prepare for event entry.

#### 5. View attendance history

After adding check-out, users can track the attendance lifecycle of each ticket in the **Attendance History** tab inside **Profile**.

![User attendance history](/images/5-Workshop/event-portal-demo/08-user-attendance-history.png)

Statuses to explain:

1. **Registered**: the user has a ticket but has not checked in yet.
2. **Checked-in**: Admin has confirmed event entry.
3. **Checked-out**: Admin has confirmed event exit or completion.

Each attendance item shows event title, date, location, ticket code, registration time, check-in time, and check-out time if available.

#### 6. User flow summary

```text
Open app -> Register/Login -> Browse events -> View details -> Register ticket -> View My Tickets -> View Attendance History
```

This proves the application supports the main attendee needs: finding events, registering tickets, using ticket codes at the gate, and tracking attendance status afterward.

