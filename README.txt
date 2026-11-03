SIMPLE LEAVE REQUEST — CAMUNDA 8
=================================

Files
-----
1. simple_leave_request.bpmn
   BPMN process with Start Event -> User Task -> End Event.

2. leave_request.form
   Camunda Form linked to the User Task using form ID:
   leave-request-form

Form fields and process-variable keys
-------------------------------------
Employee Name  -> employeeName
Leave Date     -> leaveDate
Leave Type     -> leaveType
Reason         -> reason

The form values are submitted as process variables when the user
completes the User Task.

IMPORT AND DEPLOY
-----------------
1. Open Camunda Modeler.
2. Open simple_leave_request.bpmn.
3. Open leave_request.form in Modeler as well.
4. Make sure the form ID is exactly: leave-request-form
   (The BPMN User Task references this ID.)
5. Save both files.
6. Deploy the form and BPMN process to the same Camunda 8 cluster.
   In Modeler, deploy the form first, then deploy the BPMN process.
   The form binding is set to "latest".

RUN AND TEST
------------
1. Open Operate and start a new instance of "Simple Leave Request".
2. Open Tasklist.
3. Find the "Fill Leave Request Form" task.
4. Claim the task if required by your Tasklist configuration.
5. Enter Employee Name, Leave Date, Leave Type and Reason.
6. Submit/complete the task.
7. Open the process instance in Operate and inspect its variables.

Expected process variables
--------------------------
employeeName
leaveDate
leaveType
reason

Note
----
This is intentionally a simple form-submission exercise. It does not
include manager approval, balance validation, DMN, or service tasks.
The date is a text field with YYYY-MM-DD guidance to keep the example
simple and portable across Camunda 8 form versions.
