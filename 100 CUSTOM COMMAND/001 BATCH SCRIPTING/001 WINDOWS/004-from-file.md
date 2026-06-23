```bat
@echo off

for /f "tokens=1,* delims==" %%a in (commands.txt) do (
    if /i "%%a"=="%1" (
        call %%b
        goto :eof
    )
)

echo Usage:
type commands.txt token 1,* %%a and %%b where define explain
```

---------------

## Recomended:

```bat
@echo off
setlocal EnableDelayedExpansion

for /f "tokens=1,*" %%a in (file.txt) do (

    set "key=%%a"
    set "value=%%b"

    if /i "!key!"=="%1" (
        call !value!
        goto :eof
    )
)

echo Key not found
```

**File.txt:**
- no delims
```
run dotnet run
build dotnet build
```

-------------

## Explain
- /f
- delims : what type devide like :, =  (Here = used)
- token : delims devided in part 1st part 1, 2nd part 2, 3rd part 3 (Here only 2 part)
- Equivalend : 
   - %%a = First token
    - %%b = Second token
    - %%c = Third token
    - %%d = Fourth token
    .........

- %1 1st argument after app or file name