# Pitching - Pitching Statistics Visualization

This folder contains components used to **display and visualize pitching statistics** for a player.

## Structure

- **`CreatePitcherDiagrams.tsx`** - Combines the stats table and bar chart for pitchers.
- **`PitchingStatsTable.tsx`** - Displays pitcher performance metrics in a table.
- **`PitchSumsBarChart.tsx`** - Renders a bar chart of pitch type distributions.

## Component Details

### `CreatePitcherDiagrams.tsx`
- **Purpose**: Combines **PitchingStatsTable** and **PitchSumsBarChart** into a structured layout.
- **Key Features**:
  - Uses Material UI’s **Grid** for responsive alignment.
  - Displays **pitching stats** and **pitch distribution data** side by side.

### `PitchingStatsTable.tsx`
- **Purpose**: Displays **detailed pitcher stats** in a table format.
- **Key Features**:
  - Uses **Material UI’s Table** components for structured display.
  - Shows key stats such as:
    - Games played, starts, pitches thrown.
    - Strikeouts, walks, batters faced.
    - Advanced metrics like **In-Zone Whiff Percentage, Chase Percentage, K%, BoB%.**

### `PitchSumsBarChart.tsx`
- **Purpose**: Creates a **bar chart** representing different pitch types.
- **Key Features**:
  - Uses **Material UI `BarChart`** for visualization.
  - Displays counts of each pitch type (Fastball, Slider, Changeup, etc.).
  - Adjusts bar color and scaling dynamically based on team themes.

## Usage

These components work together to visualize **pitching tendencies** and provide insights into a pitcher’s effectiveness.

Example usage:
```tsx
<CreatePitcherDiagrams stats={playerPitchingStats} sums={playerPitchSums} />
```

This will render a **pitching stats table** and a **bar chart** of pitch distribution.

