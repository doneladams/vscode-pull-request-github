# Contributing

Thank you for your interest in contributing to this extension! This project welcomes contributions and suggestions.

Aftering cloning and building, check out the [issues list](https://github.com/Microsoft/vscode-pull-request-github/issues?q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc). Issues labeled [good first issue](https://github.com/Microsoft/vscode-pull-request-github/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+sort%3Aupdated-desc+label%3A%22good+first+issue%22) are great candidates to work on. If you're new to writing extensions for VSCode, reading through some of the [documentation](https://code.visualstudio.com/docs/extensions/overview) on extensions is helpful.

## Build and Run

### Prerequisites

- [Git](https://git-scm.com)
- [Node.JS](https://nodejs.org/en/), `>= 8.9.1, < 9.0.0`
- [Yarn](https://yarnpkg.com/en/), follow the [installation guide](https://yarnpkg.com/en/docs/install)
- [VSCode Insiders](https://code.visualstudio.com/insiders/)

If you want explore the source code of this extension yourself, it's easy to get started. Simply follow these steps:

1. Clone the repository
1. Run yarn
1. Compile in the background
	- Run yarn watch
	- Or you can directly start this task by Command Palette -> Run Build Task

To run and debug the extension, press F5.

## Tests

The tests for the extension can be run with `yarn test`.

## Architecture
This extension uses a handful of VSCode APIs, some of which are still being developed. Some features and bugs may require making changes to VSCode itself instead of the extension; these are tagged with `upstream/vscode`.

At a high level, the code in `src` is organized into:
- `authentication`: All code related to the authentication flow
- `common`: Any utility methods. This also includes the code for parsing git diff hunks and mapping comment positions
- `github`: Code that directly makes requests to GitHub
- `view`: The classes that contribute the tree views of the extension, and the `reviewManager` class which orchestrates switching into and out of "Review Mode"

The `preview-src` folder contains all of the code for the "Description" webview, the content shown when clicking on any of the "Description" nodes in the tree.

The entry point of the extension is `extension.ts`.

The VSCode APIs the extension uses to create or display UI are:
- `registerTreeDataProvider`: Creates the "GitHub Pull Requests" tree view and "Changes in Pull Request" tree view
- `createWebviewPanel`: Creates the "Description" page shown for each pull request
- `registerTextDocumentContentProvider`: Returns file contents when clicking on file changes within the tree view
- `registerDecorationProvider`: Adds the '◆' indicators to the explorer and contributed tree view that indicate a file has been commented on
- `reigsterStatusBaritem`: Adds the "Signed in" status bar item
- `registerDocumentCommentsProvider`: Displays ranges you can comment on within the editor and handles adding comments
- `registerWorkspaceCommentsProvider`: Displays the comments panel and handles navigation to files when selecting comments

## Pull Requests
Most contributions require you to agree to a Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us the rights to use your contribution. For details, visit cla.microsoft.com.

When you submit a pull request, a CLA-bot will automatically determine whether you need to provide a CLA and decorate the PR appropriately (e.g., label, comment). Simply follow the instructions provided by the bot. You will only need to do this once across all repos using our CLA.

Before creating a pull request, if the issues involves making changes to the UI, please discuss it in the issue beforehand. This will help keep reviews focused on the code changes.

## Code of Conduct
This project has adopted the Microsoft Open Source Code of Conduct. Be considerate to others and try to be courteous and professional at all times. For more information see the Code of Conduct FAQ or contact opencode@microsoft.com with any additional questions or comments.