# Project 

## Overview

`Project` is a React functional component designed to render a customizable and interactive dashboard. This dashboard is comprised of several draggable and droppable widgets, each representing different aspects of a patient management system such as tasks, screenings, vitals, and more.

## Features

- **Drag-and-Drop Functionality**: Allows users to rearrange dashboard widgets to suit their preferences using `react-beautiful-dnd`.
- **Minimizable Documentation**: Each widget can potentially contain documentation that is minimizable.
- **Responsive Design**: Widgets rearrange themselves to fit different screen sizes.
- **User Guidance**: A tooltip provides users with instructions on how to interact with the page.

## Structure

- `DragDropContext`: A context provider from `react-beautiful-dnd` that enables drag-and-drop functionality for its child components.
- `Droppable`: A droppable area where draggable components can be placed.
- `Draggable`: Each widget that can be dragged and dropped within the `Droppable` area.
- `Grid`: An MUI component that creates a responsive layout grid for the widgets.
- `Paper`: An MUI component that serves as a surface for each widget, giving it an elevation effect.

## State Management

The component's state is managed using the `useState` hook:

- `components`: An array of objects, each representing a widget. Each widget object contains an `id` and a `Component`.

The `useCallback` hook is used for the `onDragEnd` event handler to improve performance by memoizing the function.

## Event Handlers

- `onDragEnd`: A callback function that updates the order of the widgets when they are dragged and dropped.

## Dependencies

- **Material-UI** (`@mui/material`): Provides the UI components used in the dashboard.
- **React Beautiful DnD** (`react-beautiful-dnd`): Provides the drag-and-drop functionality.
- **Material Icons** (`@mui/icons-material`): Provides the help icon used in the guidance tooltip.


--- 


# Conditions Component 

## Overview

The `Conditions` component is designed to manage and display health conditions and patient education in an interactive format. It leverages React's functional component architecture, along with hooks for state management, to offer a dynamic user experience. The component features expandable accordions for health conditions, tabbed interfaces for patient education, and a dialog modal for note-taking functionalities.

## Features

- **Interactive Accordions**: Utilize for detailed presentation of health conditions, allowing users to expand or collapse information as needed.
- **Tabbed Interface for Patient Education**: Facilitates easy navigation through educational material organized into distinct tabs.
- **Note-taking Dialog Modal**: Enables users to add personalized notes for each condition, enhancing the customizability of patient care plans.

## State Management

This component makes use of React's `useState` hook to manage component state, including:
- `tabValue`: Controls the active tab within the patient education section.
- `open`: Toggles the visibility of the dialog used for adding notes.
- `note`: Holds the input value for the user's note.

## Event Handlers

The component integrates several event handlers to manage user interactions:
- `handleTabChange`: Updates the active tab state upon user interaction.
- `handleClickOpen`: Triggers the display of the note-taking dialog.
- `handleClose`: Closes the note-taking dialog without saving the note.
- `handleSave`: Stores the note input by the user and closes the dialog.

## Component Structure

`Conditions` is primarily divided into two sections, each contained within a `Grid` item:
- **Conditions Overview**: This section displays a list of health conditions using accordion components for each condition. Users can expand these to view more information.
- **Patient Education**: Utilizes a tab interface, allowing users to switch between different educational topics. Each topic is rendered within its respective tab panel.

## Components Utilized

The following Material-UI components are used:
- `Accordion`, `AccordionSummary`, and `AccordionDetails`: For the collapsible sections detailing health conditions.
- `Tabs` and `Tab`: For creating the tabbed navigation in the patient education section.
- `Dialog`, `DialogContent`, and `DialogActions`: For implementing the modal dialog functionality for note-taking.
- `TextField`: Allows users to input text for their notes.
- `Button`: Used within the dialog for saving or discarding notes.

## Data

Dynamic rendering of conditions and educational content is powered by two arrays:
- `conditionsData`: Contains information on various health conditions.
- `educationData`: Holds content for the patient education tabs.


---


# Demographics Component 

## Overview

The `Demographics` component is designed to display detailed demographic information about a patient, along with information about their primary care provider (PCP) and billing specialist. This component is built using React and Material UI, ensuring a responsive and visually appealing presentation.

## Features

