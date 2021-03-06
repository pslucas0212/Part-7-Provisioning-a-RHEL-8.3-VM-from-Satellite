# Part 7: Provisioning a RHEL 8.3 VM from Satellite

[Tutorial Menu](https://github.com/pslucas0212/RedHat-Satellite-VM-Provisioning-to-vSphere-Tutorial)

Now that we have completed all of our prep work we can now provision VMs to our VMWware cluster using the specification we defined in the compute profile.  As part of the provisioning process Satellite will request an available IP address from our DHCP server, update the forward and reverse DNS zone records, provision the VM on our VMWare cluster, and register the new RHEL VM to both our Satellite server and Red Hat Insights.

First make sure we have selected the Operations Department and moline for the organizations and location.  On the side menu choose Hosts -> Create Host.

![Host -> Create Host](/images/sat95.png)

On the All Hosts > Create Hosts page will start with the Host tab.  For this exercise I'm letting Satellite generate a random hostname for the server, but you could of course enter a hostname that follows your organization's server naming standards.  Choose the following options to complete this tab.

Option Name | Choice
----------- | ------
Host Group | hg-rhel8-prem-server

![Host Group](/images/sat96a.png)

You will notice that all the other fields are automatically populated.  The Virtual Machine tab has been pre-populated with the information from the compute profile we created.  Please feel free to review this tab.  Next we will choose the Operating System tab.

On the Operating System tab chose the following settings for the options listed below

Option Name | Choice
----------- | ------
Provisioning Method | Image Based
Image | img-rhel8-prem-server

Next click the Resolve button next to the Provisioning Templates option.  Make sure that you see the UserData open-vm-tools template.  Type in the root password for this system. 

![Operating Systems](/images/sat97b.png)

Now click the Interfaces tab.  You should see that Satellite has already assigned an ip address to our new RHEL VM.  You can now click the blue Submit button to start the provisioning process.

![Interfaces](/images/sat98a.png)

After clicking the blue Submit button, you will next see the steps in the provisioning process on the All Hosts > Create Host page.

![Example Provisioning Process](/images/sat99.png)

After the RHEL VM has been provisioned and while the installation is progressing, you will see on the All Hosts screen for your new VM.  Next click the clear link found next to the Pending Installation message in the Build Properties field.

![Click the clear link](/images/sat100.png)

You will now see that the properties section has changed and the Status property is reporting an Error.  The Error indicates that there are available RHEL security errata that can be applied to our new RHEL VM.  Click the clear link next to the Security errata applicable status found in the Errata property field to clear the Error status.  

![Click the clear lin](/images/sat101.png)

On the side menu Hosts | Content Hosts to navigate to our newly provisioned VM.

![Hosts | Content Hosts](/images/sat102.png)

On the Content Hosts page you will see that our VM is registered with Satellite and its most recent checkin date with our Satellite server.  Also you will see the number of installable updates available.  We will cover installing updates and patches in a future tutorial.

![Content Hosts Page](/images/sat103.png)

Let's make sure our new RHEL VM is registered to Insights.  Navigate to the [Red Hat Hybrid Cloud](https://cloud.redhat.com/) and login.  Click on the Console log in link in the upper right and corner and follow the Red Hat login and password prompts.

![Red Hat Hybrid Cloud](/images/sat104.png)

Now you will be at the Red Hat Hybrid Cloud Console. On the Hybrid Cloud Console you'll see a dashboard for RHEL, Red Hat App services, Ansible Automation Platform and OpenShift.  Also you'll find recommended tools and articles for you to explore.

On the side menu click the Red Hat Enterprise Linux link to navigate to Red hat Enterprise Linux Insights.  From the Red Hat Insights page: "Included with Red Hat subscriptions, Insights uses predictive analytics and deep domain expertise to reduce complex operational tasks from hours to minutes, including identifying security and performance risks, tracking licenses, and managing costs."

For more information see the links in the Insights Articles section below.

![Red Hat Hybrid Cloud Console](images/sat105.png)

Now we will see the Red Hat Enterprise Linux Insights page.  On the side menu, click the Inventory link.

![RHEL Insights](/images/sat106.png)

On the Inventory page, we see that our VM has been successfully registered with Insights.  In a future article we will look at how to automatically push updates from the Insight page to a VM managed by Satellite.

![Insights Inventory](/images/sat107.png)

This concludes our series on provisioning VMs to VMWare from Satellite.  This series gives you a small glimpse into the capabilities of Satellite.  Satellite provides us with an easy way to curate content, provision new RHEL systems and patch/update RHEL systems for our RHEL environments across all deployment platforms on-prem and in the cloud.

## Insights Articles
[Red Hat Insights: Predictive analytics for Red Hat Enterprise Linux](https://www.redhat.com/en/resources/insights-predictive-risk-analytics-datasheet)  
[Save administrator time and effort by activating Red Hat Insights to automate monitoring](https://www.redhat.com/cms/managed-files/ma-save-administrator-time-analyst-paper-f25355-202009-en.pdf)



## References  
[Installing Satellite Server from a Connected Network](https://access.redhat.com/documentation/en-us/red_hat_satellite/6.9/html/installing_satellite_server_from_a_connected_network/index)   
[Simple Content Access](https://access.redhat.com/articles/simple-content-access)  
[Provisioning VMWare using userdata via Satellite 6.3-6.6](https://access.redhat.com/blogs/1169563/posts/3640721)  
[Understanding Red Hat Content Delivery Network Repositories and their usage with Satellite 6](https://access.redhat.com/articles/1586183)

