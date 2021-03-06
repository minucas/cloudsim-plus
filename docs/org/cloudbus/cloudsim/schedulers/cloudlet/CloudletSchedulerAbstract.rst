.. java:import:: java.util.function Consumer

.. java:import:: java.util.function Function

.. java:import:: java.util.stream Collectors

.. java:import:: java.util.stream Stream

.. java:import:: org.cloudbus.cloudsim.cloudlets Cloudlet

.. java:import:: org.cloudbus.cloudsim.cloudlets Cloudlet.Status

.. java:import:: org.cloudbus.cloudsim.cloudlets CloudletExecutionInfo

.. java:import:: org.cloudbus.cloudsim.resources Ram

.. java:import:: org.cloudbus.cloudsim.resources ResourceManageable

.. java:import:: org.cloudbus.cloudsim.schedulers.cloudlet.network PacketScheduler

.. java:import:: org.cloudbus.cloudsim.util Conversion

.. java:import:: org.cloudbus.cloudsim.util Log

.. java:import:: org.cloudbus.cloudsim.utilizationmodels UtilizationModel

.. java:import:: org.cloudbus.cloudsim.vms Vm

.. java:import:: org.cloudbus.cloudsim.resources Processor

CloudletSchedulerAbstract
=========================

.. java:package:: org.cloudbus.cloudsim.schedulers.cloudlet
   :noindex:

.. java:type:: public abstract class CloudletSchedulerAbstract implements CloudletScheduler

   Implements the basic features of a \ :java:ref:`CloudletScheduler`\ , representing the policy of scheduling performed by a virtual machine to run its \ :java:ref:`Cloudlets <Cloudlet>`\ . So, classes extending this must execute Cloudlets. The interface for cloudlet management is also implemented in this class. Each VM has to have its own instance of a CloudletScheduler.

   :author: Rodrigo N. Calheiros, Anton Beloglazov, Manoel Campos da Silva Filho

Constructors
------------
CloudletSchedulerAbstract
^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:constructor:: public CloudletSchedulerAbstract()
   :outertype: CloudletSchedulerAbstract

   Creates a new CloudletScheduler object. A CloudletScheduler must be created before starting the actual simulation.

Methods
-------
addCloudletToExecList
^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected void addCloudletToExecList(CloudletExecutionInfo cloudlet)
   :outertype: CloudletSchedulerAbstract

   Adds a Cloudlet to the list of cloudlets in execution.

   :param cloudlet: the Cloudlet to be added

addCloudletToFinishedList
^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected void addCloudletToFinishedList(CloudletExecutionInfo cloudlet)
   :outertype: CloudletSchedulerAbstract

addCloudletToWaitingList
^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected void addCloudletToWaitingList(CloudletExecutionInfo cloudlet)
   :outertype: CloudletSchedulerAbstract

cloudletCancel
^^^^^^^^^^^^^^

.. java:method:: @Override public Cloudlet cloudletCancel(int cloudletId)
   :outertype: CloudletSchedulerAbstract

cloudletExecutedInstructionsForElapsedTime
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected long cloudletExecutedInstructionsForElapsedTime(CloudletExecutionInfo rcl, double currentTime)
   :outertype: CloudletSchedulerAbstract

   Computes the length of a given cloudlet, in number of Instructions (I), that has been executed since the last time cloudlet processing was updated.

   This method considers the delay for actually starting the Cloudlet execution due to the time to transfer \ :java:ref:`required Cloudlet files <Cloudlet.getRequiredFiles()>`\  from the Datacenter storage (such as a SAN) to the Vm running the Cloudlet.

   During this transfer time, the method will always return 0 to indicate that the Cloudlet was not processed in fact, it is just waiting the required files to be acquired. The required time to transfer the files is stored in the \ :java:ref:`CloudletExecutionInfo.getFileTransferTime()`\  attribute and is set when the Cloudlet is submitted to the scheduler.

   :param rcl: the Cloudlet to compute the executed length
   :param currentTime: current simulation time
   :return: the executed length, in number of Instructions (I), since the last time cloudlet was processed.

   **See also:** :java:ref:`.updateCloudletsProcessing(double)`

