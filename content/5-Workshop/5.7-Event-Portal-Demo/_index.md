---
title : "User and Admin Flow Demo"
date : 2026-07-12
weight : 7
chapter : false
pre : " <b> 5.7. </b> "
---

#### Demo objective

After completing the backend and frontend deployment steps, this section documents the demo flow of **AWS Serverless Event Portal** for the two main roles: **User** and **Admin**. The demo starts from registration/login and then covers the key workflows: browsing events, registering tickets, check-in, check-out, and attendance history.

The React/Vite frontend calls the configured backend APIs. Therefore, event listing, ticket creation, check-in, check-out, and attendance history are not static UI screens; they represent data processed by the backend.

#### 1. User role

The User is the event attendee. After registering or logging in, the user can browse events, open event details, register for a ticket, and review personal tickets.

Main User features:

1. Register a new account or log in with an existing account.
2. View event data from the backend.
3. Search and filter events by category.
4. View event details before registration.
5. Register for a ticket and receive a ticket code.
6. Review registered tickets in **My Tickets**.
7. Track **Attendance History** to see registered, checked-in, and checked-out states.

#### 2. Admin role

The Admin operates the event management system. Admin uses a prepared account to access the dashboard, manage events, view registered members, and handle check-in/check-out at the event gate.

Main Admin features:

1. Log in with the prepared admin account.
2. View event and registration metrics from the admin dashboard.
3. Create, update, or delete events.
4. View the registered member list of each event.
5. Select the event to operate on the QR Check-in screen.
6. Choose **Check-in** or **Check-out** mode before scanning QR/entering a ticket code.
7. Confirm attendance status and update backend data.

#### 3. Overall workflow

User flow:

```text
Register/Login -> Browse events -> View details -> Register ticket -> View ticket -> Track attendance history
```

Admin flow:

```text
Admin login -> Open dashboard -> Manage events -> View members -> Check-in -> Check-out
```

The new demo point is that the system now supports the full event attendance lifecycle. Users can review their attendance status after being checked in or checked out, while Admins can confirm both entry and exit actions.

#### 4. Detailed role-based sections

The detailed demo is split into two subsections:

1. [User flow](5.7.1-User-flow/)
2. [Admin flow](5.7.2-Admin-flow/)

This separation makes each responsibility clear. Users focus on joining events, while Admins focus on event operations.

#### 5. Quick conclusion

This demo shows a complete flow from authentication to real attendance operations. The check-in, check-out, and attendance history features make the application closer to a real event portal scenario.

