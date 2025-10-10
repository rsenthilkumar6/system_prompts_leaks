### Generic rules:

* For Admin Portal-style applications, use a hierarchical layout system. A root layout must house global components (side nav, header), while child screens populate the dynamic content area.
* **Mandatory states**: Every component and page must manage loading, error, and empty conditions.
* **Standardize these core screens**: an authentication suite (login, signup, password reset), a user profile manager (with avatar sync), and an app settings page (for theme and data clearance).
* **Decouple grid rendering**: Create separate grid components that receive data via props, isolating presentation from data management.
* Build a standardized **component library** with reusable UI elements (buttons, toasts, labels) that inherit styling from global theme files. Use these components consistently across all pages, avoiding inline styles.

### UX/UI Technical Specifications:
* Choose a 4 pt or 8 pt spacing system for margins, padding, line-heights, and element sizes must be exact multiples.
* **Use consistent spacing tokens** (e.g., 4, 8, 16, 24 32px) - never arbitrary values like 5 px or 13 px.
* Apply visual grouping ("spacing friendship"): tighter gaps (4-8px) for related items, larger gaps (16-24px) for distinct groups.
* **Ensure typographic rhythm**: font-size, line-heighs, and spacing aligned to the grid (e.g., 16 px text with 24 px line-height).
* **Maintain touch-area accessibility**: buttons and controls should meet or exceed 48x48 px, padded using grid units.

### Specific to Flutter Project:

* When creating flutter project always use **--org com.ns**
* remove all the comments from **pubspec.yaml** 
* update the **analysis_options.yaml** with below default options

```yaml
include: package:flutter_lints/flutter.yaml

dartfmt:
  trailing-comma: always
  wrap-simple-functions: true

dart_style:
  use_trailing_commas: true

linter:
  rules:
    require_trailing_commas: true

formatter:
  trailing_commas: preserve
  page_width: 80

analyzer:
  errors:
    invalid_annotation_target: ignore

exclude:
  - "**/*.g.dart"
  - "**/*.freezed.dart"
  - "**/ffigen.yaml"
  - "**/pubspec.yaml"
  - "**/native/**"
```

* create **.vscode/settings.json** file with below default configuration

```json
{
    "editor.formatOnSave": true,
    "[dart]": {
        "editor.formatOnSave": true,
    },
}
```

* Always ensure **main.dart** file has `WidgetsFlutterBinding.ensureInitialized();` and if any initialization or loading logic is required use **microtask** to for them.
* Aim for separation of concerns similar to MVC/MVVM, with defined Model, View, and ViewModel/Controller roles; Model will be a Freezed annoted class, View can be a Stateless/Stateful/Hooks/Consumer widget and ViewMode/Controller will be Riverpod annotated class.
* UI files should not exceed 200-300 lines.
  - Break files using part and part of.
  - Only one class per file.
  - No single function should exceed 30-50 lines. Refactor into smaller helpers if needed.
  - Use small, private Widget classes instead of private helper methods that return a Widget.
  - Break down large build() methods into smaller, reusable private Widget classes.
* For image place holders use **https://placehold.co/600x400** with **NetworkImage** providers

## Theming
- Define a centralized ThemeData object to ensure a consistent application-wide style.
- Use Material 3 by setting useMaterial3: true in your ThemeData.
- Implement support for both light and dark themes, ideal for a user-facing theme toggle (ThemeMode.light, ThemeMode.dark, ThemeMode.system).
- Generate harmonious color palettes from a single color using ColorScheme.fromSeed.

```dart
final ThemeData lightTheme = ThemeData(
  useMaterial3: true,
  colorScheme: ColorScheme.fromSeed(
    seedColor: Colors.deepPurple,
    brightness: Brightness.light,
  ),
  // ... other theme properties
);
```

- Include a wide range of color concentrations and hues in the palette to create a vibrant and energetic look and feel.
- Use specific theme properties (e.g., appBarTheme, elevatedButtonTheme) to customize the appearance of individual Material components.
- For custom fonts, use the google_fonts package. Define a TextTheme to apply fonts consistently.

```dart
// 1. Add the dependency
// flutter pub add google_fonts

// 2. Define a TextTheme with a custom font
final TextTheme appTextTheme = TextTheme(
  displayLarge: GoogleFonts.oswald(fontSize: 57, fontWeight: FontWeight.bold),
  titleLarge: GoogleFonts.roboto(fontSize: 22, fontWeight: FontWeight.w500),
  bodyMedium: GoogleFonts.openSans(fontSize: 14),
);
```