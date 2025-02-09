# Visual Studio Code

### ~/.vscode/settings.json

Note the `.envFile` setting -- that must be combined with a `.env` file at the project root with `PYTHONPATH=./app` (assuming your code is in the subdir `app`  )

```json
{
    "workbench.colorCustomizations": {
        "activityBar.background": "#c2817f",
        "activityBar.foreground": "#15202b",
        "activityBar.inactiveForeground": "#15202b99",
        "activityBarBadge.background": "#336c35",
        "activityBarBadge.foreground": "#e7e7e7",
        "titleBar.activeBackground": "#b25f5c",
        "titleBar.inactiveBackground": "#b25f5c99",
        "titleBar.activeForeground": "#e7e7e7",
        "titleBar.inactiveForeground": "#e7e7e799",
        "statusBar.background": "#b25f5c",
        "statusBarItem.hoverBackground": "#c2817f",
        "statusBar.foreground": "#e7e7e7"
    },
    "peacock.color": "#b25f5c",
    "python.pythonPath": "/Users/william/.virtualenvs/biorad_api-1pnfAOVW/bin/python",
    "python.testing.pytestArgs": ["tests"],
    "python.testing.unittestEnabled": false,
    "python.testing.nosetestsEnabled": false,
    "python.testing.pytestEnabled": true,
    "python.analysis.openFilesOnly": false,
    "python.analysis.memory.keepLibraryLocalVariables": true,
    "python.autoComplete.addBrackets": true,
    "python.venvPath": "~/.virtualenvs",
    "python.testing.cwd": "${workspaceFolder}",
    "python.linting.pep8Path": "pep8",
    "python.envFile": "${workspaceFolder}/.env",
    "python.linting.pep8Enabled": false,
    "python.sortImports.path": "/usr/local/bin/isort",
    "autoDocstring.docstringFormat": "google",
    "python.formatting.blackPath": "/usr/local/bin/black",
    "python.autoComplete.extraPaths": ["${workspaceFolder}/app"]
}