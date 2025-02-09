# List of All Intended APIs

## Authentication & User Management

### User Registration
**POST**
<span style="color: green">`/api/auth/register`</span>  
Register a new user and return JWT token

### User Login
**POST** `/api/auth/login`  
Authenticate users and return JWT token

### User Logout
**POST** `/api/auth/logout`  
Invalidate JWT session

### Get User Profile
**GET** `/api/users/{userId}`  
Fetch user details

### Update User Profile
**PUT** `/api/users/{userId}`  
Update user details (name, email, etc.)

### Delete User Account
**DELETE** `/api/users/{userId}`  
Soft delete/permanently delete user

### Change Password
**POST** `/api/users/{userId}/password`  
Secure password change

### Reset Password (Forgot Password) ?
**POST** `/api/auth/reset-password`  
Sends email with reset link

## Crop Selection

### Get Available Crops
**GET** `/api/crops`  
Fetch all available crops

### Select Crops
**POST** `/api/user-crops`  
User selects multiple crops to track

### Get User Selected Crops
**GET** `/api/user-crops/{userId}`  
Fetch crops selected by a specific user

### Deselect Crops
**DELETE** `/api/user-crops/{userId}/{cropId}`  
Remove crop from the user’s selection

## Daily Logs (Elasticsearch)

### Submit Daily Log
**POST** `/api/daily-log/{userId}`  
Users log daily activities for their crops

### Fetch User’s Daily Logs
**GET** `/api/daily-log/{userId}`  
Retrieve all logs of a user

### Fetch User’s Certain Logs
**GET** `/api/daily-log/{userId}/{logId}`  
Retrieve certain log of a user

### Fetch Logs for a Specific Crop
**GET** `/api/daily-log/{userId}/{cropId}`  
Retrieve logs for a specific crop of the user

### Fetch Daily Logs by Date
**GET** `/api/daily-log/{userId}/date/{logDate}`  
Fetch logs for a specific date

## Chat System

### Start a Chat Session
**POST** `/api/chat-sessions`  
Create a chat session between user and officer

### Send a Message
**POST** `/api/chats`  
Send a message (text/attachment)

### Fetch Chat History
**GET** `/api/chats/{chatSessionId}`  
Retrieve messages of a chat session

### Upload Chat Attachment
**POST** `/api/chat-attachments`  
Upload an image/document as an attachment

### Get Chat Attachments
**GET** `/api/chat-attachments/{chatId}`  
Fetch all attachments in a chat

## Broad Data Visualization (Elasticsearch) (Both Admin and Local Officer)

### Generate Data Report
**POST** `/api/data-visualization`  
Generate aggregated farming insights for an officer

### Fetch Data Reports
**GET** `/api/data-visualization/{officerId}`  
Fetch previously generated reports

### Filter Data Reports
**GET** `/api/data-visualization`  
Query by `filter_area`, `filter_crop`, or date range

## Alerts & Notifications

### Create an Alert
**POST** `/api/alert`
Officer/user creates a disease or weather alert

### Fetch Unread Alerts for A User
**GET** `/api/alerts/{userId}/unread`
Fetch all unread alerts for a user.

### Mark Alert as Read
**PATCH** `/api/alerts/{alertId}/read`
Mark an alert as read by the user.

### Fetch All Alerts for A User
**GET** `/api/alerts/{userId}`
Fetch all alerts for a user.

### Fetch Specific Alert for a User
**GET** `/api/alert/{alertId}`  
Retrieve certain alert assigned to a user

### Fetch Alerts for a Specific Crop
**GET** `/api/alerts/{cropId}`  
Get alerts specific to a user’s crop

### Fetch Alerts by Type
**GET** `/api/alerts?type={type}`
Filter alerts by type (e.g., disease, weather, task).

### Update an Alert
**PUT** `/api/alerts/{alertId}`
Update an existing alert (change description, time, or type).

### Snooze an Alert Type ?
**PATCH** `/api/alerts/snooze/{alertType}`
Snooze a specific type of alert for a specific duration.

### Delete an Alert
**DELETE** `/api/alert/{alertId}`  
Remove an alert

### Delete multiple Alerts
**DELETE** `/api/alerts`  
Remove multiple alerts

## Administrative APIs (Admin Only)

### Get All Users
**GET** `/api/admin/users`  
Admin fetches all users

### Get All Local Officers
**GET** `/api/admin/officers`  
Admin fetches all officers

### Local Officer Registration
**POST** `/api/admin/register/officer`  
Register a new local officer

### Delete Any User
**DELETE** `/api/admin/user/{userId}`  
Admin deletes any user account

### Delete Any Officer
**DELETE** `/api/admin/officer/{userId}`  
Admin deletes any officer account

### Get System Logs
**GET** `/api/logs`  
Fetch application logs (admin-only)

## Miscellaneous

### Health Check API
**GET** `/api/health`  
Check system status
