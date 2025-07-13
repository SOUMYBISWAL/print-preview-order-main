# Overview

This is a PrintLite web application - a document printing service platform built with a full-stack TypeScript architecture. The application allows users to upload documents, configure print settings, place orders, and track deliveries. It includes both customer-facing features and an admin panel for order management.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

The application follows a modern full-stack architecture with clear separation between client and server:

## Frontend Architecture
- **Framework**: React with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **UI Framework**: Tailwind CSS with shadcn/ui component library
- **State Management**: TanStack Query for server state, localStorage for cart/user data
- **Routing**: React Router for client-side navigation
- **Styling**: Tailwind CSS with CSS variables for theming

## Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **Database**: PostgreSQL with Drizzle ORM
- **Database Provider**: Neon serverless PostgreSQL
- **Session Storage**: In-memory storage (development) with interface for database storage

## Project Structure
```
├── client/          # React frontend application
├── server/          # Express.js backend API
├── shared/          # Shared TypeScript schemas and types
└── migrations/      # Database migration files
```

# Key Components

## Frontend Components
- **Pages**: Upload, PrintSettings, Checkout, OrderConfirmation, Cart, Admin, Login, Account
- **UI Components**: Comprehensive shadcn/ui component library
- **Layout Components**: Navbar with cart counter and user authentication, Footer
- **Business Logic**: File upload with page counting, print pricing calculator, order management

## Backend Components
- **Storage Interface**: Abstracted storage layer supporting both in-memory and database storage
- **Route Registration**: Modular route system for API endpoints
- **Database Connection**: Neon PostgreSQL with connection pooling
- **Development Setup**: Vite integration for hot module replacement

## Database Schema
- **Users Table**: Basic user authentication with username/password
- **Storage Models**: User management with interfaces for CRUD operations
- **Schema Validation**: Zod schemas for type-safe data validation

# Data Flow

## User Authentication Flow
1. Users register/login with mobile number and password
2. User data stored in localStorage (development) with database interface ready
3. Admin users identified by special credentials
4. Authentication state managed across components via custom events

## Order Processing Flow
1. File upload with automatic page counting for PDFs and images
2. Print settings configuration (paper type, color, sides, copies)
3. Dynamic pricing calculation based on settings
4. Cart management with localStorage persistence
5. Checkout with user details and payment method selection
6. Order confirmation with tracking ID generation

## Admin Management Flow
1. Admin dashboard for order oversight
2. Order status tracking and updates
3. Revenue and statistics monitoring
4. Customer order history management

# External Dependencies

## Core Dependencies
- **@neondatabase/serverless**: PostgreSQL database connectivity
- **drizzle-orm**: Type-safe database ORM
- **@tanstack/react-query**: Server state management
- **@radix-ui/***: Accessible UI primitives
- **react-router-dom**: Client-side routing
- **tailwindcss**: Utility-first CSS framework

## Development Dependencies
- **vite**: Build tool and development server
- **typescript**: Type checking and compilation
- **esbuild**: Fast JavaScript bundler for production
- **tsx**: TypeScript execution for development

## File Processing
- Built-in file upload with drag-and-drop support
- PDF page counting using basic pattern matching
- Image file support for printing
- File type validation and size limits

# Deployment Strategy

## Build Process
- **Frontend**: Vite builds optimized React application to `dist/public`
- **Backend**: esbuild bundles Express server to `dist/index.js`
- **Database**: Drizzle migrations for schema management

## Environment Configuration
- **Development**: tsx for TypeScript execution, Vite dev server
- **Production**: Node.js serves bundled application
- **Database**: Neon PostgreSQL with connection string configuration

## Replit Integration
- Runtime error modal for development debugging
- Cartographer plugin for enhanced development experience
- Development banner for external access

The architecture is designed for scalability with clear interfaces between components, making it easy to extend functionality, add new features, or migrate to different database providers. The storage abstraction layer allows for easy transition from development to production database systems.