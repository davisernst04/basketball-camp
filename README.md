# Basketball Coaching Platform

A modern web application for managing basketball coaching camps and programs, built with Next.js and Supabase.

## Overview

This platform provides a comprehensive solution for basketball coaching businesses to manage their camps, programs, and player registrations. Parents can easily register their children, while coaches and administrators can manage camps and view participant information through an intuitive dashboard.

## Features

### Public-Facing
- **Home Page**: Accessible landing page showcasing coaching services, upcoming camps, and programs
- **Parent Registration**: Streamlined registration process for parents to enroll their children in camps and programs
- **Program Pages**: Detailed information about available basketball programs and training sessions

### Administrative
- **Camp Dashboard**: Centralized view for managing camps, participants, and schedules
- **Program Management**: Create, edit, and organize basketball programs and training curricula

## Tech Stack

- **Frontend**: Next.js 14+ (App Router)
- **Backend**: Supabase
  - Authentication
  - PostgreSQL Database
  - Real-time subscriptions
  - Storage for media assets
- **Styling**: Tailwind CSS
- **TypeScript**: For type safety

## Prerequisites

Before you begin, ensure you have the following installed:
- Node.js 18.x or higher
- npm or yarn
- Git

## Getting Started

### 1. Clone the Repository

```bash
git clone <repository-url>
cd basketball-coaching-platform
```

### 2. Install Dependencies

```bash
npm install
# or
yarn install
```

### 3. Set Up Supabase

1. Create a new project at [supabase.com](https://supabase.com)
2. Copy your project URL and anon key
3. Set up the database schema (see Database Schema section)

### 4. Environment Variables

Create a `.env.local` file in the root directory:

```env
NEXT_PUBLIC_SUPABASE_URL=your_supabase_project_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
```

### 5. Run the Development Server

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

## Database Schema

### Tables

#### `players`
- `id` (uuid, primary key)
- `first_name` (text)
- `last_name` (text)
- `date_of_birth` (date)
- `parent_email` (text)
- `parent_phone` (text)
- `emergency_contact` (text)
- `medical_info` (text, optional)
- `created_at` (timestamp)

#### `camps`
- `id` (uuid, primary key)
- `name` (text)
- `description` (text)
- `start_date` (date)
- `end_date` (date)
- `capacity` (integer)
- `age_min` (integer)
- `age_max` (integer)
- `price` (decimal)
- `status` (enum: draft, published, full, completed)
- `created_at` (timestamp)

#### `programs`
- `id` (uuid, primary key)
- `name` (text)
- `description` (text)
- `duration_weeks` (integer)
- `skill_level` (enum: beginner, intermediate, advanced)
- `age_group` (text)
- `created_at` (timestamp)

#### `registrations`
- `id` (uuid, primary key)
- `player_id` (uuid, foreign key)
- `camp_id` (uuid, foreign key)
- `registration_date` (timestamp)
- `payment_status` (enum: pending, paid, refunded)
- `created_at` (timestamp)

### Row Level Security (RLS)

Enable RLS on all tables and create appropriate policies:
- Public read access for published camps and programs
- Authenticated users can create registrations
- Admin users can manage all data

## Project Structure

```
basketball-coaching-platform/
├── app/
│   ├── (public)/
│   │   ├── page.tsx           # Home page
│   │   ├── register/
│   │   │   └── page.tsx       # Registration form
│   │   └── programs/
│   │       └── page.tsx       # Programs listing
│   ├── (dashboard)/
│   │   └── dashboard/
│   │       └── page.tsx       # Camp dashboard
│   ├── layout.tsx
│   └── globals.css
├── components/
│   ├── ui/                    # Reusable UI components
│   ├── forms/                 # Form components
│   └── layout/                # Layout components
├── lib/
│   ├── supabase/
│   │   ├── client.ts          # Supabase client
│   │   └── server.ts          # Server-side Supabase
│   └── utils.ts               # Utility functions
├── types/
│   └── database.ts            # TypeScript types
└── public/
    └── images/                # Static assets
```

## Key Routes

- `/` - Home page
- `/register` - Player registration form
- `/programs` - Available programs
- `/dashboard` - Camp management dashboard (protected)

## Authentication

The platform uses Supabase Authentication with the following features:
- Email/password authentication for administrators
- Magic link authentication option
- Protected routes using middleware

## Deployment

### Vercel (Recommended)

1. Push your code to GitHub
2. Import the project in Vercel
3. Add environment variables
4. Deploy

### Other Platforms

The application can be deployed to any platform that supports Next.js applications.

## Environment Variables Reference

| Variable | Description | Required |
|----------|-------------|----------|
| `NEXT_PUBLIC_SUPABASE_URL` | Your Supabase project URL | Yes |
| `NEXT_PUBLIC_SUPABASE_ANON_KEY` | Your Supabase anonymous key | Yes |

## Development Roadmap

- [ ] Basic home page
- [ ] Player registration form
- [ ] Camp listing and details
- [ ] Admin dashboard
- [ ] Payment integration
- [ ] Email notifications
- [ ] Attendance tracking
- [ ] Mobile app version

## Contributing

Contributions are welcome! Please follow these steps:
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a pull request

## License

[Choose appropriate license]

## Support

For questions or support, contact [your-email@example.com]

## Acknowledgments

- Next.js documentation
- Supabase documentation
- Basketball coaching community feedback