- **Responsive Design**: Adapts to various screen sizes for optimal viewing on desktops and mobile devices.
- **Material UI Components**: Utilizes Material UI components for a consistent and modern UI design.
- **Structured Information Display**: Organizes patient information and care team details in a clear and accessible manner.

### Data Structure

The component uses a predefined `patientDemoData` object to simulate patient and care team information. This object includes:

- Patient Name, Age, Gender, Patient ID, Date of Birth, and Email
- Primary Care Physician (PCP) and Billing Provider details (name, specialty, practice location)

### Main Components

- **`Box`**: Provides the outer container with spacing and overflow control.
- **`Paper`**: Acts as the main content container with elevation for depth.
- **`Grid`**: Organizes the content into responsive columns.
- **`Typography`**: Displays text information in various styles.
- **`Button`** and **`Divider`**: Enhances the UI with actionable items and visual separation.

### Responsive Design

The component uses `useMediaQuery` to adapt the layout according to the screen size. The `matches` variable toggles the layout between a compact view for smaller screens and a more spaced view for larger screens.


---


# Diagnoses Component 

## Overview

The `Diagnoses` component is designed to display a list of patient diagnoses in a visually appealing manner. It differentiates between chronic and acute conditions using background colors and chips, providing a quick and intuitive way to assess patient health issues.

## Features

- Dynamically generated list of diagnoses.
- Visual differentiation between chronic and acute conditions.
- Responsive design for varied screen sizes.

### State Management

This component is stateless and relies on the `diagnoses` array for its data, making it suitable for static rendering or as part of a larger, dynamic application where its state is managed externally.

### Responsive Design

Utilizes the `useMediaQuery` hook from Material-UI to adapt the layout according to the screen size.

### Styling

Custom styles are applied using the `sx` prop, allowing for direct integration with the theme provided by Material-UI's `ThemeProvider`.

## Component Structure

- **`Paper`**: Acts as the outer container with elevation for depth.
- **`Typography`**: Displays the heading "Active Diagnoses" at the top of the component.
- **`List` and `ListItem`**: Used to render the list of diagnoses. Each item has customized styling based on whether the condition is chronic.
- **`ListItemText`**: Displays the name of the diagnosis and its last updated date.
- **`Chip`**: Indicates if a diagnosis is chronic.

## Data Model

The component expects an array of diagnosis objects, each containing:
- `id` (number): Unique identifier for the diagnosis.
- `name` (string): Name of the diagnosis.
- `isChronic` (boolean): Whether the condition is chronic.
- `lastUpdated` (string): The last update date of the diagnosis.


---


# Documentation Component 

## Overview

The `Documentation` component is a dynamic, interactive UI element designed to facilitate user engagement with documentation tasks. It combines several Material-UI components to create a feature-rich documentation interface that includes a dialog with tabs for different functionalities, inputs for text, and the ability to add custom purposes.

## Features

- **Dynamic Dialog Box**: Utilizes a dialog box that can switch between minimized and maximized states, allowing users to interact with the documentation without leaving the context of their current task.
- **Tabbed Interface**: Offers a tabbed interface within the dialog for different documentation aspects, such as inputting text and managing purposes.
- **Purpose Management**: Users can add custom "purposes" for their documentation, enhancing the categorization and retrieval of documentation notes.
- **Interactive Tooltips**: Provides additional information through tooltips, making the interface intuitive and informative.
- **Responsive and Accessible**: Adopts Material-UI's responsive and accessibility features, ensuring the component is usable across different devices and by users with varying accessibility needs.

### State Management

The component uses React's `useState` hook to manage several pieces of its state:
- Dialog open/close state.
- Minimized/maximized state for the dialog.
- The current value of the documentation text input.
- The current tab selection.
- The list of purposes and the input value for adding new purposes.

### Event Handlers

- `handleOpen` and `handleClose`: To open and close the dialog.
- `toggleMinimize`: To switch between the minimized and maximized states of the dialog.
- `handleInputChange`: To update the documentation text input value.
- `handleChangeTab`: To switch between tabs.
- `handlePurposeInputChange`: To update the purpose input value.
- `handleAddPurpose`: To add a new purpose to the list.

### Layout and Styling

