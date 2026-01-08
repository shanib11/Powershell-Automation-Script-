# Create output folder
$Folder = "C:\SOC-Triage"
New-Item -ItemType Directory -Force -Path $Folder

# 1. Running processes (top CPU)
Get-Process |
Sort-Object CPU -Descending |
Select-Object -First 10 Name, Id, CPU |
Out-File "$Folder\processes.txt"

# 2. Active network connections
Get-NetTCPConnection |
Where-Object State -eq "Established" |
Select-Object LocalAddress, LocalPort, RemoteAddress, RemotePort |
Out-File "$Folder\network.txt"

# 3. Recent process creation events (last 20)
Get-WinEvent -FilterHashtable @{
    LogName = 'Security'
    Id = 4688
} -MaxEvents 20 |
Select TimeCreated, Message |
Out-File "$Folder\process_creation.txt"

# 4. Recent PowerShell activity
Get-WinEvent -FilterHashtable @{
    LogName = 'Microsoft-Windows-PowerShell/Operational'
} -MaxEvents 20 |
Select TimeCreated, Message |
Out-File "$Folder\powershell_activity.txt”
