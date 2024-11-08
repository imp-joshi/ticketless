Creating a new Rust project to replicate the functionality of Ticketify (Ticketless) involves several steps. Here is a detailed roadmap to guide you through the process:

### Phase 1: Project Setup

1. **Initialize Project**
   - Create a new Rust project using Cargo.
   - Set up a new Git repository and connect it to GitHub.

2. **Set Up Rocket**
   - Add Rocket dependencies to `Cargo.toml`.
   - Configure Rocket for development and production environments.

3. **Set Up Diesel**
   - Add Diesel dependencies to `Cargo.toml`.
   - Configure Diesel with PostgreSQL.
   - Create initial database schema and run migrations.

4. **Set Up Docker**
   - Create `Dockerfile` for the Rust backend.
   - Create `docker-compose.yml` to manage multi-container applications (backend, database).

### Phase 2: Backend Development

1. **User Authentication**
   - **Models**: User
   - **Endpoints**: Register, Login, Logout, Authentication Middleware

2. **Event Management**
   - **Models**: Event, SubEvent, AddonItem
   - **Endpoints**: Create Event, Update Event, Delete Event, List Events, Event Details

3. **Ticket Management**
   - **Models**: Ticket
   - **Endpoints**: Create Ticket, Update Ticket, Delete Ticket, List Tickets, Ticket Details

4. **Transaction Management**
   - **Models**: Transaction
   - **Endpoints**: Create Transaction, Update Transaction, List Transactions, Transaction Details

5. **QR Code Generation and Scanning**
   - **Models**: QRCode
   - **Endpoints**: Generate QR Code, Scan QR Code

6. **Admin Dashboard**
   - **Endpoints**: Admin Statistics, Manage Users, Manage Events, Manage Tickets

### Phase 3: Frontend Development (Next.js with React)

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

### Phase 4: Integration and Testing

1. **Integrate Frontend and Backend**
   - Set up API calls from the frontend to the backend.
   - Handle authentication and authorization.

2. **Write Unit and Integration Tests**
   - Backend: Use Rust's built-in test framework.
   - Frontend: Use Jest and React Testing Library.

3. **Set Up CI/CD Pipeline**
   - Use GitHub Actions or Travis CI for continuous integration and deployment.

### Detailed Breakdown of Pages and Components

#### Backend (Rust with Rocket)

1. **User Authentication**
   - **Models**: User
   - **Endpoints**:
     - `POST /register`: Register a new user.
     - `POST /login`: Authenticate a user and return a JWT.
     - `POST /logout`: Invalidate the user's session.
     - Middleware to protect routes and ensure only authenticated users can access certain endpoints.

2. **Event Management**
   - **Models**: Event, SubEvent, AddonItem
   - **Endpoints**:
     - `POST /events`: Create a new event.
     - `PUT /events/:id`: Update an existing event.
     - `DELETE /events/:id`: Delete an event.
     - `GET /events`: List all events.
     - `GET /events/:id`: Get details of a specific event.

3. **Ticket Management**
   - **Models**: Ticket
   - **Endpoints**:
     - `POST /tickets`: Create a new ticket.
     - `PUT /tickets/:id`: Update an existing ticket.
     - `DELETE /tickets/:id`: Delete a ticket.
     - `GET /tickets`: List all tickets.
     - `GET /tickets/:id`: Get details of a specific ticket.

4. **Transaction Management**
   - **Models**: Transaction
   - **Endpoints**:
     - `POST /transactions`: Create a new transaction.
     - `PUT /transactions/:id`: Update an existing transaction.
     - `GET /transactions`: List all transactions.
     - `GET /transactions/:id`: Get details of a specific transaction.

5. **QR Code Generation and Scanning**
   - **Models**: QRCode
   - **Endpoints**:
     - `POST /qrcodes`: Generate a new QR code.
     - `POST /qrcodes/scan`: Scan a QR code and validate the ticket.

6. **Admin Dashboard**
   - **Endpoints**:
     - `GET /admin/stats`: Get statistics for the admin dashboard.
     - `GET /admin/users`: List all users.
     - `GET /admin/events`: List all events.
     - `GET /admin/tickets`: List all tickets.

#### Frontend (Next.js with React)

1. **Home Page**
   - **Components**:
     - `EventList`: Displays a list of events.
     - `EventCard`: Displays a summary of an event.

2. **Event Details Page**
   - **Components**:
     - `EventDetails`: Displays detailed information about an event.
     - `SubEventList`: Displays a list of sub-events for the event.
     - `AddonItemList`: Displays a list of addon items for the event.
     - `TicketPurchaseForm`: Allows users to purchase tickets for the event.

3. **User Registration Page**
   - **Components**:
     - `RegistrationForm`: Handles user registration.

4. **User Login Page**
   - **Components**:
     - `LoginForm`: Handles user login.

5. **User Dashboard**
   - **Components**:
     - `UserProfile`: Displays user profile information.
     - `UserTickets`: Displays a list of tickets purchased by the user.

6. **Admin Dashboard**
   - **Components**:
     - `AdminStats`: Displays statistics for the admin dashboard.
     - `ManageUsers`: Allows admins to manage users.
     - `ManageEvents`: Allows admins to manage events.
     - `ManageTickets`: Allows admins to manage tickets.

7. **QR Code Scanning Page**
   - **Components**:
     - `QRCodeScanner`: Handles QR code scanning for ticket validation.

### Summary of Roadmap

1. **Project Setup**
   - Initialize project, set up Rocket, Diesel, and Docker.

2. **Backend Development**
   - User Authentication: Models and endpoints.
   - Event Management: Models and endpoints.
   - Ticket Management: Models and endpoints.
   - Transaction Management: Models and endpoints.
   - QR Code Generation and Scanning: Models and endpoints.
   - Admin Dashboard: Endpoints.

3. **Frontend Development**
   - Home Page: EventList, EventCard.
   - Event Details Page: EventDetails, SubEventList, AddonItemList, TicketPurchaseForm.
   - User Registration Page: RegistrationForm.
   - User Login Page: LoginForm.
   - User Dashboard: UserProfile, UserTickets.
   - Admin Dashboard: AdminStats, ManageUsers, ManageEvents, ManageTickets.
   - QR Code Scanning Page: QRCodeScanner.

4. **Integration and Testing**
   - Integrate frontend and backend, write unit and integration tests, set up CI/CD pipeline.

This detailed roadmap provides a comprehensive guide to developing the Ticketless project in Rust with Rocket and Next.js with React, covering all key aspects of the project.