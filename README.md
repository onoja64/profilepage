# Documentation for React Native Home Component

## Overview

The `Home` component is the main entry point of a React Native product catalog application, converted from a Next.js web application. It serves as the landing page, displaying a header with branding, a background image, business statistics, a tabbed navigation view, and a fixed bottom navigation bar. The component includes a loading state to simulate data fetching and integrates with other components like `TabView`, `ProductsPage`, and `LoadingSpinner`.

## File Path

- **`Home.js`**: Located at the root of the project, this file contains the `Home` component.

## Dependencies

- **React Native Components**:
  - `View`, `Text`, `Image`, `StyleSheet`, `ScrollView` (assumed for conversion).
- **Custom Components**:
  - `TabView`: Renders tabbed navigation for sections like "Overview," "Products," etc.
  - `ProductsPage`: Displays product catalog details within the "Products" tab.
  - `LoadingSpinner`: Displays a loading animation during the initial loading state.
- **Assets**:
  - Images in `../assets/` (e.g., `back.png`, `whatsapp.png`, `cover.png`, `kmglogo.png`, `check.png`, `pro.png`, `dot.png`, `favorite.png`, `contact.png`).

## Component Structure

### Home

- **Purpose**: Acts as the main landing page, orchestrating the app's primary UI elements and navigation.
- **Props**:
  - None (standalone component).
- **State**:
  - `isLoading`: Boolean to manage the loading state (initially `true`, set to `false` after 3 seconds).
- **Features**:
  - Displays a loading spinner (`LoadingSpinner`) for 3 seconds on initial load.
  - Renders a header with back and WhatsApp icons, and the "KMGRobust" title.
  - Shows a background cover image with a logo overlay.
  - Displays business stats (e.g., "24M Revenue," "1-10 Employees," "15 Years Old").
  - Integrates `TabView` for tabbed navigation with predefined tabs ("Overview," "Products," "Posts," "Certificates," "Representatives").
  - Includes a fixed bottom navigation bar with "Favorite" and "Contact" actions.
- **Dependencies**:
  - `TabView`, `ProductsPage`, `LoadingSpinner`.
  - Assets for icons and background images.

## Code Breakdown

### State and Effects

- **State**:
  - `isLoading`: Controls the visibility of the `LoadingSpinner`. Set to `false` after a 3-second delay to simulate data fetching.
- **Effects**:
  - A `useEffect` hook sets a timer to toggle `isLoading` after 3 seconds and clears the timer on component unmount.

### Tabs Configuration

- **Tabs Array**:
  - An array of tab objects (`id`, `title`, `content`) used by `TabView`:
    - `"overview"`: Static content with a heading and paragraph.
    - `"products"`: Renders the `ProductsPage` component.
    - `"posts"`, `"certificates"`, `"representatives"`: Static content with headings and paragraphs.

### UI Elements

- **Header**:
  - Displays back and WhatsApp icons flanking the "KMGRobust" title.
- **Cover Section**:
  - A background image (`cover.png`) with a logo (`kmglogo.png`) overlay.
- **Business Stats**:
  - Text stats ("24M Revenue," "1-10 Employees," "15 Years Old") separated by dot icons.
- **Tabbed Navigation**:
  - Uses `TabView` to render tabs for different sections.
- **Bottom Navigation**:
  - A fixed bar with "Favorite" and "Contact" icons for quick actions.

## Styling Approach

- **Conversion from Tailwind CSS**:
  - Tailwind classes (e.g., `bg-white`, `flex`, `gap-[95px]`, `p-4`, `rounded-lg`) are converted to React Native `StyleSheet` styles (assumed in conversion).
  - Example mappings:
    - `bg-white` → `backgroundColor: "#FFF"`.
    - `flex gap-[95px]` → `flexDirection: "row"`, `gap: 95`.
    - `p-4` → `padding: 16` (4 units ≈ 16px).
    - `rounded-lg` → `borderRadius: 8`.
    - `bg-cover bg-no-repeat bg-center` → `resizeMode: "cover"`.
    - `fixed bottom-0 left-0 right-0` → `position: "absolute"`, `bottom: 0`, `left: 0`, `right: 0`.
- **Layout**:
  - Uses `flexDirection: "row"` for horizontal layouts (e.g., header, stats).
  - Fixed bottom navigation with `position: "absolute"`.

## Limitations

- **SVGs**: The original web version uses SVGs (e.g., `back.svg`, `whatsapp.svg`). In React Native, these are assumed to be converted to PNGs (e.g., `back.png`). Use `react-native-svg` for SVG support if needed.
- **Background Image**:
  - React Native doesn’t support `style={{ backgroundImage: "url(...)" }}`. Use an `<ImageBackground>` component instead.
- **Performance**:
  - The loading state is simulated with a fixed 3-second delay. For real data fetching, replace with an API call.

## Debugging Tips

- **Loading State**:
  - Verify the `isLoading` state toggles correctly after 3 seconds.
  - Check if `LoadingSpinner` renders and disappears as expected.
- **Images Not Loading**:
  - Ensure image paths are correct (e.g., `../assets/back.png`).
  - Add `onError` to debug:
    ```javascript
    <Image
      source={require("../assets/back.png")}
      onError={(e) => console.log("Error:", e.nativeEvent.error)}
    />
    ```
  - Clear Metro cache: `npx react-native start --reset-cache`.
- **TabView Issues**:
  - Ensure `TabView` receives the `tabs` array correctly.
  - Check if `ProductsPage` renders within the "Products" tab.

## How to Run

1. **Install Dependencies**:
   ```bash
   npm install
   ```
2. **Run**:
   ```bash
   npm run dev
   ```
