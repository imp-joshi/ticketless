### Detailed Tech Stack for Ticketless

#### Backend (Rust with Rocket)

1. **Framework**: Rocket
   - **Usage**: Building web applications and APIs.
   - **Dependencies**: `rocket`, `rocket_contrib`

2. **Database ORM**: Diesel
   - **Usage**: Database interactions.
   - **Dependencies**: `diesel`, `diesel_cli`, `dotenv`

3. **Database**: PostgreSQL
   - **Usage**: Storing data.
   - **Dependencies**: PostgreSQL server

4. **Authentication**: JWT (JSON Web Tokens)
   - **Usage**: User authentication and authorization.
   - **Dependencies**: `jsonwebtoken`, `bcrypt`

5. **Task Queue**: Tokio
   - **Usage**: Asynchronous tasks.
   - **Dependencies**: `tokio`

6. **Message Broker**: Redis
   - **Usage**: Task queue management.
   - **Dependencies**: `redis`

7. **Payment Gateway**: Stripe or PayPal
   - **Usage**: Handling payments.
   - **Dependencies**: `stripe`, `paypal`

8. **QR Code Generation**: qrcode
   - **Usage**: Generating QR codes.
   - **Dependencies**: `qrcode`

9. **Email Service**: Lettre
   - **Usage**: Sending emails.
   - **Dependencies**: `lettre`

10. **Web Server**: Rocket's built-in server or Nginx
    - **Usage**: Serving the application.
    - **Dependencies**: Nginx (optional)

11. **Background Tasks**: Tokio
    - **Usage**: Handling background tasks.
    - **Dependencies**: `tokio`

12. **Cache**: Redis
    - **Usage**: Caching data.
    - **Dependencies**: `redis`

13. **Containerization**: Docker
    - **Usage**: Containerizing the application.
    - **Dependencies**: Docker, Docker Compose

14. **Webhooks**: Custom implementation using Rocket
    - **Usage**: Handling webhooks.
    - **Dependencies**: `rocket`

#### Models

1. **User**
   - Fields: `id`, `username`, `email`, `password_hash`, `created_at`, `updated_at`

2. **Event**
   - Fields: `id`, `name`, `description`, `date`, `location`, `created_at`, `updated_at`

3. **SubEvent**
   - Fields: `id`, `event_id`, `name`, `description`, `fee`, `created_at`, `updated_at`

4. **AddonItem**
   - Fields: `id`, `event_id`, `name`, `description`, `price`, `stock`, `created_at`, `updated_at`

5. **Ticket**
   - Fields: `id`, `event_id`, `user_id`, `qr_code`, `status`, `created_at`, `updated_at`

6. **Transaction**
   - Fields: `id`, `ticket_id`, `user_id`, `amount`, `status`, `payment_gateway`, `created_at`, `updated_at`

#### Routes

1. **User Authentication**
   - `POST /register`
   - `POST /login`
   - `POST /logout`

2. **Event Management**
   - `POST /events`
   - `PUT /events/:id`
   - `DELETE /events/:id`
   - `GET /events`
   - `GET /events/:id`

3. **Ticket Management**
   - `POST /tickets`
   - `PUT /tickets/:id`
   - `DELETE /tickets/:id`
   - `GET /tickets`
   - `GET /tickets/:id`

4. **Transaction Management**
   - `POST /transactions`
   - `PUT /transactions/:id`
   - `GET /transactions`
   - `GET /transactions/:id`

5. **QR Code Generation and Scanning**
   - `POST /qrcodes`
   - `POST /qrcodes/scan`

6. **Admin Dashboard**
   - `GET /admin/stats`
   - `GET /admin/users`
   - `GET /admin/events`
   - `GET /admin/tickets`

#### Controllers

1. **UserController**
   - Handles user registration, login, and logout.

2. **EventController**
   - Handles event creation, updating, deletion, and retrieval.

3. **TicketController**
   - Handles ticket creation, updating, deletion, and retrieval.

4. **TransactionController**
   - Handles transaction creation, updating, and retrieval.

5. **QRCodeController**
   - Handles QR code generation and scanning.

6. **AdminController**
   - Handles admin-specific functionalities like statistics and user management.

#### Frontend (Next.js with React)

1. **Framework**: Next.js
   - **Usage**: Server-side rendering and static site generation.
   - **Dependencies**: `next`, `react`, `react-dom`

2. **Library**: React
   - **Usage**: Building user interfaces.
   - **Dependencies**: `react`, `react-dom`

3. **State Management**: Redux or Context API
   - **Usage**: Managing application state.
   - **Dependencies**: `redux`, `react-redux` (for Redux)

4. **Styling**: CSS Modules or styled-components
   - **Usage**: Styling components.
   - **Dependencies**: `css-modules`, `styled-components`

5. **Forms**: Formik or React Hook Form
   - **Usage**: Handling form inputs and validation.
   - **Dependencies**: `formik`, `react-hook-form`

