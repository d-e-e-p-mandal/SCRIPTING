# Windows: Global Custom Commands

**Location:** C:\bin

## Bin Folder
```bash
mkdir C:\bin
```

**File:** C:\bin\app.bat

**Now Write Own Logic in app.bat**
```bat
@echo off
```

------------ 

## Add Bin Folder to PATH

### Temporary
```cmd
set PATH=%PATH%;C:\bin
```

### Permanent
**Open:**
- Environment Variables

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
```bash
echo %PATH%
```

**Output contains:**
```text
C:\bin
```

## Run Command
```bash
app
```

---

## Explain

```cmd
%PATH%;C:\bin
```

- `%PATH%`
  - Keep all existing command locations exactly as they are.

**Example:**

```text
C:\Windows\System32;
C:\Program Files\Git\bin;
...
```

- `;`
  - PATH separator in Windows.

- `C:\bin`
  - Add custom command folder.

**Result:**

```text
C:\Windows\System32;
C:\Program Files\Git\bin;
...
C:\bin
```