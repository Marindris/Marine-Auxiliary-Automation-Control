# Marine Auxiliary System – Control Philosophy

## 1. Purpose

The system supplies service water from tank T-101 to downstream shipboard consumers using two redundant pumps, P-101A and P-101B.

One pump operates as the duty pump while the second pump remains available as the standby pump.

The PLC monitors tank level, pump status, valve position and discharge pressure to ensure safe and reliable operation.

## 2. Operating Modes

The system shall provide two operating modes:

### Auto Mode

In Auto mode, the PLC controls the pumps and motorised valves automatically.

The PLC shall:

* Check all required permissives before starting a pump.
* Start the selected duty pump when water transfer is required.
* Monitor pump running feedback and discharge pressure.
* Stop or inhibit the pumps if an unsafe condition occurs.
* Attempt to use the standby pump if the duty pump fails.

### Manual Mode

In Manual mode, the operator may issue pump and valve commands from the HMI.

Safety interlocks shall remain active even when the system is in Manual mode.

## 3. Pump A Start Sequence

When P-101A is selected as the duty pump and a start request is received:

1. Verify that the tank level is above the Low-Low limit.
2. Verify that P-101A has no active fault.
3. Command XV-101A to open.
4. Wait for XV-101A Open Feedback.
5. Start P-101A.
6. Verify P-101A Run Feedback.
7. Verify that discharge pressure PT-101 rises above the minimum operating pressure.
8. Declare P-101A running normally.

If any required condition is not satisfied, the pump start shall be prevented or aborted.

## 4. Normal Stop Sequence

When P-101A is required to stop:

1. Remove the P-101A start command.
2. Confirm that P-101A Run Feedback is OFF.
3. Command XV-101A to close.
4. Confirm XV-101A Closed Feedback.

The same sequence shall apply to P-101B.

## 5. Low-Low Tank Level Protection

If LSLL-101 becomes active:

* Stop any running service-water pump.
* Prevent both pumps from starting.
* Generate a Low-Low Tank Level alarm.

This protects the pumps from operating without sufficient water.

## 6. Pump Failure

A pump failure shall be detected if:

* The pump reports a fault or trip, or
* A start command is issued but Run Feedback is not received within the permitted time.

If the duty pump fails:

1. Stop the failed pump.
2. Generate a pump failure alarm.
3. If the standby pump is healthy and all permissives are satisfied, start the standby pump.

## 7. Failure to Establish Pressure

After a pump starts, PT-101 shall be monitored.

If the pump is confirmed running but adequate discharge pressure is not established within the permitted time:

* Generate a Low Discharge Pressure / Pump Failure alarm.
* Stop the affected pump.
* Attempt to start the standby pump if available.

## 8. Motorised Valve Failure

If a valve is commanded open but Open Feedback is not received within the permitted time:

* Generate a Valve Failed to Open alarm.
* Prevent the associated pump from starting.

If a valve is commanded closed but Closed Feedback is not received within the permitted time:

* Generate a Valve Failed to Close alarm.

## 9. Duty / Standby Operation

Normally:

* One pump shall be designated Duty.
* The other pump shall be designated Standby.

Example:

P-101A = Duty
P-101B = Standby

If P-101A becomes unavailable while service is required, the PLC shall automatically attempt to start P-101B.

The operator shall eventually be able to change which pump is designated Duty from the HMI.

## 10. High-High Tank Level

If LSHH-101 becomes active:

* Generate a High-High Tank Level alarm.
* Display the alarm on the HMI.

The initial project version does not automatically operate any filling equipment because tank filling is outside the current simulation scope.

## 11. Alarm Summary

The initial system shall include at least the following alarms:

* Tank Level High-High
* Tank Level Low-Low
* P-101A Fault
* P-101B Fault
* P-101A Failed to Start
* P-101B Failed to Start
* XV-101A Failed to Open
* XV-101B Failed to Open
* Low Discharge Pressure
* Duty Pump Failure / Standby Pump Started
