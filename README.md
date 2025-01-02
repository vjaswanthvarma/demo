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
``` #mermaid
LessonActivityContent
├── useEffect 1: Fetch course and lesson data
├── useEffect 2: Update breadcrumbs and sidebar
├── Conditional Rendering:
│   ├── Loading spinner if data is being fetched
│   └── Main UI (ProgressBar, Question, Navigation)
└── Cleanup: Reset sidebar when component unmounts
graph TD
    A[LessonActivityContent] -->|Dispatches| B[setSidebar("activity")]
    A -->|Fetches| C[Course Data]
    A -->|Fetches| D[Lesson Data]
    C -->|API Call| E[getCourseById]
    D -->|API Call| F[getLessonById]
    E -->|Updates| G[Redux: setCourse]
    F -->|Updates| H[Redux: setLesson]

    A -->|Checks| I[Status: "idle" or "loading"]
    I -->|Renders| J[Loading Component]
    I -->|Else| K[Render Main Content]

    K -->|Renders| L[ProgressBar]
    K -->|Renders| M[Question Component]
    K -->|Conditional Render| N[ActivityNavigation]

    subgraph UI Rendering
        B -->|Updates| O[Global Sidebar State]
        L -->|Updates| P[Progress Bar UI]
        M -->|Displays| Q[Lesson Content]
        N -->|Navigates| R[Next/Previous Activities]
    end

    subgraph Error Handling
        A -->|Handles Errors| S[NotFound Component]
    end


   
