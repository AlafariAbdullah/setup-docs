# 🧠 Auto-Sync Minecraft World with Git

I often play Minecraft on my desktop at home, but when I’m on the go with my laptop, transferring my world manually used to be a hassle. I had to remote into my desktop, zip the save folder, spin up a Python HTTPS server, and download it from my laptop. That got old quickly.

So, I spent two quick hours writing a pair of simple scripts — one for Windows, one for macOS — to automatically run `git pull` before launching Minecraft, and `git push` after exiting the game. Now my Minecraft world syncs seamlessly between devices using GitHub.

- I assume you'd just use your .minecraft as your repo to sync your settings, mods and all other game related files (including saves), but I am not entirely sure if there'd be compatibility issues or not.

## ⚙️ How It Works

1. Your Minecraft world is stored in a [local Git repository](https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github).
2. When you launch Minecraft:
   - The script pulls the latest version of the world from GitHub.
3. When you exit Minecraft:
   - The script automatically commits your changes and pushes them to GitHub.

No more zipping, no more remote desktop. Just pure automation.

*‼️Replace any path with your own path‼️*
---
The logic is basically "If a process called Java wasstarted and closed while the script is running, check for changes in the world files and push them"
 - I decided to use the java process (instead of "Minecraft {version}") to check if the game is open or not since i don't use java for other purposes. If you use java, replace the process name with process name of your respective version, or you'd try to search for a process with a prefix "Minecraft" but execlude the Launcher, the base for the loop is to determine if the user opened the game (past the launcher) or just opened it and closed it 
---

## 🪟 Windows Script (`minecraft_launcher.bat`)

```bat
@echo off
cd ""C:\Users\abdul\AppData\Roaming\.minecraft\saves\1.WorldName""
: World Repo Path "Drive:\{User}\AppData\Roamin\.minecraft\saves\NAME"

echo Pulling latest changes...
git pull

echo Launching Minecraft...
start "" /WAIT """C:\Program Files (x86)\Minecraft Launcher\MinecraftLauncher.exe"""
: Minecraft Launcher Path

echo.
echo Waiting for game process to fully close...
: checkloop
tasklist | findstr /I java.exe >nul
if %errorlevel%==0 (
    echo 🟢 Still running...
    timeout /t 5 >nul
    goto checkloop
)
echo 🔴 Minecraft has closed.

echo Backing up your world to GitHub...

git add .
: Check if there are any changes staged
git diff --cached --quiet
if %errorlevel%==0 (
    echo 🟡 No changes to commit.
) else (
    git commit -m "Auto backup via Windows"
    git push
    echo ✅ Backup pushed to GitHub!
)

pause

```
✅ Replace <YourName> and <YourWorldFolder> with your actual info
✅ Replace the path to MinecraftLauncher.exe if it’s different
Note: I added prompts since i didn't find a one click way to make a .bat run in the background without showing a CMD window. But I assume there's a way to do so.
⸻

## 🍎 macOS Script (minecraft_launcher.sh)
```
#!/bin/bash

# Navigate to the gitrepo (the world folder)
cd "/Users/Abdullah/Library/Application Support/minecraft/saves/WorldName"
# World Repo Path "/Users/{User}/Library/Application Support/minecraft/saves/WorldName"

# Pull latest version from github
git pull

# Open Minecraft
open "/Applications/Minecraft.app"
# Path to your Minecraft.app

# Wait until Minecraft is actually running (java process appears -not launcher-)
until pgrep -x "java" > /dev/null; do
    sleep 2
done



# Wait until Minecraft fully closes (java process ends)
while pgrep -x "java" > /dev/null; do
    sleep 5
done

# Minecraft has closed

# Perform Git backup only after Minecraft was opened and closed
git add .
if git diff --cached --quiet; then
    echo "No changes."
else
    git commit -m "Auto backup via MacOS"
    git push
fi


```
✅ Make it executable with `chmod +x minecraft_launcher.sh` (Via MacOS terminal)
✅ You can launch it from Automator (if you want it to appear in Spotlight Search)

⸻

## 📝 Tips
- Make sure both devices use the same branch and repo.
- Always exit Minecraft before switching devices.
- Git handles the history — you just focus on playing 
- You'd add a custom icon to each and replace your actual game launcher shortcut with the scripts

⸻

Feel free to fork, improve, or reach out if you have suggestions!
Check out my [Linkedin](https://sa.linkedin.com/in/alafari-abdullah)

⸻
