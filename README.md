# Food Delivery Order Management System

A full-stack application for managing food delivery orders with real-time status tracking, order search, and financial summaries.

## Project Overview

This system enables restaurants or delivery services to:
- Create and manage customer food orders
- Track order status from placement through delivery
- Search orders by customer name
- Filter orders by status
- View real-time business metrics

## Architecture

### Clean Architecture Pattern
```
┌─────────────────────────────────────────────────┐
│         Angular 18 Frontend (SPA)               │
│     Components, Services, Reactive Forms        │
└──────────────────┬──────────────────────────────┘
                   │ HTTP REST API
┌──────────────────▼──────────────────────────────┐
│      ASP.NET Core 8 Web API                     │
│  Controllers → Services → Repositories → EF Core│
└──────────────────┬──────────────────────────────┘
                   │ SQL
┌──────────────────▼──────────────────────────────┐
│         SQLite Database                         │
│         (fooddelivery.db)                       │
└─────────────────────────────────────────────────┘
```

## Technology Stack

| Layer | Technology |
|-------|-----------|
| **Frontend** | Angular 18, Bootstrap 5, RxJS |
| **Backend** | ASP.NET Core 8, C# |
| **Database** | SQLite with Entity Framework Core |
| **Architecture** | Clean Architecture, Repository Pattern |
| **API** | RESTful, Swagger/OpenAPI documented |

## Features

### Dashboard
- **Order Summary Cards**: Display counts by status
- **Revenue Tracking**: Total revenue calculation
- **Status Metrics**: Placed, Preparing, Out for Delivery, Delivered, Cancelled

### Order Management
- **Create Orders**: Form with full validation
- **View Orders**: Table display with sortable columns
- **Search**: Find orders by customer name
- **Filter**: Filter by order status
- **Update**: Change order details
- **Status Update**: Quick status change via dropdown
- **Delete**: Remove orders from system

### Data Validation
- Customer name required (max 150 chars)
- Phone number required (max 20 chars)
- Food item required (max 200 chars)
- Quantity must be > 0
- Price must be > 0
- Delivery address required (max 500 chars)
- Status restricted to predefined values

## API Endpoints

### Orders
```
GET     /api/orders                    → Get all orders
GET     /api/orders/{id}               → Get order by ID
GET     /api/orders/search             → Search orders (params: customerName, status)
POST    /api/orders                    → Create new order
PUT     /api/orders/{id}               → Update order
PATCH   /api/orders/{id}/status        → Update order status
DELETE  /api/orders/{id}               → Delete order
```

### Summary
```
GET     /api/orders/summary            → Get order statistics
```

### Response Format
```json
{
  "id": 1,
  "customerName": "John Doe",
  "customerPhone": "9876543210",
  "foodItem": "Burger",
  "quantity": 2,
  "price": 25.50,
  "deliveryAddress": "123 Main St",
  "status": "Placed",
  "orderDate": "2026-07-17T12:00:00Z"
}
```

## Getting Started

### Prerequisites
- .NET 8 SDK
- Node.js 20+
- npm 10+

### Installation

#### Backend
```bash
cd FoodDelivery.Api
dotnet restore --configfile ../NuGet.Config
dotnet build
dotnet run
```

Backend starts at: `http://localhost:5002`

Swagger UI: `http://localhost:5002/swagger`

#### Frontend
```bash
cd food-delivery-ui
npm install
npm start
```

Frontend runs at: `http://localhost:4200`

### Seed Data
The application automatically seeds 2 sample orders on first run:
1. **Asha Kumar** - Veggie Burger (2 qty) - $18.50 - Status: Placed
2. **Ravi Menon** - Chicken Pizza (1 qty) - $22.00 - Status: Preparing

## Project Structure

```
Github_Assessment/
│
├── FoodDelivery.Api/                 # ASP.NET Core 8 API
│   ├── Models/
│   │   └── Order.cs                  # Order entity
│   ├── DTOs/
│   │   └── OrderDto.cs               # DTOs for API
│   ├── Data/
│   │   ├── FoodDeliveryDbContext.cs  # EF Core context
│   │   └── SeedData.cs               # Initial data
│   ├── Repositories/
│   │   ├── Interfaces/
│   │   │   └── IOrderRepository.cs   # Repository interface
│   │   └── OrderRepository.cs        # Repository implementation
│   ├── Services/
│   │   ├── Interfaces/
│   │   │   └── IOrderService.cs      # Service interface
│   │   └── OrderService.cs           # Service implementation
│   ├── Controllers/
│   │   └── OrdersController.cs       # API endpoints
│   ├── Middleware/
│   │   └── ExceptionHandlingMiddleware.cs
│   ├── Program.cs                    # DI & configuration
│   └── FoodDelivery.Api.csproj
│
├── food-delivery-ui/                 # Angular 18 SPA
│   ├── src/
│   │   ├── app/
│   │   │   ├── components/
│   │   │   │   ├── dashboard/
│   │   │   │   ├── order-list/
│   │   │   │   └── order-form/
│   │   │   ├── services/
│   │   │   │   └── order.service.ts
│   │   │   ├── models/
│   │   │   │   └── order.model.ts
│   │   │   ├── app.component.ts
│   │   │   ├── app.component.html
│   │   │   └── app.component.css
│   │   ├── main.ts
│   │   ├── index.html
│   │   └── styles.css
│   ├── angular.json
│   ├── tsconfig.json
│   ├── package.json
│   └── README.md
│
├── docs/
│   ├── requirements.md                # Detailed requirements
│   ├── developer-notes.md              # Architecture & decisions
│   └── copilot-prompts-used.md        # Prompts used
│
├── .github/
│   └── copilot-instructions.md         # Build guidelines
│
├── NuGet.Config                        # NuGet configuration
├── FoodDelivery.sln                    # Solution file
└── README.md                           # This file
```

