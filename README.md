# Airbnb Clone Project

This project is a simplified Airbnb booking platform designed to help developers practice full-stack backend development using Django, MySQL, and GraphQL.

## Project Goals
- Understand collaborative GitHub workflows
- Master backend design and architecture
- Practice secure API development
- Gain CI/CD deployment experience

## Technology Stack
- Django: Web framework
- MySQL: Relational database
- GraphQL: Query language for APIs
- Docker: Containerization
- GitHub Actions: CI/CD automation

---

## 👥 Task 1: Team Roles

In this project, various roles mirror real-world backend development teams. Below is a description of each key role and their responsibilities:

### 🔧 Backend Developer

Responsible for developing the core application logic, APIs, and business rules. Uses Django to create models, views, and serializers, ensuring smooth data flow between the database and the frontend.

### 🧱 Database Administrator (DBA)

Designs and maintains the database structure. Focuses on creating optimized schemas, managing migrations, enforcing data integrity, and ensuring secure, performant data storage using MySQL.

### 🔐 DevOps Engineer

Handles the automation of deployment processes. Sets up CI/CD pipelines using GitHub Actions and Docker, manages environment variables, monitors uptime, and ensures the app can be scaled and maintained efficiently.

### 🎨 UI/UX Consultant (Optional in solo projects)

Offers guidance on designing intuitive and user-friendly interfaces. While not always a separate role in backend-focused projects, their input ensures API endpoints serve frontend needs effectively.

### 📋 Technical Writer / Project Planner

Documents the project structure, architecture, and API usage. Ensures clarity in README files, architecture decisions, and contributor guidelines for future team members or collaborators.

---

## 🛠️ Technology Stack

This project leverages a modern backend stack designed for scalability, maintainability, and secure data handling. Below is a breakdown of the key technologies used and their roles in the system:

### 🐍 Django

A high-level Python web framework that enables rapid development of secure and maintainable web applications. Used to build RESTful APIs, manage authentication, and define business logic.

### 🐬 MySQL

A reliable, relational database system used to store and manage structured data such as users, bookings, properties, reviews, and payments.

### 🔄 GraphQL

A powerful query language for APIs that allows clients to request exactly the data they need. Enables flexible data fetching, especially helpful when integrating with frontend interfaces.

### 🐳 Docker

Used for containerizing the application, ensuring consistent environments across development, testing, and production. Simplifies dependency management and deployment.

### ⚙️ GitHub Actions

Automates testing, building, and deployment workflows. Integrated into the CI/CD pipeline to ensure code quality and delivery efficiency.

### 🔒 JWT (JSON Web Tokens)

Secures API endpoints by implementing stateless authentication. Ensures users’ sessions are validated using encoded tokens rather than storing sessions server-side.

---

## 🗄️ Database Design

The application relies on a well-structured relational database to manage users, listings, transactions, and reviews. Below are the core entities and their relationships:

---

### 👤 **Users**

Represents individuals using the platform, either as guests or hosts.

**Key Fields:**

* `id`: Primary key
* `username`: Unique user handle
* `email`: Contact email
* `password_hash`: Encrypted password
* `is_host`: Boolean indicating if the user can post listings

---

### 🏠 **Properties**

Details about homes/apartments available for booking.

**Key Fields:**

* `id`: Primary key
* `owner_id`: Foreign key to `Users`
* `title`: Name of the listing
* `description`: Text description
* `price_per_night`: Numeric value

**Relationships:**

* Each property belongs to one user (host)
* A user can have multiple properties

---

### 📅 **Bookings**

Represents a guest’s reservation of a property.

**Key Fields:**

* `id`: Primary key
* `property_id`: Foreign key to `Properties`
* `user_id`: Foreign key to `Users`
* `check_in_date`: Start date
* `check_out_date`: End date

**Relationships:**

* Each booking is linked to one property and one user

---

### ⭐ **Reviews**

Feedback from guests after a stay.

**Key Fields:**

* `id`: Primary key
* `property_id`: Foreign key to `Properties`
* `user_id`: Foreign key to `Users`
* `rating`: Integer score (1–5)
* `comment`: Text field

**Relationships:**

* One user can write multiple reviews
* One property can have multiple reviews

---

### 💳 **Payments**

