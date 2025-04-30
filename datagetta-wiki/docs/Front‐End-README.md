# The Eye - Auburn Baseball Data Visualization

This project is built using [Next.js](https://nextjs.org/) and was initially bootstrapped with [`create-next-app`](https://github.com/vercel/next.js/tree/canary/packages/create-next-app). The Eye serves as a data visualization tool for Auburn Baseball, integrating various analytics to provide insights into player and team performance.

## Getting Started

To start the development server, use one of the following commands:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Once started, open [http://localhost:3000](http://localhost:3000) in your browser to access the application.

## Domain

- **Live App**: [https://datagetta.app](https://datagetta.app)
- **Domain Provider**: Squarespace
- **Domain Points To**: `datagetta.cse.eng.auburn.edu` (for Auburn authentication)
- **Auto-renew Date**: February 5, 2025

## Project Structure

- **`/app`** - Contains the core Next.js pages and layouts.
  - **`layout.tsx`** - Provides global layout structure with Material UI theming and caching.
  - **`page.tsx`** - Serves as the landing page with branding and login functionality.
  - **`/the-eye/`** - Houses primary UI components and authenticated user pages.
    - **`layout.tsx`** - Defines the structure for authenticated pages, including the sidebar, mobile nav, and top bar.
    - **`page.tsx`** - Displays conference tables and teams, querying data from Prisma.
    - **`/components/`** - Contains reusable UI components such as `UI_Layout` (sidebar, nav, etc.).
    - **`/player/`** - Handles player-related data visualization.
    - **`/team/`** - Manages team-level analytics and insights.
  - **`/utils/`** - Contains shared utilities such as theme configuration and database helpers.
- **`/prisma/`** - Contains database schema and configuration files.
- **`/public/`** - Holds static assets such as images.

## Key Technologies

- **Next.js (App Router)** - Framework for server-side rendering and static site generation.
- **React** - UI library for building components.
- **Material UI** - Ensures styling consistency across the UI.
- **Prisma** - ORM for database interactions.

## Configuration Files

- **`next.config.mjs`** - Default Next.js configuration (currently minimal but can be extended).
- **`tsconfig.json`** - TypeScript settings, including module resolution and path aliases.
- **`.eslintrc.json`** - ESLint configurations for code linting.

## Available Scripts

In the project directory, you can run:

- **`npm run dev`** - Runs the development server.
- **`npm run build`** - Builds the project for production.
- **`npm run start`** - Starts the production server.
- **`npm run lint`** - Runs ESLint for code quality checks.

## The Eye Layout (`app/the-eye/layout.tsx`)

- **Purpose**: Provides structure for authenticated pages, including:
  - A **desktop sidebar**
  - A **mobile navigation bar**
  - A **top bar**
- **Main Components**:
  - `UI_Layout`: Handles sidebar and navigation elements.
  - `Toolbar`: Adds spacing below the top bar.
  - `Box`: Manages page layout with dynamic width adjustments.

## Conference Page (`app/the-eye/page.tsx`)

- **Purpose**: Displays conferences and teams, allowing users to browse baseball data.
- **Database Query**: Uses Prisma to fetch conference and team details.
- **Main Components**:
  - `Grid`: Structures the page layout.
  - `Typography`: Displays the "Conferences" heading.
  - `ConferenceTable`: Renders tables for each conference and its teams.
  - **Query Behavior**:
    - Retrieves all conferences and their associated teams.
    - Orders teams alphabetically by `DisplayName`.

## Authentication

- Authentication is handled using **Auburn University's authentication service**.

## Prisma - Database Management

- **Prisma ORM** is used for querying the database.
- For advanced queries, **`prisma.$queryRaw`** is used (necessary for database views and functions).

### Managing Prisma Schema

- **DO NOT** edit the `schema.prisma` file directly.
- Instead, modify **`schema.sql`** in the database directory.
- After updating the schema, generate a new Prisma client:
  ```bash
  npx prisma generate
  ```

## Handling PostgreSQL BigInt Issues

- Some Material UI components do not support **BigInt** values.
- Convert BigInt to Number using:
  ```js
  JSON.parse(JSON.stringify(data, replacer));
  ```
- The `replacer` function is located in **`/app/utils/replacer.ts`**.

## Future Work

- Implement a **Search Bar**.
- Add the ability to **hide Defensive Shift and Heat Map model tabs** for non-pitchers.

## Deployment

- This application is deployed via **Vercel**.
- Changes pushed to the main branch will automatically trigger a deployment.

## Contributing

1. Fork the repository.
2. Create a new branch for your feature or fix.
3. Commit your changes and push them.
4. Open a pull request for review.

---

