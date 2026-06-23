
## File Create in *.BAT file:
```bash
@echo off
type nul > file.txt
```
**or:**

```bash
@echo off
echo. > file.txt
```

### With Content:

```bash
@echo off
echo Hello World > file.txt
```

### With Multiple Line:

```bash
@echo off
(
echo Deep
echo Mandal
) > file.txt
```