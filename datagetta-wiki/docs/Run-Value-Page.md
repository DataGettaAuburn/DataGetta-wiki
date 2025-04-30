# Run Value - Player and Team Performance Comparison

This folder contains components that **compare and visualize run values** for batters and pitchers. The run value metric helps assess the effectiveness of certain pitch types against batters and teams.

## Structure

- **Comparison Tables**:
  - `BatterComparisonTable.tsx` - Compares a pitcher's run values to a team’s batters.
  - `PitcherComparisonTable.tsx` - Compares a batter’s run values to a team’s pitchers.
- **Gauge Visualizations**:
  - `BatterScoreGauge.tsx` - Displays a batter’s run value scores per pitch type.
  - `PitcherScoreGauge.tsx` - Displays a pitcher’s run value scores per pitch type.
- **Run Value Models**:
  - `CreateRunValueModels.tsx` - Queries data and generates run value comparisons between players and teams.
- **Comparison Queries**:
  - `CreateBatterComparisonTable.tsx` - Fetches batters for team comparison.
  - `CreatePitcherComparisonTable.tsx` - Fetches pitchers for team comparison.
- **Team Selection**:
  - `CreateTeamSelect.tsx` - Retrieves and validates the team list.
  - `TeamSelect.tsx` - Provides a dropdown for selecting a team.

---

## Component Details

### `BatterComparisonTable.tsx`
- **Purpose**: Compares a pitcher’s run value scores against batters from a selected team.
- **Key Features**:
  - Uses **MUI DataGrid** to display data in a sortable table.
  - Highlights advantage:
    - **Green** (Pitcher advantage)
    - **Red** (Batter advantage)
  - Columns include batter side, pitch type, and run value scores.

### `PitcherComparisonTable.tsx`
- **Purpose**: Compares a batter’s run values against a team’s pitchers.
- **Key Features**:
  - Uses **MUI DataGrid** for visualization.
  - Highlights advantage using color-coded scores.
  - Displays pitcher handedness, pitch type, and calculated scores.

### `BatterScoreGauge.tsx` & `PitcherScoreGauge.tsx`
- **Purpose**: Displays run values in a **gauge chart format** for better visualization.
- **Key Features**:
  - Uses **MUI Gauge** components.
  - Dynamically assigns values to each pitch type.
  - Adjusts display based on handedness and batting/pitching side.

### `CreateRunValueModels.tsx`
- **Purpose**: Queries **batter and pitcher run values** and renders the appropriate components.
- **Key Features**:
  - Determines whether a player is a batter or pitcher.
  - Fetches **run value statistics** from the database.
  - Dynamically renders:
    - `PitcherScoreGauge` for pitchers.
    - `BatterScoreGauge` for batters.
    - `CreateBatterComparisonTable` & `CreatePitcherComparisonTable` for analysis.

### `CreateBatterComparisonTable.tsx` & `CreatePitcherComparisonTable.tsx`
- **Purpose**: Fetches team-specific data for comparison tables.
- **Key Features**:
  - Uses **Prisma ORM** to query batters/pitchers from a given team.
  - Orders results by pitch type for consistency.
  - Passes fetched data to `BatterComparisonTable` or `PitcherComparisonTable`.

### `CreateTeamSelect.tsx` & `TeamSelect.tsx`
- **Purpose**: Allows users to select a team for comparison.
- **Key Features**:
  - Queries **Southeastern Conference teams** for filtering.
  - Validates **selected team** to ensure it exists in the database.
  - Uses **MUI Autocomplete** to provide a dropdown selector.
  - Updates the URL dynamically upon team selection.

---

## Usage

These components work together to **analyze matchups** between batters and pitchers based on **run values**.

Example usage:
```tsx
<CreateRunValueModels team="AUB_TIG" player="John_Doe" opposingTeam="LSU_TIG" />
```

This will:
- Generate **John Doe’s** run value model.
- Compare **his performance** against batters/pitchers from **LSU Tigers**.
- Display relevant charts and tables to analyze matchup effectiveness.

