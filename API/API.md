# Authentication & User Management

## User Registration
**POST** `/api/auth/register`  
Register a new user (guest/registered_user/officer/admin)

## User Login
**POST** `/api/auth/login`  
Authenticate users and return JWT token

## User Logout
**POST** `/api/auth/logout`  
Invalidate JWT session

## Get User Profile
**GET** `/api/users/{userId}`  
Fetch user details

## Update User Profile
**PUT** `/api/users/{userId}`  
Update user details (name, email, etc.)

## Delete User Account
**DELETE** `/api/users/{userId}`  
Soft delete or permanently delete user

## Change Password
**POST** `/api/users/{userId}/change-password`  
Secure password change

## Reset Password (Forgot Password)
**POST** `/api/auth/reset-password`  
Sends email with reset link

# Crop Selection

## Get Available Crops
**GET** `/api/crops`  
Fetch all available crops

## Select Crops
**POST** `/api/user-crops`  
User selects multiple crops to track

## Get User Selected Crops
**GET** `/api/user-crops/{userId}`  
Fetch crops selected by a specific user

## Deselect Crops
**DELETE** `/api/user-crops/{userId}/{cropId}`  
Remove crop from the user’s selection

# Daily Logs (Elasticsearch)

## Submit Daily Log
**POST** `/api/daily-log/{userId}`  
Users log daily activities for their crops

## Fetch User’s Daily Logs
**GET** `/api/daily-log/{userId}`  
Retrieve all logs of a user

## Fetch User’s Certain Logs
**GET** `/api/daily-log/{userId}/{logId}`  
Retrieve certain log of a user

## Fetch Logs for a Specific Crop
**GET** `/api/daily-log/{userId}/{cropId}`  
Retrieve logs for a specific crop of the user

## Fetch Daily Logs by Date
**GET** `/api/daily-log/{userId}/date/{logDate}`  
Fetch logs for a specific date

# Chat System

## Start a Chat Session
**POST** `/api/chat-sessions`  
Create a chat session between user and officer

## Send a Message
**POST** `/api/chats`  
Send a message (text/attachment)

## Fetch Chat History
**GET** `/api/chats/{chatSessionId}`  
Retrieve messages of a chat session

## Upload Chat Attachment
**POST** `/api/chat-attachments`  
Upload an image/document as an attachment

## Get Chat Attachments
**GET** `/api/chat-attachments/{chatId}`  
Fetch all attachments in a chat

# Broad Data Visualization (Elasticsearch)

## Generate Data Report
**POST** `/api/data-visualization`  
Generate aggregated farming insights for an officer

## Fetch Data Reports
**GET** `/api/data-visualization/{officerId}`  
Fetch previously generated reports

## Filter Data Reports
**GET** `/api/data-visualization`  
Query by `filter_area`, `filter_crop`, or date range

# Alerts & Notifications

## Create an Alert
**POST** `/api/alerts`  
Officer/user creates a disease or task reminder alert

## Fetch Alerts for a User
**GET** `/api/alerts/{userId}`  
Retrieve all alerts assigned to a user

## Fetch Alerts for a Specific Crop
**GET** `/api/alerts/{cropId}`  
Get alerts specific to a user’s crop

## Fetch Specific Alert for a User
**GET** `/api/alert/{alertId}`  
Retrieve certain alert assigned to a user

## Delete an Alert
**DELETE** `/api/alerts/{alertId}`  
Remove an alert

# Administrative APIs

## Get All Users
**GET** `/api/admin/users`  
Admin fetches all users

## Update User Role
**PUT** `/api/admin/users/{userId}/role`  
Change a user's role (upgrade/downgrade)

## Delete Any User
**DELETE** `/api/admin/users/{userId}`  
Admin deletes any user account

# Miscellaneous

## Health Check API
**GET** `/api/health`  
Check system status

## Get System Logs
**GET** `/api/logs`  
Fetch application logs (admin-only)
