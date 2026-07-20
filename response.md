# AI Prompt Used for GitHub Copilot

## Objective

The following prompt was provided to GitHub Copilot Chat to guide the AI in building the **Food Delivery Order Management System**. The prompt was designed to ensure that the generated solution followed the assignment requirements, clean architecture principles, coding standards, and best practices while encouraging incremental development instead of generating the complete solution in a single response.

---

## Prompt

You are an experienced Senior Full-Stack .NET and Angular developer.

Help me build a complete **Food Delivery Order Management System** using the following technology stack:

* ASP.NET Core 8 Web API
* Angular 18
* Entity Framework Core
* SQLite (preferred) or In-Memory Database
* Bootstrap for the UI

### Development Guidelines

* Build the project incrementally and do not generate the entire application in a single response.
* Follow clean architecture principles while keeping the project simple and maintainable.
* Generate production-quality, readable, and well-structured code.
* Explain the purpose of every generated file before providing the code.
* Review generated code for correctness before presenting it.
* Wait for confirmation before proceeding to the next development step.

### Backend Requirements

Generate:

* Models
* DTOs
* DbContext
* Repository Layer
* Service Layer
* Controllers
* Dependency Injection
* Validation
* Exception Handling
* Swagger Configuration
* CORS Configuration
* Seed Data

### Order Entity

Include the following properties:

* Id
* CustomerName
* CustomerPhone
* FoodItem
* Quantity
* Price
* DeliveryAddress
* Status
* OrderDate

### Validation Rules

* CustomerName is required.
* CustomerPhone is required.
* FoodItem is required.
* DeliveryAddress is required.
* Quantity must be greater than zero.
* Price must be greater than zero.
* Status must only allow:

  * Placed
  * Preparing
  * OutForDelivery
  * Delivered
  * Cancelled

### API Endpoints

Generate the following REST APIs:

* GET /api/orders
* GET /api/orders/{id}
* GET /api/orders/search?customerName=&status=
* POST /api/orders
* PUT /api/orders/{id}
* PATCH /api/orders/{id}/status
* DELETE /api/orders/{id}
* GET /api/orders/summary

### Dashboard Summary

Generate an endpoint that returns:

* Total Orders
* Placed Orders
* Preparing Orders
* OutForDelivery Orders
* Delivered Orders
* Cancelled Orders
* Total Revenue

### Frontend Requirements

Generate an Angular application with:

* Order Model
* Order Service
* Dashboard Component
* Order List Component
* Order Form Component

Implement:

* Dashboard summary cards
* Order listing
* Create Order
* Update Order
* Delete Order
* Search by Customer Name
* Filter by Status
* Status update
* Form validation
* API error handling
* Loading spinner
* Bootstrap styling

### Coding Standards

* Use async/await throughout the application.
* Apply dependency injection where appropriate.
* Use meaningful naming conventions.
* Keep the code clean, modular, and easy to understand.
* Avoid unnecessary complexity.
* Do not implement authentication, JWT, Docker, Kubernetes, Azure services, microservices, or cloud deployment.

### Documentation

Generate and maintain the following files:

* .github/copilot-instructions.md
* docs/requirements.md
* docs/copilot-prompts-used.md
* docs/developer-notes.md
* README-AI-FULLSTACK-SUBMISSION.md

The README should include:

* Project Overview
* Architecture
* Technology Stack
* Features
* API Endpoints
* Backend Setup Instructions
* Frontend Setup Instructions
* Folder Structure
* Screenshots Placeholder
* Future Enhancements

### Working Approach

For every development step:

1. Explain the objective.
2. Generate the required code.
3. Explain the generated implementation.
4. Suggest testing steps.
5. Wait for confirmation before proceeding to the next step.

---

## Outcome

Using this prompt, GitHub Copilot was guided to generate the application incrementally while maintaining code quality, readability, and alignment with the assignment requirements. Each generated code block was reviewed, validated, and refined before being incorporated into the final solution.
