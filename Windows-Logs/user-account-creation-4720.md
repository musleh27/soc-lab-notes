# User Account Creation Detection (Event ID 4720)

## Objective

Detect unauthorized user account creation events that may indicate persistence.

## Scenario

Simulated attacker behavior by creating a new local user account on a Windows system.

## Steps Performed

* Opened Command Prompt as Administrator
* Executed the following command:
  net user attacker123 Password123! /add

## Log Analysis

* Navigated to Event Viewer → Windows Logs → Security
* Filtered logs for Event ID 4720

## Key Findings

* Event ID: 4720 (User Account Created)
* Subject (Creator): musleh
* New Account Created: attacker123
* Timestamp: 2026-04-16 3:25:13 AM

## SOC Analysis

The account **attacker123** was created by user **musleh**.
User account creation is a common persistence technique used by attackers to maintain access.

The event occurred at **3:25 AM**, which is outside typical working hours and may indicate suspicious activity.

## Detection Strategy

* Monitor Event ID 4720 for new account creation
* Validate if the creator account is authorized
* Correlate with:

  * Event ID 4624 (successful logins)
  * Event ID 4625 (failed logins)
  * Event ID 4672 (admin privileges assigned)

## Conclusion

Event ID 4720 is critical for detecting potential persistence mechanisms.
Unauthorized or unusual account creation should be treated as a high-severity alert and investigated immediately.
