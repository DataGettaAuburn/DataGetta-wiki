# HeatMap - Pitching Heat Map Visualization

This folder contains components used to **generate and display heat maps** for a pitcher’s pitch locations and effectiveness.

## Structure

- **`CreateHeatMaps.tsx`** - Queries data from the database and generates heat maps for different pitch types.
- **`HeatMap.tsx`** - Dynamically creates SVG-based heat maps by assigning colors to pitch zones.
- **`PitchTypeHeatMap.tsx`** - Displays heat maps for different pitch types and organizes them into a visual grid.

## Component Details

### `CreateHeatMaps.tsx`
- **Purpose**: Fetches pitch data from the database and renders heat maps for various pitch types.
- **Key Features**:
  - Uses **Prisma ORM** to query pitch data.
  - Supports multiple pitch types: Fastball, Slider, Changeup, etc.
  - Passes formatted data to `PitchTypeHeatMap.tsx` for rendering.

### `HeatMap.tsx`
- **Purpose**: Renders a **heat map SVG** representing pitch density and effectiveness.
- **Key Features**:
  - Uses color blending to visually differentiate pitch success and density.
  - Defines **strike-zone boundaries** to overlay on the heat map.
  - Dynamically positions each pitch in a **16x20 grid**.
  - Uses **RGB color blending** to adjust heat intensity.

### `PitchTypeHeatMap.tsx`
- **Purpose**: Displays **heat maps** for a specific pitch type (e.g., Fastball, Slider, etc.).
- **Key Features**:
  - Accepts `heatmap` data from `CreateHeatMaps.tsx`.
  - Renders three heat maps per pitch type:
    - **All Pitches**
    - **Successful Pitches**
    - **Pitch Ratio**
  - Organizes maps into a structured grid using **Material UI `Grid`**.
  - Displays a **title and separator** for each pitch type.

## Usage

These components work together to visualize **pitching tendencies** and provide insights into a pitcher’s effectiveness.

Example usage:
```tsx
<CreateHeatMaps player="John_Doe" team="AUB_TIG" />
```

This will generate heat maps for **John Doe** from **Auburn Tigers** and visualize how he pitches across different zones.