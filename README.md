# Customer Management API - Study Project

A full-stack web application built with Node.js, Fastify, Prisma, and React for learning API development and customer management.

## 📋 Project Overview

This project demonstrates the implementation of a RESTful API for customer management with a modern tech stack. It includes CRUD operations for customers with a clean architecture separating controllers, services, and database operations.

## 🚀 Tech Stack

### Backend

- **Node.js** - Runtime environment
- **Fastify** - Fast and low overhead web framework
- **TypeScript** - Type-safe JavaScript
- **Prisma** - Modern database toolkit and ORM
- **MongoDB** - NoSQL database
- **@fastify/cors** - CORS support

### Frontend

- **React 19** - UI library
- **TypeScript** - Type-safe JavaScript
- **Vite** - Fast build tool and dev server
- **ESLint** - Code linting

## 📁 Project Structure

```
projeto-api/
├── backend/
│   ├── src/
│   │   ├── controllers/     # Request handlers
│   │   ├── services/        # Business logic
│   │   ├── prisma/          # Database client
│   │   ├── routes.ts        # API routes
│   │   └── server.ts        # Server configuration
│   ├── prisma/
│   │   └── schema.prisma    # Database schema
│   └── package.json
└── frontend/
    ├── src/
    │   ├── components/      # React components
    │   ├── App.tsx          # Main app component
    │   └── main.tsx         # Entry point
    └── package.json
```

## 🛠️ Installation & Setup

### Prerequisites

- Node.js (v16 or higher)
- npm or yarn
- MongoDB Atlas account (or local MongoDB)

### Backend Setup

1. Navigate to the backend directory:

```bash
cd backend
```

2. Install dependencies:

```bash
npm install
```

3. Set up environment variables:

```bash
cp .env.example .env
```

Update the `.env` file with your MongoDB connection string:

```env
DATABASE_URL="your_mongodb_connection_string"
```

4. Generate Prisma client:

```bash
npx prisma generate
```

5. Start the development server:

```bash
npm run dev
```

The API will be running on `http://localhost:3333`

### Frontend Setup

1. Navigate to the frontend directory:

```bash
cd frontend
```

2. Install dependencies:

```bash
npm install
```

3. Start the development server:

```bash
npm run dev
```

The frontend will be running on `http://localhost:5173`

## 📚 API Endpoints

### Base URL: `http://localhost:3333`

| Method | Endpoint            | Description           | Body                              |
| ------ | ------------------- | --------------------- | --------------------------------- |
| GET    | `/test`             | Health check          | -                                 |
| POST   | `/customer`         | Create a new customer | `{ name: string, email: string }` |
| GET    | `/customers`        | Get all customers     | -                                 |
| DELETE | `/customer?id={id}` | Delete a customer     | -                                 |

### API Examples

**Create Customer:**

```bash
curl -X POST http://localhost:3333/customer \
  -H "Content-Type: application/json" \
  -d '{"name": "John Doe", "email": "john@example.com"}'
```

**Get All Customers:**

```bash
curl http://localhost:3333/customers
```

**Delete Customer:**

```bash
curl -X DELETE "http://localhost:3333/customer?id=customer_id_here"
```

## 🗄️ Database Schema

The application uses a simple Customer model:

```prisma
model Customer {
  id         String    @id @default(auto()) @map("_id") @db.ObjectId
  name       String
  email      String
  status     Boolean
  created_at DateTime? @default(now())
  updated_at DateTime? @default(now())

  @@map("customers")
}
```

## 🏗️ Architecture

### Backend Architecture

- **Controllers**: Handle HTTP requests and responses
- **Services**: Contain business logic and data validation
- **Prisma Client**: Database operations and type-safe queries

### Key Files

- [`server.ts`](backend/src/server.ts) - Fastify server setup with CORS and error handling
- [`routes.ts`](backend/src/routes.ts) - API route definitions
- [`CreateCustomerService`](backend/src/services/CreateCustomerService.ts) - Customer creation logic
- [`ListCustomersService`](backend/src/services/ListCustomersService.ts) - Customer listing logic
- [`DeleteCustomerService`](backend/src/services/DeleteCustomerService.ts) - Customer deletion logic

## 🔧 Development Scripts

### Backend

```bash
npm run dev          # Start development server with hot reload
```

### Frontend

```bash
npm run dev          # Start development server
npm run build        # Build for production
npm run preview      # Preview production build
npm run lint         # Run ESLint
```

## 📝 Learning Objectives

This project demonstrates:

- RESTful API design principles
- Clean architecture with separation of concerns
- TypeScript usage in Node.js applications
- Database operations with Prisma ORM
- Error handling and validation
- CORS configuration
- Modern React development with Vite

## 🤝 Contributing

This is a study project, but feel free to:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

## 📄 License

This project is for educational purposes.
