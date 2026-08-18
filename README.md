# OpenPLC-FUXA

In this repository you will find all the relevant OpenPLC code and FUXA underlying connections (tag) and UI code for the demo I posted on Linkedin article https://www.linkedin.com/pulse/demonstration-openplc-fuxa-athanasios-rizoulis-kktif/

This demonstration was made possible with OpenPLC-runtime v4.1.9, OpenPLC-Editor v4.2.11, and FUXA 1.3.3
Work progresses fast on these repositories, so just download the latest you find.

Virtual Machines were installed on Oracle VM Virtualbox.
Typical settings are: two vCPUs, two GB RAM, host only networking.

OpenPLC-runtime and FUXA are two different VMs.
OpenPLC-Editor is run from the host (doable because of host only networking configuration)

General installation guidelines
-------------------------------
01. Get the latest OpenPLC-runtime v4 here https://github.com/Autonomy-Logic/openplc-runtime
02. OpenPLC IP address is expected to be 192.168.56.21 / 24 and 192.168.56.21:502 is the MODBUS port that FUXA server connects to.
03. Take note of the credentials for the OpenPLC runtime.
04. They will have to be entered every time you start the OpenPLC-Editor and connect to the runtime.
05. Once installed, the service starts on its own.

06. Get the latest OpenPLC-Editor v4 here https://github.com/Autonomy-Logic/openplc-editor
07. Download and open the provided project "OpenPLC-FUXA Modbus Mapping"
08. Connect to the OpenPLC runtime using the Device-Configuration menu pane (left).
09. You will have to "Clean Build and Upload" once ("Play" icon at the left icon bar).
09. The PLC should transition to "RUNNING" condition.
10. You can enter debug mode from the left icon bar (bug icon).
11. Select variable you want to monitor and add them to the debug list using the "Table icon" (top right) and selecting all the "bugs" you need.
12. Make sure Servers-Modbus server (left) is running at port 502 (this is where FUXA connects)

13. Get the latest FUXA server here https://github.com/frangoteam/FUXA
14. FUXA IP address is expected to be 192.168.56.22 / 24 and 192.168.56.22:1881 is the management interface / editor
15. I installed from source, so I had to start the server manually with:
16. $ cd ~/FUXA-1.3.3/server
17. $ npm start
18. Initially FUXA will produce a lot of connection errors. This is normal as the configuration is not imported yet.
20. Enter the FUXA configuration menu (gear icon).
Go to Plugins and install modbus-serial (this is the only one needed).  
Go to Connections and import the provided "fuxa-connections.json" (top right).  
Verify that FUXA-OpenPLC connection has the green dot at the lower left.  
This should also pull in all MODBUS tag mappings to the OpenPLC-runtime. Some values should appear on the list.  
Go to the "save icon" (top left next to the gear icon) select "Open project" and open the provided "fuxa-project.json".  

At this point you should be able to use the controls and manage the OpenPLC-runtime directly.  
Congratulations!





