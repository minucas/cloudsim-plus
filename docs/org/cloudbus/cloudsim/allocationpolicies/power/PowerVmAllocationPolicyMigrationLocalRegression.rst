.. java:import:: org.cloudbus.cloudsim.hosts.power PowerHost

.. java:import:: org.cloudbus.cloudsim.hosts.power PowerHostUtilizationHistory

.. java:import:: org.cloudbus.cloudsim.resources Resource

.. java:import:: org.cloudbus.cloudsim.selectionpolicies.power PowerVmSelectionPolicy

.. java:import:: org.cloudbus.cloudsim.vms Vm

.. java:import:: org.cloudbus.cloudsim.util MathUtil

PowerVmAllocationPolicyMigrationLocalRegression
===============================================

.. java:package:: org.cloudbus.cloudsim.allocationpolicies.power
   :noindex:

.. java:type:: public class PowerVmAllocationPolicyMigrationLocalRegression extends PowerVmAllocationPolicyMigrationDynamicUpperThresholdAbstract

   A VM allocation policy that uses Local Regression (LR) to predict host utilization (load) and define if a host is overloaded or not.

   If you are using any algorithms, policies or workload included in the power package please cite the following paper:

   ..

   * \ `Anton Beloglazov, and Rajkumar Buyya, "Optimal Online Deterministic Algorithms and Adaptive Heuristics for Energy and Performance Efficient Dynamic Consolidation of Virtual Machines in Cloud Data Centers", Concurrency and Computation: Practice and Experience (CCPE), Volume 24, Issue 13, Pages: 1397-1420, John Wiley & Sons, Ltd, New York, USA, 2012 <http://dx.doi.org/10.1002/cpe.1867>`_\

   :author: Anton Beloglazov

Constructors
------------
PowerVmAllocationPolicyMigrationLocalRegression
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:constructor:: public PowerVmAllocationPolicyMigrationLocalRegression(PowerVmSelectionPolicy vmSelectionPolicy)
   :outertype: PowerVmAllocationPolicyMigrationLocalRegression

   Creates a PowerVmAllocationPolicyMigrationLocalRegression with a \ :java:ref:`safety parameter <getSafetyParameter()>`\  equals to 0 and no \ :java:ref:`fallback policy <getFallbackVmAllocationPolicy()>`\ .

   :param vmSelectionPolicy: the policy that defines how VMs are selected for migration

PowerVmAllocationPolicyMigrationLocalRegression
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:constructor:: public PowerVmAllocationPolicyMigrationLocalRegression(PowerVmSelectionPolicy vmSelectionPolicy, double safetyParameter, PowerVmAllocationPolicyMigration fallbackVmAllocationPolicy)
   :outertype: PowerVmAllocationPolicyMigrationLocalRegression

   Creates a PowerVmAllocationPolicyMigrationLocalRegression.

   :param vmSelectionPolicy: the policy that defines how VMs are selected for migration
   :param safetyParameter: the safety parameter
   :param fallbackVmAllocationPolicy: the fallback VM allocation policy to be used when the over utilization host detection doesn't have data to be computed

Methods
-------
computeHostUtilizationMeasure
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public double computeHostUtilizationMeasure(PowerHostUtilizationHistory host) throws IllegalArgumentException
   :outertype: PowerVmAllocationPolicyMigrationLocalRegression

   Computes a Local Regression of the host utilization history to \ **estimate**\  the current host utilization. Such a value is used to generate the host over utilization threshold.

   :param host: the host
   :throws {@inheritDoc}:
   :return: the host utilization Local Regression

getMaximumVmMigrationTime
^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected double getMaximumVmMigrationTime(PowerHost host)
   :outertype: PowerVmAllocationPolicyMigrationLocalRegression

   Gets the maximum vm migration time.

   :param host: the host
   :return: the maximum vm migration time

getOverUtilizationThreshold
^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public double getOverUtilizationThreshold(PowerHost host)
   :outertype: PowerVmAllocationPolicyMigrationLocalRegression

   {@inheritDoc}. \ **In this case, this is a predicted value based on Local Regression of the utilization history.**\

   :param host: the host to get the over utilization threshold \ **prediction**\
   :return: {@inheritDoc} or \ :java:ref:`Double.MAX_VALUE`\  if the threshold could not be computed

getParameterEstimates
^^^^^^^^^^^^^^^^^^^^^

.. java:method:: protected double[] getParameterEstimates(double[] utilizationHistoryReversed)
   :outertype: PowerVmAllocationPolicyMigrationLocalRegression

   Gets utilization estimates.

   :param utilizationHistoryReversed: the utilization history in reverse order
   :return: the utilization estimates

getSchedulingInterval
^^^^^^^^^^^^^^^^^^^^^

.. java:method:: public double getSchedulingInterval()
   :outertype: PowerVmAllocationPolicyMigrationLocalRegression

   Gets the scheduling interval that defines the periodicity of VM migrations.

   :return: the scheduling interval

isHostOverUtilized
^^^^^^^^^^^^^^^^^^

.. java:method:: @Override public boolean isHostOverUtilized(PowerHost host)
   :outertype: PowerVmAllocationPolicyMigrationLocalRegression

   Checks if a host is over utilized based on estimation of CPU over utilization threshold computed using Local Regression.

   :param host: the host
   :return: true, if is host over utilized; false otherwise

setSchedulingInterval
^^^^^^^^^^^^^^^^^^^^^

.. java:method:: public final PowerVmAllocationPolicyMigrationLocalRegression setSchedulingInterval(double schedulingInterval)
   :outertype: PowerVmAllocationPolicyMigrationLocalRegression

   Sets the scheduling interval that defines the periodicity of VM migrations.

   :param schedulingInterval: the new scheduling interval

