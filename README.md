# Powershell-Automation-Script-
This script lists top CPU processes Shows active network connections Pulls recent process creation events Pulls recent PowerShell activity Saves everything for evidence You run it once.

Save this script as file in .ps1 extension .
Windows blocks scripts by default.
Run this once:
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

What this means :
Local scripts → allowed
Internet scripts → still protected

Go to the Script Folder
cd C:\SOC-Scripts
Run the Script
.\soc-triage.ps1

View the Results in other folder, that the script save there.
C:\SOC-Triage
We can see files like:
processes.txt
network.txt
process_creation.txt
powershell_activity.txt
Open them with Notepad.
