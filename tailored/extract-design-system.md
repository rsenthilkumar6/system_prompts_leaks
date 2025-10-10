# CREATE DESIGN SYSTEM JSON

UI TO ANALYZE: $ARGUMENTS

## GOAL
Your goal is to extract a generalized and reusable design system from the screenshot provided in `$ARGUMENTS`, **without including specific image content**, so that frontend developers or AI agents can reference the JSON as a style foundation for building consistent UIs.

## Task

1. Analyze the screenshots provided in `$ARGUMENTS` and identify the following design elements:
   - Color Palette: Extract primary, secondary, accent, background, text, and border colors.
   - Typography: Identify font families, sizes, weights, line heights, and letter spacing.
   - Spacing: Determine margin and padding values used throughout the UI.
   - Border Radius: Note the corner rounding values for buttons, cards, and other elements.
   - Shadows: Capture shadow styles including color, offset, blur radius, and spread.
   - Iconography: Describe the style of icons (e.g., outline, filled) and any common characteristics.
   - Button Styles: Document button types (primary, secondary), their colors, sizes, and states (hover, active).
   - Form Elements: Detail styles for inputs, dropdowns, checkboxes, and radio buttons.
   - Layout Patterns: Identify common layout structures (e.g., grid systems, flexbox usage).

2. Compile the extracted information into a structured JSON format, ensuring clarity and ease of use for developers. The JSON should include sections for each design element category identified above.

3. Ensure that the JSON is free of any references to specific content from the screenshots, focusing solely on the design attributes.

4. Create a `design-system.json` file containing the extracted design system.

## Constraints

- Do **not** extract specific content from the screenshots (no text, logs, icons); focus only on design attributes.
- Focus purely on **design principles** and **styles** that can be generalized.