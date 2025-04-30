# The Eye - Overview

This directory serves as the core structure for the Auburn Baseball analytics web application, organizing all components related to player statistics, team data, and conference-wide insights.

---

## Directory Structure

- **components/** - Contains reusable UI components such as the sidebar, navigation, and data tables.
- **player/** - Houses all player-specific pages and components, including individual stats, heat maps, and defensive models.
- **team/** - Manages team-specific pages, including rosters, batting/pitching statistics, and team navigation.
- **layout.tsx** - Defines the overall layout structure of the app, including the sidebar, top bar, and main content area.
- **page.tsx** - The landing page for the application, displaying all conferences and their associated teams.

---

## File Details

### `layout.tsx`
- **Purpose**: Provides the **global layout** for the application.
- **Key Features**:
  - Implements a **sidebar** and **top navigation**.
  - Uses **Material UI (MUI)** components for styling.
  - Dynamically adjusts layout width based on screen size.

### `page.tsx`
- **Purpose**: Serves as the **home page** of the app, listing all conferences and their teams.
- **Key Features**:
  - Queries **Prisma ORM** to fetch **conference and team data**.
  - Uses **MUI Grid** for a structured layout.
  - Renders a `ConferenceTable` for each conference with its respective teams.

---

## Summary
The `the-eye/` directory contains the core logic for managing **baseball analytics**, organizing data into **players, teams, and conferences**. The layout and home page ensure a seamless user experience with a **structured navigation system** and **efficient data retrieval**.

This directory acts as the foundation for data visualization and navigation across the application.

