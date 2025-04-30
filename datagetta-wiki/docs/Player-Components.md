# Player Components

This folder contains components used for **player-related pages**, including stat visualizations, model selectors, and general UI elements.

## Structure

- **Stat Visualization**:
  - `CreateStatsDiagrams.tsx` - Determines if a player is a batter or pitcher and generates corresponding diagrams.
- **User Interaction**:
  - `DateSelector.tsx` - Provides a date range picker for filtering stats.
  - `ModelTabs.tsx` - Creates navigation tabs for switching between different player models.
- **Player Information**:
  - `PlayerInfo.tsx` - Displays player name and team details.
- **Loading Components**:
  - `StatsTableSkeleton.tsx` - Displays a loading skeleton while data loads.

---

## Component Details

### `CreateStatsDiagrams.tsx`
- **Purpose**: Determines whether a player is a **batter or pitcher** and loads the appropriate stat diagrams.
- **Key Features**:
  - Uses **Prisma ORM** to query batter, pitcher, and pitch count statistics.
  - Calls `CreateBatterDiagrams.tsx` for hitters and `CreatePitcherDiagrams.tsx` for pitchers.
  - Returns a **"Strikeout!"** message if no data is found.

### `DateSelector.tsx`
- **Purpose**: Allows users to select a **date range** for filtering player stats.
- **Key Features**:
  - Uses **MUI DatePicker** components.
  - Updates the URL dynamically based on selected dates.
  - Prevents incorrect date selections with error handling.

### `ModelTabs.tsx`
- **Purpose**: Displays **navigation tabs** for switching between different player models.
- **Key Features**:
  - Highlights the **active tab** based on the current URL.
  - Provides links to:
    - `Stats`
    - `Defensive Shift`
    - `Heat Maps`
    - `Run Values`

### `PlayerInfo.tsx`
- **Purpose**: Displays **player name and team details**.
- **Key Features**:
  - Formats the player name for proper display.
  - Uses **MUI Typography** for consistent styling.

### `StatsTableSkeleton.tsx`
- **Purpose**: Displays a **loading skeleton** while player stats are being retrieved.
- **Key Features**:
  - Uses **MUI Skeleton** component.
  - Prevents layout shifts by maintaining element size.

---

## Summary
This folder contains essential **player-focused UI components** that enhance the experience by enabling **dynamic data updates, user interactions, and navigation** between different player models.

These components work together to ensure a **seamless data visualization experience** for coaches, analysts, and users exploring Auburn Baseball data.

---

Example Usage:
```tsx
<CreateStatsDiagrams player="John_Doe" team="AUB_TIG" startDate="2024-02-01" endDate="2024-04-01" />
```

