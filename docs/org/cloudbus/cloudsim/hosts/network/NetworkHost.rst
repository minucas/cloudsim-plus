.. java:import:: java.util ArrayList

.. java:import:: java.util List

.. java:import:: org.cloudbus.cloudsim.hosts Host

.. java:import:: org.cloudbus.cloudsim.hosts HostSimple

.. java:import:: org.cloudbus.cloudsim.network HostPacket

.. java:import:: org.cloudbus.cloudsim.schedulers.cloudlet.network PacketScheduler

.. java:import:: org.cloudbus.cloudsim.schedulers.cloudlet CloudletScheduler

.. java:import:: org.cloudbus.cloudsim.schedulers.cloudlet.network PacketSchedulerSimple

.. java:import:: org.cloudbus.cloudsim.util Conversion

.. java:import:: org.cloudbus.cloudsim.util Log

.. java:import:: org.cloudbus.cloudsim.network.switches EdgeSwitch

.. java:import:: org.cloudbus.cloudsim.network VmPacket

.. java:import:: org.cloudbus.cloudsim.resources Pe

.. java:import:: org.cloudbus.cloudsim.schedulers.vm VmScheduler

.. java:import:: org.cloudbus.cloudsim.vms Vm

.. java:import:: org.cloudbus.cloudsim.core CloudSimTags

.. java:import:: org.cloudbus.cloudsim.lists PeList

.. java:import:: org.cloudbus.cloudsim.lists VmList

.. java:import:: org.cloudbus.cloudsim.provisioners ResourceProvisioner

NetworkHost
===========

.. java:package:: org.cloudbus.cloudsim.hosts.network
   :noindex:

.. java:type:: public class NetworkHost extends HostSimple

   NetworkHost class extends \ :java:ref:`HostSimple`\  to support simulation of networked datacenters. It executes actions related to management of packets (sent and received) other than that of virtual machines (e.g., creation and destruction). A host has a defined policy for provisioning memory and bw, as well as an allocation policy for PE's to virtual machines.

   Please refer to following publication for more details:

   ..

   * \ `Saurabh Kumar Garg and Rajkumar Buyya, NetworkCloudSim: Modelling Parallel Applications in Cloud Simulations, Proceedings of the 4th IEEE/ACM International Conference on Utility and Cloud Computing (UCC 2011, IEEE CS Press, USA), Melbourne, Australia, December 5-7, 2011. <http://dx.doi.org/10.1109/UCC.2011.24>`_\

   :author: Saurabh Kumar Garg

Constructors
------------
NetworkHost
^^^^^^^^^^^

.. java:constructor:: public NetworkHost(int id, long storage, List<Pe> peList)
   :outertype: NetworkHost

   Creates a NetworkHost.

   :param id: the id
   :param storage: the storage capacity
   :param peList: the host's PEs list

NetworkHost
^^^^^^^^^^^

.. java:constructor:: @Deprecated public NetworkHost(int id, ResourceProvisioner ramProvisioner, ResourceProvisioner bwProvisioner, long storage, List<Pe> peList, VmScheduler vmScheduler)
   :outertype: NetworkHost

   Creates a NetworkHost with the given parameters.

   :param id: the id
   :param ramProvisioner: the ram provisioner
   :param bwProvisioner: the bw provisioner
   :param storage: the storage capacity
   :param peList: the host's PEs list
   :param vmScheduler: the VM scheduler

Methods
-------
addReceivedNetworkPacket
^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: public void addReceivedNetworkPacket(HostPacket hostPacket)
   :outertype: NetworkHost

   Adds a packet to the list of received packets in order to further submit them to the respective target VMs and Cloudlets.

   :param hostPacket: received network packet

getBandwidth
^^^^^^^^^^^^

.. java:method:: public double getBandwidth()
   :outertype: NetworkHost

   Gets the Host bandwidth capacity in Megabits/s.

getEdgeSwitch
^^^^^^^^^^^^^

.. java:method:: public EdgeSwitch getEdgeSwitch()
   :outertype: NetworkHost

getMaxUtilizationAmongVmsPes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: public double getMaxUtilizationAmongVmsPes(Vm vm)
   :outertype: NetworkHost

   Gets the maximum utilization among the PEs of a given VM.

   :param vm: The VM to get its PEs maximum utilization
   :return: The maximum utilization among the PEs of the VM.

getTotalDataTransferBytes
^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: public int getTotalDataTransferBytes()
   :outertype: NetworkHost

setBandwidth
^^^^^^^^^^^^

.. java:method:: public void setBandwidth(double bandwidth)
   :outertype: NetworkHost

   Sets the Host bandwidth capacity in Megabits/s.

   :param bandwidth: the bandwidth to set

setEdgeSwitch
^^^^^^^^^^^^^

.. java:method:: public void setEdgeSwitch(EdgeSwitch sw)
   :outertype: NetworkHost

updateVmsProcessing
^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public double updateVmsProcessing(double currentTime)
   :outertype: NetworkHost

vmCreate
^^^^^^^^

.. java:method:: @Override public boolean vmCreate(Vm vm)
   :outertype: NetworkHost

   {@inheritDoc}

   It also creates and sets a  for each
   Vm that doesn't have one already.

   :param vm: {@inheritDoc}
   :return: {@inheritDoc}

