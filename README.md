# LessonActivityContent Component

The `LessonActivityContent` component is part of an educational platform. It handles the rendering of lesson content for students, including progress tracking, lesson details, navigation, and dynamic data fetching.

## Features
- Fetches course and lesson data from the API.
- Displays the current lesson's content and activity.
- Tracks and displays course progress using a progress bar.
- Provides navigation for non-quiz activities.
- Dynamically updates breadcrumbs for better navigation context.

## Dependencies
The component relies on several third-party libraries and internal modules:

### External Libraries
- **React**: For component-based architecture and hooks.
- **Redux**: For state management (e.g., `useAppDispatch`, `useAppSelector`).
- **React Router**: For routing (`useParams`).
- **katex**: For rendering mathematical formulas (CSS file included).
- **UI Components**: Custom shared components such as `ProgressBar`, `Loading`, and `NotFound`.

### Internal Modules
- **Hooks**: Custom hooks like `useSessionData` and `useBreadCrumbContext`.
- **Redux Slices**: Global and session state management slices (`setSidebar`, `setBreadcrumb`, etc.).
- **API Calls**: Utility functions to fetch course and lesson data (`getCourseById`, `getLessonById`).
- **Components**: Nested components like `Question` and `ActivityNavigation`.

## Setup
1. **Install Dependencies**  
   Ensure all required libraries are installed:
   ```bash
   npm install
