# Part 7: Provisioning a RHEL 8.3 VM from Satellite

[Tutorial Menu](https://github.com/pslucas0212/RedHat-Satellite-VM-Provisioning-to-vSphere-Tutorial)

Now that we completed all of our prep work we can provision VMs on VMWware based on specificaitons we defined in the compute profile we define.  As part of the provisioning process we will grab a an available ip addreess from our dhcp server, update the forward and reverse DNS zone records. and register the VM to both our Satellite server and Insights.

First make we have selected the Operations Department and molin for the orgainzation and location.  On the side menu chose Hosts -> Create Host.

![Host -> Create Host](/images/satxx.png)

On the All Hosts > Create Hosts page will start with the Host tab.  For this exercise I'm letting Satellite generate a random name for the server, but you could of course enter a name that follows your ogranization's server naming standards.  Chose the following options to complete this tab.

Option Name | Choice
----------- | ------
Host Group | hg-rhel8-prem-server

You will notice that all the other fields will be automatically populated.  The Virtual Machine tab has been pre-populated with the information from the compute profile we created.  Please feel free to reveiw this tab.  Next we will choose the Operating System tab.

On the Operating System tab chose the following settings for the options listed below

Option Name | Choice
----------- | ------
Provisioning Method | Image Based
Image | img-rhel8-prem-server

Next click the Resolve button next to the Provisioning Templates option.


## References  
[Installing Satellite Server from a Connected Network](https://access.redhat.com/documentation/en-us/red_hat_satellite/6.9/html/installing_satellite_server_from_a_connected_network/index)   
[Simple Content Access](https://access.redhat.com/articles/simple-content-access)  
[Provisioning VMWare using userdata via Satellite 6.3-6.6](https://access.redhat.com/blogs/1169563/posts/3640721)  
[Understanding Red Hat Content Delivery Network Repositories and their usage with Satellite 6](https://access.redhat.com/articles/1586183)

