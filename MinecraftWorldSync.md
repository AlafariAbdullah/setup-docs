# 🧠 Auto-Sync Minecraft World with Git

I often play Minecraft on my desktop at home, but when I’m on the go with my laptop, transferring my world manually used to be a hassle. I had to remote into my desktop, zip the save folder, spin up a Python HTTPS server, and download it from my laptop. That got old quickly.

So, I spent two quick hours writing a pair of simple scripts — one for Windows, one for macOS — to automatically run `git pull` before launching Minecraft, and `git push` after exiting the game. Now my Minecraft world syncs seamlessly between devices using GitHub.

## ⚙️ How It Works

1. Your Minecraft world is stored in a local Git repository.
2. When you launch Minecraft:
   - The script pulls the latest version of the world from GitHub.
3. When you exit Minecraft:
   - The script automatically commits your changes and pushes them to GitHub.

No more zipping, no more servers. Just pure Git automation.

---

## 🪟 Windows Script (`minecraft_launcher.bat`)

```bat
@echo off
cd "C:\Users\<YourName>\AppData\Roaming\.minecraft\saves\<YourWorldFolder>"

echo Pulling latest world from GitHub...
git pull

echo Launching Minecraft...
start /wait "" "C:\Path\To\MinecraftLauncher.exe"

echo Committing and pushing changes...
git add .
git commit -m "Auto backup"
git push

echo Done!
pause
```
✅ Replace <YourName> and <YourWorldFolder> with your actual info
✅ Replace the path to MinecraftLauncher.exe if it’s different
⸻

🍎 macOS Script (minecraft_launcher.sh)
```
#!/bin/bash

# Navigate to the gitrepo (the world folder)
cd "/Users/Abdullah/Library/Application Support/minecraft/saves/WorldName"

# Pull latest version from github
git pull

# Open Minecraft
open "/Applications/Minecraft.app"

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
    git commit -m "Auto backup"
    git push
fi


```
✅ Make it executable with `chmod +x minecraft_launcher.sh` (Via MacOS terminal)
✅ You can launch it from Automator (if you want it to appear in Spotlight Search)

⸻

📝 Tips
- Make sure both devices use the same branch and repo.
- Always exit Minecraft before switching devices.
- Git handles the history — you just focus on playing 
- You'd add a custom icon to each and replace your actual game launcher shortcut with the scripts
⸻

Feel free to fork, improve, or reach out if you have suggestions!

---
