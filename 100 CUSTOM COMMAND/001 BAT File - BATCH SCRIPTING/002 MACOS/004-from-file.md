# macOS/Linux Version

**commands.txt:**
```text
run=./a
build=dotnet build
hello=echo Hello World
```

---

## app

```bash
#!/bin/bash

while IFS='=' read -r key value || [ -n "$key" ]
do
   key=$(echo "$key" | xargs)
   value=$(echo "$value" | xargs)
   if [ "$key" = "$1" ]; then
        eval "$value"
        exit 0
   fi
done < commands.txt

echo "Usage:"
cat commands.txt
```

---

# Explanation

## User Command

```bash
app run
```

Then:

```text
$1 = run
```

`$1` = First command-line argument.

---

## Read File

```bash
while IFS='=' read -r key value
```

Read file line by line.

Example line:

```text
run=./a
```

Split using:

```text
=
```

Result:

```text
key   = run
value = ./a
```

---

## Compare

```bash
if [ "$key" = "$1" ]
```

becomes:

```bash
if [ "run" = "run" ]
```

Result:

```text
True
```

---

## Execute

```bash
eval "$value"
```

becomes:

```bash
eval "./a"
```

Runs:

```bash
./a
```

---

## Stop Script

```bash
exit 0
```

means:

```text
Exit Successfully
```

---

# Flow

```text
app run
   │
   ▼
$1 = run
   │
   ▼
commands.txt

run=./a
build=dotnet build
   │
   ▼
key   = run
value = ./a
   │
   ▼
run == run
   │
   ▼
eval "./a"
   │
   ▼
Execute ./a
```

---

# Variable Comparison

| Windows Batch | macOS/Linux |
|--------------|-------------|
| `%1` | `$1` |
| `%%a` | `key` |
| `%%b` | `value` |
| `call %%b` | `eval "$value"` |
| `type file.txt` | `cat file.txt` |

---

# Memory Trick

```text
run=./a

Left Side  -> key
Right Side -> value

key   = run
value = ./a
```

Then:

```bash
app run
```

```text
$1 = run
```

```text
key == $1
```

```text
run == run
```

```text
Execute value
```

```text
./a
```