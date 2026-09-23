# 💻 BhavyaJustChill's Windows Terminal & PowerShell Setup

A beautifully clean, developer-focused terminal configuration featuring the **Dracula theme spectrum**, custom **PowerShell 7 workflow optimization**, and a highly interactive **Oh My Posh** setup.

---

## ✨ Features

- 🎨 **Dracula Color Palette:** Unified color schemes across Windows Terminal, PowerShell blocks, and Git states.
- 🚀 **Performance Tuning:** Pre-configured to disable distracting predictive text suggestions (`PSReadLine` tuning).
- 👤 **Context-Aware Prompt:** Displays active user profile name right next to your operating system identity.
- 📁 **Streamlined Navigation:** Strips cluttered absolute paths to display _only_ the immediate working directory.
- 🌿 **Deep Git Integration:** Dynamically updates backgrounds based on ahead/behind statuses, staged tracking, and working tree modification details.
- 🐍 **Language Segment Control:** Strips out bloated runtime blocks to cleanly display your active **Python** virtual environment states.

---

## 🛠️ Prerequisites & Font Setup

To render the terminal icons and custom Powerline symbols correctly, you **must** install the patched **Cascadia Code** variant from the official repository:

### 1. Install Oh My Posh

Install the custom prompt engine via Windows Package Manager:

```powershell
winget install JanDeDobbeleer.OhMyPosh -s winget
```

### 2. Install the Official Cascadia Code Patched Font

Do not use automated wrapper links. You can obtain the official font binaries directly from the repository source folder:

- **Direct Individual Download:**
  Go to the official [Nerd Fonts CascadiaCode Directory](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/CascadiaCode). Download the following files manually:
  - `CaskaydiaCoveNerdFont-Regular.ttf` (Standard variant)
  - `CaskaydiaCoveNerdFont-Bold.ttf` (Bold variant)
  - `CaskaydiaCoveNerdFontMono-Regular.ttf` (Strictly monospaced icons variant)

- **Scripted Official Archive Download:**
  Alternatively, you can pull the official full compiled font family asset package using standard PowerShell tools without hitting third-party links:
  ```powershell
  Invoke-WebRequest -Uri "https://github.com" -OutFile "\$env:USERPROFILE\Downloads\CascadiaCode.zip"
  ```
  Go to your Downloads folder, extract the contents, select the font files, right-click, and select **Install for all users**.

---

## 🚀 Quick Setup Instructions

### 1. Configure the PowerShell Profile

Locate your PowerShell profile path by running `echo $PROFILE`. Replace or update its contents with the logic found in `Microsoft.PowerShell_profile.ps1`:

```powershell
# Stop inline autocomplete suggestions
Set-PSReadLineOption -PredictionSource None

# Initialize Oh My Posh via the live configuration
oh-my-posh init pwsh --config "F:\cli\oh-my-posh\themes\bhavyajustchill.omp.json" | Invoke-Expression
```

### 2. Apply Windows Terminal Layouts

1. Open Windows Terminal settings (`Ctrl + ,`).
2. Click **Open JSON File** in the bottom left corner.
3. Replace or merge your global profile parameters using the configurations defined in this repository's `settings.json`. Ensure your chosen font (e.g., `"CaskaydiaCove Nerd Font"`) is assigned to your profile font family property.

### 3. Hot-Reload Changes

Apply the updates to your running session instantly without closing your window:

```powershell
. $PROFILE
```

---

## 📂 Repository Contents

- 📄 `bhavyajustchill.omp.json` - Custom two-line Dracula styled theme engine structure.
- 📜 `Microsoft.PowerShell_profile.ps1` - Session initialization behaviors and functional adjustments.
- ⚙️ `settings.json` - Global Windows Terminal structure, fonts, and window options.
