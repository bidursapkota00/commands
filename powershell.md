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

### Unzip all zipped folders recursively

```powershell
Get-ChildItem -Path "C:\Path\To\Your\MainFolder" -Recurse -Filter *.zip | ForEach-Object {
    $destination = $_.DirectoryName + "\" + ($_.BaseName)
    Expand-Archive -LiteralPath $_.FullName -DestinationPath $destination -Force
}

```

- **Description:** Unzip all zipped folders recursively in a nested folders
