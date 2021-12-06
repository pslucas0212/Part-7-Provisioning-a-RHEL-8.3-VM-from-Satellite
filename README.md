# Part 7: Provisioning a RHEL 8.3 VM from Satellite

[Tutorial Menu](https://github.com/pslucas0212/RedHat-Satellite-VM-Provisioning-to-vSphere-Tutorial)

Now that we completed all of our prep work we can provision VMs on VMWware based on specificaitons we defined in the compute profile that we created in an earlier section.  As part of the provisioning process Satellite will get an available IP address from our DHCP server, update the forward and reverse DNS zone records. and register the VM to both our Satellite server and Red Hat Insights.

First make sure we have selected the Operations Department and moline for the orgainzation and location.  On the side menu chose Hosts -> Create Host.

![Host -> Create Host](/images/sat95.png)

On the All Hosts > Create Hosts page will start with the Host tab.  For this exercise I'm letting Satellite generate a random name for the server, but you could of course enter a name that follows your ogranization's server naming standards.  Chose the following options to complete this tab.

Option Name | Choice
----------- | ------
Host Group | hg-rhel8-prem-server

![Host Group](/images/sat96a.png)

You will notice that all the other fields will be automatically populated.  The Virtual Machine tab has been pre-populated with the information from the compute profile we created.  Please feel free to reveiw this tab.  Next we will choose the Operating System tab.

On the Operating System tab chose the following settings for the options listed below

Option Name | Choice
----------- | ------
Provisioning Method | Image Based
Image | img-rhel8-prem-server

Next click the Resolve button next to the Provisioning Templates option.  Make sure that you see the UserData open-vm-tools template.  Type in the root password for this system. 

![Operating Systems](/images/sat97b.png)

Now click the Interfaces tab.  You should see that Satellite has already asked for an ip address from our DHCP server.  You click the blue Submit button to start the provisioning process.

![Interfaces](/images/sat98a.png)

You'll next see the steps in the provisioning process.

![Example Provisioning Process](/images/sat99.png)

And then you will see on the All Hosts screen the VM you just provisioned.  When the provisioning is completed the Build status will change from Pending installation to 

## References  
[Installing Satellite Server from a Connected Network](https://access.redhat.com/documentation/en-us/red_hat_satellite/6.9/html/installing_satellite_server_from_a_connected_network/index)   
[Simple Content Access](https://access.redhat.com/articles/simple-content-access)  
[Provisioning VMWare using userdata via Satellite 6.3-6.6](https://access.redhat.com/blogs/1169563/posts/3640721)  
[Understanding Red Hat Content Delivery Network Repositories and their usage with Satellite 6](https://access.redhat.com/articles/1586183)

