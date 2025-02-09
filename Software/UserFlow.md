# Mobile Application User Flow for Unserserved Farmers

This document outlines the user flow, screens, and detailed navigation for a mobile application designed for underserved farmers. The application is divided into **5 main user types**: Guest User, Registered Farmer, Officer, Admin, and System Screens. Each section describes the screens, functionality, and navigation.

---

## **Total Screens: 12**

1. **Landing Screen** (Unrestricted)
2. **Chat Screen** (Unrestricted)
3. **Daily Tips/News Screen** (Unrestricted)
4. **Login/Registration Screen** (Restricted)
5. **Home Screen (Registered User)** (Restricted)
6. **Crop Selection Screen** (Restricted)
7. **Daily Log Screen** (Restricted)
8. **Farm Data Visualization Screen** (Restricted)
9. **Officer Home Screen** (Restricted)
10. **Chat Review Screen** (Restricted)
11. **Broad Data Visualization Screen** (Restricted)
12. **Admin Dashboard Screen** (Restricted)

---

## **1. Landing Screen (Unrestricted)**

- **Purpose**: Welcome screen for all users.
- **Functionality**:
  - Large, colorful icons for key actions.
  - Options:
    - **Start Chat**: Opens the Chat Screen.
    - **Login/Register**: Redirects to the Login/Registration Screen.
    - **Continue as Guest**: Allows users to access basic features without logging in.
- **Design**:
  - Background: Farm-related image (e.g., fields, crops).
  - Icons: Large and intuitive (e.g., chat bubble, login button).
  - Text: Minimal, in local language.

---

## **2. Chat Screen (Unrestricted)**

- **Purpose**: Allows users to chat with local officers.
- **Functionality**:
  - Simple chat interface with a text box and attachment option (images/documents).
  - Pre-filled message templates for common queries (e.g., "How to treat yellow leaves?").
  - Option to chat anonymously.
- **Navigation**:
  - Accessible from the Landing Screen or during other workflows (e.g., while using Daily Log).
- **Design**:
  - Chat bubbles with clear differentiation between user and officer messages.
  - Attachment icon prominently displayed.

---

## **3. Daily Tips/News Screen (Unrestricted)**

- **Purpose**: Provides daily farming tips, weather updates, and news.
- **Functionality**:
  - Scrolling cards or images with tips and alerts.
  - Simple icons for weather, tips, and alerts.
- **Navigation**:
  - Accessible from the Landing Screen for guest users.
- **Design**:
  - Cards with large images and minimal text.
  - Icons for quick recognition (e.g., sun for weather, bulb for tips).

---

## **4. Login/Registration Screen (Restricted)**

- **Purpose**: Allows users to log in or register.
- **Functionality**:
  - Simple form with minimal fields (name, phone number, region).
  - Option to skip registration and continue as a guest.
- **Navigation**:
  - Accessible from the Landing Screen.
- **Design**:
  - Clean form with large input fields.
  - Clear call-to-action buttons (e.g., "Login", "Register").

---

## **5. Home Screen (Registered User) (Restricted)**

- **Purpose**: Central hub for registered users.
- **Functionality**:
  - **Crop Selection**: Redirects to the Crop Selection Screen.
  - **Daily Log**: Redirects to the Daily Log Screen.
  - **Chat Application**: Redirects to the Chat Screen.
  - **Farm Data**: Redirects to the Farm Data Visualization Screen.
- **Navigation**:
  - Bottom navigation bar with 3-4 main options (Home, Chat, Daily Log, Farm Data).
- **Design**:
  - Large icons with text labels for each feature.
  - Simple and intuitive layout.

---

## **6. Crop Selection Screen (Restricted)**

- **Purpose**: Allows users to select the crops they are harvesting.
- **Functionality**:
  - Static dropdown list of crops.
  - User selects or deselects crops and confirms.
  - Redirects back to the Home Screen after confirmation.
- **Navigation**:
  - Accessible from the Home Screen.
- **Design**:
  - Dropdown menu with large, easy-to-tap options.
  - Confirmation button prominently displayed.

---

## **7. Daily Log Screen (Restricted)**

- **Purpose**: Allows users to log daily activities and conditions.
- **Functionality**:
  - Predefined set of questions based on selected crops.
  - Questions are refined using an LLM (e.g., "Did it rain today?" with a rain icon).
  - User answers questions, and responses are saved automatically.
  - Option to attach photos for additional context.
- **Navigation**:
  - Accessible from the Home Screen.
- **Design**:
  - Simple, visual questions with icons.
  - Save button at the bottom of the screen.

---

## **8. Farm Data Visualization Screen (Restricted)**

- **Purpose**: Displays farm data in an easy-to-understand format.
- **Functionality**:
  - Graphs and charts showing daily logs, crop health, and weather data.
  - Filters by crop and time period.
- **Navigation**:
  - Accessible from the Home Screen.
- **Design**:
  - Simple charts with large, colorful visuals.
  - Filter options at the top of the screen.

---

## **9. Officer Home Screen (Restricted)**

- **Purpose**: Central hub for officers.
- **Functionality**:
  - **Chat Review**: Redirects to the Chat Review Screen.
  - **Broad Data Visualization**: Redirects to the Broad Data Visualization Screen.
- **Navigation**:
  - Bottom navigation bar with 2 main options (Chat Review, Farm Data).
- **Design**:
  - Large icons with text labels for each feature.
  - Simple and intuitive layout.

---

## **10. Chat Review Screen (Restricted)**

- **Purpose**: Allows officers to review and respond to user chats.
- **Functionality**:
  - Officers receive notifications for new chats.
  - They can review chats, access user’s daily logs, and respond with informed advice.
  - Option to log details from the chat review.
- **Navigation**:
  - Accessible from the Officer Home Screen.
- **Design**:
  - Chat interface with access to user logs.
  - Log button prominently displayed.

---

## **11. Broad Data Visualization Screen (Restricted)**

- **Purpose**: Allows officers to review local farming practices and issue alerts.
- **Functionality**:
  - Graphs and charts from daily logs.
  - Filters by area and crop.
- **Navigation**:
  - Accessible from the Officer Home Screen.
- **Design**:
  - Simple charts with large, colorful visuals.
  - Filter options at the top of the screen.

---

## **12. Admin Dashboard Screen (Restricted)**

- **Purpose**: Allows admins to maintain and update the application.
- **Functionality**:
  - Options to update the application, manage user data, and monitor system health.
- **Navigation**:
  - Accessible after admin login.
- **Design**:
  - Simple interface with clear buttons for each action.

---

## **Key Design Considerations**

- **Icons and Visuals**: Use large, colorful icons with simple text labels.
- **Navigation**: Use a bottom navigation bar for easy access to key features.
- **Language**: Use simple, local language with minimal text.
- **Feedback**: Provide immediate feedback for user actions (e.g., checkmarks, notifications).

---

This user flow ensures that even uneducated farmers can easily navigate the application, while still providing powerful features for registered users, officers, and admins.