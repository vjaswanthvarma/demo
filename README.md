# LessonActivityContent Component

## Description
The `LessonActivityContent` component dynamically renders lesson content for an educational platform. It handles fetching and managing data for courses and lessons, updating UI components, and integrating with global application states.

This component is designed to:
- Fetch course and lesson data from APIs.
- Display activity details such as progress and lesson content.
- Handle navigation between activities.
- Update the application's breadcrumbs and sidebar state.

---

## Props
This component does not take explicit props but relies on:
- **Redux state** for session and activity details.
- **React Router parameters** for course and chapter IDs.
- **Custom Hooks** for session data and breadcrumb management.

---

## Dependencies
Below are the dependencies used by the `LessonActivityContent` component:

| Dependency        | Description                                   |
|-------------------|-----------------------------------------------|
| `ProgressBar`     | Displays the progress of course completion.  |
| `useAppDispatch`  | Dispatches actions to Redux.                 |
| `useAppSelector`  | Accesses state from Redux.                   |
| `useBreadCrumbContext` | Manages breadcrumbs.                     |
| `useSessionData`  | Fetches session-specific data.               |
| `NotFound`        | Displays an error page when data isn't found.|
| `Loading`         | Renders a spinner while fetching data.       |
| `Question`        | Renders lesson content.                      |
| `ActivityNavigation` | Handles navigation between activities.    |

---

## Features
1. **Dynamic Data Fetching**:
   - Fetches course and lesson details using APIs: `getCourseById` and `getLessonById`.
   - Updates Redux with the fetched data using `setCourse` and `setLesson`.

2. **State Management**:
   - Updates Redux for global (`setSidebar`, `setBreadcrumb`) and session states.

3. **UI Components**:
   - Displays progress with `ProgressBar`.
   - Shows loading or error states (`Loading`, `NotFound`).
   - Renders lesson content using the `Question` component.

4. **Responsive Design**:
   - Layout adapts to various screen sizes using Tailwind CSS.
   - Supports dark mode.

5. **Navigation**:
   - Provides navigation for non-quiz activities with `ActivityNavigation`.

---

## Code Overview
```mermaid
flowchart TD
    A[Component Mount] --> B{Course Exists?}
    B -->|No| C[Fetch Course Data]
    B -->|Yes| D{Entity Exists?}
    
    C --> E[Update Redux Store with Course]
    E --> D
    
    D -->|No| F[Fetch Lesson Data]
    D -->|Yes| G[Setup Side Effects]
    
    F --> H[Update Redux Store with Lesson]
    H --> G
    
    G --> I[Set Sidebar to 'activity']
    G --> J[Update Breadcrumbs]
    
    K[Component Render] --> L{Check Status}
    L -->|idle/loading| M[Show Loading]
    L -->|ready| N[Render Content]
    
    N --> O[Header with Progress]
    N --> P[Question Component]
    N --> Q{Is Quiz?}
    Q -->|No| R[Activity Navigation]
    Q -->|Yes| S[No Navigation]
    
    T[Component Unmount] --> U[Reset Sidebar to 'global']
