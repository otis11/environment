# Table of contents
* [SSH Keys](#ssh-keys)
* [Windows Envrionment](#windows-environment)
* [VSCode](#vscode)

# SSH Keys
Create a ssh key on your machine.
```bash
ssh-keygen -t ed25519
cat ~/.ssh/id_ed25519.pub
```
SSH Key Settings:
- [GitHub](https://github.com/settings/keys)

# Windows Environment
### Add bin to PATH
1. Go to `Edit environment variables for your account` (just search)
2. Under `User variables for X` select `Path` and click `Edit`
3. Click on `New` and add the absolute path to the folder

### C++ Compiler
1. Install [msys2](https://www.msys2.org/)
2. Install mingw toolchain
```bash
pacman -S --needed base-devel mingw-w64-ucrt-x86_64-toolchain
```
3. Add `C:\msys64\ucrt64\bin` to [PATH](#add-bin-to-path)
4. Open new `cmd` and use `gcc`

### Git
1. Install [Git for Windows](https://git-scm.com/download/win)
2. Add `C:\Program Files\Git\cmd` to [Path](#add-bin-to-path)
3. Open new `cmd` and use `git`

# VSCode
### Font: Fira Code
https://github.com/tonsky/FiraCode/wiki/Installing

### user settings.json
```json
{
    // some useful shortcuts
    // ctrl +               space completion in context
    // ctrl + t             search symbol in workspace
    // ctrl + p             execute command
    // alt + shift + o      organize imports 
    "editor.inlineSuggest.enabled": true,
    "editor.cursorStyle": "block",
    "editor.cursorBlinking": "phase",
    "window.title": "${rootName}${separator}${rootPath}${separator}${activeEditorShort}",
    "window.menuBarVisibility": "compact",",
    "editor.cursorSurroundingLines": 4,
    // Disable confirmation stuff 
    "terminal.integrated.enableMultiLinePasteWarning": false,
    "explorer.confirmDragAndDrop": false,
    "explorer.confirmDelete": false,
    // Disable other stuff/declutter UI
    "terminal.integrated.showExitAlert": false,
    "workbench.tips.enabled": false,
    "workbench.startupEditor": "none",
    "workbench.layoutControl.enabled": false,
    "breadcrumbs.enabled": false,
    "explorer.openEditors.visible": 0,
    "editor.minimap.enabled": false,
    "editor.guides.indentation": false,
    "editor.lineNumbers": "off",
    // File tree view
    "explorer.compactFolders": false,
    "workbench.tree.indent": 16,
    "workbench.tree.renderIndentGuides": "none",
    // Format & Autosave
    "editor.formatOnPaste": true,
    "editor.formatOnSave": true,
    "files.autoSave": "onWindowChange",
    // Font
    "terminal.integrated.fontFamily": "Fira Code",
    "editor.fontFamily": "Fira Code",
    "editor.fontLigatures": true,
    /// Git 
    /// otherwise it will do merge stuff which makes git history bad 
    /// https://github.com/microsoft/vscode/issues/174198 
    "git.rebaseWhenSync": true,
    /// Languages & Tools
    "eslint.validate": [
        "vue",
        "javascript",
        "javascriptreact",
        "typescript",
    ],
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    "tailwindCSS.emmetCompletions": true,
    "files.associations": {
        ".env": "dotenv"
    },
    "dotenv.enableAutocloaking": false,
    // idk, maybe try 
    "editor.guides.bracketPairs": false,
}
```
### keybindings.json
```json
[
    // so comment lines moves the cursor down after commenting. Easy to comment multiple lines
    {
        "key": "ctrl+/",
        "command": "runCommands",
        "args": {
            "commands": [
                "editor.action.commentLine",
                "cursorDown"
            ]
        },
        "when": "editorTextFocus"
    },
]
```
### extensions
```text
EditorConfig.EditorConfig
dotenv.dotenv-vscode
ms-vscode.cpptools
ms-vscode-remote.remote-wsl
```