The component layout is primarily defined using Material-UI's `Grid`, `Paper`, `AppBar`, `Toolbar`, `Tabs`, `Tab`, `Dialog`, `TextField`, `Button`, `IconButton`, `Typography`, `Chip`, and `Stack` components, with inline styling provided via the `sx` prop.

## Customization

Customization can be done through the following approaches:
- Modifying the `sx` prop values to change the styling of the components.
- Adjusting the event handlers and state management logic to fit specific requirements.
- Expanding the component to include more tabs or functionalities based on the project's needs.


---


# Goals Component

## Overview

The `Goals` component is designed to manage and display a patient's health goals within a healthcare application. It provides functionalities such as listing goals, adding new goals, editing existing goals, and appending notes to goals. The component integrates with `@mui/x-date-pickers` for date selection, enhancing the user experience in managing goal-related notes.

## Features

- **List Patient Goals**: Displays all patient goals with their current status.
- **Add New Goals**: Allows users to add new health goals.
- **Edit Existing Goals**: Enables editing the text of existing goals.
- **Add Notes to Goals**: Supports adding dated notes to specific goals to track progress or changes.
- **Responsive Design**: Adapts to different screen sizes for optimal viewing on any device.

## State Management

The component uses React's `useState` hook for managing:
- The list of patient goals and notes.
- The visibility and state of the modal for adding/editing goals and notes.
- The currently selected goal for editing or note addition.
- The text input for new or edited goals and notes.
- The date selection for new notes.

## Interaction Handlers

- **Modal Operations**: Functions to open and close the modal, including setting up for adding a new goal, editing an existing goal, or adding a note.
- **Goal and Note Management**: Functions to handle the input changes for new or edited goals and notes, saving these changes, and updating the component's state.

## Modal Design

The modal provides a dynamic form that switches between adding/editing goals and adding notes to goals based on the user interaction. It utilizes `TextField` for input and `DesktopDatePicker` for date selection.


---


# Medications Component 

## Overview

The `Medications` component displays a list of a patient's medications, including their names, associated conditions, and the last fill date. It visually highlights medications that need a refill based on the time elapsed since the last fill date or a `refillNeeded` flag.

## Features

- Displays a list of medications with detailed information.
- Highlights medications that require a refill.
- Adapts to different screen sizes for optimal viewing across devices.

### Data Structure

The component uses an array of medication objects, each containing:
- `id`: A unique identifier.
- `name`: The name of the medication.
- `condition`: The health condition treated by the medication.
- `lastFillDate`: The date when the medication was last filled.
- `refillNeeded` (optional): A boolean flag indicating if a refill is explicitly needed.

### Refill Logic

A medication is considered to need a refill if:
- More than 30 days have passed since the `lastFillDate`.
- The `refillNeeded` flag is `true`.

### Styling

The component uses Material-UI's `Paper`, `List`, `ListItem`, `ListItemText`, `Typography`, and `Chip` components for layout and styling, with additional styles applied for responsiveness and visual feedback.

- Medications needing a refill are highlighted with a different background color and a "Refill Needed" chip.
- Responsive design adjusts the maximum width based on screen size.

### Dependencies

- `@mui/material`: For the UI components and styling.
- `useTheme` and `useMediaQuery`: From Material-UI to support responsive design.


---


# PatientSummary Component 

## Overview

`PatientSummary` is a React component designed to display a comprehensive summary of patient information, including personal details, care team contacts, care plans, and insurance details. It features an interactive documentation section that can be minimized or expanded, supporting the addition of notes or purposes related to the patient's care.

## Features

- Displays patient's personal information and care team contacts.
- Lists detailed care plans and insurance information.
- Provides an interactive documentation dialog with minimize and maximize functionality.
- Supports adding custom text notes and purposes within the documentation section.

The component uses React's `useState` hook to manage:
- The active tab for displaying different sections of the patient summary.
- The open state of the documentation dialog.
- The minimized state of the documentation dialog.
- The input values for adding documentation notes and purposes.

### Layout and UI Components

- **Tabs and TabPanel**: For navigating between different sections of the patient summary.
- **Dialog**: For adding documentation notes and purposes.
- **AppBar and Toolbar**: For the dialog's title bar, including minimize and maximize actions.
- **TextField**: For inputting documentation notes and purposes.
- **Chip**: For displaying added purposes.
- **Responsive Design**: Utilizes Material-UI's `useMediaQuery` to adapt the layout based on the screen size.

