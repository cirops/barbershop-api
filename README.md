# BarberShop - Barber Appointment Scheduling

## Running the project:
- Run `yarn` in the root folder;
- Make a copy of your `.env.example` file;
- Set up a PostgreSQL connection using the details specified in `ormconfig.json` (you can use a local PostgreSQL installation or Docker);
- Ensure you have a database created in PostgreSQL with the same name as specified in `ormconfig.json`;
- Set up a Redis connection with the port matching the one in your `.env` file.

## Password Recovery

**Requirements**

- Users should be able to recover their password by providing their email;
- Users should receive an email with password recovery instructions;
- Users should be able to reset their password.

**Non-Functional Requirements**

- Use Mailtrap for testing email sends in the development environment;
- Use Amazon SES for email sends in production;
- Email sends should be handled in the background (background job).

**Rules**

- The reset password link sent by email should expire in 2 hours;
- Users need to confirm their new password when resetting it.

# Profile Update

**Requirements**

- Users should be able to update their name, email, and password.

**Non-Functional Requirements**

**Rules**

- Users cannot change their email to one that’s already in use;
- To update their password, users must provide their old password;
- Users must confirm their new password when updating it.

# Provider Dashboard

**Requirements**

- Users should be able to list their appointments for a specific day;
- Providers should receive a notification whenever a new appointment is made;
- Providers should be able to view unread notifications.

**Non-Functional Requirements**

- Provider's daily appointments should be stored in cache;
- Provider's notifications should be stored in MongoDB;
- Provider's notifications should be sent in real-time using Socket.io.

**Rules**

- Notifications should have a read/unread status so that the provider can manage them.

# Service Appointments

**Requirements**

- Users should be able to list all registered service providers;
- Users should be able to view the days of a month with at least one available time slot for a provider;
- Users should be able to view available time slots on a specific day for a provider;
- Users should be able to schedule a new appointment with a provider.

**Non-Functional Requirements**

- The provider listing should be stored in cache.

**Rules**

- Each appointment should last exactly 1 hour;
- Appointments should be available between 8 AM and 6 PM (first at 8 AM, last at 5 PM);
- Users cannot schedule an appointment at an already booked time;
- Users cannot schedule an appointment in the past;
- Users cannot book services with themselves.
