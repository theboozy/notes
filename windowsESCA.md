# WINDOWS PRIVILEGE ESCALATION

#### DLL SEARCH ORDER
```
reg query "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\KnownDLLs"
```
#### CHECK UAC SETTINGS
```
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System
```

# AS INVOKER ??? ASK A QUESTION

# PRIVELEGE ESCALATION LOCATIONS

### SCHEDULED TASKS

#### The following commands can be used to idenitfy vulnerable tasks using CMD and PowerShell:
```
schtasks /query /fo LIST /v``   # List all Tasks in List format
schtasks /query /fo LIST /v | Select-String -Pattern "STRING OR REGEX PATTERN"
```
# ASK ABOUT THE RELEVANCE OF THESE
```
schtasks.exe /query /fo LIST /v | Select-String -Pattern "Task To Run" -CaseSensitive -Context 0,6``
   # Searches for *Task To Run* and outputs that line, along with the 6 lines following it in order to show the *Run As User* setting too.
schtasks.exe /query /fo LIST /v | Select-String -Pattern "Task To Run" -CaseSensitive |Select-String -Pattern "COM handler" -NotMatch``
   # Excludes results that we dont want to seein order to help narrow down vulnerable directory locations
   # Open and view tasks from the Task Scheduler GUI Application
```

# ADD IN PUTTTY.EXE NOTES


# RELEVANCE ?????
#### WINDOWS REGISTRY 
```
New-ItemProperty -path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Run -name "Updater" -PropertyType expandstring -value 'C:\Windows\System32\cmd.exe /c calc.exe' -force
```

