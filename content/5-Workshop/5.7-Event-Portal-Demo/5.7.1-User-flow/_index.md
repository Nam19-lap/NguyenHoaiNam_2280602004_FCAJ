---
title : "User Flow"
date : 2026-07-12
weight : 1
chapter : false
pre : " <b> 5.7.1. </b> "
---

#### Objective of the User flow

The User flow shows the experience of an event participant on the deployed Event Portal website. The user starts from the home page, registers or signs in, browses events, opens event details, and checks registered tickets.

#### 1. Register or sign in

A new participant can select **Register now** to create a user account. The registration form asks for name, email, and password. After the account is created, the user can sign in and use the event registration features.

![User registration screen](/images/5-Workshop/event-portal-demo/00-register-page.png)

If the account already exists, the user can use the login screen.

![EventPortal login screen](/images/5-Workshop/event-portal-demo/00-login-page.png)

After signing in, the navigation bar shows **My Tickets**, which indicates that the session is active and the user can access personal features. This registration flow is intended for normal participant accounts; administrator accounts are provided separately.

#### 2. Browse events

The home page displays all events returned by the backend. Each event card contains the cover image, category, date, title, location, short description, and remaining seats.

![Event listing page](/images/5-Workshop/event-portal-demo/01-homepage-events.png)

Available interactions:

1. **Search**: filter events by title or description.
2. **Category filter**: select Technology, Music, or Education.
3. **View details**: open the event detail page.
4. **Seat status**: check available seats before registering.

The frontend calls `GET /events`. When a category is selected, it calls a filtered endpoint such as `GET /events?category=music`.

#### 3. View event details

When the user selects an event, the detail page shows full information including time, location, description, and seat status.

![User event details and ticket](/images/5-Workshop/event-portal-demo/02-user-event-detail-ticket.png)

Main elements on the detail page:

- **Cover image** for quick visual identification.
- **Title and category** to describe the event topic.
- **Time and location** for attendance planning.
- **Event description** for detailed context.
- **Seat status** showing registered seats compared with total seats.
- **Ticket card** when the user has already registered.

If the user has not registered yet, the right-side panel shows a **Register ticket** button. When clicked, the frontend calls the registration API. The backend creates a registration record, updates seat counts, and returns ticket information.

#### 4. Check registered tickets

After signing in, the user can open **My Tickets** to review registered events.

![User registered ticket list](/images/5-Workshop/event-portal-demo/03-user-my-tickets.png)

This screen is important because it:

1. Confirms successful event registration.
2. Shows the ticket code for check-in.
3. Allows the user to return to event details.
4. Demonstrates that the frontend can retrieve registration data from the backend.

The backend returns user registration records and enriches them with event metadata so the frontend can display event title, date, location, and ticket code.

#### 5. User flow summary

The User flow can be summarized as:

```text
Open app -> Register/Sign in -> Browse events -> View details -> Register ticket -> Open My Tickets
```

This flow proves that the application supports the core participant features: event discovery, event details, registration, and personal ticket management.
