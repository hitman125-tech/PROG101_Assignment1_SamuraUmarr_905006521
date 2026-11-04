PSEUDOCODE

Main System
BEGIN
   DISPLAY "SMART WASTE MANAGEMENT SYSTEM"
   DISPLAY "1. Resident"
   DISPLAY "2. Administrator"
   DISPLAY "3. Collection Team"
   DISPLAY "4. Exit"
   INPUT choice
   IF choice = 1 THEN
       CALL Resident_Module
   ELSE IF choice = 2 THEN
       CALL Administrator_Module
   ELSE IF choice = 3 THEN
       CALL Collection_Module
   ELSE IF choice = 4 THEN
       DISPLAY "Thank you for using the system"
 
   ELSE
      DISPLAY "Invalid choice" 
   END IF
 
END
END
Waste Reporting
BEGIN Resident_Module
   DISPLAY "Enter your full name"
   INPUT resident_name
   DISPLAY "Enter your location"
  INPUT location
   DISPLAY "Enter waste category"
   INPUT waste_category
   DISPLAY "Describe the waste problem"
   INPUT description
   IF resident_name = EMPTY OR location = EMPTY
     OR description = EMPTY THEN
       DISPLAY "Please complete all required fields"
   ELSE
       GENERATE report_ID
       SAVE resident_name
       SAVE location
       SAVE waste_category
       SAVE description
       SET status = "Pending"
       DISPLAY "Report submitted successfully"
       DISPLAY "Report ID: ", report_ID
   END IF
END Resident_Module
Report Verification
BEGIN Administrator_Module
   INPUT username
   INPUT password
   IF login_details_are_valid THEN
       DISPLAY "Administrator Dashboard"
      RETRIEVE submitted_reports
       FOR EACH report IN submitted_reports DO
          DISPLAY report_details
           DISPLAY "Approve or Reject Report"
           INPUT decision
          IF decision = "Approve" THEN
               SET status = "Verified"
              ASSIGN collection_team
               DISPLAY "Team Assigned"
           ELSE
               SET status = "Rejected"
               DISPLAY "Report Rejected"
           END IF
 
       END FOR
   ELSE
       DISPLAY "Invalid Login Details"
   END IF
END Administrator_Module
Collection Status Update
BEGIN Track_Report
   DISPLAY "Enter Report ID"
   INPUT report_ID
   SEARCH database FOR report_ID
   IF report_ID EXISTS THEN
       RETRIEVE report_status
       DISPLAY "Report Status: ", report_status
   ELSE
      DISPLAY "Report Not Found"
   END IF
END Track_Report
 
