# Vmware-HA

VMware HA Details 



Hi everybody

As we know VMWare Vsphere is a something like a complate solution for Virtualization and one of the famous component of Vsphere is ESXI(Hypervisor).

After Installation Hypervisor on the our Hosts we can manage there via another Vsphere Component that name is VCenter.

Vcenter have so many Feature for our Data Center and one of that is HA or High Availability.

But what tasks doing HA and What is HA for Virtualization ? in the simple description HA is careful about our services and if one VM goes down or failed , HA can Restart that VM on another Host or if One Host complately goes down, HA can restart all of VMs was Run on failed Host.

That help to have a Data Center with small down time not without down time.

But how it work ? HA have different subcomponent and have some prerequisites for enabling it on our Cluster.

when we decide to have HA in our Data Center in the first step we must create Cluster in VCenter and then Enable HA then Add two or more Host to that.

In the HA Enabled Cluster we have two type of Host HA Agent:

Master

Slave

All of Hosts in the cluster is one of this type, but keep in your mind we have only one Master Agent and another Hosts are Slave.

Master Agent:

Each host become Master Agent have different task by other Hosts become Slave.

Master Agent get status of VMs from Slave Hosts and send that information to VCenter and if VCenter change a Config of something, Master represent that config to slave hosts.

And one of important Task of Master Agent is about detect a Host was Failed and now which VMs must be Restarted on another Host and restart on which Host.

If one Host goes down, Master Agent send that information to VCenter, But if Master Agent goes down what happened ? as we talk before it, we have only one Master Agent without any redundant or backup or any other option, by the way, when Master Agent goes down and Slaves doesn't receive any heartBeat from her Master Agent, they know Master was Failed and all of Slaves must doing an Election to select who is next Master Agent, and this takes time about 15 second and after Master Agent was defined, Master Agent try to Restart Failed VMs on another Hosts, keep in minde your Network services was running on Master Agent won't be Restarted after 15 Second to Define new Master Agent. and then Master Agent send Slave Information to VCenter.



Ok, this is part one of VMWARE HA and another part coming soon.

Best Regard.



