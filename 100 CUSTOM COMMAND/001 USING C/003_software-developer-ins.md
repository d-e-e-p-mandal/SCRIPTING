# Type 1 : Visual Steps

**Step 1:**
- Double-click Run.pkg.
- You already did this and got:
- “Run.pkg Not Opened”
- Click Done.

**Step 2:**
*Open:*
-  Apple Menu → System Settings

**Step 3:**
- Click:
- Privacy & Security
- Scroll all the way down to the bottom.
- You should see something similar to:
Security
"Run.pkg" was blocked from use because it is not from an identified developer.
[ Open Anyway ]

or

"Run.pkg" was blocked to protect your Mac.
[ Open Anyway ]

---

If You Don’t See “Open Anyway”

----

# Type 2 : CMD
**Open Terminal and run:**
```bash
xattr -dr com.apple.quarantine
```

```bash
xattr -dr com.apple.quarantine ~/Downloads/<Folder Name>/Run.pkg
```

Then:
```bash
open /Users/deep/Desktop/Run.pkg
```

-------

To know exactly why macOS is blocking it, run:
```
spctl -a -vvv -t install Run.pkg
```

* Unsigned package
* Not notarized package
* Broken package structure
* Quarantine attribute
* Certificate problem.