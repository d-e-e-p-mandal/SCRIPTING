# Mac OS:

```sh
#!/bin/bash

if [ "$1" = "run" ]; then
    dotnet run
    exit 0
fi

if [ "$1" = "build" ]; then
    dotnet build
    exit 0
fi

echo "Usage:"
echo "./app.sh run"
echo "./app.sh build"
```

---------------

## Explation:
- fi : end of if



---------
## Permission:
**Give Permisto to Folder:**
```text
chmod +x app.sh
```

## Explain:
- chmod  = Change Mode (change permissions)
- +x     = Add execute permission
- app.sh = File name

## Why Permission: Explain:
**Check permissions:**
```
ls -l app.sh
```
**Output:**
```
-rwxr-xr-x  1 deepmandal  staff  200 Jun 20 10:00 app.sh
```

```
-rw-r--r--  1 deepmandal staff  100 Jun 20 10:00 app.sh
│─────────│  │ │         │      │             │
Permissions  │ Owner     Group  Size          File Name
             │
         Link Count
```

**Explain:**

```
-
```
The first character indicates the file type.

Symbol | Meaning
-------|---------
   \-   |  Regular file
   d   |  Directory (folder)
   l   |  Symbolic links


**Before:**
```text
-rw-r--r--
```
**Means:**
```
rw-   r--   r--
│     │     │
│     │     └── Others
│     └──────── Group
└────────────── Owner
```


**Owner Permissions:**
```
rw-
```

Permission | Meaning
----|----
r   | Read
w   | Write
\-  | No Execute


**After After chmod +x Permision:**
```
-rwxr-xr-x
```

## Run:
./app.sh run
./app.sh build


------
