# Batting - Player Hitting Statistics Visualization

This folder contains components used to **display and visualize batting statistics** for a player.

## Structure

- **`BattingStatsBarChart.tsx`** - Renders a bar chart of key batting statistics.
- **`BattingStatsTable.tsx`** - Displays detailed batting statistics in a table format.
- **`CreateBatterDiagrams.tsx`** - Combines both the table and bar chart into a single layout.

## Component Details

### `BattingStatsBarChart.tsx`
- **Purpose**: Creates a **bar chart** to display various batting statistics.
- **Key Features**:
  - Uses the **Material UI `BarChart`** component.
  - Formats data to match chart requirements.
  - Displays the following statistics:
    - OBP (On-Base Percentage)
    - SLUG (Slugging Percentage)
    - OPS (On-Base Plus Slugging)
    - CHASE (Chase Percentage)
    - IZW (In-Zone Whiff Percentage)
    - ISO (Isolated Power)
    - K% (Strikeout Percentage)
    - BoB (Base on Balls Percentage)

### `BattingStatsTable.tsx`
- **Purpose**: Displays batting statistics in a **structured table** format.
- **Key Features**:
  - Uses **Material UI `Table`** components for styling.
  - Shows the following detailed batting statistics:
    - Games played
    - Plate appearances
    - At-bats
    - Batting average
    - Hits, strikes, walks, strikeouts
    - Homeruns, extra-base hits, sacrifice plays, hit-by-pitch
    - Total bases

### `CreateBatterDiagrams.tsx`
- **Purpose**: **Combines** the bar chart and stats table into a structured layout.
- **Key Features**:
  - Uses **Material UI `Grid`** for responsive design.
  - Displays both the `BattingStatsTable` and `BattingStatsBarChart` components.
  - Ensures data is consistently formatted and visualized effectively.

## Usage

These components are used in player profiles to provide **statistical insights into batting performance**.

Example usage:
```tsx
<CreateBatterDiagrams stats={playerBattingStats} />
```

This will render both the table and bar chart for the given player's batting statistics.

