***Elastic***

**Objective**

Implement and optimize an Elastic Stack (Elasticsearch, Logstash, and Kibana) solution to centralize, analyze, and visualize system logs and application data, improving real-time monitoring, troubleshooting efficiency, and decision-making through actionable insights.
- Using TryHackMe questions

  **Steps**

Log into Elastic

![image](https://github.com/user-attachments/assets/c1ffb51c-122b-43f0-b651-a6f5973810ae)

Navigate to discover from the hamburger menu on the left 

![image](https://github.com/user-attachments/assets/82c48067-659b-4b48-8397-e5db7db34466)

Set absolute time to Dec 1st 9:00am - Dec 1st 9:30am

![image](https://github.com/user-attachments/assets/cf3ae7c4-1945-4e6d-9740-e0cc0b1aa0ed)

Since there is too much data I will create columns using the search field names starting with host.hostname

![image](https://github.com/user-attachments/assets/eb28cbf0-1579-4c62-8965-579e69b762ea)

user.name

![image](https://github.com/user-attachments/assets/6a5d79e7-6df0-47da-80a1-4ec8c7395ff7)

event.category

![image](https://github.com/user-attachments/assets/6a0fba2c-f5a5-46da-85b0-c771776507f2)

process.command_line to show any malicious scripts 

![image](https://github.com/user-attachments/assets/fa6639fa-f7d2-4a6e-a4b2-d1727df957c2)

event.outcome to show if the event was successful or not

![image](https://github.com/user-attachments/assets/a9b622fb-0413-4583-bb36-7e76ea8dcabb)

Now I can see that the service admin account has ran successful powershell scripts 

![image](https://github.com/user-attachments/assets/ca18bd51-a44c-489e-8760-1fee711d3989)

Now I will add a source.ip to filter out the ip address

![image](https://github.com/user-attachments/assets/25c5204c-81bb-40e8-aae3-b2a94d743a4d)

I need to see when this first occured so I will set back my start date to November 29th

![image](https://github.com/user-attachments/assets/d57d09e4-0e46-4841-8f2f-6df623081c89)

There is 6,814 hits  

![image](https://github.com/user-attachments/assets/06b896b8-d270-439e-bd4e-b2d4d4da37d3)

I will narrow this down with a filter by using the servie admin name 

![image](https://github.com/user-attachments/assets/0e55720b-aa96-48b5-abc2-ae93e7635f98)

I will also filter using the source ip address 

![image](https://github.com/user-attachments/assets/1f54ac2d-e7d1-400f-aad2-f377b4b9ce82)

It filtered down to 5,702 hits

![image](https://github.com/user-attachments/assets/888d8498-abf5-4c2d-a966-f323348325a6)

Seems to be a password spraying attack.
now I will filter down for authentication 

![image](https://github.com/user-attachments/assets/7545fe0a-3958-4383-927f-54903ffa1b6b)

Aslo, I will filter out the source ip to see if there is another source ip being used
a new source ip of 10.0.255.1 has now appeared with 1,100 hits
with a successful event outcome

![image](https://github.com/user-attachments/assets/aaa10493-cf90-4cbc-a395-7fc02caf29f2)

now I will remove the filters and investgate the powershell command

![image](https://github.com/user-attachments/assets/5a11a0bc-3bba-4419-b08d-7720086b9834)

I will take the powershell command and run it in CyberChef
using a base64 encoding it shows Install-WindowsUpdate -AcceptAll -AutoReboot

![image](https://github.com/user-attachments/assets/e31afcbc-3864-4f2d-b28e-d350368b5df5)

using all of the data I collected I answered all of the TryHackMe questions correctly

![image](https://github.com/user-attachments/assets/e36824fb-2145-4b82-8654-d83c23dfbc4e)












































