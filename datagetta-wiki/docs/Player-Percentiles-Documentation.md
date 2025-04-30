## 📊 Player Percentiles Page – Documentation

**Author:** Liam Maher  
**Last Modified:** 05/11/2025

---

### 🔍 Overview

The **Percentiles Page** displays statistical performance percentiles for individual pitchers based on **pitch type** and **season year** (currently 2024 and 2025). It dynamically pulls data from PostgreSQL views and presents the results visually using Material UI progress bars.

This page is designed to support **interactive filtering** via a dropdown menu and dynamically swaps between `pitcher_percentiles_by_pitchtype_2024` and `pitcher_percentiles_by_pitchtype_2025`.

---

### ⚙️ Core Components

#### ✅ `CreatePlayerPercent.tsx`
- Server component that:
  - Accepts `playerName`, `pitchType`, and `year` as props.
  - Dynamically selects the correct SQL view:
    ```ts
    const viewName = `pitcher_percentiles_by_pitchtype_${year}`;
    ```
  - Fetches data with parameterized queries using Prisma.
  - Validates `year` to prevent injection or invalid data access.
  - Renders a styled progress bar chart for each stat.

#### ✅ `FilterDropdowns.tsx`
- Client-side dropdown component for:
  - Pitch type (`Fastball`, `Slider`, etc.)
  - Year (`2024`, `2025`)
- Syncs selection to URL query parameters using `useRouter()` and `useSearchParams()`.

#### ✅ `page.tsx`
- Reads search parameters and passes them as props.
- Displays both the dropdowns and the stat bar chart.

#### ✅ `layout.tsx`
- Applies page padding and MUI theming layout across the player profile view.

---

### 📆 Season-Specific Views (2024 and 2025)

Currently, PostgreSQL views such as `pitcher_percentiles_by_pitchtype_2024` and `pitcher_percentiles_by_pitchtype_2025` are created **manually** each season.

Each view:
- Filters all data to just that season (using `seasons` table join on `SeasonTitle`)
- Computes:
  - `FIP`
  - `K %`
  - `BB %`
  - `Chase %`
  - `Velocity %`
  - `Induced Vertical Break`
  - `Horizontal Break`
- Groups by both **pitcher** and **pitch type**
- Applies `PERCENT_RANK()` to calculate percentile for each metric

#### 🔮 Future Suggestion: Automate View Generation
To reduce maintenance effort:
- Consider creating a **parameterized materialized view** or
- Build a **season-agnostic view** that includes a `year` column and filters in the app layer

---