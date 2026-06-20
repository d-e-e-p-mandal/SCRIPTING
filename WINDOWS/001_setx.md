setx Command

setx is used to permanently save environment variables in Windows.

Unlike:
```bash
set PATH=%PATH%;C:\bin
```
which works only for the current Command Prompt,
```bash
setx PATH "%PATH%;C:\bin"
```
saves it permanently.

⸻

Add Custom Folder to PATH

setx PATH "%PATH%;C:\bin"

After running:

C:\bin

is added to PATH.

Open a new CMD window.

⸻

Verify

echo %PATH%

Output contains:

...
C:\bin
...

⸻

Example

Create:

C:\bin\app.bat

Add PATH:

setx PATH "%PATH%;C:\bin"

Open new CMD:

app

Windows finds:

C:\bin\app.bat

and executes it.

⸻

Difference

Temporary

set PATH=%PATH%;C:\bin

Works only in current terminal.

⸻

Permanent

setx PATH "%PATH%;C:\bin"

Saved permanently in Windows.

⸻

Common Examples

setx JAVA_HOME "C:\Program Files\Java\jdk-24"
setx NODE_ENV "production"
setx PATH "%PATH%;C:\bin"

⸻

Note

After using setx:

Close CMD
Open New CMD

because existing terminals do not automatically reload the updated environment variables.