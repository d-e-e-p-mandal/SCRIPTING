[Pre]() My File :mkdir -p ~/bin
[pre]() Run File: app

# Mac OS: Global:
Location: ~/bin   : Home : Users/(username)

**Bin Folder:**
```bash
mkdir -p ~/bin
```

**Run file:**
```bash
touch ~/bin/app
```
**Permission:**
```bash
chmod +x ~/bin/app
```

## Now write own logic on app

===

## For zsh (default on macOS):
```bash
nano ~/.zshrc
```
**Example:**
```bash
export PATH="$PATH:$HOME/bin"
```
- ctrl + o
- enter 
- ctrl + x (Y)

```bash
source ~/.zshrc  
```

**Or: Direct add to /.zshrc**

```bash
echo 'export PATH="$PATH:$HOME/bin"' >> ~/.zshrc
```
```bash
source ~/.zshrc  
```


## Run Command

```cmd
app
```


## Explain:
```
"$PATH:$HOME/bin"
```
- This $PATH: - Keep all existing command locations (Current Direcorty)