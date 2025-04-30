# Player Directory

This directory contains all **player-related data and components** for displaying individual player statistics, heat maps, run value models, and defensive shifts.

## Structure

- **[teamName]/** - Dynamic folder that holds **all players for a specific team**.
- **components/** - Contains **shared UI components** used in player pages.

## Player Pages

Each player has a dedicated page within their **team folder**, structured as follows:

- **stats/** - Displays player statistics over a given date range.
- **heatMap/** - Shows heat maps for pitchers.
- **runValue/** - Displays run value models for players.
- **shiftModel/** - Displays defensive shifting models.

## Components

The `components/` folder contains shared components for displaying:

- **Batting and pitching stats**
- **Heat maps for pitches**
- **Defensive shift models**
- **Run value models**

These components allow for **dynamic data visualization** and enable interactive exploration of player performance.

---

### Example Player Page Structure
```
/player/
  [teamName]/
    [playerName]/
      stats/
      heatMap/
      runValue/
      shiftModel/
  components/
```

This directory ensures **organized player data management** and **efficient data retrieval** for Auburn Baseball analytics.

