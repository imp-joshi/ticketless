Based on the features and functionalities described for the Ticketless project, here is a detailed schema for the database, including all the tables and their fields:

### Database: PostgreSQL

#### 1. Users Table
Stores information about users.

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(255) NOT NULL UNIQUE,
    email VARCHAR(255) NOT NULL UNIQUE,
    password_hash VARCHAR(255) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### 2. Events Table
Stores information about events.

```sql
CREATE TABLE events (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    date TIMESTAMP NOT NULL,
    location VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### 3. SubEvents Table
Stores information about sub-events within an event.

```sql
CREATE TABLE sub_events (
    id SERIAL PRIMARY KEY,
    event_id INTEGER REFERENCES events(id) ON DELETE CASCADE,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    fee DECIMAL(10, 2) NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### 4. AddonItems Table
Stores information about addon items for an event.

```sql
CREATE TABLE addon_items (
    id SERIAL PRIMARY KEY,
    event_id INTEGER REFERENCES events(id) ON DELETE CASCADE,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    price DECIMAL(10, 2) NOT NULL,
    stock INTEGER NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### 5. Tickets Table
Stores information about tickets for events.

```sql
CREATE TABLE tickets (
    id SERIAL PRIMARY KEY,
    event_id INTEGER REFERENCES events(id) ON DELETE CASCADE,
    user_id INTEGER REFERENCES users(id) ON DELETE CASCADE,
    qr_code TEXT NOT NULL,
    status VARCHAR(50) NOT NULL DEFAULT 'pending',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### 6. Transactions Table
Stores information about transactions for ticket purchases.

```sql
CREATE TABLE transactions (
    id SERIAL PRIMARY KEY,
    ticket_id INTEGER REFERENCES tickets(id) ON DELETE CASCADE,
    user_id INTEGER REFERENCES users(id) ON DELETE CASCADE,
    amount DECIMAL(10, 2) NOT NULL,
    status VARCHAR(50) NOT NULL DEFAULT 'pending',
    payment_gateway VARCHAR(50),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### 7. EventSubEvents Table
Stores the relationship between events and sub-events.

```sql
CREATE TABLE event_sub_events (
    event_id INTEGER REFERENCES events(id) ON DELETE CASCADE,
    sub_event_id INTEGER REFERENCES sub_events(id) ON DELETE CASCADE,
    PRIMARY KEY (event_id, sub_event_id)
);
```

#### 8. EventAddonItems Table
Stores the relationship between events and addon items.

```sql
CREATE TABLE event_addon_items (
    event_id INTEGER REFERENCES events(id) ON DELETE CASCADE,
    addon_item_id INTEGER REFERENCES addon_items(id) ON DELETE CASCADE,
    PRIMARY KEY (event_id, addon_item_id)
);
```

### Summary of Tables and Schema

#### Users Table
- `id`: Primary key
- `username`: Unique username
- `email`: Unique email
- `password_hash`: Hashed password
- `created_at`: Timestamp of creation
- `updated_at`: Timestamp of last update

#### Events Table
- `id`: Primary key
- `name`: Event name
- `description`: Event description
- `date`: Event date and time
- `location`: Event location
- `created_at`: Timestamp of creation
- `updated_at`: Timestamp of last update

#### SubEvents Table
- `id`: Primary key
- `event_id`: Foreign key referencing `events(id)`
- `name`: Sub-event name
- `description`: Sub-event description
- `fee`: Sub-event fee
- `created_at`: Timestamp of creation
- `updated_at`: Timestamp of last update

#### AddonItems Table
- `id`: Primary key
- `event_id`: Foreign key referencing `events(id)`
- `name`: Addon item name
- `description`: Addon item description
- `price`: Addon item price
- `stock`: Addon item stock
- `created_at`: Timestamp of creation
- `updated_at`: Timestamp of last update

#### Tickets Table
- `id`: Primary key
- `event_id`: Foreign key referencing `events(id)`
- `user_id`: Foreign key referencing `users(id)`
- `qr_code`: QR code for the ticket
- `status`: Ticket status (e.g., pending, confirmed, checked-in)
- `created_at`: Timestamp of creation
- `updated_at`: Timestamp of last update

#### Transactions Table
- `id`: Primary key
- `ticket_id`: Foreign key referencing `tickets(id)`
- `user_id`: Foreign key referencing `users(id)`
- `amount`: Transaction amount
- `status`: Transaction status (e.g., pending, completed, failed)
- `payment_gateway`: Payment gateway used (e.g., Razorpay)
- `created_at`: Timestamp of creation
- `updated_at`: Timestamp of last update

#### EventSubEvents Table
- `event_id`: Foreign key referencing `events(id)`
- `sub_event_id`: Foreign key referencing `sub_events(id)`
- `PRIMARY KEY (event_id, sub_event_id)`

#### EventAddonItems Table
- `event_id`: Foreign key referencing `events(id)`
- `addon_item_id`: Foreign key referencing `addon_items(id)`
- `PRIMARY KEY (event_id, addon_item_id)`

This schema provides a comprehensive structure for the Ticketless project's database, covering all the necessary tables and their relationships.