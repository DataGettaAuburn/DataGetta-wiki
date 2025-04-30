# Defensive Shift Model - Player Positioning Analysis

This folder contains components that **visualize defensive shifts** for various pitch types. These models help analyze how defensive positioning affects play outcomes based on pitch selection and batter handedness.

## Structure

- **Shift Model Generation**:
  - `CreateShiftingModels.tsx` - Queries shift model data and generates visualizations.
  - `PitchTypeShiftModel.tsx` - Generates defensive shift SVGs for different pitch types.
  - `ShiftingModel.tsx` - Creates the actual SVG-based defensive shift heatmap.

---

## Component Details

### `CreateShiftingModels.tsx`
- **Purpose**: Fetches **defensive shift model data** for different pitch types and sends them to the visualization components.
- **Key Features**:
  - Uses **Prisma ORM** to query shift data from the database.
  - Retrieves **model values** for multiple pitch types (Fastball, Sinker, Changeup, Slider, Curveball, Cutter, Splitter).
  - Converts queried data to JSON before passing it to `PitchTypeShiftModel.tsx`.

### `PitchTypeShiftModel.tsx`
- **Purpose**: Takes queried shift model data and renders **SVG-based defensive shifts**.
- **Key Features**:
  - Displays **left-side** and **right-side** defensive shift visualizations.
  - Generates a label for each pitch type.
  - Uses **MUI Grid layout** to structure visuals.
  - If no data exists for a pitch type, it returns an empty component.

### `ShiftingModel.tsx`
- **Purpose**: Creates **color-coded heatmaps** to represent defensive shifts.
- **Key Features**:
  - Uses **Auburn’s branding colors**:
    - **Navy Blue** for outfield shift intensity.
    - **Orange** for infield shift intensity.
  - Dynamically adjusts shading based on shift percentages.
  - Uses SVG **polygon fills** to render defensive positions.
  - Displays percentage values inside each shift region.

---

## Usage

These components generate **defensive shift insights** to analyze player positioning based on pitch selection.

Example usage:
```tsx
<CreateShiftingModels player="John_Doe" team="AUB_TIG" />
```

This will:
- Fetch **John Doe’s** shift data.
- Generate **shift models** for different pitch types.
- Display **color-coded** defensive alignment to highlight strategic positioning.

This tool is useful for **coaches and analysts** to determine how fielders should adjust based on pitcher tendencies and batter matchups.

