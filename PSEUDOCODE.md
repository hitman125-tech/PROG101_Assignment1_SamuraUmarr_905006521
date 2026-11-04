# SMART WASTE MANAGEMENT SYSTEM (SWMS)
## Pseudocode Documentation

### 1. Main System

```text
START
DISPLAY "SMART WASTE MANAGEMENT SYSTEM"
DISPLAY "1. Resident"
DISPLAY "2. Administrator"
DISPLAY "3. Collection Team"
DISPLAY "4. Exit"

INPUT choice

IF choice = 1 THEN
    CALL ResidentModule
ELSE IF choice = 2 THEN
    CALL AdministratorModule
ELSE IF choice = 3 THEN
    CALL CollectionTeamModule
ELSE
    DISPLAY "Goodbye"
END IF

STOP
```

### 2. Resident Waste Reporting

```text
START
INPUT resident_name
INPUT location
INPUT waste_category
INPUT description

IF any required field is empty THEN
    DISPLAY "Please complete all fields"
ELSE
    GENERATE report_ID
    SAVE report_details
    SET status = "Pending"
    DISPLAY report_ID
    DISPLAY "Report submitted successfully"
END IF

STOP
```

### 3. Administrator Verification

```text
START
INPUT username
INPUT password

IF login_details are correct THEN
    DISPLAY pending_reports

    FOR EACH report
        IF report is valid THEN
            SET status = "Verified"
            ASSIGN collection_team
        ELSE
            SET status = "Rejected"
        END IF
    END FOR
ELSE
    DISPLAY "Invalid login"
END IF

STOP
```

### 4. Collection Team Module

```text
START
DISPLAY assigned_tasks

FOR EACH task
    SET status = "In Progress"
    INPUT completion_status

    IF completion_status = "Yes" THEN
        SET status = "Completed"
    END IF

    SAVE task_status
END FOR

STOP
```

### 5. Report Tracking

```text
START
INPUT report_ID
SEARCH for report_ID

IF report exists THEN
    DISPLAY report_details
    DISPLAY current_status
ELSE
    DISPLAY "Report not found"
END IF

STOP
```

### 6. Report Summary

```text
START
SET total_reports = 0
SET pending = 0
SET verified = 0
SET completed = 0

FOR EACH report
    INCREASE total_reports

    IF status = "Pending" THEN
        INCREASE pending
    ELSE IF status = "Verified" THEN
        INCREASE verified
    ELSE IF status = "Completed" THEN
        INCREASE completed
    END IF
END FOR

DISPLAY total_reports
DISPLAY pending
DISPLAY verified
DISPLAY completed

STOP
```
