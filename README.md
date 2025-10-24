# Terminal Snippets

<!-- Plugin description -->
Terminal Snippets is an plugin that allows you to quickly inject predefined command snippets into the terminal.

## Features

- 🚀 Quick access to frequently used terminal commands
- 📁 Organize snippets by categories with automatic submenus
- 🔤 Dynamic variables (project info, date/time, clipboard, etc.)
- 💬 Interactive variables (prompts, choices, confirmations)
- ⚙️ Easy configuration through Settings > Tools > Terminal Snippets
- 🎯 One-click command injection via terminal toolbar icon
- 💾 Persistent storage of your custom snippets
- 📤 Import/Export snippets as JSON
- 🔄 Compatible with both Classic Terminal and Reworked Terminal 2025

## Usage

1. Configure your snippets in **Settings > Tools > Terminal Snippets**
2. Open a terminal window (**View > Tool Windows > Terminal**)
3. Click the **Terminal Snippets** icon in the terminal toolbar
4. Select a snippet to inject it into the terminal

<!-- Plugin description end -->

## Installation

### Manual Installation

1. Download the latest `Terminal-Snippets-X.X.X.zip` from [my Jetbrains MarketPlace Page](https://plugins.jetbrains.com/vendor/jawehrung)
2. Open your Jetbrains IDE
3. Go to <kbd>Settings/Preferences</kbd> > <kbd>Plugins</kbd>
4. Click the <kbd>⚙️</kbd> icon > <kbd>Install Plugin from Disk...</kbd>
5. Select the downloaded ZIP file
6. Restart IntelliJ IDEA

## Configuration

1. Go to <kbd>Settings/Preferences</kbd> > <kbd>Tools</kbd> > <kbd>Terminal Snippets</kbd>
2. Add your custom snippets with:
   - **Name**: Display name of the snippet
   - **Category**: Group snippets together (e.g., "Build", "Git", "Docker")
   - **Command**: The command to inject (supports multi-line)
3. Click <kbd>OK</kbd> to save

### Categories

- Snippets are automatically organized by category in the dropdown menu
- If you have multiple categories, they appear as submenus
- If you have only one category, snippets are displayed in a flat list
- Leave category blank to use the default "General" category

### Import/Export

- **Export**: Click the Export button to save your snippets as JSON with timestamp
- **Import**: Click the Import button to load snippets from a JSON file
- Duplicate snippets (same name + category) are automatically skipped during import

## Variables

Terminal Snippets supports both static and interactive variables in your commands.

### Static Variables

These variables are automatically resolved when the snippet is executed:

| Variable | Description | Example |
|----------|-------------|----------|
| `${PROJECT_NAME}` | Current project name | `echo "Building ${PROJECT_NAME}"` |
| `${PROJECT_PATH}` | Current project path | `cd ${PROJECT_PATH}` |
| `${FILE_PATH}` | Currently open file path | `cat ${FILE_PATH}` |
| `${SELECTION}` | Selected text in editor | `echo "${SELECTION}"` |
| `${CLIPBOARD}` | Clipboard content | `echo ${CLIPBOARD}` |
| `${DATE}` | Current date (dd/MM/yyyy) | `echo "Build date: ${DATE}"` |
| `${TIME}` | Current time (HH:mm:ss) | `echo "Build time: ${TIME}"` |
| `${YEAR}` | Current year | `mkdir backup-${YEAR}` |
| `${MONTH}` | Current month (01-12) | `echo "Month: ${MONTH}"` |
| `${MONTH_NAME_SHORT}` | Short month name (Jan, Feb...) | `echo "${MONTH_NAME_SHORT}"` |
| `${MONTH_NAME_FULL}` | Full month name (January...) | `echo "${MONTH_NAME_FULL}"` |
| `${DAY}` | Current day (01-31) | `echo "Day: ${DAY}"` |
| `${HOUR}` | Current hour (00-23) | `echo "Hour: ${HOUR}"` |
| `${MINUTE}` | Current minute (00-59) | `echo "Minute: ${MINUTE}"` |
| `${USERLOGIN}` | System username | `echo "User: ${USERLOGIN}"` |
| `${GIT_BRANCH}` | Current Git branch | `echo "Branch: ${GIT_BRANCH}"` |
| `${GIT_COMMIT}` | Current commit hash (full) | `echo "Commit: ${GIT_COMMIT}"` |
| `${GIT_COMMIT_SHORT}` | Current commit hash (short) | `git tag v1.0-${GIT_COMMIT_SHORT}` |
| `${GIT_REMOTE}` | Git remote URL | `echo "Remote: ${GIT_REMOTE}"` |

### Interactive Variables

These variables prompt the user for input when the snippet is executed:

| Variable | Description | Example |
|----------|-------------|----------|
| `${VAR:Description}` | Simple text input | `git commit -m "${VAR:Commit message}"` |
| `${VAR:Description:Default}` | Text input with default value | `docker run -p ${VAR:Port:8080}:8080 app` |
| `${CHOICE:Description:opt1\|opt2}` | Dropdown selection | `mvn clean ${CHOICE:Phase:install\|package\|deploy}` |
| `${CONFIRM:Description}` | Yes/No confirmation | `echo "Confirmed: ${CONFIRM:Delete files?}"` |
| `${PASSWORD:Description}` | Masked password input | `docker login -p ${PASSWORD:Docker password}` |
| `${PATH:Description}` | File/folder picker | `cd ${PATH:Select directory}` |

### Variable Examples

**Build with timestamp:**
```bash
echo "Building ${PROJECT_NAME} on ${DATE} at ${TIME}"
gradlew clean build
```

**Interactive deployment:**
```bash
cd ${PROJECT_PATH}
mvn clean ${CHOICE:Select phase:package|install|deploy}
echo "Deployed by ${USERLOGIN} at ${TIME}"
```

**Git-aware build:**
```bash
echo "Building ${PROJECT_NAME} from branch ${GIT_BRANCH}"
echo "Commit: ${GIT_COMMIT_SHORT}"
gradlew build -Pversion=${GIT_BRANCH}-${GIT_COMMIT_SHORT}
```

**Conditional execution:**
```bash
echo "Delete all logs?"
if [ "${CONFIRM:Are you sure?}" = "yes" ]; then
  rm -rf logs/*
fi
```

## Default Snippets

The plugin comes with two example snippets:
- **Pip Upgrade** (Category: Python)
- **Git Status** (Category: Git)

## Terminal Compatibility

### Classic Terminal
- ✅ Commands are injected into the prompt
- ✅ Multi-line commands are supported
- ✅ Press <kbd>Enter</kbd> to execute
- ✅ You can modify the command before execution

### Reworked Terminal 2025
- ✅ Commands are executed automatically
- ✅ Multi-line commands execute line by line
- ℹ️ No modification possible before execution (API limitation)


---
Plugin based on the [IntelliJ Platform Plugin Template][template].

[template]: https://github.com/JetBrains/intellij-platform-plugin-template
[docs:plugin-description]: https://plugins.jetbrains.com/docs/intellij/plugin-user-experience.html#plugin-description-and-presentation
