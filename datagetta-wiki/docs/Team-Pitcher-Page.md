# Team Pitcher Page

This folder contains the `page.tsx` file, which is responsible for displaying the **pitching statistics** of a specific team. It dynamically retrieves and presents data related to the team's pitchers.

## File Overview

### `page.tsx`
- **Purpose**: Renders a **pitching stats table** for the selected team.
- **Key Functionalities**:
  - Retrieves the `teamName` from the URL parameters.
  - Uses **React Suspense** to display a loading skeleton while fetching data.
  - Calls `CreatePitcherTable.tsx` to query and render the data.

## How It Works
1. The `teamName` parameter is extracted and decoded.
2. A **fallback skeleton** (`TableSkeleton.tsx`) is displayed while data loads.
3. `CreatePitcherTable.tsx` is called to fetch and display the **team’s pitcher statistics**.

## Example Usage
```tsx
<Suspense fallback={<TableSkeleton />}>
    <CreatePitcherTable team={decodedTeamName} />
</Suspense>
```

## Dependencies
- `CreatePitcherTable.tsx` - Fetches and structures **pitcher statistics**.
- `TableSkeleton.tsx` - Displays a **loading animation** while data is being retrieved.

---
This file ensures a **seamless user experience** by dynamically fetching and displaying pitcher-related data for any selected team.

