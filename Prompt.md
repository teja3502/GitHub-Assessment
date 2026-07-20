# Prompt Used for AI-Assisted Development

## Objective

This project was developed with the assistance of GitHub Copilot Chat using a structured prompt that guided AI to generate the application incrementally while following clean architecture, coding standards, and software engineering best practices.

The objective of the prompt was to ensure that the generated solution remained readable, maintainable, and aligned with the assignment requirements instead of generating the complete application in a single response.

---

# AI Prompt

You are an experienced Senior Full-Stack .NET and Angular developer.

Help me build a complete **Food Delivery Order Management System** using the following technology stack:

- ASP.NET Core 8 Web API
- Angular 18
- Entity Framework Core
- SQLite (preferred) or In-Memory Database
- Bootstrap for the UI

## Development Guidelines

- Build the application incrementally.
- Do not generate the entire solution in a single response.
- Follow Clean Architecture principles.
- Produce production-quality, clean, and maintainable code.
- Explain every generated file before providing code.
- Review generated code for correctness.
- Wait for confirmation before continuing to the next development step.

## Backend Requirements

Generate:

- Models
- DTOs
- DbContext
- Repository Layer
- Service Layer
- Controllers
- Dependency Injection
- Validation
- Exception Handling Middleware
- Swagger Configuration
- CORS Configuration
- Seed Data

### Order Entity

Include the following properties:

- Id
- CustomerName
- CustomerPhone
- FoodItem
- Quantity
- Price
- DeliveryAddress
- Status
- OrderDate

### Validation Rules

- CustomerName is required.
- CustomerPhone is required.
- FoodItem is required.
- DeliveryAddress is required.
- Quantity must be greater than zero.
- Price must be greater than zero.
- Status must allow only:

  - Placed
  - Preparing
  - OutForDelivery
  - Delivered
  - Cancelled

## REST API Endpoints

Generate the following endpoints:

- GET /api/orders
- GET /api/orders/{id}
- GET /api/orders/search
- POST /api/orders
- PUT /api/orders/{id}
- PATCH /api/orders/{id}/status
- DELETE /api/orders/{id}
- GET /api/orders/summary

## Dashboard Summary

Generate an endpoint that returns:

- Total Orders
- Placed Orders
- Preparing Orders
- OutForDelivery Orders
- Delivered Orders
- Cancelled Orders
- Total Revenue

## Frontend Requirements

Generate an Angular application with:

- Order Model
- Order Service
- Dashboard Component
- Order List Component
- Order Form Component

Implement:

- Dashboard summary cards
- Order listing
- Create Order
- Update Order
- Delete Order
- Search by Customer Name
- Filter by Status
- Status update
- Form validation
- API error handling
- Loading spinner
- Bootstrap styling

## Coding Standards

- Use async/await throughout the application.
- Apply dependency injection.
- Use meaningful naming conventions.
- Keep the code modular and maintainable.
- Avoid unnecessary complexity.
- Do not implement authentication, JWT, Docker, Kubernetes, Azure services, microservices, or cloud deployment.

## Documentation

Generate and maintain:

- .github/copilot-instructions.md
- docs/requirements.md
- docs/prompt.md
- docs/developer-notes.md
- README.md

The README should include:

- Project Overview
- Architecture
- Technology Stack
- Features
- API Endpoints
- Backend Setup
- Frontend Setup
- Folder Structure
- Screenshots Placeholder
- Future Enhancements

## Development Workflow

For every development step:

1. Explain the objective.
2. Generate the required code.
3. Explain the implementation.
4. Suggest testing steps.
5. Wait for confirmation before proceeding.

---

# Outcome

Using this prompt, GitHub Copilot generated the application incrementally while maintaining consistency with the assignment requirements and modern development practices.

The generated code was reviewed, refined, and validated before being incorporated into the final solution.

The AI assistance primarily accelerated boilerplate generation, project structure creation, and implementation guidance, while final integration, verification, debugging, and testing were performed manually to ensure correctness and completeness.