### Interaction Handlers

- Tab change, dialog open/close, minimize/maximize, and input change handlers facilitate the component's interactive features.


---


# Recent Component

## Overview

The `Recent` component is designed to display recent patient appointments and encounters in a healthcare application. It provides a clear and concise view of the patient's latest interactions with healthcare providers and coordinators, including details such as date, provider name, and a brief description of the encounter or appointment.

## Features

- Displays a list of recent appointments and encounters in separate sections.
- Utilizes Material-UI `Grid`, `Paper`, `List`, `ListItem`, and `Typography` components for layout and styling.
- Responsive design adapts to different screen sizes, ensuring readability across devices.
- Uses `Tooltip` to provide additional detail on hover or tap, enhancing user experience by revealing more information without cluttering the UI.

## Layout and Styling

- The component is divided into two main sections, each occupying half of the screen on medium-sized devices and the full width on smaller screens.
- Each section is contained within a `Paper` component to distinguish the lists from the rest of the UI.
- A custom background color is applied to `ListItem` components for visual differentiation.
- Tooltips are used to display the full details of each appointment or encounter when the user hovers over or taps on a list item.

This component does not manage state internally; it receives data as static arrays defined within the component. For dynamic data, modifications would be required to fetch data from an external source or props.

### Data Structure

Appointments and encounters are defined as arrays of objects, where each object contains:
- `date`: The date of the appointment or encounter.
- `provider` or `coordinator`: The name of the healthcare provider or coordinator involved.
- `detail`: A brief description of the appointment or encounter.

### Responsive Design

The component uses `useMediaQuery` and the theme's breakpoints to adjust the layout based on the screen size, ensuring a responsive design that accommodates various devices.


---


# RPMdashboard Component 

## Overview

The `RPMdashboard` (Remote Patient Monitoring Dashboard) component is designed to provide healthcare providers with a quick overview of patients' health metrics, recent alerts, and notes. It allows for the monitoring of critical patient health information, facilitating timely interventions and patient engagement.

## Features

- Dynamically generated tabs for each patient's health condition.
- Displays critical metrics, alerts, and notes for each patient.
- Responsive design adapts to various screen sizes.
- Modal for adding new notes to a patient's record.

### State Management

- Utilizes React's `useState` for managing:
  - The active tab selection.
  - The visibility state of the modal for adding notes.
- Data for patient health conditions, metrics, and notes are currently mocked within the component for demonstration purposes.

### Responsive Design

- Adapts the tab layout based on the screen size using `useMediaQuery` and the theme's breakpoints.
- Uses a modal for adding notes, ensuring accessibility on devices of all sizes.

### Health Metric Highlighting

- Critical health metrics are dynamically styled based on predefined conditions (e.g., elevated blood pressure or glucose levels) to quickly draw attention to potential health concerns.

### Modal for Adding Notes

- A modal is implemented for adding new notes to a patient's record, enhancing the component's interactivity.
- Includes a text field for inputting the note and buttons for saving or canceling the action.

### Accessibility

- `a11yProps` function and related attributes ensure that the component is accessible, particularly for users navigating with screen readers or keyboards.



---


# Screenings Component

## Overview

`Screenings` is a React component designed to display various health-related screenings, assessments, vaccines, and health risks in a tabbed interface. It aims to provide an organized and accessible way for users (e.g., patients or healthcare providers) to review critical health information.

## Features

- Displays information in a tabbed layout for easy navigation between different health categories: Screenings, Health Risks, Assessments, and Vaccines.
- Each tab contains a list of related items, showing the name, details, and the current status (current, overdue, pending) of each item.
- Utilizes Material-UI components for a cohesive and responsive design.

### State Management

- The component uses React's `useState` hook to manage the currently selected tab.

### Tabbed Interface

- The Material-UI `Tabs` and `Tab` components are used to create the tabbed interface.
- `TabPanel` custom component to display the content corresponding to the selected tab.

### Data Structure

- Mock data is structured as an object containing arrays for each category (`screenings`, `healthRisks`, `assessments`, `vaccines`). Each array contains objects with the fields `name`, `details`, and `status`.

