MOYO Order Management System (OMS)
Overview

The MOYO Order Management System (OMS) is a modular, microservice-based backend system designed to manage orders, vendors, inventory, and pricing. The system supports real-time order intake, inventory allocation, and asynchronous event processing. It is built to integrate with frontend systems and supports event-driven architectures via the Outbox Pattern, with future Kafka integration.

The OMS is ideal for managing complex order workflows in retail, delivery, or similar business environments.

Features

Order Management: Create, track, and manage orders with line items.

Inventory & Pricing: Maintain inventory stock levels and product pricing.

Vendor Management: Add and manage vendor information.

Event-Driven Architecture: Outbox pattern implemented to handle asynchronous order events.

Modular Design: Easy to extend for additional services like Client Portals or Product Management.

Security: OAuth2-ready vendor login integration (planned with Keycloak).

RESTful API: Fully documented endpoints for CRUD operations on orders, inventory, and vendors.

Technologies & Tools 
Layer	Technology	Purpose
Backend	Java 21, Spring Boot 3	Core application logic
Database	PostgreSQL, Flyway	Persistent storage & schema migrations
Containerization	Docker, Adminer	Local development and DB management
API Testing	Thunder Client / Postman	Endpoint testing
Security	Spring Security, OAuth2/Keycloak	Vendor authentication
Event Streaming	Kafka (planned), Outbox Pattern	Asynchronous event handling
Frontend	React / HTML+JS (planned)	Admin and client-facing interfaces


Database Schema

vendor – Stores vendor details.

inventory – Tracks inventory stock levels.

price – Stores product prices.

orders – Stores order metadata (status, createdAt, externalOrderId).

order_line – Line items for each order, linked to orders.

outbox_event – Stores events for async processing with Kafka.

Relationships:

Order → OrderLine is One-to-Many (@OneToMany).

Inventory and Price are linked to Vendor for multi-vendor support.

Setup Instructions
Prerequisites

Java 21

Maven 3.9+

PostgreSQL 15+

Docker & Docker Compose (optional, for DB)

Node.js + npm (if connecting frontend later)

Steps

Clone the repository

git clone https://github.com/yourusername/moyo-oms.git
cd moyo-oms


Configure PostgreSQL

Update application.yml with your DB credentials.

Ensure the database exists (e.g., order_mgmt).

Run Flyway migrations

mvn flyway:migrate


Start the application

mvn spring-boot:run




Testing endpoints

Use Thunder Client or Postman.

Example endpoint:
POST /orders – create a new order.

Docker (optional)

docker compose up -d

API Endpoints
Method	Endpoint	Description
POST	/orders	Create a new order
GET	/orders/{id}	Retrieve order by ID
POST	/vendors	Add a new vendor
POST	/inventory	Add inventory item
GET	/inventory	List inventory items
POST	/prices	Add product price

More endpoints can be added as needed.
