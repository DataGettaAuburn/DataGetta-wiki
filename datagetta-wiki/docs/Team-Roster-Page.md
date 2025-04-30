# Team Roster Page

This directory contains the page responsible for displaying the **team's roster**.

## File Overview

### `page.tsx`
- **Purpose**: Renders the **roster table** for a given team.
- **Key Features**:
  - Uses **React Suspense** to handle loading states with `TableSkeleton`.
  - Dynamically fetches the **team's roster** from the database using `CreateRosterTable`.
  - Decodes the `teamName` parameter to ensure proper formatting.

## Component Breakdown

### `CreateRosterTable`
- Queries and formats the **team's roster**.
- Displays a **sortable table** of players.

### `TableSkeleton`
- Provides a **loading state** for the roster table.

## Usage Example
```tsx
<Suspense fallback={<TableSkeleton />}>
    <CreateRosterTable team="AUB_TIG" />
</Suspense>
```

## Summary
This page is an essential part of the **team analytics section**, providing users with a **detailed roster list** for each team in Auburn Baseball.

