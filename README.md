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
- **Backend & Database**: Supabase (PostgreSQL with built-in APIs)
- **Authentication**: Supabase Auth with role-based access control
- **Styling**: Tailwind CSS for responsive, modern UI design
- **Language**: TypeScript throughout for type safety and developer experience
- **Validation**: Zod for form and API validation

### Why This Stack?

This technology combination was chosen for its balance of developer experience, rapid development, and production readiness:

- **Next.js** provides excellent SEO for public pages (crucial for parent discovery), fast page loads, and a streamlined development experience with the App Router
- **Supabase** offers a complete backend solution with PostgreSQL database, authentication, real-time subscriptions, and file storage - eliminating the need to configure and manage separate services
- **Supabase Auth** handles secure authentication with minimal configuration, supporting multiple auth methods and row-level security policies
- **Row Level Security (RLS)** ensures data is automatically secured at the database level, with policies enforcing who can access what data
- **TypeScript** ensures code quality and catches potential issues before they reach production, with automatic type generation from Supabase schemas

## Data Model

The application is built around four core entities:

**Players**: Store comprehensive information about enrolled children including personal details, parent contacts, emergency information, and medical notes. Protected by RLS policies to ensure privacy.

**Camps**: Represent individual basketball camps with configurable dates, capacity limits, age restrictions, pricing, and status tracking (draft, published, full, completed). Public read access for published camps, admin-only write access.

**Programs**: Define structured basketball training curricula with details about duration, skill levels, and target age groups. Publicly viewable with administrative control over creation and updates.

**Registrations**: Link players to camps with payment tracking and enrollment status. Ensures data integrity with unique constraints and proper foreign key relationships.

**Users**: Admin and coach accounts managed through Supabase Auth with custom role attributes for system access control.

## Security Architecture

The platform leverages Supabase's Row Level Security (RLS) for comprehensive data protection:

- **Public Data**: Published camps and programs are readable by anyone
- **Parent Data**: Parents can create registrations but cannot view other families' information
- **Player Information**: Strictly protected with policies ensuring only authorized admins can access sensitive data
- **Admin Access**: Full CRUD operations on all tables for authenticated admin users
- **Automatic Enforcement**: Security policies are enforced at the database level, not just the application layer

## Real-time Capabilities

Supabase's real-time engine enables live updates across the platform:

- Dashboard displays update automatically as new registrations come in
- Camp capacity counters reflect changes instantly
- Multiple admins can work simultaneously without conflicts
- Parents see immediate confirmation when registration is successful

## Project Structure

The codebase follows Next.js 14+ App Router conventions with clear separation of concerns:

```
basketball-coaching-platform/
├── app/
│   ├── (public)/           # Public-facing pages
│   │   ├── page.tsx        # Home/landing page
│   │   ├── register/       # Registration flow
│   │   └── programs/       # Program listings
│   ├── (dashboard)/        # Protected admin routes
│   │   └── dashboard/      # Camp management
│   ├── api/                # API routes for server actions
│   └── auth/               # Auth callbacks and flows
├── components/
│   ├── ui/                 # Reusable UI components
│   ├── forms/              # Form components with validation
│   └── layout/             # Layout and navigation
├── lib/
│   ├── supabase/
│   │   ├── client.ts       # Client-side Supabase client
│   │   ├── server.ts       # Server-side Supabase client
│   │   └── middleware.ts   # Auth middleware
│   └── utils.ts            # Utility functions
├── types/
│   └── database.types.ts   # Auto-generated from Supabase
└── supabase/
    ├── migrations/         # Database migrations
    └── seed.sql           # Seed data
```

## Supabase Integration

The application uses Supabase's client libraries with environment-specific configurations:

- **Client-side**: For public data access and user interactions
- **Server-side**: For protected operations and admin functions
- **Middleware**: For route protection and session management
- **Type Generation**: Automatic TypeScript types from database schema

## Deployment Architecture

The application is designed for modern serverless deployment:

- **Frontend/Backend**: Deployed to Vercel with automatic CI/CD from GitHub
- **Database & Auth**: Fully managed by Supabase with automatic backups
- **Edge Functions**: Optional Supabase Edge Functions for complex server-side logic
- **Environment Configuration**: Managed through platform-specific environment variable systems
- **SSL/Security**: Automatic HTTPS and security headers

## Database Schema

The database follows a relational model with the following structure:

**players** table stores participant information with fields for personal details, parent contact, emergency information, and optional medical notes.

**camps** table manages camp instances with scheduling, capacity, age restrictions, pricing, and status workflow.

**programs** table defines training curricula with duration, skill level categorization, and age group targeting.

**registrations** table creates the many-to-many relationship between players and camps, tracking payment status and registration timestamps.

**profiles** table (linked to Supabase Auth) extends user accounts with role information and metadata for admin users.

All tables include created_at and updated_at timestamps for audit trails, with proper foreign key constraints and indexes for query performance.

## Future Enhancements

Potential features on the roadmap include:

- Payment processing integration (Stripe) for seamless transactions
- Automated email notifications via Supabase Edge Functions for registration confirmations and camp reminders
- Attendance tracking with check-in/check-out functionality using real-time updates
- Digital waiver signing and document management using Supabase Storage
- Parent portal for viewing child progress and upcoming schedules
- Coach evaluation and feedback system with structured data collection
- Analytics dashboard for business insights using Supabase's built-in analytics
- Mobile application leveraging Supabase's mobile SDKs
- Waitlist management with automatic notification when spots open
- Multi-location support for coaching businesses with multiple facilities

## Development Status

This is an active project in development. The core architecture and data model are established, with ongoing work on feature implementation and user experience refinement.

## Technical Requirements

- Node.js 18.x or higher
- Supabase account (free tier available)
- Modern web browser with JavaScript enabled
- Git for version control

## Contributing

Contributions are welcome! Whether you're interested in adding features, improving documentation, or fixing bugs, please feel free to open issues or submit pull requests.

## License

[Choose appropriate license]

## Contact

For questions, suggestions, or collaboration opportunities, please open an issue or reach out via [your contact method].

---

Built with ❤️ for basketball coaching communities
