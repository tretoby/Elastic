# **Elastic Stack: Centralized Log Analysis and Threat Detection**

## **Objective**  
Implement and optimize the Elastic Stack (**Elasticsearch**, **Logstash**, and **Kibana**) to centralize, analyze, and visualize system logs and application data. This project enhances real-time monitoring, streamlines troubleshooting, and provides actionable insights.  
This task also includes answering **TryHackMe** questions using the Elastic Stack.

---

## **Steps**

### **1. Log into Elastic**  
Start by logging into the Elastic Stack dashboard.  
![image](https://github.com/user-attachments/assets/c1ffb51c-122b-43f0-b651-a6f5973810ae)

---

### **2. Navigate to the Discover Tab**  
Access the **Discover** section from the hamburger menu on the left-hand side.  
![image](https://github.com/user-attachments/assets/82c48067-659b-4b48-8397-e5db7db34466)

---

### **3. Set the Time Range**  
Adjust the time range to **December 1st, 9:00 AM - December 1st, 9:30 AM** using the **absolute time** setting.  
![image](https://github.com/user-attachments/assets/cf3ae7c4-1945-4e6d-9740-e0cc0b1aa0ed)

---

### **4. Create Search Columns for Better Clarity**  
Use the search field to create columns for easier data analysis:  

#### **a. Add `host.hostname`**  
![image](https://github.com/user-attachments/assets/eb28cbf0-1579-4c62-8965-579e69b762ea)

#### **b. Add `user.name`**  
![image](https://github.com/user-attachments/assets/6a5d79e7-6df0-47da-80a1-4ec8c7395ff7)

#### **c. Add `event.category`**  
![image](https://github.com/user-attachments/assets/6a0fba2c-f5a5-46da-85b0-c771776507f2)

#### **d. Add `process.command_line`**  
Reveal malicious scripts by adding the `process.command_line` field.  
![image](https://github.com/user-attachments/assets/fa6639fa-f7d2-4a6e-a4b2-d1727df957c2)

#### **e. Add `event.outcome`**  
Check whether events were successful by adding `event.outcome`.  
![image](https://github.com/user-attachments/assets/a9b622fb-0413-4583-bb36-7e76ea8dcabb)

---

### **5. Identify Suspicious Activity**  
Analyze the data to find that the service admin account successfully ran PowerShell scripts.  
![image](https://github.com/user-attachments/assets/ca18bd51-a44c-489e-8760-1fee711d3989)

---

### **6. Add and Analyze Source IP**  
Include the `source.ip` field to filter and analyze IP addresses involved in the activity.  
![image](https://github.com/user-attachments/assets/25c5204c-81bb-40e8-aae3-b2a94d743a4d)

---

### **7. Investigate Initial Occurrence**  
Adjust the start date to **November 29th** to determine when the activity began.  
![image](https://github.com/user-attachments/assets/d57d09e4-0e46-4841-8f2f-6df623081c89)  

This search yields **6,814 hits**.  
![image](https://github.com/user-attachments/assets/06b896b8-d270-439e-bd4e-b2d4d4da37d3)

---

### **8. Narrow Down Results**  
#### **a. Filter by Service Admin Account**  
Apply a filter using the service admin account name.  
![image](https://github.com/user-attachments/assets/0e55720b-aa96-48b5-abc2-ae93e7635f98)

#### **b. Filter by Source IP**  
Further narrow down the results using the source IP address.  
![image](https://github.com/user-attachments/assets/1f54ac2d-e7d1-400f-aad2-f377b4b9ce82)  

This reduces the hits to **5,702**.  
![image](https://github.com/user-attachments/assets/888d8498-abf5-4c2d-a966-f323348325a6)

---

### **9. Investigate Authentication Events**  
Filter specifically for **authentication events** to identify suspicious login attempts.  
![image](https://github.com/user-attachments/assets/7545fe0a-3958-4383-927f-54903ffa1b6b)

---

### **10. Check for Additional Source IPs**  
Remove existing filters to uncover other potential source IP addresses. A new IP, **10.0.255.1**, is identified with **1,100 hits**, including successful events.  
![image](https://github.com/user-attachments/assets/aaa10493-cf90-4cbc-a395-7fc02caf29f2)

---

### **11. Investigate PowerShell Commands**  
Remove filters to investigate suspicious PowerShell commands used by the admin account.  
![image](https://github.com/user-attachments/assets/5a11a0bc-3bba-4419-b08d-7720086b9834)

---

### **12. Decode PowerShell Script with CyberChef**  
Take the PowerShell command and decode it using **CyberChef** with **Base64 encoding**. The decoded script reveals:  
`Install-WindowsUpdate -AcceptAll -AutoReboot`  
![image](https://github.com/user-attachments/assets/e31afcbc-3864-4f2d-b28e-d350368b5df5)

---

### **13. Answer TryHackMe Questions**  
Using the data collected throughout the analysis, all **TryHackMe** questions were answered correctly.  
![image](https://github.com/user-attachments/assets/e36824fb-2145-4b82-8654-d83c23dfbc4e)

---

## **Conclusion**  
This project demonstrates the power of the Elastic Stack in centralized log management and threat detection. By effectively filtering, analyzing, and correlating data, suspicious activities such as password spraying attacks and unauthorized PowerShell scripts were identified. The project highlights the importance of real-time log analysis for maintaining system security.







































