Assume you already have:

RunCLI.pkg

and want users to install it without the “Apple could not verify” warning.

Step 1: Buy Apple Developer Account

Open browser:

https://developer.apple.com

Sign in with Apple ID.

Buy:

Apple Developer Program

Cost:

$99/year

Result:

Developer Account Activated

⸻

Step 2: Install Xcode Tools

Terminal:

xcode-select --install

Result:

Xcode Command Line Tools Installed

Verify:

xcode-select -p

⸻

Step 3: Find Team ID

Open:

https://developer.apple.com/account

Go:

Membership

Example:

Team ID: ABC123XYZ9

Save it.

⸻

Step 4: Create App-Specific Password

Open:

https://appleid.apple.com

Go:

Sign-In and Security
↓
App-Specific Passwords
↓
Generate Password

Example:

abcd-efgh-ijkl-mnop

Save it.

⸻

Step 5: Verify Signing Certificate

Terminal:

security find-identity -v

Look for:

Developer ID Installer: Deep Mandal

Example output:

Developer ID Installer: Deep Mandal (ABC123XYZ9)

⸻

Step 6: Build Your Package

You already have:

RunCLI.pkg

If not:

pkgbuild \
--root package-root \
--identifier com.deep.runcli \
--version 1.0.0 \
RunCLI.pkg

Result:

RunCLI.pkg

⸻

Step 7: Sign Package

Terminal:

productsign \
--sign "Developer ID Installer: Deep Mandal" \
RunCLI.pkg \
RunCLI-Signed.pkg

Result:

RunCLI-Signed.pkg

⸻

Step 8: Save Apple Credentials

Terminal:

xcrun notarytool store-credentials runcli

Enter:

Apple ID: your@email.com
Team ID: ABC123XYZ9
App Password: abcd-efgh-ijkl-mnop

Result:

Credentials stored in Keychain

⸻

Step 9: Submit To Apple

Terminal:

xcrun notarytool submit RunCLI-Signed.pkg \
--keychain-profile runcli \
--wait

Meaning:

runcli = saved credentials

Apple checks:

Malware
Package Integrity
Security

Wait a few minutes.

⸻

Step 10: Check Result

Expected:

status: Accepted

If accepted:

Apple approved your package

⸻

Step 11: Staple Approval

Terminal:

xcrun stapler staple RunCLI-Signed.pkg

Result:

Apple approval embedded inside package

⸻

Step 12: Verify

Terminal:

spctl -a -vv -t install RunCLI-Signed.pkg

Expected:

accepted
source=Notarized Developer ID

⸻

Step 13: Rename Final Package

mv RunCLI-Signed.pkg RunCLI.pkg

⸻

Step 14: Upload

Upload:

RunCLI.pkg

to:

GitHub Releases
Website
Google Drive

⸻

Step 15: User Experience

User downloads:

RunCLI.pkg

Double-clicks:

Install

No warning.

No:

Apple could not verify this software

message appears.

⸻

Final Flow

Create RunCLI.pkg
        ↓
Sign Package
        ↓
Submit To Apple
        ↓
Apple Approves
        ↓
Staple Approval
        ↓
Upload
        ↓
User Downloads
        ↓
Double Click Install
        ↓
run hello