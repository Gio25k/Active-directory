#  VM creation & testing connectivity
<p align="center">



This tutorial outlines the  VM creation & testing connectivity.<br />






<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)



<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.gyazo.com/0f4b091705c9b18d9e2e63b6a2562189.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Within Azure, Create a resource group
  Create a Virtual Network and select the new resource group you created
  ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
</p
<br />

<p>
<img src="https://i.gyazo.com/d03ad05cdbe36115c7b2cf9cd217bb17.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a new virtual machine and name it DC-1
  Under the Image tab select Windows Server 2022 Datacenter:Azure Edition
  Always Make sure you confirm your lisence when creating.
  "Size" at least 2vcpus
</p>
<br />

<p>
<img src="https://i.gyazo.com/6c658f66dd6fccb357470ce1d73f0ded.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to "Networking" Tab and under virtual network select the virtual network you previously created.
</p>
<br />
<p>
<img src="https://i.gyazo.com/3ae9c596c5bfd56e8d69ee36f704e7c9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />

<p>
<img src="https://i.gyazo.com/9433a1a58dc58a23b1967768497d022a.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Change your Domain Controllers Private IP Address to "Static"
  Go to network settings in DC-1 VM. Click on "Network Interface / IP Configuration" box
  Click on "ipconfig1" And then next to Allocation you switch from dynamic to static and save.
</p>
<br />

<p>
<img src="https://i.gyazo.com/e575c25b1415fa3e3b12726bcc1b46dc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to "Windows Defender Firewall with Advanced Security" and click "Windows Defender Firewall Properties"
</p>
<br />
<p>
<img src="https://i.gyazo.com/9614fcb1478174ec8166c0efc46d6067.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Turn off "Firewall State" in the 3 tabs "Domain Profile", "Private Profile", and "Public Profile"
Make sure you click "Apply" and "Ok" to continue on
</p>
<br />

<p>
<img src="https://i.gyazo.com/ef20a0fe2263aba5329834ae4d568bc0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Retrieve DC-1 VM private IP address and copy it
Navigate to Client-1 VM -> Network Settings -> click on "Network Interface / IP configuration" box
On the left side of window, click on "DNS servers"

</p>
<br />
<p>
<img src="https://i.gyazo.com/d6a1447e3925118aad36f285db21db79.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
Under "DNS servers", select the "Custom" option and paste the DC-1 private IP address

<p>



<img src="https://camo.githubusercontent.com/9cbc328a84031a431502655f70f0ec16fcf10cf14560a806a2c0dd6bcb488442/68747470733a2f2f692e696d6775722e636f6d2f38677a644373362e706e67" height="80%" width="80%" alt="Disk Sanitization Steps"/>
Within the Client-1 VM, open PowerShell
Ping the Domain Controller by typing "ping(private IP address)" (Example: ping 10.0.0.4)
Observe and make sure the ping is successful
</p>
<br />
