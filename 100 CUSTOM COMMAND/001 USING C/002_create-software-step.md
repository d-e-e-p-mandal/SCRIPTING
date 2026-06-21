# Run Create Software:

- Create a Directory.
- create c code and save compile file in this directory.

- install.sh file
```bash
touch install.sh
```
```bash
nano install.sh
```

*write:*
```bash
#!/bin/bash

sudo cp run /usr/local/bin/run

sudo chmod +x /usr/local/bin/run

echo "Run Installed Successfully"
```
**Save:**
```bash
Ctrl + O
Enter
Ctrl + X
```

```
RunPlatform
├── run
└── install.sh
```

*Local Permission:*
```bash
chmod +x install.sh
```



### Create Release Folder
```
RunPlatform
├── run
├── install.sh
├── README.md
└── LICENSE
```


## Package:

```bash
mkdir -p package-root/usr/local/bin
```
```
package-root
└── usr
    └── local
        └── bin
```

```bash
cp run package-root/usr/local/bin/
```
```
package-root
└── usr
    └── local
        └── bin
            └── run
```

### Build .pkg Installer
**Run:**
```bash
pkgbuild \
--root package-root \
--identifier com.deep.run \
--version 1.0 \
Run.pkg
```

```
RunPlatform
├── Run.pkg
├── run
├── install.sh
├── README.md
├── LICENSE
└── package-root
```

-automtic Generated :Run.pkg