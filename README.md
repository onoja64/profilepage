# Documentation for Next.js Home Component

## Overview

The `Home` component is the main entry point of a Next.js web application for a product catalog. It serves as the landing page, displaying a header with branding, a background image, business statistics, a tabbed navigation view, and a fixed bottom navigation bar. The component includes a loading state to simulate data fetching and integrates with other components like `TabView`, `ProductsPage`, and `LoadingSpinner`. Styling is handled using Tailwind CSS.

## File Path

- **`Home.js`**: Located at the root of the Next.js project (likely in `pages/index.js` or a similar entry point).

## Dependencies

- **Next.js Components**:
  - `Image`: For optimized image rendering (`next/image`).
- **React Hooks**:
  - `useState`, `useEffect`: For managing state and side effects.
- **Custom Components**:
  - `TabView`: Renders tabbed navigation for sections like "Overview," "Products," etc.
  - `ProductsPage`: Displays product catalog details within the "Products" tab.
  - `LoadingSpinner`: Displays a loading animation during the initial loading state.
- **Assets**:
  - Images in `/public/assets/` (e.g., `back.svg`, `whatsapp.svg`, `cover.png`, `kmglogo.png`, `check.png`, `pro.png`, `dot.png`, `favorite.png`, `contact.png`).

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
  - Displays back and WhatsApp icons flanking the "KMGRobust" title using `flex`, `gap-[95px]`, `items-center`, and `justify-center`.
- **Cover Section**:
  - A background image (`cover.png`) with a logo (`kmglogo.png`) overlay, styled with `bg-cover`, `bg-no-repeat`, `bg-center`, `h-[150px]`, and `flex items-bottom justify-bottom`.
- **Business Stats**:
  - Text stats ("24M Revenue," "1-10 Employees," "15 Years Old") separated by dot icons, styled with `flex`, `gap-2`, `items-center`, `text-[12px]`, `text-gray-500`, `font-bold`, and `pl-10`.
- **Tabbed Navigation**:
  - Uses `TabView` to render tabs for different sections.
- **Bottom Navigation**:
  - A fixed bar with "Favorite" and "Contact" icons, styled with `fixed`, `bottom-0`, `left-0`, `right-0`, `flex-row`, `justify-around`, `items-center`, `h-[70px]`, `bg-white`, `border-t`, and `border-gray-200`.

## Styling Approach

- **Tailwind CSS**:
  - The component uses Tailwind CSS utility classes for styling.
  - Key classes include:
    - `bg-white`: White background for the main container.
    - `flex gap-[95px] items-center justify-center`: Flex layout for the header with a 95px gap.
    - `text-[14px] font-extrabold`: Text styling for the "KMGRobust" title.
    - `bg-cover bg-no-repeat bg-center h-[150px]`: Background image styling for the cover section.
    - `w-[90px] h-[90px] mt-[7rem] ml-[1rem] border-rounded-full`: Logo styling.
    - `text-[20px] font-extrabold pl-10`: Styling for the "KMG Robu" heading.
    - `text-[12px] text-gray-500 font-bold`: Styling for business stats.
    - `fixed bottom-0 left-0 right-0`: Fixed positioning for the bottom navigation bar.
    - `flex-row justify-around items-center h-[70px] bg-white border-t border-gray-200`: Bottom navigation bar layout and styling.

## How to Run

1. **Install Dependencies**:
   ```bash
   npm install
   ```
2. **Run**:
   ```bash
   npm run dev
   ```
