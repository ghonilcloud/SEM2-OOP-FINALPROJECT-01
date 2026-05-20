# FYPL Database Management System

A comprehensive Java-based database management system designed to streamline operations for the First Year Program Leaders (FYPL) organization. This application provides a complete solution for managing student information, tracking disciplinary records, and organizing events.

## 🎯 Overview

The FYPL Database Management System is a sophisticated Java application that manages three interconnected databases:

1. **FYPL Database** - Maintains comprehensive student information including contact details, academic majors, positions, and divisions
2. **Punishments Database** - Tracks disciplinary records linked to students with dates and reasons
3. **Events Database** - Manages FYPL-organized events with assigned roles and attendee information

The system provides a CLI-based interface with a menu-driven design for easy navigation and operation. It implements OOP principles with abstract classes, interfaces, and inheritance to ensure clean, maintainable code.

## ✨ Features

### Student Management
- **View All Students** - Display complete list of FYPL members with all details
- **Add Students** - Register new students with validation for:
  - Unique NIM (Student ID) enforcement
  - Email format validation (must contain @ and .)
  - Contact number validation (numeric values only)
  - Major selection from 8 predefined programs
  - Position assignment (Leader, Partner, Dual Role, etc.)
  - Division classification (Event or Mobile)
- **Update Student Records** - Modify existing student information with real-time validation
- **Remove Students** - Delete student records with cascading deletion in related tables

### Punishments Management
- **View Punishment Records** - Display all disciplinary actions with student names and dates
- **Issue Punishments** - Record new disciplinary actions with:
  - Student selection from existing database
  - Punishment type documentation
  - Reason specification
  - Automatic date recording
- **Remove Punishment Records** - Delete outdated or incorrect punishment entries

### Events Management
- **View Events** - Display all scheduled events with complete role assignments and details
- **Create Events** - Organize new events with:
  - Event naming and categorization (Seminar, Workshop, Lecture, Guest Seminar)
  - Detailed descriptions
  - Role assignment for 6 key positions (MC, Timekeeper, Slides, 2x Mobile)
  - Seat capacity management
  - Date scheduling (DD-MM-YYYY format)
- **Remove Events** - Cancel or delete events from the system

### Data Validation
- Input type checking (integers, strings, emails)
- Referential integrity maintenance
- Error handling with user-friendly messages
- Invalid input recovery with retry mechanisms

## 🏗️ System Architecture

### Design Patterns Used

```
DatabaseOperation (Abstract Base Class)
    ├── FYPLDatabaseOperation (implements Viewable)
    ├── PunishmentsDatabaseOperation
    └── EventDatabaseOperation (implements Viewable)
```

## 📋 Prerequisites

- **Java JDK 8 or higher**
- **MySQL Server 5.7+**
- **MySQL Workbench** (for database import/setup)
- **JDBC Driver** - MySQL Connector/J (included in classpath during compilation)

## 🔧 Installation & Setup

### Step 1: Clone or Download Project

```bash
# Download the project files to your desired location
```

### Step 2: Prepare Java Environment

Ensure your CLASSPATH includes the MySQL JDBC driver:
```bash
# Windows
set CLASSPATH=%CLASSPATH%;path\to\mysql-connector-java-x.x.x.jar

# Linux/Mac
export CLASSPATH=$CLASSPATH:path/to/mysql-connector-java-x.x.x.jar
```

### Step 3: Compile Java Code

```bash
javac main.java
```

## 📊 Database Configuration

### Import CSV Files to MySQL

1. **Open MySQL Workbench**
2. **Connect to your MySQL Server**
3. **Create schema** named `final_project_schema`

4. **For each CSV file** (fypldatabase.csv, punishmentsdatabase.csv, eventdatabase.csv):
   - Right-click on the schema
   - Select "Table Data Import Wizard"
   - Choose the CSV file
   
5. **Configure import settings as follows:**
   - **Field Separator:** `;` (semicolon)
   - **Line Separator:** `LF` (Line Feed)
   - **Enclosed Strings in:** `"` (double quotes)
   - **Treat NULL values:** Yes

### Database Schema Overview

**fypldatabase**
```
NIM (Long) - PRIMARY KEY, Student ID
Name (String)
Email (String)
Contact Number (Long)
Major (String) - 8 options
Position (String)
Division (String) - Event or Mobile
```

**punishmentsdatabase**
```
PunishmentID (Int) - PRIMARY KEY, Auto-increment
NIM (Long) - FOREIGN KEY → fypldatabase
Date (Date)
Reason (String)
Punishment (String)
```

**eventdatabase**
```
EventID (Int) - PRIMARY KEY, Auto-increment
EventName (String)
EventType (String) - Seminar, Workshop, Lecture, Guest Seminar
EventDescription (String)
MC (String) - Format: "NIM-Name"
Timekeeper (String) - Format: "NIM-Name"
Slides (String) - Format: "NIM-Name"
Mobile1 (String) - Format: "NIM-Name"
Mobile2 (String) - Format: "NIM-Name"
Seats (Long)
Date (String) - Format: DD-MM-YYYY
```

### Update Connection Credentials

In `main.java`, locate the connection strings in the Main class:

```java
fyplDatabaseOperation = new FYPLDatabaseOperation(
    "jdbc:mysql://127.0.0.1:3306/final_project_schema",
    "root",           // Username
    "0n34lW4s33m"     // Password
);
```

**Replace with your MySQL credentials:**
- Host: `127.0.0.1` (localhost)
- Port: `3306` (default MySQL port)
- Database: `final_project_schema`
- Username: Your MySQL username
- Password: Your MySQL password

## 🚀 Usage

### Running the Application

```bash
java Main
```

## 🤝 Contributing

This is a student project for SEM2 OOP Final Project. 