cloudletFinish
^^^^^^^^^^^^^^

.. java:method:: @Override public void cloudletFinish(CloudletExecutionInfo rcl)
   :outertype: CloudletSchedulerAbstract

cloudletPause
^^^^^^^^^^^^^

.. java:method:: @Override public boolean cloudletPause(int cloudletId)
   :outertype: CloudletSchedulerAbstract

cloudletSubmit
^^^^^^^^^^^^^^

.. java:method:: @Override public double cloudletSubmit(Cloudlet cloudlet)
   :outertype: CloudletSchedulerAbstract

cloudletSubmit
^^^^^^^^^^^^^^

.. java:method:: @Override public double cloudletSubmit(Cloudlet cl, double fileTransferTime)
   :outertype: CloudletSchedulerAbstract

findCloudletInAllLists
^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected Optional<CloudletExecutionInfo> findCloudletInAllLists(double cloudletId)
   :outertype: CloudletSchedulerAbstract

   Search for a Cloudlet into all Cloudlet lists.

   :param cloudletId: the id of the Cloudlet to search for
   :return: an \ :java:ref:`Optional`\  value that is able to indicate if the Cloudlet was found or not

findCloudletInList
^^^^^^^^^^^^^^^^^^

.. java:method:: protected Optional<CloudletExecutionInfo> findCloudletInList(double cloudletId, List<CloudletExecutionInfo> list)
   :outertype: CloudletSchedulerAbstract

   Search for a Cloudlet into a given list.

   :param cloudletId: the id of the Cloudlet to search for
   :param list: the list to search the Cloudlet into
   :return: an \ :java:ref:`Optional`\  value that is able to indicate if the Cloudlet was found or not

findSuitableWaitingCloudletToStartExecutingAndRemoveIt
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected Optional<CloudletExecutionInfo> findSuitableWaitingCloudletToStartExecutingAndRemoveIt()
   :outertype: CloudletSchedulerAbstract

   Try to find the first Cloudlet in the waiting list that the number of required PEs is not higher than the number of free PEs. If a Cloudlet is found, sets its status to \ :java:ref:`Status.INEXEC`\  and returns it, removing such Cloudlet from the waiting list.

   :return: an \ :java:ref:`Optional`\  containing the found Cloudlet or an empty Optional otherwise

getAllocatedMipsForCloudlet
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public double getAllocatedMipsForCloudlet(CloudletExecutionInfo rcl, double time)
   :outertype: CloudletSchedulerAbstract

getCloudletExecList
^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public List<CloudletExecutionInfo> getCloudletExecList()
   :outertype: CloudletSchedulerAbstract

getCloudletFailedList
^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected List<CloudletExecutionInfo> getCloudletFailedList()
   :outertype: CloudletSchedulerAbstract

   Gets the list of failed cloudlets.

   :return: the cloudlet failed list.

getCloudletFinishedList
^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public List<CloudletExecutionInfo> getCloudletFinishedList()
   :outertype: CloudletSchedulerAbstract

getCloudletPausedList
^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected List<CloudletExecutionInfo> getCloudletPausedList()
   :outertype: CloudletSchedulerAbstract

   Gets the list of paused cloudlets.

   :return: the cloudlet paused list

getCloudletStatus
^^^^^^^^^^^^^^^^^

.. java:method:: @Override public int getCloudletStatus(int cloudletId)
   :outertype: CloudletSchedulerAbstract

getCloudletToMigrate
^^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public Cloudlet getCloudletToMigrate()
   :outertype: CloudletSchedulerAbstract

   Returns the first cloudlet in the execution list to migrate to another VM, removing it from the list.

   :return: the first executing cloudlet or \ :java:ref:`Cloudlet.NULL`\  if the executing list is empty

getCloudletWaitingList
^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected List<CloudletExecutionInfo> getCloudletWaitingList()
   :outertype: CloudletSchedulerAbstract

   Gets a List of cloudlet waiting to be executed on the VM.

   :return: the cloudlet waiting list