### Styling

- Uses the Material-UI `useTheme` hook and `Chip` component to dynamically style items based on their status (e.g., current, overdue, pending).
- Custom styles applied via the `sx` prop to Material-UI components for layout and spacing adjustments.


---


# Checker Component 

## Overview

The `Checker` component is designed to dynamically present a series of health-related questions to the user, allowing for an interactive symptom checking experience. It utilizes `framer-motion` for smooth animations between questions, enhancing user engagement.

## Features

- Presents a series of questions with multiple-choice answers to the user.
- Animates transitions between questions for a polished user experience.
- Provides "Next" and "Back" navigation buttons to move through questions.
- Displays a "Submit" button upon reaching the final question to complete the symptom check.

### State Management

- Uses React's `useState` hook to track the current question index.
- Utilizes conditional rendering based on the current question index to display the appropriate question and set of answers.

### Animation

- Leverages `framer-motion` for animating the entrance and exit of questions.
- Configures animations to smoothly transition in the horizontal direction as the user navigates through questions.

### Responsive Design

- Adapts layout and styling based on the screen width using Material-UI's `useMediaQuery` hook, ensuring a responsive design that accommodates various devices.

### Navigation Controls

- "Next" and "Back" buttons allow the user to navigate through the questions.
- Buttons are conditionally enabled or disabled based on the current question index to prevent navigation beyond the available questions.
- A "Submit" button is shown when the user reaches the final question, signaling the completion of the symptom check.


---


# Tasks Component

## Overview

The `Tasks` component is designed for managing and displaying tasks in a healthcare management system. It allows users to add new tasks with details such as title, due date, priority, and message. Each task is visualized with its status indicated by color-coded chips, enhancing the user interface for better task management.

## Features

- Dynamic listing of tasks with critical information displayed.
- Color-coded chips to indicate task priority/status for quick visual reference.
- Modal form for adding new tasks with fields for title, due date, priority, and message.
- Responsive design adapts to different screen sizes.


### State Management

- Uses React's `useState` hook to manage the list of tasks, modal open state, and the input fields for new task creation.

### UI Components

- **Paper**: Serves as the container for the task list, providing a clean background and shadow.
- **Typography**: Displays titles and text content.
- **Button** and **IconButton**: Used for actions like adding new tasks and marking tasks as complete or removing them.
- **Modal**: Contains the form for adding new tasks.
- **TextField** and **Select**: Input fields within the modal for entering new task details.
- **Chip**: Indicates the priority/status of each task with color coding.

### Handling Events

- Event handlers are implemented for opening/closing the modal, updating input field values, and adding new tasks to the list.

### Styling

- Material-UI's `useTheme` and `useMediaQuery` hooks are utilized for responsive styling.
- Custom styles are applied using the `sx` prop, especially for modal positioning and task list item styling based on priority/status.


---


# Vitals Component

## Overview

The `Vitals` component displays a list of the most recent vital signs for a patient, including information such as the vital sign name, its value, and the date it was recorded. This component highlights critical vital signs to quickly draw attention to any potential health issues.

## Features

- Displays a table of recent vital signs for a patient.
- Highlights critical vital signs in a different color to quickly alert healthcare providers.
- Responsive design adapts to different screen sizes, ensuring accessibility across devices.

### Data Structure

The component uses an array of objects, `vitals`, where each object represents a vital sign with the following properties:
- `name`: The name of the vital sign.
- `value`: The recorded value of the vital sign.
- `date`: The date the vital sign was recorded.
- `isCritical`: A boolean indicating whether the vital sign's value is considered critical.

### Styling

- Critical vital signs are styled with a bold font weight and the color set to `theme.palette.error.main` to make them stand out.
- The `getStyle` function dynamically returns styling based on the `isCritical` property of each vital sign.
- Uses Material-UI's `useTheme` and `useMediaQuery` hooks to adapt the layout and styling based on the screen size.

### Layout

- Utilizes Material-UI's `Paper`, `TableContainer`, `Table`, `TableHead`, `TableBody`, `TableRow`, and `TableCell` components to structure and display the list of vital signs.
- The responsive design hides some columns on smaller screens for improved readability, with conditional rendering based on the `matchesSM` state.

~*jkb