Handles payment tracking for bookings.

**Key Fields:**

* `id`: Primary key
* `booking_id`: Foreign key to `Bookings`
* `amount`: Paid amount
* `status`: e.g., “pending”, “completed”, “failed”
* `transaction_date`: Timestamp of payment

**Relationships:**

* One booking can have one payment

---

## ✨Task 4: Feature Breakdown

The Airbnb Clone project includes several core features essential to a functional and scalable property booking platform. Each feature is designed with both user experience and backend logic in mind.

---

### 👤 User Authentication and Authorization

Users can sign up, log in, and access the platform securely. Authenticated users can view or manage content depending on their role (host or guest). Uses JWT for secure, stateless session handling.

---

### 🏠 Property Listing Management

Hosts can create, update, and delete property listings. This includes adding descriptions, images, and pricing information. Each listing is tied to a host’s account.

---

### 📅 Booking System

Guests can book available properties by selecting check-in and check-out dates. The backend validates availability and creates a booking record linked to the guest and the property.

---

### ⭐ Review System

After completing a stay, guests can leave a review and rating for the property. These reviews are displayed on the property page, offering social proof and feedback for future guests.

---

### 💳 Payment Integration

Secure payment functionality processes bookings. Each payment is associated with a booking and includes validation, transaction logging, and status updates.

---

### 🔒 Secure API Layer

All backend endpoints are secured via authentication middleware, permission checks, and data validation to ensure that users can only access or modify resources they own or are allowed to view.

---

### 📈 Admin and Analytics Support *(optional advanced feature)*

Backend support for admin-level access to track system-wide metrics, moderate listings or users, and generate usage reports for internal insights.

---

## 🛡️ Task 5: API Security

Ensuring robust API security is a cornerstone of this project. Users trust the platform with sensitive data such as login credentials, payment information, and personal bookings — so strong security measures are essential.

---

### ✅ Authentication

The application uses **JWT (JSON Web Tokens)** to authenticate users securely. Tokens are issued at login and attached to subsequent requests, ensuring the user’s identity is verified without storing session state on the server.

---

### ✅ Authorization

Role-based access control (RBAC) ensures that only users with the appropriate privileges can access or modify specific data. For example, only a property owner can edit or delete their listings, and only the guest who made a booking can cancel it.

---

### ✅ Data Validation & Input Sanitization

Every input sent to the API (e.g., registration details, property info) is rigorously validated to prevent injection attacks, malformed requests, or data corruption.

---

### ✅ Rate Limiting

Basic throttling mechanisms are implemented to prevent abuse such as brute-force login attempts or rapid API spamming, enhancing platform stability and protecting user accounts.

---

### ✅ Secure Payment Handling

Sensitive payment data is handled via third-party services (like Stripe or PayPal), ensuring compliance with industry standards such as **PCI-DSS**. This prevents storage of credit card info on the server itself.

---

### ✅ HTTPS & Token Expiry

All traffic is expected to run over HTTPS to encrypt communication. Tokens have expiration timestamps to limit the impact of token theft.

---

## 🔄 CI/CD Pipeline

Continuous Integration and Continuous Deployment (CI/CD) are essential for modern backend projects. They help automate the development process, ensuring reliable testing, building, and deployment without manual errors.

---

### 🧪 Continuous Integration (CI)

CI ensures that any new code pushed to the repository is automatically tested and validated. This minimizes bugs and conflicts early in the development process.

**Tools Used:**

* **GitHub Actions**: Automatically runs tests, checks formatting, and ensures that changes do not break existing code.

**Typical Workflow:**

* Developer pushes code → GitHub Actions runs checks (e.g., linting, tests) → Code is approved or rejected

---

### 🚀 Continuous Deployment (CD)

CD automates the deployment of code once it's passed CI checks. This allows for fast iteration and consistent delivery to staging or production environments.

**Tools & Setup:**

* **Docker**: Packages the application and dependencies in a container, ensuring consistency across environments.
* **GitHub Actions**: Can be configured to deploy to cloud services (e.g., Heroku, AWS, Render) upon successful CI.

---

### 💡 Benefits of CI/CD:

* Faster development cycles
* Early detection of bugs
* Safer deployments
* Consistent environments from development to production

---

