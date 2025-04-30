# Components - The Eye

This folder contains reusable UI components used throughout the application. These components help ensure consistency and modularity across the interface.

## Structure

- **`assets/`** - Contains SVG assets used in the UI, including logos.
- **`ConferenceTable.tsx`** - Displays conference and team information with links to team pages.
- **`DesktopSideBar.tsx`** - Sidebar for desktop views.
- **`MobileSideBar.tsx`** - Sidebar optimized for mobile devices.
- **`TabGroup.tsx`** - Combines the logo and navigation tabs.
- **`Tabs.tsx`** - Handles individual tab components used in sidebars.
- **`TopBar.tsx`** - Renders the top navigation bar, including a future search bar.
- **`UI_Layout.tsx`** - Combines layout components and manages mobile menu behavior.

## Component Details

### `ConferenceTable.tsx`
- Displays a table of teams within a conference.
- Each team is a clickable link that navigates to its team page.
- Uses Material UI's `Table`, `TableCell`, and `Typography` for styling.

### `DesktopSideBar.tsx`
- Permanent sidebar visible only on desktop screens (`lg` and up).
- Uses Material UI's `Drawer` component for structure.
- Contains `TabGroup.tsx` for navigation tabs.

### `MobileSideBar.tsx`
- Temporary sidebar optimized for mobile screens.
- Toggles open/close state based on user interaction.
- Uses `Drawer` component with an overlay effect.
- Contains `TabGroup.tsx` for navigation.

### `TabGroup.tsx`
- Displays The Eye logo at the top.
- Contains `Tabs.tsx` for navigation.
- Clicking the logo navigates back to the home page (`/the-eye`).

### `Tabs.tsx`
- Defines sidebar navigation items.
- Contains hardcoded links for Auburn's team page and general teams list.
- Uses Material UI’s `List`, `ListItemButton`, and `ListItemText`.

### `TopBar.tsx`
- Displays the top navigation bar.
- Contains a **menu button** for opening the mobile sidebar.
- Will eventually include a **search bar**.
- Uses Material UI’s `AppBar`, `Toolbar`, and `IconButton`.

### `UI_Layout.tsx`
- Wraps all layout components together.
- Manages mobile menu state and transitions.
- Uses `useState` to control sidebar toggle behavior.

## Usage

Each component is designed to be imported and used across different sections of the app to maintain consistency in styling and behavior.

Example usage:
```tsx
import ConferenceTable from "../components/ConferenceTable";

<ConferenceTable name="SEC" teams={[{ TeamName: "Auburn", DisplayName: "Auburn Tigers" }]} />
```

For more details on a specific component, refer to its file directly.

