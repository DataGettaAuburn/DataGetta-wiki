# Player Page Layout

This folder contains all the player-specific models and data visualizations for a given player within a team.

## Structure

- **`heatMap/`** - Displays a player's heat maps based on pitch data.
- **`runValue/`** - Shows the player's run value model against different opponents.
- **`shiftModel/`** - Provides defensive shift models based on pitch tendencies.
- **`stats/`** - Displays statistical breakdowns for a player over a selected date range.
- **`layout.tsx`** - Defines the layout for all player-related pages.

## `layout.tsx` Overview

This file serves as the layout for **all player pages**, ensuring a consistent structure across different visualizations and stat models. It fetches **player details from the database**, displays player information, and renders navigation tabs for switching between different models.

### Key Functionalities

1. **Extracts `teamName` and `playerName` from the URL parameters.**
2. **Queries the database** using Prisma to retrieve:
   - The player's full name.
   - The team’s display name.
3. **Displays a navigation bar (`ModelTabs`)** for switching between different data visualizations.
4. **Renders `PlayerInfo`** to show player details at the top of the page.
5. **Wraps all child components (`children`)** to allow each model's respective page to be displayed within the layout.

### Key Components Used

- **`ModelTabs`** - Navigation tabs for switching between different player models.
- **`PlayerInfo`** - Displays the player's name and team information.
- **`Box`** - Provides structured spacing and padding.

## How It Works

1. Fetches the **player's name and team** using Prisma.
2. Displays a **top navigation bar** (`ModelTabs`) for selecting different data visualizations.
3. Shows **player details** (`PlayerInfo`) at the top of the page.
4. Renders **child components** (`{children}`), allowing specific player models (heat maps, stats, etc.) to load dynamically.

## Example Usage

This layout automatically wraps all player-related pages when accessed through:

```
/the-eye/player/{teamName}/{playerName}/
```

For example:

```
/the-eye/player/AUB_TIG/John_Doe/
```

This would display **John Doe’s** player page, where users can navigate between different models such as heat maps, stats, and shift models using the `ModelTabs` navigation.

