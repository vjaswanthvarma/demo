# LessonActivityContent Component

The `LessonActivityContent` component is a React functional component that serves as a core part of an educational platform. It handles the display of lesson content, progress tracking, and activity navigation for users.

---

## Description
This component dynamically fetches and renders lesson data for a course. It integrates with Redux for state management and React Router for routing. It provides:
- A progress bar showing course completion.
- A detailed lesson content display.
- Navigation for non-quiz activities.

---

## Props
This component does not directly accept props. Instead, it relies on Redux state and React Router parameters.

| Prop           | Description                     | Type    |
|----------------|---------------------------------|---------|
| N/A            | This component uses context/state hooks instead of props. | N/A     |

---

## Components Used
The `LessonActivityContent` component uses the following components:

| Component              | Description                                |
|------------------------|--------------------------------------------|
| `ProgressBar`          | Displays the user's progress in the course. |
| `Question`             | Renders the main lesson content for the current activity. |
| `ActivityNavigation`   | Provides navigation controls for non-quiz activities. |
| `Loading`              | Displays a loading indicator while data is being fetched. |
| `NotFound`             | Displays an error message if course or lesson data cannot be loaded. |

---

## Dependencies
This component uses the following dependencies:

- **React**: For component structure and lifecycle methods.
- **Redux**: For global state management (`useAppDispatch`, `useAppSelector`).
- **React Router**: For URL-based routing and parameter extraction (`useParams`).
- **Tailwind CSS**: For responsive and dark-mode-friendly styling.
- **Custom Hooks**:
  - `useSessionData`: Retrieves session-specific information.
  - `useBreadCrumbContext`: Updates the breadcrumb navigation.

---

## Example Usage
Include this component in your app's routing structure:
```jsx
<Route path="/courses/:courseId/chapters/:chapterId" element={<LessonActivityContent />} />

   
