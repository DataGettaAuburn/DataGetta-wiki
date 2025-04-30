# Player Stats - Time-Filtered Data Analysis

This folder contains the **player stats visualization** for a specific pitcher within a given date range.

## Files

- **`page.tsx`** - Displays player statistics between a selected `startDate` and `endDate`.

## `page.tsx` Overview

This file dynamically renders **player statistics** for a given time period. It decodes the **team name**, **player name**, **start date**, and **end date** from the URL parameters and passes them to the `CreateStatsDiagrams` component.

### Key Components:

- **`Box`**: Wrapper for the page layout.
- **`DateSelector`**: Allows users to filter stats based on a start and end date.
- **`Suspense`**: Ensures smooth loading by displaying `StatsTableSkeleton` while stats load.
- **`CreateStatsDiagrams`**: Generates visual representations of the player's performance over the selected time range.

## How It Works

1. Extracts **team name**, **player name**, **start date**, and **end date** from the URL parameters.
2. Displays a **DateSelector** to allow users to adjust the timeframe.
3. Uses **`Suspense`** to show a loading skeleton while `CreateStatsDiagrams` processes the data.
4. Calls `CreateStatsDiagrams` to visualize the player's performance over the selected period.

## Example Usage

This page is accessed dynamically through the app's routing system:

```
/the-eye/player/{teamName}/{playerName}/stats/{startDate}/{endDate}
```

For example:

```
/the-eye/player/AUB_TIG/John_Doe/stats/2024-04-01/2024-04-15
```

This would generate a statistical breakdown of **John Doe**, a pitcher from **AUB_TIG**, between **April 1, 2024**, and **April 15, 2024**.

