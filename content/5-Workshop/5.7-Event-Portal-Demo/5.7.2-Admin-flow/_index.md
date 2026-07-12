---
title : "Admin Flow"
date : 2026-07-12
weight : 2
chapter : false
pre : " <b> 5.7.2. </b> "
---

#### Objective of the Admin flow

The Admin flow shows the role of the event operator on the deployed Event Portal website. The admin can do more than view data; they can manage events, monitor registrations, inspect member lists, and support check-in.

The administrator does not create an account through the public registration form. Instead, an admin account is prepared and provided in advance so that only authorized users can access the management features.

#### 1. Sign in as Admin

The admin signs in through the same login screen as a normal user, but uses the provided admin credentials. After successful login, the system recognizes the administrator role and shows the admin navigation items.

![EventPortal login screen](/images/5-Workshop/event-portal-demo/00-login-page.png)

After this step, the admin can access:

- **Admin**: dashboard and event management.
- **Check-in**: QR/ticket-code check-in simulation.
- **Profile**: current account information.

#### 2. Admin dashboard

The dashboard is the main admin screen. It summarizes total events, total ticket registrations, and average fill rate.

![Admin dashboard](/images/5-Workshop/event-portal-demo/04-admin-dashboard.png)

Main dashboard sections:

1. **Metric cards**: total events, total registrations, and fill rate.
2. **Event table**: image, title, category, date, location, and ticket count.
3. **Members button**: open the registered member list for an event.
4. **Edit button**: open the event edit form.
5. **Delete button**: remove an event if needed.
6. **Open QR Check-in**: navigate to the attendance screen.

The dashboard helps the admin quickly understand the operational status of the portal without manually checking each API.

#### 3. Create or edit events

When selecting **Add new event**, the application opens a modal form. The form allows the admin to enter the title, category, total seats, time, location, image URL, and description.

![Admin create event modal](/images/5-Workshop/event-portal-demo/06-admin-create-event-modal.png)

Create event processing flow:

1. Admin enters event data.
2. Frontend validates required fields such as title, time, location, and total seats.
3. Frontend sends a create-event request to the backend.
4. Backend creates event metadata and a default ticket when needed.
5. After saving, the event list is refreshed.

This feature demonstrates that the system is not only reading data but also supports admin operations that modify backend data.

#### 4. View event members

From the dashboard, the admin can select **Members** to view users registered for a specific event.

![Admin event member list](/images/5-Workshop/event-portal-demo/05-admin-members.png)

The member list helps with:

- Checking which users registered for an event.
- Verifying ticket codes before check-in.
- Tracking attendee status.
- Preparing an attendance list for event operations.

The backend retrieves registrations by event id, and the frontend displays the corresponding member list.

#### 5. QR Check-in

The **QR Check-in** screen simulates attendance verification at the event entrance. The admin selects an event, enters or scans a ticket code, and confirms check-in.

![Admin QR Check-in](/images/5-Workshop/event-portal-demo/07-admin-qr-checkin.png)

Main components:

1. **Event dropdown**: select the event for check-in.
2. **Camera/QR area**: simulate camera-based QR scanning.
3. **Ticket code / QR payload**: manually enter a ticket code if needed.
4. **Ticket code examples**: available ticket codes used during check-in verification.
5. **Checked-in list**: display tickets already confirmed.

When the admin selects a ticket to scan, the frontend calls the check-in API. The backend verifies the ticket code, updates `checkedIn`, and returns the result to the frontend.

#### 6. Admin flow summary

The Admin flow can be summarized as:

```text
Admin sign in -> Open dashboard -> Manage events -> View members -> Check in attendees
```

This flow proves that the system includes the core event operation features required by organizers: monitoring data, managing events, checking member lists, and supporting attendance verification.
