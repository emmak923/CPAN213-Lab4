# Responsive Dashboard App - Lab 4

## Student Information

- **Name:** Ema Maeda
- **Student ID:** N01678730
- **Course:** CPAN 213
- **Lab:** Lab 4 - Responsive Layouts with Flexbox
- **Date:** October 16, 2025

## Project Description

This responsive dashboard application demonstrates advanced Flexbox layout techniques,
responsive design patterns, and platform-specific styling in React Native.

## Features Implemented

- Responsive grid system with breakpoint detection
- Dashboard widgets with statistics and trends
- Orientation-aware layouts
- Platform-specific styling (iOS/Android)
- Pull-to-refresh functionality
- Performance-optimized StyleSheets

## Technologies Used

- React Native 0.72+
- React Native Orientation Locker
- React Native Vector Icons
- Platform-specific APIs

## Installation

1. Clone the repository
2. Install dependencies: `npm install`
3. Install iOS pods (macOS only): `cd ios && pod install`
4. Run on Android: `npx react-native run-android`
5. Run on iOS: `npx react-native run-ios`

## Project Structure

src/  
 ├── components/  
 │ ├── DashboardHeader.js  
 │ ├── ResponsiveGrid.js  
 │ └── widgets/  
 │ ├── BaseWidget.js  
 │ └── StatisticWidget.js  
 ├── screens/  
 │ └── DashboardScreen.js  
 ├── styles/  
 │ └── theme.js  
 └── utils/
└── responsive.js

## Responsive Breakpoints

- Small phones: < 350px
- Medium phones: 350-400px
- Large phones: 400-500px
- Tablets: 500-805px
- Large tablets/Desktop: > 805px

## Grid Columns by Device

- Small: 1 column
- Medium: 2 columns
- Tablet Portrait: 2 columns
- Tablet Landscape: 4 columns

## Performance Notes

- All animations run at 60fps
- StyleSheet.create used for all styles
- Memoization applied where necessary
- Native driver enabled for animations

## Screenshots

See `/screenshots` folder for app images on different devices.

## Known Issues

- Layout Fillers in ResponsiveGrid: The ResponsiveGrid uses empty <View> elements as placeholders to ensure the last row remains visually aligned and evenly spaced when the number of items is less than the calculated column count.
- Platform Shadow Inconsistency: The theme system uses Platform.select to implement shadows via shadowColor/Offset/Opacity/Radius on iOS and elevation on Android.
- Orientation Change Flash: When quickly rotating the device, a brief flicker or minor layout jump can occasionally be observed as the Dimensions API updates, the grid columns recalculate, and the entire screen re-renders to adjust for the new aspect ratio.
- Unnecessary Component Re-renders: Although React.memo has been applied to reusable components, unnecessary re-renders occur when the parent component (DashboardScreen) updates its state (pull-to-refresh or orientation change). This is due to the reference instability of function props like renderItem or re-created data arrays during state updates, even when content is functionally unchanged.

## Future Enhancements

- Dynamic Widget Customization: Implement user controls to allow the showing/hiding of widgets and support drag-to-reorder functionality. Persist these layout preferences using local storage.

- Advanced Data Visualization: Introduce Chart Widgets (e.g., bar charts and line charts) to display time-series data and trends more effectively , ensuring they also adhere to the responsive sizing rules.

- Dark Mode Implementation: Extend the theme.js color palette to include a dark color scheme and implement a global context to manage theme switching.

- Render Optimization & UX: Apply useMemo to stabilize non-primitive values (objects/arrays) passed as props to further enhance re-render performance.
