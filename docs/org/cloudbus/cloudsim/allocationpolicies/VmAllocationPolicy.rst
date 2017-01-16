.. java:import:: java.util Collections

.. java:import:: java.util List

.. java:import:: java.util Map

.. java:import:: org.cloudbus.cloudsim.datacenters Datacenter

.. java:import:: org.cloudbus.cloudsim.hosts Host

.. java:import:: org.cloudbus.cloudsim.vms Vm

VmAllocationPolicy
==================

.. java:package:: org.cloudbus.cloudsim.allocationpolicies
   :noindex:

.. java:type:: public interface VmAllocationPolicy

   An interface to be implemented by each class that represents a policy used by a \ :java:ref:`Datacenter`\  to choose a \ :java:ref:`Host`\  to place or migrate a given \ :java:ref:`Vm`\ .

   :author: Manoel Campos da Silva Filho

Fields
------
NULL
^^^^

.. java:field::  VmAllocationPolicy NULL
   :outertype: VmAllocationPolicy

   A property that implements the Null Object Design Pattern for \ :java:ref:`VmAllocationPolicy`\  objects.

Methods
-------
allocateHostForVm
^^^^^^^^^^^^^^^^^

.. java:method::  boolean allocateHostForVm(Vm vm)
   :outertype: VmAllocationPolicy

   Allocates a host for a given VM.

   :param vm: the VM to allocate a host to
   :return: $true if the host could be allocated; $false otherwise

allocateHostForVm
^^^^^^^^^^^^^^^^^

.. java:method::  boolean allocateHostForVm(Vm vm, Host host)
   :outertype: VmAllocationPolicy

   Allocates a specified host for a given VM.

   :param vm: the VM to allocate a host to
   :param host: the host to allocate to the given VM
   :return: $true if the host could be allocated; $false otherwise

deallocateHostForVm
^^^^^^^^^^^^^^^^^^^

.. java:method::  void deallocateHostForVm(Vm vm)
   :outertype: VmAllocationPolicy

   Releases the host used by a VM.

   :param vm: the vm to get its host released

getDatacenter
^^^^^^^^^^^^^

.. java:method::  Datacenter getDatacenter()
   :outertype: VmAllocationPolicy

   Gets the \ :java:ref:`Datacenter`\  associated to the Allocation Policy.

getHostList
^^^^^^^^^^^

.. java:method::  <T extends Host> List<T> getHostList()
   :outertype: VmAllocationPolicy

   Gets the list of Hosts available in a \ :java:ref:`Datacenter`\ , that will be used by the Allocation Policy to place VMs.

   :param <T>: The generic type
   :return: the host list

optimizeAllocation
^^^^^^^^^^^^^^^^^^

.. java:method::  Map<Vm, Host> optimizeAllocation(List<? extends Vm> vmList)
   :outertype: VmAllocationPolicy

   Optimize allocation of the VMs according to current utilization.

   :param vmList: the vm list
   :return: the new vm placement map, where each key is a VM and each value is the host where such a Vm has to be placed

setDatacenter
^^^^^^^^^^^^^

.. java:method::  void setDatacenter(Datacenter datacenter)
   :outertype: VmAllocationPolicy

   Sets the Datacenter associated to the Allocation Policy

   :param datacenter: the Datacenter to set
