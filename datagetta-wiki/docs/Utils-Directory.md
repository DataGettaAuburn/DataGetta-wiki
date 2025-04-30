# Utils Directory

This folder contains utility files that provide core functionality for the application, including database management, type definitions, custom components, and theme settings.

## Structure
- **Database Management**:
  - `db.ts` - Initializes the **Prisma Client** for database interactions.
- **Custom Components**:
  - `Link.tsx` - A custom **Next.js & MUI Link** component for navigation.
- **Data Handling**:
  - `replacer.ts` - Handles **BigInt conversion issues** in JSON data for compatibility.
- **Styling & Theme**:
  - `theme.ts` - Defines the **MUI theme** based on **Auburn’s branding guide**.
- **Type Definitions**:
  - `types.ts` - Defines **TypeScript types** for database queries and views.

---

## File Details

### `db.ts`
- **Purpose**: Establishes a **single database connection** for Prisma ORM to avoid issues with Next.js dev server reloads.
- **Key Features**:
  - Prevents **multiple database connections** in development mode.
  - Enables **query logging** for debugging.

### `Link.tsx`
- **Purpose**: Combines **Next.js Link** with **MUI Link** for navigation.
- **Key Features**:
  - Provides **MUI styling** for links.
  - Supports **custom font weight and underlining options**.

### `replacer.ts`
- **Purpose**: Converts `bigint` values into **numbers** for JSON serialization.
- **Key Features**:
  - Fixes **compatibility issues** when passing BigInt values as props.
  - Provides **custom replacers** for different database models (**batters, pitchers, run values**).

### `theme.ts`
- **Purpose**: Defines the **MUI theme** using Auburn’s official branding.
- **Key Features**:
  - Uses **Auburn’s navy and orange colors**.
  - Customizes **typography** using the `Inter` font.
  - Defines **primary, secondary, and text colors**.

### `types.ts`
- **Purpose**: Defines **TypeScript types** for database queries.
- **Key Features**:
  - Defines **batting stats, pitching stats, and pitch summaries**.
  - Supports **custom types for run values and player performance metrics**.

---

## Summary
The `utils/` folder contains essential utility files for:
- **Database connectivity (Prisma ORM)**
- **TypeScript type definitions**
- **Custom JSON serialization handling**
- **Global application theming**
- **Navigation components**

These utilities ensure **efficient data handling, consistent styling, and seamless navigation** within the application.

