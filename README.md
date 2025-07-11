# Vulnerable Banking Application

> **⚠️ WARNING**: This is an intentionally vulnerable application designed for educational purposes only. DO NOT use in production or expose to the internet.

## Overview

This is a mobile banking application built with React Native (Expo) and Supabase, intentionally designed with security vulnerabilities to demonstrate common web application security risks. The application showcases both vulnerable and secure implementations of banking features, making it an excellent resource for security training and awareness.

## Features

- **User Authentication** (Email/Password)
- **Balance Management**
- **Money Transfers** between users
- **Deposits** (with Stripe integration)
- **Admin Dashboard** (for privileged users)
- **User Profiles** with avatars

## Tech Stack

- **Frontend**: React Native (Expo)
- **Backend**: Supabase (PostgreSQL, Auth, Storage, Edge Functions)
- **Payment Processing**: Stripe
- **State Management**: React Context
- **UI Components**: React Native Elements

## Intentionally Vulnerable Features

### 1. Insecure Direct Object Reference (IDOR) in Money Transfers
- **Vulnerability**: The transfer function trusts client-provided `from_user_id` without proper ownership verification
- **Impact**: Users can transfer money from any account by modifying the `from_user_id`
- **Location**: `supabase/functions/transfer-funds/index.ts`

### 2. Broken Access Control in Admin Functions
- **Vulnerability**: Missing proper role-based access controls
- **Impact**: Regular users might access admin-only functionality
- **Location**: `components/AdminDashboard.tsx`

### 3. Insufficient Input Validation
- **Vulnerability**: Lax input validation on client and server
- **Impact**: Potential for various injection attacks
- **Example**: `components/SendMoney.tsx`

## Secure Counterparts

For each vulnerability, there should be a corresponding secure implementation that demonstrates proper security practices. These are typically found in parallel branches or commented code sections.

## Getting Started

### Prerequisites

- Node.js 16+
- npm or yarn
- Expo CLI (`npm install -g expo-cli`)
- Supabase account
- Stripe account (for payment processing)

### Installation

1. Clone the repository:
   ```bash
   git clone [repository-url]
   cd vulnerable-bank
   ```

2. Install dependencies:
   ```bash
   npm install
   # or
   yarn
   ```

3. Set up environment variables:
   Create a `.env` file in the root directory with:
   ```
   SUPABASE_URL=your_supabase_url
   SUPABASE_ANON_KEY=your_supabase_anon_key
   STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key
   ```

4. Set up Supabase:
   - Create a new Supabase project
   - Run the SQL migrations from `supabase/migrations/`
   - Configure Row Level Security (RLS) policies

5. Start the development server:
   ```bash
   expo start
   ```

## Security Training Guide

This application is designed to be used in security training. Each vulnerability is documented with:

1. **Vulnerability Description**: What the issue is
2. **Attack Vector**: How to exploit it
3. **Impact**: Potential consequences
4. **Remediation**: How to fix it
5. **References**: OWASP Top 10 mapping and additional resources

## Contributing

This project is for educational purposes. If you'd like to contribute additional vulnerabilities or improvements to the training materials, please submit a pull request.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

Joel Mbaka - [GitHub](https://github.com/joelmbaka) | [Email](mailto:mbakajoe26@gmail.com)

## Acknowledgments

- OWASP for their excellent security resources
- Supabase for the amazing backend services
- The React Native community for their support and packages
