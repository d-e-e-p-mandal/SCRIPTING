# Linux:
**File Name:** `*.sh`

# Mac OS:
**File Name:** `*.sh` or `*.zsh` or `don't use extension`

**Example:** `app` | No extension used here

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
echo "./app run"
echo "./app build"
```

## Permission:
**Give Permisto to Folder:**
```text
chmod +x app
```

## Run:
./app run
./app build

--------

# Make it look exactly like a command
