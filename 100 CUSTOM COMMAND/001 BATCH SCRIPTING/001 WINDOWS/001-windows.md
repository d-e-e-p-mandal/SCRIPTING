# Windows Batch Scripting:
**File Name:** `*.bat`

```bat
::C:\bin

@echo off

if "%1"=="run" (
    dotnet run
    goto :eof
)

if "%1"=="build" (
    dotnet build
    goto :eof
)

echo Usage:
echo app run
echo app build
```