# Player Stats - Redirect Page

This folder contains a **redirect mechanism** to ensure a player's stats page is accessed with the required `startDate` and `endDate` parameters.

## Files

- **`page.tsx`** - Redirects users to a dynamically generated stats page with a default date range.

## `page.tsx` Overview

This file exists to **redirect users** to a player's stats page with an appropriate time range when the `startDate` and `endDate` parameters are missing. Since these dates are required to query the database, this redirect ensures the proper routing without user input.

### Key Functionalities:

- **Decodes `teamName` and `playerName` from the URL parameters.**
- **Defines a `startOfSeason` date (February 16, 2024).**
- **Fetches the current date using `dayjs()`.**
- **Constructs a URL with a valid date range and redirects the user permanently.**

## How It Works

1. Extracts **team name** and **player name** from the URL parameters.
2. Defines a fixed **start-of-season date** (`2024-02-16`).
3. Retrieves the **current date** dynamically.
4. Constructs a **permanent redirect URL** in the format:

```
/the-eye/player/{teamName}/{playerName}/stats/{startDate}/{endDate}
```

5. Uses `permanentRedirect()` from `next/navigation` to **automatically reroute** users to the correct stats page.

## Example Usage

This page is accessed dynamically through the app's routing system:

```
/the-eye/player/{teamName}/{playerName}/stats
```

For example:

```
/the-eye/player/AUB_TIG/John_Doe/stats
```

This would **automatically redirect** the user to:

```
/the-eye/player/AUB_TIG/John_Doe/stats/2024-02-16/2024-04-25
```

Where `2024-02-16` is the **start of the season**, and `2024-04-25` is the **current date**.

This ensures proper functionality when accessing player stats without requiring the user to manually enter date parameters.