getCurrentMipsShare
^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public List<Double> getCurrentMipsShare()
   :outertype: CloudletSchedulerAbstract

getCurrentRequestedBwPercentUtilization
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public double getCurrentRequestedBwPercentUtilization()
   :outertype: CloudletSchedulerAbstract

getCurrentRequestedRamPercentUtilization
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public double getCurrentRequestedRamPercentUtilization()
   :outertype: CloudletSchedulerAbstract

getEstimatedFinishTimeOfCloudlet
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected double getEstimatedFinishTimeOfCloudlet(CloudletExecutionInfo rcl, double currentTime)
   :outertype: CloudletSchedulerAbstract

   Gets the estimated time when a given cloudlet is supposed to finish executing. It considers the amount of Vm PES and the sum of PEs required by all VMs running inside the VM.

   The estimated time is not a future simulation time but a time interval that the Cloudlet is expected to finish.

   The estimated time is not a future simulation time but a time interval that the Cloudlet is expected to finish.

   :param rcl: cloudlet to get the estimated finish time
   :param currentTime: current simulation time
   :return: the estimated finish time of the given cloudlet

getEstimatedFinishTimeOfSoonerFinishingCloudlet
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected double getEstimatedFinishTimeOfSoonerFinishingCloudlet(double currentTime)
   :outertype: CloudletSchedulerAbstract

   Gets the estimated time, considering the current time, that a next Cloudlet is expected to finish.

   :param currentTime: current simulation time
   :return: the estimated finish time of sooner finishing cloudlet, that represents a future simulation time

getFreePes
^^^^^^^^^^

.. java:method:: @Override public int getFreePes()
   :outertype: CloudletSchedulerAbstract

   Gets the number of PEs currently not being used.

getPacketScheduler
^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public PacketScheduler getPacketScheduler()
   :outertype: CloudletSchedulerAbstract

getPreviousTime
^^^^^^^^^^^^^^^

.. java:method:: @Override public double getPreviousTime()
   :outertype: CloudletSchedulerAbstract

getProcessor
^^^^^^^^^^^^

.. java:method:: protected Processor getProcessor()
   :outertype: CloudletSchedulerAbstract

   Processor object created every time the processing of VMs is executed. It represent the last CPU capacity assigned to the scheduler.

   **See also:** :java:ref:`CloudletScheduler.updateVmProcessing(double,List)`

getRequestedCpuPercentUtilization
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public double getRequestedCpuPercentUtilization(double time)
   :outertype: CloudletSchedulerAbstract

getRequestedMipsForCloudlet
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public double getRequestedMipsForCloudlet(CloudletExecutionInfo rcl, double time)
   :outertype: CloudletSchedulerAbstract

getUsedPes
^^^^^^^^^^

.. java:method:: @Override public int getUsedPes()
   :outertype: CloudletSchedulerAbstract

getVm
^^^^^

.. java:method:: @Override public Vm getVm()
   :outertype: CloudletSchedulerAbstract

hasFinishedCloudlets
^^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public boolean hasFinishedCloudlets()
   :outertype: CloudletSchedulerAbstract

isThereEnoughFreePesForCloudlet
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected boolean isThereEnoughFreePesForCloudlet(CloudletExecutionInfo c)
   :outertype: CloudletSchedulerAbstract

   Checks if the amount of PEs required by a given Cloudlet is free to use.

   :param c: the Cloudlet to get the number of required PEs
   :return: true if there is the amount of free PEs, false otherwise

isTherePacketScheduler
^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public boolean isTherePacketScheduler()
   :outertype: CloudletSchedulerAbstract

