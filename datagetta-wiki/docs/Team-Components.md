# Team Components

This folder contains components used for **team-related pages**, including player stats tables, roster displays, and navigation elements.

## Structure

- **Tables**:
  - `BatterTable.tsx` - Displays batting statistics for players.
  - `PitcherTable.tsx` - Displays pitching statistics for players.
  - `PitchSumsTable.tsx` - Displays pitch type usage for pitchers.
  - `RosterTable.tsx` - Displays team roster information.
- **Data Fetching**:
  - `CreateBatterTable.tsx` - Queries batting stats and passes them to `BatterTable.tsx`.
  - `CreatePitcherTable.tsx` - Queries pitching stats and pitch type usage, passing results to `PitcherTable.tsx` and `PitchSumsTable.tsx`.
  - `CreateRosterTable.tsx` - Queries team roster information and passes it to `RosterTable.tsx`.
- **Navigation & UI**:
  - `TableTabs.tsx` - Provides navigation between roster, batting, and pitching pages.
  - `TeamInfo.tsx` - Displays team name and conference.
- **Loading Components**:
  - `TableSkeleton.tsx` - Displays a loading skeleton while table data is being retrieved.

---

## Component Details

### `BatterTable.tsx`
- **Purpose**: Displays **batting statistics** for a team's players.
- **Key Features**:
  - Uses **MUI DataGrid** to display tabular data.
  - Player names link to their individual stat pages.
  - Includes various batting metrics such as **AVG, OPS, HR, BB%**.

### `PitcherTable.tsx`
- **Purpose**: Displays **pitching statistics** for a team's players.
- **Key Features**:
  - Uses **MUI DataGrid** to display tabular data.
  - Player names link to their individual stat pages.
  - Displays key metrics like **ERA, IP, K%, BB%**.

### `PitchSumsTable.tsx`
- **Purpose**: Displays **pitch type usage** for a team's pitchers.
- **Key Features**:
  - Shows the number of pitches thrown for each pitch type.
  - Links pitcher names to their individual stat pages.

### `RosterTable.tsx`
- **Purpose**: Displays a **team’s roster**.
- **Key Features**:
  - Uses **MUI DataGrid** to display roster information.
  - Player names link to their individual stat pages.

### `CreateBatterTable.tsx`
- **Purpose**: Queries the **batter statistics database** and sends data to `BatterTable.tsx`.
- **Key Features**:
  - Uses **Prisma ORM** to retrieve data from `batter_stats_view_2024`.

### `CreatePitcherTable.tsx`
- **Purpose**: Queries **pitching statistics** and **pitch type usage**.
- **Key Features**:
  - Uses **Prisma ORM** to retrieve data from `pitcher_stats_view_2024` and `pitch_sums_view_2024`.
  - Passes results to `PitcherTable.tsx` and `PitchSumsTable.tsx`.

### `CreateRosterTable.tsx`
- **Purpose**: Queries and displays a **team’s roster**.
- **Key Features**:
  - Uses **Prisma ORM** to fetch all players on a team.
  - Orders players **alphabetically** before passing to `RosterTable.tsx`.

### `TableTabs.tsx`
- **Purpose**: Provides navigation **tabs** to switch between **Roster, Batting, and Pitching**.
- **Key Features**:
  - Highlights the **active tab** based on the current URL.
  - Allows seamless navigation between different team data pages.

### `TeamInfo.tsx`
- **Purpose**: Displays **team name and conference**.
- **Key Features**:
  - Uses **MUI Typography** for consistent styling.

### `TableSkeleton.tsx`
- **Purpose**: Displays a **loading skeleton** while table data is being retrieved.
- **Key Features**:
  - Uses **MUI Skeleton** component.
  - Prevents layout shifts by maintaining element size.

---

## Summary
This folder contains essential **team-focused UI components** that enhance the experience by enabling **dynamic data updates, user interactions, and navigation** between different team models.

These components work together to ensure a **seamless data visualization experience** for coaches, analysts, and users exploring Auburn Baseball data.

---

Example Usage:
```tsx
<CreateBatterTable team="AUB_TIG" />
```

