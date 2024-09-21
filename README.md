# inventory-discrepancy-report

# Demo
![ezgif com-animated-gif-maker](https://github.com/user-attachments/assets/2f05721a-692a-44ed-9ff8-bd372091d444)

# Summary

Created a discrepancy report in Power BI that identify discrepant inventory records between two databases and sends near real time e-mail alert to business stakeholders.

# Description

Inventory plays a critical role in the success of any retail business. Discrepancies or issues within the inventory can disrupt the entire business process, leading to potential losses and customer dissatisfaction. Timely identification and resolution of inventory problems are essential for maintaining operational efficiency. To address this challenge, I developed a robust solution using Power BI that automatically detects inventory discrepancies in near real-time. The system not only identifies mismatches but also triggers automated email alerts to business stakeholders, enabling prompt corrective action and minimizing potential disruptions.

**Tools used:** AWS RedShift, Microsoft Power BI

# Flow Diagram

![Inventory Discrepancy - Page 2](https://github.com/user-attachments/assets/26f75067-1a30-4d20-a85c-b127640b5d7c)

# Steps

1. Create two mockup databases (Source & Destination) in Amazon RedShift.
2. Connect Power BI with RedShift through DirectQuery mode, ensuring inventory updates in RedShift are reflected in near real-time in Power BI.
   Build the following features in Power BI:
   2.1. Inventory Dashboard: Provides a real-time view of the current inventory state, leveraging data from the source system.
   2.2. Inventory Audit (Main Feature): Performs checks for any mismatches between the Source and Destination databases. If discrepancies are detected, Power BI triggers an alert, prompting the relevant user to take immediate action.

**Inventory Dashbaord**
This dashboard offers a real-time snapshot of the inventory using card visuals and charts. Additionally, an **Understock Alert Slicer** allows users to filter locations with a supply quantity lower than the safety stock, helping prevent out-of-stock issues.

Sample Image
![image](https://github.com/user-attachments/assets/734c33e1-fe00-4a4f-a7e6-b1094b797dc6)

**Inventory Audit**
Data from both databases are merged in Power Query Editor. Using the in_eq measure, mismatches between inventory buckets in the two databases are identified. Once a mismatch is detected, an arrow icon appears in the relevant bucket of the destination table, indicating whether the source database holds a higher or lower quantity than the destination database.

![mismatchinvaudit](https://github.com/user-attachments/assets/2d0c923e-3276-448c-bff1-2157197c7b2e)

**Email alert**
An alert system in Power BI monitors the in_eq measure. When the value changes from 0 to 1, an automatic email is triggered, notifying all listed recipients with a custom message. Note: Due to trial account limitations, the refresh rate is set to 1 hour, meaning alerts will check for changes every hour.
![image](https://github.com/user-attachments/assets/f11ebdf1-f38a-487e-a543-e60355b17878)
