# Team Batter Page

This folder contains the **team batter statistics page**, which displays batting stats for all players on a given team.

## File Overview

### `page.tsx`
- **Purpose**: Generates the team batter stats page dynamically based on the provided team name.
- **Key Features**:
  - **Fetches and Displays Batting Stats**:
    - Uses `CreateBatterTable.tsx` to generate the batting table.
  - **Suspense and Loading State**:
    - Wraps the batter stats table in `React.Suspense`, using `TableSkeleton.tsx` as a fallback to enhance performance and user experience.
  - **Dynamic Routing**:
    - Extracts `teamName` from the URL and decodes it for use in queries.

## Component Breakdown
- `CreateBatterTable.tsx`: Queries and formats batting stats before rendering them in a table.
- `TableSkeleton.tsx`: Displays a loading skeleton while data is being fetched.

## Example Usage
The page is automatically routed based on the team name in the URL:
```url
/the-eye/team/AUB_TIG/batter
```
This will display all batter stats for Auburn Tigers.

## Summary
This page provides **team-wide batting statistics** in a structured and easy-to-read table, leveraging server-side rendering for fast and efficient data retrieval.

