<p align="center">

  ![image](https://github.com/user-attachments/assets/461b0cb7-b956-4063-88e4-315506a4cc12)

</p>

<h1>DNS Traffic and Local Cache Exercises</h1>
In this tutorial, we will observe DNS traffic between our VM and Server. <br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools


<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Windows Server 2022


<h2>Actions and Observations</h2>

<p>

![Screenshot 2024-11-14 211324](https://github.com/user-attachments/assets/f4cd7497-d7ec-4fbf-b2ed-4069c5b8ec5b)

![Screenshot 2024-11-14 211531](https://github.com/user-attachments/assets/d1db7fa3-8528-4976-8a11-12ff934aec59)

![Screenshot 2024-11-14 211717](https://github.com/user-attachments/assets/6ecf5ac7-f61e-4300-91f9-bbdf62409772)

</p>
<p>
A-Record Exercise:

Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)

Connect/log into Client-1 as an admin (mydomain\jane_admin)

From Client-1 try to ping “mainframe” notice that it fails, in Powershell

Nslookup “mainframe” notice that it fails (no DNS record)

Create a DNS A-record on DC-1 for “mainframe” and have it point to DC-1’s Private IP address

Go back to Client-1 and try to ping it. Observe that it works

</p>
<br />

<p>

![Screenshot 2024-11-14 211920](https://github.com/user-attachments/assets/7ce6a3fd-1fb1-4f1d-bdd8-885be3b346d2)

![Screenshot 2024-11-14 212109](https://github.com/user-attachments/assets/a04063df-bf49-4bda-b55b-595105f8ce03)

</p>
<p>
Local DNS Cache Exercise:

Go back to DC-1 and change mainframe’s record address to 8.8.8.8

Go back to Client-1 and ping “mainframe” again. Observe that it still pings the old address

Observe the local dns cache (ipconfig /displaydns)

Flush the DNS cache (ipconfig /flushdns).

Observe that the cache is empty (ipconfig /displaydns)

Attempt to ping “mainframe” again. Observe the address of the new record is showing up

</p>
<br />

<p>

![Screenshot 2024-11-14 212410](https://github.com/user-attachments/assets/d9b9a706-4b8c-4340-932e-8b28580ba68d)

![Screenshot 2024-11-14 212531](https://github.com/user-attachments/assets/01a3251a-1300-478f-a36e-296928f9eaa7)

![Screenshot 2024-11-14 212620](https://github.com/user-attachments/assets/f0e038ea-090d-461a-afb9-3a66b07871e7)

</p>
<p>
CNAME Record Exercise

Go back to DC-1 and create a CNAME record that points the host “search” to “www.google.com”

Go back to Client-1 and attempt to ping “search”, observe the results of the CNAME record

On Client-1, nslookup “search”, observe the results of the CNAME record

</p>
<br />
