# Versioning of the Database Schema

This document outlines the step-by-step upgrading of the database schema for the **Learnathon** application. 

## Version 1.0.0: Basic User and Crop Management

### Requirements
- **User Management**: Basic user registration and authentication.
- **Crop Management**: Allow users to view and select crops.

### Schema Design

#### Users Table
```sql
CREATE TABLE Users (
    id UUID PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    password TEXT NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### Crops Table
```sql
CREATE TABLE Crops (
    id UUID PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT
);
```

#### User_Crops Table
```sql
CREATE TABLE User_Crops (
    id UUID PRIMARY KEY,
    user_id UUID REFERENCES Users(id) ON DELETE CASCADE,
    crop_id UUID REFERENCES Crops(id) ON DELETE CASCADE,
    selected_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Relationships
- **Users → User_Crops (1:N)**: One user can select multiple crops.

---

## Version 1.1.0: Added Daily Logging and Basic Communication

### New Requirements
- **Daily Logging**: Users can log daily observations for their selected crops.
- **Basic Communication**: Users can send messages to officers.

### Schema Updates

#### Daily_Log Table
```sql
CREATE TABLE Daily_Log (
    id UUID PRIMARY KEY,
    user_id UUID REFERENCES Users(id) ON DELETE CASCADE,
    crop_id UUID REFERENCES Crops(id) ON DELETE CASCADE,
    log_data JSON NOT NULL,
    log_date DATE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

#### Chat Table
```sql
CREATE TABLE Chat (
    id UUID PRIMARY KEY,
    sender_id UUID REFERENCES Users(id) ON DELETE CASCADE,
    receiver_id UUID REFERENCES Users(id) ON DELETE CASCADE,
    message TEXT NOT NULL,
    sent_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

### Relationships
- **Users → Daily_Log (1:N)**: Each user can log multiple entries per day.
- **Users → Chat (1:N)**: A user can send multiple messages.

---

## Version 1.2.0: Enhanced Communication

### New Requirements
- **Chat Attachments**: Allow file attachments in chat messages.

### Schema Updates

#### Chat_Attachment Table
```sql
CREATE TABLE Chat_Attachment (
    id UUID PRIMARY KEY,
    chat_id UUID REFERENCES Chat(id) ON DELETE CASCADE,
    attachment TEXT NOT NULL,
    type VARCHAR(20) NOT NULL
);
```

---

## Version 2.0.0: Added User Roles

### New Requirements
- **User Roles**: Introduce roles (guest, registered_user, officer, admin) for access control.

### Schema Updates

#### Users Table Update
```sql
ALTER TABLE Users
ADD COLUMN user_type ENUM('guest', 'registered_user', 'officer', 'admin') NOT NULL DEFAULT 'guest';
```

---

## Version 2.1.0: Data Visualization

### New Requirements
- **Data Visualization**: Officers can generate reports based on filtered data.

### Schema Updates

#### Broad_Data_Visualization Table
```sql
CREATE TABLE Broad_Data_Visualization (
    id UUID PRIMARY KEY,
    officer_id UUID REFERENCES Users(id) ON DELETE CASCADE,
    filter_area VARCHAR(255),
    filter_crop UUID REFERENCES Crops(id) ON DELETE CASCADE,
    data_report JSON NOT NULL,
    generated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
---

## Version 2.2.0: Alerts and Notifications

### New Requirements
- **Alerts**: Users receive alerts for crop diseases or task reminders.

### Schema Updates

#### Alerts Table
```sql
CREATE TABLE Alerts (
    id UUID PRIMARY KEY,
    user_id UUID REFERENCES Users(id) ON DELETE CASCADE,
    crop_id UUID REFERENCES Crops(id) ON DELETE CASCADE,
    alert_text TEXT NOT NULL,
    alert_type ENUM('disease', 'task_reminder') NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```
---

## Version 2.3.0: Chat Sessions

### New Requirements
- **Chat Sessions**: Track chat sessions between users and officers.

### Schema Updates

#### Chat_Session Table
```sql
CREATE TABLE Chat_Session (
    id UUID PRIMARY KEY,
    chat_id UUID REFERENCES Chat(id) ON DELETE CASCADE,
    user_id UUID REFERENCES Users(id) ON DELETE CASCADE,
    officer_id UUID REFERENCES Users(id) ON DELETE CASCADE,
    started_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## Version 2.4.0: Alert Read Mark

### New Requirements
- **Mark Alerts as Read**

### Schema Updates

#### Alerts Table
```sql
ALTER TABLE Alerts
ADD COLUMN read_at TIMESTAMP;
```

## Indexing and Optimization
```sql
CREATE INDEX idx_users_email ON Users(email);
CREATE INDEX idx_chat_sent_at ON Chat(sent_at);
CREATE INDEX idx_alerts_user_id ON Alerts(user_id);
```

## Version 3.0.0: Detailed Alert Management

### New Requirements
- **More control over Alerts and Notifications**

### Schema Updates
```sql
CREATE TYPE alert_type_enum AS ENUM ('task', 'crop', 'weather');
CREATE TYPE priority_enum AS ENUM ('low', 'medium', 'high');
CREATE TYPE task_type_enum AS ENUM ('water plants', 'fertilizer');
CREATE TYPE weather_type_enum AS ENUM ('draught', 'flood', 'storm', 'heatwave');
```

```sql
CREATE TABLE Alerts (
    id UUID PRIMARY KEY,
    user_id UUID NOT NULL,
    alert_type alert_type_enum NOT NULL,
    priority priority_enum NOT NULL,
    created_at TIMESTAMP NOT NULL DEFAULT NOW(),
    read_at TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id) ON DELETE CASCADE
);
```

```sql
CREATE TABLE TaskAlerts (
    alert_id UUID PRIMARY KEY,
    task_type task_type_enum NOT NULL,
    alert_text TEXT NOT NULL,
    due_time TIMESTAMP NOT NULL,
    FOREIGN KEY (alert_id) REFERENCES Alerts(id) ON DELETE CASCADE
);
```

```sql
CREATE TABLE CropAlerts (
    alert_id UUID PRIMARY KEY,
    crop_id UUID NOT NULL,
    alert_text TEXT NOT NULL,
    FOREIGN KEY (alert_id) REFERENCES Alerts(id) ON DELETE CASCADE,
    FOREIGN KEY (crop_id) REFERENCES crops(id) ON DELETE CASCADE
);
```

```sql
CREATE TABLE WeatherAlerts (
    alert_id UUID PRIMARY KEY,
    weather_type weather_type_enum NOT NULL,
    forecasted_at TIMESTAMP NOT NULL,
    FOREIGN KEY (alert_id) REFERENCES Alerts(id) ON DELETE CASCADE
);
```

## Indexing and Optimization
```sql
CREATE INDEX idx_users_email ON Users(email);
CREATE INDEX idx_chat_sent_at ON Chat(sent_at);
CREATE INDEX idx_alerts_user_id ON Alerts(user_id);
```

---

## Final Schema

The final schema incorporates all the features and optimizations added throughout the design process. It supports -
- user management
- crop tracking
- daily logging
- Chat management
- data visualization
- alerts and notifications 

-while adhering to database normalization principles. <br/>
Each version was built upon the previous one, ensuring scalability, maintainability, and adherence to best practices.