6. **HTTP Client**: Axios or Fetch API
   - **Usage**: Making HTTP requests to the backend.
   - **Dependencies**: `axios`

#### Pages

1. **Home Page**
   - **Components**: EventList, EventCard

2. **Event Details Page**
   - **Components**: EventDetails, SubEventList, AddonItemList, TicketPurchaseForm

3. **User Registration Page**
   - **Components**: RegistrationForm

4. **User Login Page**
   - **Components**: LoginForm

5. **User Dashboard**
   - **Components**: UserProfile, UserTickets

6. **Admin Dashboard**
   - **Components**: AdminStats, ManageUsers, ManageEvents, ManageTickets

7. **QR Code Scanning Page**
   - **Components**: QRCodeScanner

#### Components

1. **EventList**: Displays a list of events.
2. **EventCard**: Displays a summary of an event.
3. **EventDetails**: Displays detailed information about an event.
4. **SubEventList**: Displays a list of sub-events for the event.
5. **AddonItemList**: Displays a list of addon items for the event.
6. **TicketPurchaseForm**: Allows users to purchase tickets for the event.
7. **RegistrationForm**: Handles user registration.
8. **LoginForm**: Handles user login.
9. **UserProfile**: Displays user profile information.
10. **UserTickets**: Displays a list of tickets purchased by the user.
11. **AdminStats**: Displays statistics for the admin dashboard.
12. **ManageUsers**: Allows admins to manage users.
13. **ManageEvents**: Allows admins to manage events.
14. **ManageTickets**: Allows admins to manage tickets.
15. **QRCodeScanner**: Handles QR code scanning for ticket validation.

#### Services

1. **ApiService**: Handles API calls to the backend.
2. **AuthService**: Manages user authentication and authorization.
3. **EventService**: Manages event-related operations.
4. **TicketService**: Manages ticket-related operations.
5. **TransactionService**: Manages transaction-related operations.
6. **QRCodeService**: Manages QR code generation and scanning.

#### State Management

1. **Redux**: Manages global state.
   - **Store**: Centralized store for the application state.
   - **Reducers**: Functions to update the state based on actions.
   - **Actions**: Functions to dispatch actions to the store.
   - **Selectors**: Functions to select specific parts of the state.

#### DevOps and Deployment

1. **Containerization**: Docker
   - **Usage**: Containerizing the backend and frontend applications.
   - **Dependencies**: Docker, Docker Compose

2. **Environment Management**: `.env` files
   - **Usage**: Managing environment variables.
   - **Dependencies**: `dotenv`

3. **CI/CD**: GitHub Actions or Travis CI
   - **Usage**: Continuous integration and deployment.
   - **Dependencies**: GitHub Actions, Travis CI

#### Testing

1. **Backend Testing**: Rust's built-in test framework
   - **Usage**: Writing unit and integration tests.
   - **Dependencies**: Rust's built-in test framework

2. **Frontend Testing**: Jest and React Testing Library
   - **Usage**: Writing unit and integration tests.
   - **Dependencies**: `jest`, `@testing-library/react`

3. **Linting**: Clippy (for Rust) and ESLint (for JavaScript/TypeScript)
   - **Usage**: Ensuring code quality.
   - **Dependencies**: `clippy`, `eslint`

#### Version Control

1. **Repository**: Git (hosted on GitHub)
   - **Usage**: Version control and collaboration.
   - **Dependencies**: Git, GitHub

### Summary of Tech Stack

1. **Backend**: Rocket, Diesel, PostgreSQL, JWT, Tokio, Redis, Stripe/PayPal, qrcode, Lettre, Nginx, Docker, Webhooks
2. **Models**: User, Event, SubEvent, AddonItem, Ticket, Transaction
3. **Routes**: User Authentication, Event Management, Ticket Management, Transaction Management, QR Code Generation and Scanning, Admin Dashboard
4. **Controllers**: UserController, EventController, TicketController, TransactionController, QRCodeController, AdminController
5. **Frontend**: Next.js, React, Redux/Context API, CSS Modules/styled-components, Formik/React Hook Form, Axios/Fetch API
6. **Pages**: Home Page, Event Details Page, User Registration Page, User Login Page, User Dashboard, Admin Dashboard, QR Code Scanning Page
7. **Components**: EventList, EventCard, EventDetails, SubEventList, AddonItemList, TicketPurchaseForm, RegistrationForm, LoginForm, UserProfile, UserTickets, AdminStats, ManageUsers, ManageEvents, ManageTickets, QRCodeScanner
8. **Services**: ApiService, AuthService, EventService, TicketService, TransactionService, QRCodeService
9. **State Management**: Redux
10. **DevOps and Deployment**: Docker, `.env` files, GitHub Actions/Travis CI
11. **Testing**: Rust's built-in test framework, Jest, React Testing Library, Clippy, ESLint
12. **Version Control**: Git, GitHub

This detailed tech stack provides a comprehensive guide to developing the Ticketless project in Rust with Rocket and Next.js with React, covering all key aspects of the project.