# BseriesV2
Deploying a basic website on Azure B series v2 Burstable VMs 


Welcome to my Personal Bseries v2 Repository!

This repository contains code for deploying a basic web app workload on the new [Azure B series v2 VMs](https://techcommunity.microsoft.com/t5/azure-compute-blog/announcing-public-preview-of-new-burstable-vms-bsv2-basv2-and/ba-p/3868024). 
The goal of this repository is to showcase a lightweight workload that is suitable for Azure B series v2 VM type, which can be used by the community to follow begin/upgrade their Azure journey with B series (CPU burstable VMs. 


A) Prerequisites:- 
1) Deploy an Azure Linux VM (b2alsv2 size used in the demo).
2) (Optional) Ensure your VM has > 1 core or 2 vCPUs and 4 GiB of RAM. Linux command = cat /proc/cpuinfo


B) Install Apache 
1) sudo apt update
2) sudo apt install -y apache2

C) Enable 80 port in VM security configurations - required to host website publicly
1) Create a new Security inbound port rule = got to VM overview in Azure portal -> click on Networking settings (on the left bar) -> click on blue "Add inbound Rule -> Set destination port to 80 and give it a name + click "add"

D) Validate Apache functionality
1) sudo systemctl status apache2
2) Paste the public Ip of the VM in the browser to validate server running

E) Download website files in the VM in the apache directory
1) git clone https://github.com/rishabv90/BseriesV2.git - or any other files you have (git is already installed)
2) Remove Apache homepage - sudo rm /var/www/html/index.html
3) Copy current html files to the apache directory = sudo cp -r * /var/www/html/
4) Restart the Apache server - sudo systemctl restart apache2
5) Check the status of server - sudo systemctl status apache2
6) Refresh the Ip address website to see HTML file 
