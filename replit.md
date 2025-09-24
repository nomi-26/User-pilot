# Overview

GateGuardian is an advanced IoT face recognition door lock management system that provides comprehensive security monitoring and user management capabilities. The application is built as a full-stack web application with real-time features, allowing administrators to manage users, monitor access logs, control door locks, and receive security alerts through an intuitive dashboard interface.

The system integrates face recognition technology with traditional door control mechanisms, providing both automated access through biometric identification and manual override capabilities. It features role-based access control, real-time notifications, and detailed analytics for security monitoring.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture
The client-side application is built using React with TypeScript, featuring a modern component-based architecture. The UI is constructed using shadcn/ui components built on top of Radix UI primitives, providing accessible and customizable interface elements. The application uses Wouter for client-side routing and TanStack Query for efficient server state management and caching.

The frontend implements real-time communication through WebSocket connections, enabling live updates for door status changes, access logs, and security alerts. The application supports both light and dark themes with a custom theme provider, and includes responsive design patterns for mobile and desktop devices.

## Backend Architecture
The server is built on Express.js with TypeScript, following a modular route-based architecture. The application implements session-based authentication using Passport.js with OpenID Connect integration for Replit Auth. Session data is persisted using PostgreSQL with connect-pg-simple for session storage.

The backend exposes RESTful API endpoints for user management, access control, door operations, and analytics. It implements WebSocket support for real-time features, allowing the server to push live updates to connected clients for access events and system status changes.

## Database Design
The application uses PostgreSQL as the primary database with Drizzle ORM for type-safe database operations. The schema includes tables for users, face profiles, access logs, door status, notifications, and session management. The database design supports role-based access control with user roles (admin, resident) and face recognition status tracking (active, pending, inactive).

Key relationships include user-to-face-profiles (one-to-many), user-to-access-logs (one-to-many), and comprehensive audit trails for all system activities. The schema uses UUID primary keys and includes proper indexing for performance optimization.

## Authentication & Authorization
The system implements Replit Auth with OpenID Connect for secure user authentication. Session management is handled through PostgreSQL-backed sessions with configurable TTL settings. The application includes middleware for authentication verification and role-based access control throughout the API endpoints.

User profiles include role-based permissions (admin vs resident), with different access levels for system management functions. Face recognition status is tracked separately from user accounts, allowing for staged onboarding of biometric authentication.

## Real-time Features
WebSocket integration provides live updates for door access events, status changes, and security alerts. The client maintains persistent connections to receive real-time notifications, which are displayed through toast notifications and update relevant dashboard components automatically.

The system supports broadcasting events to multiple connected clients, ensuring all administrators receive immediate notifications of security events and system status changes.

# External Dependencies

## Cloud Database
- **Neon Database**: PostgreSQL database hosting with connection pooling through @neondatabase/serverless
- **Database URL**: Environment variable-based configuration for database connections

## UI Component Libraries
- **Radix UI**: Comprehensive set of accessible, unstyled UI primitives for building the component system
- **Tailwind CSS**: Utility-first CSS framework for responsive design and theming
- **Lucide React**: Icon library providing consistent iconography throughout the application

## Authentication Services
- **Replit Auth**: OpenID Connect authentication provider for user management and session handling
- **Passport.js**: Authentication middleware with OpenID Connect strategy implementation

## Development Tools
- **Vite**: Build tool and development server with hot module replacement
- **TypeScript**: Type safety across the entire application stack
- **Drizzle Kit**: Database migration and schema management tools