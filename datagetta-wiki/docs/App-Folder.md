# App Folder

The `app/` folder serves as the root directory for the Next.js application, containing the foundational layout and landing page.

## Structure
- `the-eye/` - The main application logic and UI components.
- `utils/` - Utility functions, theming, database connections, and type definitions.
- `layout.tsx` - Defines the global layout, including Material UI theming.
- `page.tsx` - The landing page for the application.

---

## File Descriptions

### `layout.tsx`
- **Purpose**: Acts as the **root layout** for the application.
- **Key Features**:
  - Uses **Material UI** for styling.
  - Integrates **Next.js App Router caching** for performance.
  - Applies **global theming** from `utils/theme.ts`.
  - Includes **CSS Baseline** for consistent styles.

### `page.tsx`
- **Purpose**: The **landing page** for the app, located at `https://datagetta.app`.
- **Key Features**:
  - Displays an **animated background** using `lineAnimation.gif`.
  - Shows the **app title (DATA GETTA)** in Auburn colors.
  - Provides a **Login button** that redirects users to `/the-eye/`.
  - Uses **Material UI components** for styling.

---

## Summary
The `app/` folder contains the **core layout and landing page** for the application, ensuring that global styles, themes, and performance optimizations are applied consistently throughout the project.

