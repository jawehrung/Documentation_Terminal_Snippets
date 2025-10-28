<!-- Keep a Changelog guide -> https://keepachangelog.com -->

# Terminal Snippets Changelog

## [1.0.3] - 2025-10-28

### Added

- Environment variable support via ${ENVVAR:VAR_NAME} syntax
- File variables: FILE_NAME, FILE_DIR, PACKAGE_NAME
- Module variable: MODULE_NAME for multi-module projects
- System variables: USER_HOME, OS_NAME
- Git variables: GIT_ROOT, GIT_USER_NAME, GIT_USER_EMAIL, GIT_TAG_LATEST
- Build tool versions: GRADLE_VERSION, MAVEN_VERSION

## [1.0.2] - 2025-10-24

### Added

- "Insert Variable" button in snippet editor with popup menu

## [1.0.1] - 2025-10-20

### Added

- Quick access to terminal command snippets via toolbar icon
- Category-based organization with automatic submenu generation
- Persistent storage of custom snippets
- Import/Export functionality with JSON format and timestamp
- Duplicate detection during import (based on name + category)
- Multi-line command support for both Classic and Reworked Terminal 2025
- 19 static variables: PROJECT_NAME, PROJECT_PATH, FILE_PATH, SELECTION, CLIPBOARD, DATE, TIME, YEAR, MONTH, DAY, HOUR, MINUTE, MONTH_NAME_SHORT, MONTH_NAME_FULL, USERLOGIN, ENVVAR, GIT_BRANCH, GIT_COMMIT, GIT_COMMIT_SHORT, GIT_REMOTE
- 4 Git variables: GIT_BRANCH, GIT_COMMIT, GIT_COMMIT_SHORT, GIT_REMOTE
- 6 interactive variable types: VAR (text input), VAR with default, CHOICE (dropdown), CONFIRM (yes/no), PASSWORD (masked), PATH (file picker)
- Automatic sorting by category then name in settings table
- Double-click to edit snippets in settings panel
- 18 pre-built snippet template files (250+ ready-to-use snippets)
- Default snippets: Pip Upgrade (Python) and Git Status (Git)

### Changed

- Add button opens editor dialog immediately (creates snippet only on OK)
- Export filename includes timestamp: terminal-snippets-yyyyMMdd-HHmmss.json

### Fixed

- Multi-line command handling for Classic Terminal (appends \n)
- Multi-line command handling for Reworked Terminal (executes line by line)
- Deprecated API: replaced addExtraActions with individual addExtraAction calls

[Unreleased]: https://github.com/jawehrung/Documentation_Terminal_Snippets/compare/v1.0.3...HEAD
[1.0.3]: https://github.com/jawehrung/Documentation_Terminal_Snippets/compare/v1.0.2...v1.0.3
[1.0.2]: https://github.com/jawehrung/Documentation_Terminal_Snippets/compare/v1.0.1...v1.0.2
[1.0.1]: https://github.com/jawehrung/Documentation_Terminal_Snippets/commits/v1.0.1
