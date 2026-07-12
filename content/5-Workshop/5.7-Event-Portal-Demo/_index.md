---
title : "User and Admin Flow Demo"
date : 2026-07-12
weight : 7
chapter : false
pre : " <b> 5.7. </b> "
---

#### Demo objective

After completing the backend and frontend deployment steps in the workshop, this section documents the demonstration of the **AWS Serverless Event Portal** running on AWS services. The goal is not only to show screenshots, but also to explain how the main features work for the two primary roles:

- **User**: an event participant who can browse events, register an account, sign in, view event details, register for tickets, and manage personal tickets.
- **Admin**: an administrator who uses a provided admin account to review the dashboard, manage events, inspect event members, and support QR/ticket-code check-in.

During the demo, the React/Vite frontend is hosted as a static website on Amazon S3, while the backend APIs are exposed through Amazon API Gateway and processed by AWS Lambda. The application data is stored and retrieved through the deployed backend services, which makes the demo closer to the actual serverless architecture of the project.

#### 1. Starting from the login screen

When the user selects **Login**, the application opens the authentication form. The same form is used by both User and Admin accounts. Normal users can register and sign in through the application, while administrators use accounts that are prepared and provided in advance.

![EventPortal login screen](/images/5-Workshop/event-portal-demo/00-login-page.png)

The login screen contains:

1. An **Email** field to identify the account.
2. A **Password** field to simulate authentication.
3. A provided admin account can be used to access the administrator role.
4. A **Register now** link for new users.

After a successful login, authenticated requests are sent to the deployed backend APIs. The backend uses the account role to determine whether the current user should access normal participant features or administrator functions.

#### 2. Registering a new user account

If a participant does not have an account, they can switch to the registration form. The registration form asks for name, email, and password so a new user account can be created for event registration.

![User registration screen](/images/5-Workshop/event-portal-demo/00-register-page.png)

This registration flow verifies that:

1. The user can provide basic profile information.
2. The frontend calls the registration function from AuthContext.
3. The backend authentication flow processes the registration request.
4. After the account is created, the user can sign in and use event registration features.

Administrator accounts are not created through this public registration form. They are prepared and assigned separately so that only authorized users can access management functions.

#### 3. Home page after backend integration

After opening the application, the home page displays events returned by the backend API. Summary metrics such as total events, total registrations, and fill rate are calculated from backend data.

![Event listing page](/images/5-Workshop/event-portal-demo/01-homepage-events.png)

Main functions on the home page:

- Display events as event cards.
- Search events by name or content.
- Filter events by category such as Technology, Music, or Education.
- Open the detail page to view full information and perform registration actions.

#### 4. Splitting the demo by role

For clarity, the detailed demo is divided into two sub-sections:

1. [User flow](5.7.1-User-flow/)
2. [Admin flow](5.7.2-Admin-flow/)

This structure makes the responsibilities of each role easier to understand. The User flow focuses on the participant experience, while the Admin flow focuses on event management and check-in operations.

#### 5. Quick conclusion

This overview confirms that the deployed system supports a complete flow from sign-up/sign-in to role-based feature usage. The frontend is not only a static interface; it calls the AWS backend APIs to retrieve events, tickets, registrations, and admin data.
