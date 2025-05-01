### Remote Desktop (RDP)
> Similar to a Secure Shell connection, the Remote Desktop Protocol connection should not be exposed to the Internet, as it would be considered a poor security practice (without using a VPN, for example).
1. Enable the built-in Remote Desktop Protocol (RDP) client in Windows 11.
   ![enable_rdp_on_windows_(rdp_server)](https://github.com/vitaliizghonnik/it-support-ticketing-lab/blob/main/Remote%20Access/screenshots/rdp_screenshots/enable_rdp_on_windows_(rdp_server).png)
2. Install Remmina Remote Desktop Client software on the Ubuntu VM Client.
   ```bash
   sudo apt install remmina
   ```
3. Launch the Remmina Remote Desktop Client software on Ubuntu and choose RDP protocol connection. Enter the IP Address of the Windows 11 RDP Server to connect to, like 192.168.133.134.
   ![rdp_to_windows_form_ubuntu.png](https://github.com/vitaliizghonnik/it-support-ticketing-lab/blob/main/Remote%20Access/screenshots/rdp_screenshots/rdp_to_windows_form_ubuntu.png)
