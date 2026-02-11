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


## MOST IMPORTANT REGISTRY KEYS
```
HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run
```
```
HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run
```

# SERVIES
## CLIKC ON THE DESCRIPTION TAB AND SORT TO FIND THE SERVICE WITH NO DESCRIPTION, EVENTUALY THE EMPTY ONES WILL GO TO THE TOP
## EMPTY DESCRIPTIONS AND MISPELLINGS
## WEIRD EXECUTABLE

COPY PATH TO EXECUTABLE AND PASTE INTO FILE EXPLORER, LOOK FOR OTHER ARTFACTS IN THAT SAME DIRECTORY
ALSO IN FILE EXPLORER MAKE SURE TO TAKE A QUICK GLANCE AT THE HIDDEN FOLDERS 
   VIEW ---> [ CHECK ] HIDDEN ITEMS

CHANGE THE SORT TO FIND THE FEWEST 

we'll b e woring off the run more often than not becuase we want it to run every time, 

# audtipol /get /category:* findstr /i "success failure"
   make sure to run as an administrator


# SCHEDULED TASKS
## TAKE A LOOK AT THE TRIGGERS - WHAT CAUSES IT
## TAKE A LOOK AT THE ACTIONS - WHAT IS GOING ON


GIVEN AN EXECUTBALE

CONSISTENT THING IN REG OR SCHTASKS

RENAME OLD EXEC TO RANDOM - RENAME THE NEW AS THE OLD THATS SCHEDUELD TO RUN



# LOG ITEMS IS EVENT VIEWER

WINDOWS LOGS, RIGHT CLICK, PROPERTIES.

CREATE (CHANGE TIME SET)  ANY TIME --> CUSTOM RANGE, CHANGE TIME AND DATES TO MATCH WHAT YOURE LOOKING FOR
