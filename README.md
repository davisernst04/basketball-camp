# Basketball Coaching Platform

A modern, full-stack web application designed to streamline basketball camp management and player registrations for coaching businesses.

## About

This platform bridges the gap between basketball coaching businesses and families by providing an intuitive system for camp management, player registration, and program organization. Built with modern web technologies, it offers a seamless experience for both administrators managing multiple camps and parents enrolling their children.

## The Problem It Solves

Basketball coaching businesses often struggle with:
- Manual registration processes that are time-consuming and error-prone
- Difficulty tracking player information and camp capacity
- Limited visibility into program schedules and availability
- Fragmented systems for payments, communications, and administration

This platform consolidates these workflows into a single, cohesive application that scales with the business.

## Key Features

### For Parents & Players
- **Public Landing Page**: Discover available camps and programs with detailed information about schedules, pricing, and skill levels
- **Simple Registration**: Intuitive form-based registration process with validation to ensure all necessary information is captured
- **Program Discovery**: Browse basketball programs filtered by age group, skill level, and duration

### For Coaches & Administrators
- **Camp Dashboard**: Comprehensive view of all camps with real-time registration counts, capacity tracking, and participant management
- **Program Management**: Create and organize basketball training programs with flexible configurations for different skill levels and age groups
- **Player Database**: Centralized storage of player information including emergency contacts and medical information
- **Registration Oversight**: Track payment status, manage waitlists, and handle camp logistics efficiently

## Technical Architecture

### Stack

- **Frontend**: Next.js 14+ with App Router for server-side rendering and optimal performance
- **Database**: PostgreSQL for robust, relational data management
- **ORM**: Prisma for type-safe database access and intuitive query building
- **Authentication**: NextAuth.js (Auth.js v5) for secure admin authentication
- **Styling**: Tailwind CSS for responsive, modern UI design
- **Language**: TypeScript throughout for type safety and developer experience

### Why This Stack?

This technology combination was chosen for its balance of developer experience, type safety, and production readiness:

- **Next.js** provides excellent SEO for public pages (crucial for parent discovery), fast page loads, and a streamlined development experience
- **Prisma + PostgreSQL** offers end-to-end type safety with automatic TypeScript type generation from the database schema, making the codebase more maintainable and less prone to runtime errors
- **NextAuth.js** handles authentication securely with minimal configuration, supporting role-based access for different admin levels
- **TypeScript** ensures code quality and catches potential issues before they reach production

## Data Model

The application is built around four core entities:

**Players**: Store comprehensive information about enrolled children including personal details, parent contacts, emergency information, and medical notes.

**Camps**: Represent individual basketball camps with configurable dates, capacity limits, age restrictions, pricing, and status tracking (draft, published, full, completed).

**Programs**: Define structured basketball training curricula with details about duration, skill levels, and target age groups.

**Registrations**: Link players to camps with payment tracking and enrollment status, ensuring data integrity with unique constraints.

**Users**: Admin and coach accounts with role-based permissions for system access.

## Project Structure

The codebase follows Next.js 14+ App Router conventions with clear separation of concerns:

- Public-facing pages live in route groups for easy identification
- API routes handle server-side logic with proper authentication middleware
- Prisma schema defines the database structure in a single, version-controlled file
- Type definitions are automatically generated from the Prisma schema
- Reusable UI components promote consistency across the application

## Security Considerations

- Role-based access control ensures only authorized users can access administrative features
- Prisma's parameterized queries prevent SQL injection attacks
- NextAuth.js provides secure session management with encrypted tokens
- Environment variables keep sensitive configuration out of the codebase
- Database migrations are version-controlled for audit trails

## Deployment Architecture

The application is designed for modern serverless deployment:

- **Frontend/Backend**: Deployed to Vercel with automatic CI/CD from GitHub
- **Database**: Hosted on platforms like Neon, Railway, or Vercel Postgres for managed PostgreSQL
- **Migrations**: Applied automatically during deployment or via CI/CD pipeline
- **Environment Configuration**: Managed through platform-specific environment variable systems

## Future Enhancements

Potential features on the roadmap include:

- Payment processing integration (Stripe) for seamless transactions
- Automated email notifications for registration confirmations and camp reminders
- Attendance tracking with check-in/check-out functionality
- Digital waiver signing and document management
- Parent portal for viewing child progress and upcoming schedules
- Coach evaluation and feedback system
- Analytics dashboard for business insights
- Mobile application for on-the-go access

## Development Status

This is an active project in development. The core architecture and data model are established, with ongoing work on feature implementation and user experience refinement.

## Contributing

Contributions are welcome! Whether you're interested in adding features, improving documentation, or fixing bugs, please feel free to open issues or submit pull requests.

## Technical Requirements

- Node.js 18.x or higher
- PostgreSQL database (local or hosted)
- Modern web browser with JavaScript enabled

## License

[Choose appropriate license]

## Contact

For questions, suggestions, or collaboration opportunities, please open an issue or reach out via [your contact method].

---

Built with ❤️ for basketball coaching communities