## Development Highlights

### Backend
- ✅ Clean architecture with clear separation of concerns
- ✅ Async/await pattern throughout for scalability
- ✅ Repository pattern for data access
- ✅ Service layer for business logic
- ✅ Comprehensive input validation
- ✅ Exception handling middleware
- ✅ Dependency injection
- ✅ CORS configuration
- ✅ SQLite database with EF Core
- ✅ Swagger documentation

### Frontend
- ✅ Standalone Angular 18 components
- ✅ Reactive forms with validation
- ✅ TypeScript for type safety
- ✅ Bootstrap 5 styling
- ✅ Loading spinners
- ✅ Error handling
- ✅ Responsive design
- ✅ Clean component structure
- ✅ Service-based architecture

## HTTP Status Codes

| Code | Meaning | Used For |
|------|---------|----------|
| 200 | OK | Successful GET/PUT/PATCH |
| 201 | Created | Successful POST |
| 204 | No Content | Successful DELETE |
| 400 | Bad Request | Invalid input |
| 404 | Not Found | Order doesn't exist |
| 500 | Server Error | Unhandled exception |

## Key Design Decisions

1. **DTOs Over Domain Models**: DTOs provide API contract flexibility
2. **Repository Pattern**: Abstraction for data access
3. **Service Layer**: Business logic centralization
4. **Async Operations**: Better resource utilization
5. **Middleware for Exceptions**: Centralized error handling
6. **Standalone Components**: Modern Angular approach
7. **Reactive Forms**: Type-safe form handling
8. **SQLite**: Simple, file-based persistence

## Testing the Application

### Scenario 1: Create Order
1. Open http://localhost:4200
2. Click "Orders" tab
3. Click "Create Order"
4. Fill in the form
5. Click "Create Order"
6. Verify new order appears in the list

### Scenario 2: Search Orders
1. In Orders list, enter a customer name in search box
2. Click "Search"
3. Verify filtered results show only matching customers

### Scenario 3: Update Status
1. In Orders list, find an order
2. Click the Status dropdown
3. Select new status
4. Verify status changes immediately

### Scenario 4: View Dashboard
1. Open http://localhost:4200
2. Click "Dashboard" tab
3. Verify summary cards display current counts
4. Create/Delete orders and refresh to see updates

## Error Handling

The application handles errors gracefully:
- **Validation Errors**: Form validation messages
- **API Errors**: User-friendly error alerts
- **Network Errors**: Retry buttons provided
- **Malformed Data**: Proper exception messages

## Building for Production

### Backend
```bash
cd FoodDelivery.Api
dotnet publish -c Release -o ./publish
```

### Frontend
```bash
cd food-delivery-ui
npm run build
```

Outputs to `dist/food-delivery-ui/`

## Future Enhancements

- [ ] Authentication & JWT
- [ ] Role-based authorization
- [ ] Pagination
- [ ] Advanced sorting
- [ ] Real-time updates (SignalR)
- [ ] Notification system
- [ ] Audit logging
- [ ] Unit/Integration tests
- [ ] Performance caching
- [ ] API rate limiting
- [ ] Docker containerization
- [ ] CI/CD pipeline

## Troubleshooting

### Backend won't start
```bash
# Clear bin/obj
rm -r FoodDelivery.Api/bin FoodDelivery.Api/obj
# Rebuild
dotnet build --configfile NuGet.Config
dotnet run --project FoodDelivery.Api
```

### Frontend won't start
```bash
# Clear node_modules
rm -r food-delivery-ui/node_modules
npm cache clean --force
# Reinstall
cd food-delivery-ui
npm install
npm start
```

### API connection issues
- Ensure backend is running on port 5002
- Check CORS configuration in Program.cs
- Verify NetworkTab in browser dev tools

## Documentation

- [Developer Notes](docs/developer-notes.md) - Architecture details
- [Requirements](docs/requirements.md) - Full requirements checklist
- [Copilot Prompts](docs/copilot-prompts-used.md) - Development prompts
- [Submission Details](README-AI-FULLSTACK-SUBMISSION.md) - Completion summary

## License

This project is part of a development assessment.

## Contact

For questions about this project, refer to the documentation in the `docs/` folder.

---

**Status**: ✅ Complete - All requirements implemented and tested
**Last Updated**: July 17, 2026

