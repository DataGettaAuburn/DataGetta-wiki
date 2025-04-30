# Team Directory

This folder contains the structure for displaying team-specific data within **The Eye** application. Each team has pages for **batting stats, pitching stats, and roster information**.

- **[teamName]/** - A dynamic folder containing pages for each individual team, including:
  - `batter/` - Displays team batting stats.
  - `pitcher/` - Displays team pitching stats.
  - `roster/` - Displays the team's full roster.
  - `layout.tsx` - Defines the layout for team-specific pages.
- **components/** - Contains reusable UI components for rendering team-related data, such as tables and navigation elements.


## Overview

This directory is responsible for organizing all pages and components that handle team-specific data. It is dynamically structured to allow seamless navigation between teams and their respective statistics, providing an efficient and interactive experience for users analyzing Auburn Baseball data.


---

## File Details

### `layout.tsx`
- **Purpose**: Provides a **consistent layout** for team pages, displaying the team name, conference, and navigation tabs.
- **Key Features**:
  - Retrieves **team information** (name and conference) from the database using Prisma.
  - Uses **MUI components** to structure the layout and enhance UI design.
  - Includes `TableTabs.tsx` for **navigation** between **Roster, Batting, and Pitching pages**.
  - Displays `TeamInfo.tsx` to show **team details**.
  - Renders **dynamic children components** for each specific team page (batting, pitching, or roster).

---

## Summary
The `[teamName]/` directory provides a **structured and navigable** interface for users to explore team-specific data. The `layout.tsx` ensures **consistent styling** and **efficient data retrieval**, improving the user experience when browsing different team pages.

