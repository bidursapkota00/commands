## PowerShell

### Remove `.git` directory recursively

```powershell
Remove-Item -Path .git -Recurse -Force
```

- **Description:** Deletes the `.git` directory and all its contents recursively.

### Get a list of all files (including hidden ones)

```powershell
Get-ChildItem -Force
```

- **Description:** Lists all items in the current directory, including hidden files.

### Manually add the project directory to PYTHONPATH

```powershell
$env:PYTHONPATH = "C:\Users\dell\Desktop\test"
```

- **Description:** When module not found error occurs in projects