moveNextCloudletsFromWaitingToExecList
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected void moveNextCloudletsFromWaitingToExecList()
   :outertype: CloudletSchedulerAbstract

   /** Selects the next Cloudlets in the waiting list to move to the execution list in order to start executing them. While there is enough free PEs, the method try to find a suitable Cloudlet in the list, until it reaches the end of such a list.

   The method might also exchange some cloudlets in the execution list with some in the waiting list. Thus, some running cloudlets may be preempted to give opportunity to previously waiting cloudlets to run. This is a process called \ `context switch <https://en.wikipedia.org/wiki/Context_switch>`_\ . However, each CloudletScheduler implementation decides how such a process is implemented. For instance, Space-Shared schedulers may just perform context switch just after currently running Cloudlets completely finish executing.

   This method is called internally by the \ :java:ref:`CloudletScheduler.updateVmProcessing(double,List)`\  one.

processCloudletSubmit
^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected double processCloudletSubmit(CloudletExecutionInfo rcl, double fileTransferTime)
   :outertype: CloudletSchedulerAbstract

   Process a Cloudlet after it is received by the \ :java:ref:`cloudletSubmit(Cloudlet,double)`\  method, that creates a \ :java:ref:`CloudletExecutionInfo`\  object to encapsulate the submitted Cloudlet and record execution information.

   :param rcl: the CloudletExecutionInfo that encapsulates the Cloudlet object
   :param fileTransferTime: time required to move the required files from the SAN to the VM
   :return: expected finish time of this cloudlet (considering the time to transfer required files from the Datacenter to the Vm), or 0 if it is in a waiting queue

removeCloudletFromExecList
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected boolean removeCloudletFromExecList(CloudletExecutionInfo cloudlet)
   :outertype: CloudletSchedulerAbstract

   Removes a Cloudlet from the list of cloudlets in execution.

   :param cloudlet: the Cloudlet to be removed
   :return: true if the Cloudlet was found and remove from the execution list.

removeCloudletFromWaitingList
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected boolean removeCloudletFromWaitingList(CloudletExecutionInfo cloudlet)
   :outertype: CloudletSchedulerAbstract

removeNextFinishedCloudlet
^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public Cloudlet removeNextFinishedCloudlet()
   :outertype: CloudletSchedulerAbstract

runningCloudletsNumber
^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public int runningCloudletsNumber()
   :outertype: CloudletSchedulerAbstract

setCloudletExecList
^^^^^^^^^^^^^^^^^^^

.. java:method:: protected final void setCloudletExecList(List<CloudletExecutionInfo> cloudletExecList)
   :outertype: CloudletSchedulerAbstract

setCloudletWaitingList
^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected final void setCloudletWaitingList(List<CloudletExecutionInfo> cloudletWaitingList)
   :outertype: CloudletSchedulerAbstract

setCurrentMipsShare
^^^^^^^^^^^^^^^^^^^

.. java:method:: protected void setCurrentMipsShare(List<Double> currentMipsShare)
   :outertype: CloudletSchedulerAbstract

   Sets the list of current mips share available for the VM using the scheduler.

   :param currentMipsShare: the new current mips share

   **See also:** :java:ref:`.getCurrentMipsShare()`

setPacketScheduler
^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public void setPacketScheduler(PacketScheduler packetScheduler)
   :outertype: CloudletSchedulerAbstract

setPreviousTime
^^^^^^^^^^^^^^^

.. java:method:: protected final void setPreviousTime(double previousTime)
   :outertype: CloudletSchedulerAbstract

   Sets the previous time when the scheduler updated the processing of cloudlets it is managing.

   :param previousTime: the new previous time

setVm
^^^^^

.. java:method:: @Override public void setVm(Vm vm)
   :outertype: CloudletSchedulerAbstract

timeSpan
^^^^^^^^

.. java:method:: protected double timeSpan(double currentTime)
   :outertype: CloudletSchedulerAbstract

   Computes the time span between the current simulation time and the last time the scheduler updated the processing of it's managed cloudlets. The method manages to correct precision issues of double values math operations.

   :param currentTime: the current simulation time

updateCloudletProcessing
^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected void updateCloudletProcessing(CloudletExecutionInfo rcl, double currentTime)
   :outertype: CloudletSchedulerAbstract

   Updates the processing of a specific cloudlet of the Vm using this scheduler.

   :param rcl: The cloudlet to be its processing updated
   :param currentTime: current simulation time

updateVmProcessing
^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public double updateVmProcessing(double currentTime, List<Double> mipsShare)
   :outertype: CloudletSchedulerAbstract

