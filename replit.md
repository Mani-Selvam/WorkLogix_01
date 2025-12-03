# WorkLogix - Employee Work Tracking & Task Management System

## Overview
WorkLogix is a comprehensive full-stack employee work tracking and task management application built with React, Express, PostgreSQL, and TypeScript. It provides features for task management, time-based reporting, performance monitoring, and team collaboration.

## Project Architecture

### Technology Stack
- **Frontend**: React 18 + TypeScript + Vite
- **Backend**: Express.js + TypeScript
- **Database**: PostgreSQL (Drizzle ORM)
- **UI Components**: Radix UI + Tailwind CSS
- **Authentication**: Passport.js (Local & Google OAuth)
- **Real-time**: WebSocket (ws library)
- **Payments**: Stripe integration
- **Email**: Nodemailer + Resend

### Project Structure
```
├── client/               # Frontend React application
│   ├── src/             # React components and pages
│   └── index.html       # Entry HTML file
├── server/              # Backend Express application
│   ├── index.ts         # Main server entry point
│   ├── routes.ts        # API routes
│   ├── db.ts            # Database connection
│   ├── passport.ts      # Authentication configuration
│   ├── storage.ts       # Database operations
│   └── vite.ts          # Vite dev server setup
├── shared/              # Shared types and schemas
│   └── schema.ts        # Drizzle database schema
├── public/              # Static assets
└── dist/                # Production build output
```

## Recent Changes (December 3, 2024)

### Replit Environment Setup
1. **Database Configuration**: Connected to Replit's built-in PostgreSQL database
   - Database URL: `postgresql://postgres:password@helium:5432/heliumdb`
   - Ran migrations using `npm run db:push`
   - Created initial super admin user

2. **Vite Configuration**: Updated for Replit's proxy environment
   - Set host to `0.0.0.0`
   - Port set to `5000` (Replit's exposed port)
   - Enabled `allowedHosts: true` for iframe compatibility
   - Configured HMR with clientPort 5000

3. **Cache Control**: Added headers to prevent caching issues
   - `Cache-Control: no-store, no-cache, must-revalidate, proxy-revalidate`
   - Ensures updates are visible immediately in Replit's iframe

4. **Workflow Configuration**: Set up development server workflow
   - Command: `npm run dev`
   - Port: 5000 (webview)
   - Auto-starts on project load

5. **Deployment Configuration**: Configured for production
   - Build: `npm run build`
   - Run: `npm start`
   - Target: autoscale (for stateless web application)

## Environment Variables

### Required for Development
- `DATABASE_URL`: PostgreSQL connection string (auto-configured by Replit)
- `SESSION_SECRET`: Session encryption key (auto-configured by Replit)

### Optional Features
- `FIREBASE_SERVICE_ACCOUNT_KEY`: Firebase Admin SDK credentials (for Firebase auth)
- `GOOGLE_CLIENT_ID`: Google OAuth client ID
- `GOOGLE_CLIENT_SECRET`: Google OAuth client secret
- `STRIPE_SECRET_KEY`: Stripe payment processing
- `RESEND_API_KEY`: Email service API key

## Super Admin Credentials
- **Email**: superadmin@worklogix.com
- **Password**: worklogix@26
- **Role**: super_admin

## Key Features
1. **Multi-tenant Company Management**: Support for multiple companies with isolated data
2. **User Roles**: Super Admin, Company Admin, Team Leader, Company Member
3. **Task Management**: Assign, track, and manage tasks with priorities and deadlines
4. **Time Tracking**: Daily, weekly, and monthly reports
5. **Performance Ratings**: Feedback system for employee performance
6. **Real-time Updates**: WebSocket support for live notifications
7. **File Uploads**: Support for document attachments
8. **Automated Attendance**: Cron job for marking absent users
9. **Email Notifications**: Company verification and user notifications

## Database Schema
The application uses PostgreSQL with the following main tables:
- `companies`: Multi-tenant company data
- `users`: User accounts with role-based access
- `tasks`: Task assignments and tracking
- `reports`: Daily/weekly/monthly work reports
- `messages`: Internal messaging system
- `ratings`: Performance reviews
- `fileUploads`: Document management
- `archiveReports`: Historical data

## Development Commands
- `npm install`: Install dependencies
- `npm run dev`: Start development server (port 5000)
- `npm run build`: Build for production
- `npm start`: Run production server
- `npm run db:push`: Push database schema changes
- `npm run check`: TypeScript type checking

## Production Deployment
The application is configured for Replit's autoscale deployment:
1. Builds both frontend and backend using Vite and esbuild
2. Serves static files from `dist/public`
3. Runs Express server on port 5000
4. Automatically scales based on traffic

## Notes
- The frontend uses Replit's proxy in development, accessed via iframe
- All hosts are allowed in dev mode for proxy compatibility
- Cache control headers prevent stale content in iframe
- Session cookies are configured for secure production use
- Daily cron job runs at 11:59 PM IST for attendance marking
