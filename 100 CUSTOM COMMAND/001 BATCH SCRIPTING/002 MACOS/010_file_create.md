## File Create in *.SH file:
```bash
#!/bin/bash

touch file.txt
```

Or:
```bash
#!/bin/bash

> file.txt
```

### With Content:

```bash
#!/bin/bash

echo "Hello World" > file.txt
```

### With Multiple Line:

```bash
#!/bin/bash

echo "Deep" > file.txt
echo "Mandal" >> file.txt
```

```bash
#!/bin/bash

cat > file.txt << EOF
Deep
Mandal
EOF
```