# Windows: Global Custom Commands

[Pre]() My File: bin
[Pre]() Run File: app


# Windows: Global
**Location:**
```text
C:\bin
```

## Bin Folder

```bash
mkdir C:\bin
```

---

## Create Command File

```bash
type nul > C:\bin\app.bat
```

or

```cmd
notepad C:\bin\app.bat
```


## Now Write Own Logic in app.bat

```bat
@echo off
```
===


## Add Bin Folder to PATH

### Temporary
```cmd
set PATH=%PATH%;C:\bin
```

### Permanent
**Open:**
```text
Environment Variables
```

**Add:**
```text
C:\bin
```
**to:**
```text
PATH
```

**Or:** Not Recomended Not working for of length issue 1024

```bash
setx PATH "%PATH%;C:\bin"
```

- Restart Terminal after running.

## Verify

```cmd
echo %PATH%
```

Output contains:

```text
C:\bin
```

## Run Command

```cmd
app
```

---

# Explain

```cmd
%PATH%;C:\bin
```

- `%PATH%`
  - Keep all existing command locations exactly as they are.

Example:

```text
C:\Windows\System32;
C:\Program Files\Git\bin;
...
```

- `;`
  - PATH separator in Windows.

- `C:\bin`
  - Add custom command folder.

Result:

```text
C:\Windows\System32;
C:\Program Files\Git\bin;
...
C:\bin
```

Now when you type:

```cmd
app
```

Windows searches:

```text
C:\Windows\System32
↓
C:\Program Files\Git\bin
↓
...
↓
C:\bin
↓
app.bat found
```

and executes:

```text
C:\bin\app.bat
```

---

# Linux/macOS vs Windows

| Linux/macOS | Windows |
|------------|----------|
| `~/bin` | `C:\bin` |
| `app` | `app.bat` |
| `chmod +x app` | Not Required |
| `export PATH="$PATH:$HOME/bin"` | `setx PATH=%PATH%;C:\bin` |
| `source ~/.zshrc` | Restart Terminal |
| `app` | `app` |

---

# Flow

```text
Create app.bat
        ↓
Store in C:\bin
        ↓
Add C:\bin to PATH
        ↓
Open New Terminal
        ↓
app
        ↓
Windows Finds C:\bin\app.bat
        ↓
Execute Script
```



-------