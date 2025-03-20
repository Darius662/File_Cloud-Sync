# **FileSync Automation Script**

A PowerShell-based file synchronization script designed to automate selective file transfers between two directories. The script is optimized for scenarios requiring the synchronization of specific folders and files between the ```CAQMDM_EMiL_Import``` (reffered as ```E:```) and the Azure-mounted drive ```emil-input``` (refered as ```Z:```). It only transfers files older than a specified threshold (60 seconds) and maintains daily log files for audit purposes.
Features

    Selective File Transfer: Moves only files older than 60 seconds to prevent transferring newly modified files.
    Two-Way Synchronization:
        Files in Project1 and Project2 from E: to Z:.
        Files in _fehler, _logs, and _readme folders from Z: to E:.
    Daily Log Files: Generates a single log file per day, appending each synchronization event, with logs named in the YYYY-MM-DD_Sync.log format.
    Automated Directory Creation: Creates destination directories if they don't already exist.


<details>
<summary>Folder Structure</summary>

Both the local (```E:```) and remote (```Z:```) drives should follow this folder structure:
```ruby
E:\ (or Z:\)
├── Folder1
│   ├── Project1
│   │   ├── _retry
│   │   ├── _fehler
│   │   ├── _readme
│   │   ├── _logs
│   │   └── _copy
│   └── Project2
│       ├── _retry
│       ├── _fehler
│       ├── _readme
│       ├── _logs
│       └── _copy
└── Fodler2
    ├── Project1
    └── Project2
```
</details>
<details>
<summary>Configuration Options</summary>
    File Age Threshold: The $fileAgeThreshold variable is set to 60 seconds by default. Adjust this value if you need to move files based on a different age threshold.
    Log File Location: By default, log files are saved in C:\Logs with a daily timestamped filename. Update $logFile to customize the location if needed.
</details>
<details>
<summary>Example Log Output</summary>

Each run of the script generates entries in a log file, tracking each file moved and any directories created:
```ruby
2024-10-30 12:01:23 - Starting synchronization...
2024-10-30 12:01:30 - Created directory: Z:\Folder 1\Folder a
2024-10-30 12:01:35 - Moved file from E:\Folder 1\Folder a\example.txt to Z:\Folder 1\Folder a
2024-10-30 12:02:00 - Moved file from Z:\Folder 2\Folder b\_logs\logfile.log to E:\Folder 2\Folder b\_logs
2024-10-30 12:02:10 - Synchronization complete.
```
</details>
