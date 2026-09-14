# Set up your portfolio on Windows

Follow this guide in order, using **Windows PowerShell** for the commands and your browser for GitHub sign-in and repository creation. You'll clone ITC3, copy its starter files into your own portfolio, and upload your work to your own GitHub repository.

Run **one command at a time**. Read the explanation and check the result before continuing. If a command fails, stop there. If you already started the previous setup guide, show me what you've completed before repeating setup; keep your existing files.

## Before you start

Create your account at [GitHub](https://github.com/signup), verify your email, and follow [NFARThom](https://github.com/NFARThom). Send me your GitHub username so I can invite you to ITC3. Accept the invitation I send using that same account.

In your [GitHub email settings](https://github.com/settings/emails), enable **Keep my email addresses private** and copy the GitHub-provided `noreply` address. You'll use it in step 5. Replace `YOUR NAME` and `YOUR GITHUB NOREPLY ADDRESS` below with your information, keeping the quotation marks.

## 1. Install the tools

Open **Windows PowerShell** from Start. Run these lines separately:

```powershell
winget install --id Git.Git --exact --source winget
winget install --id Microsoft.VisualStudioCode --exact --source winget
```

| Part | What it does |
| --- | --- |
| `winget install` | Uses Windows Package Manager to install an application. |
| `--id` | Selects the application by its package identifier. |
| `Git.Git` | Installs Git, which tracks your local file history. |
| `Microsoft.VisualStudioCode` | Installs VS Code, where you'll write and preview Markdown. |
| `--exact` | Requires an exact match for the package identifier. |
| `--source winget` | Uses the WinGet package catalog. |

Accept the installation prompts. An already-installed or up-to-date message is fine. If Windows needs administrator credentials or doesn't recognize `winget`, ask me to help with installation. [WinGet command reference](https://learn.microsoft.com/en-us/windows/package-manager/winget/install).

**Close the entire PowerShell window and open a new one**, then check the tools:

```powershell
git --version
code --version
```

Each command asks that program to display its version. Both should print version information before you continue.

## 2. Check your access to ITC3

In your browser, sign in to GitHub using the account you gave me. Open [ITC3](https://github.com/NFARThom/ITC3) and check that you can see its files.

If the page says **404** or you can't see the repository, check that you accepted my invitation using that account. Show me if access still fails before continuing.

## 3. Clone ITC3 onto your computer

Make a folder for your Git projects:

```powershell
New-Item -ItemType Directory -Path "$env:USERPROFILE\GitHub" -Force
```

- `New-Item` creates something; `-ItemType Directory` makes it a folder.
- `-Path` specifies where. `$env:USERPROFILE` means your Windows user folder.
- `\GitHub` is the new folder inside it. Quotes keep paths containing spaces together.
- `-Force` lets this command reuse the parent folder if it already exists.

Move PowerShell into that folder:

```powershell
Set-Location "$env:USERPROFILE\GitHub"
```

`Set-Location` changes the folder where the next commands run.

Now clone the shared starter:

```powershell
git clone --depth 1 https://github.com/NFARThom/ITC3.git ITC3
```

| Part | What it does |
| --- | --- |
| `git clone` | Downloads a repository and its working files. |
| `--depth 1` | Limits downloaded history to the latest commit, keeping the starter clone small. |
| `https://github.com/NFARThom/ITC3.git` | Identifies the shared ITC3 repository. |
| `ITC3` | Names the new local folder. |

When Git requests sign-in, choose **Sign in with your browser** if prompted. Use the same GitHub account from step 2, approve access, and complete two-factor authentication if requested. Git for Windows includes **Git Credential Manager**, which handles this sign-in and remembers it for later Git commands. If you're already authenticated, you may not see a prompt. [Sign-in reference](https://docs.github.com/en/get-started/git-basics/caching-your-github-credentials-in-git).

Wait for cloning to finish and the PowerShell prompt to return. This uses ITC3's default branch. PowerShell stays in your `GitHub` folder after cloning. If access is denied, check the account used for Git sign-in and that you accepted my invitation; show me the error if it still fails. [Clone reference](https://git-scm.com/docs/git-clone).

## 4. Create your portfolio and copy the starter files

The two folders have different jobs:

| Folder | Purpose |
| --- | --- |
| `GitHub\ITC3` | The shared starter you just cloned. |
| `GitHub\it-support-portfolio` | Your own work and Git history. Do your writing here. |

Create your working folder:

```powershell
New-Item -ItemType Directory -Path .\it-support-portfolio
```

`.\` means the current folder. This creates `it-support-portfolio` beside `ITC3`. If the folder already exists, stop and show me before copying anything into it.

**This next command fills your new portfolio folder.** Run it while PowerShell is still in `GitHub`. It copies `WRITEUP-TEMPLATE.md`, `README.md`, `write-ups`, and the other starter files from `ITC3` into `it-support-portfolio`:

```powershell
Copy-Item -Path .\ITC3\* -Destination .\it-support-portfolio -Recurse -Force -Exclude .git
```

| Part | What it does |
| --- | --- |
| `Copy-Item` | Copies files and folders. |
| `-Path .\ITC3\*` | Selects the contents of the ITC3 folder; `*` means all items. |
| `-Destination .\it-support-portfolio` | Places the copies in your portfolio. |
| `-Recurse` | Includes the files inside subfolders. |
| `-Force` | Includes hidden items, such as configuration files. |
| `-Exclude .git` | Leaves ITC3's Git history and connection in the starter folder. |

Your portfolio will start with its own first commit. The shared starter stays intact. [Copy command reference](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/copy-item).

```powershell
Set-Location .\it-support-portfolio
Get-ChildItem -Force
```

`Set-Location` enters your portfolio. `Get-ChildItem` lists its contents; `-Force` includes hidden items. Check that you can see `README.md`, `WRITEUP-TEMPLATE.md`, `.gitignore`, and `write-ups`. There should be no `.git` folder yet.

Confirm that the template and write-up folder arrived:

```powershell
Test-Path .\WRITEUP-TEMPLATE.md -PathType Leaf
Test-Path .\write-ups -PathType Container
```

`Test-Path` checks a location. `Leaf` checks for a file; `Container` checks for a folder. **Both commands must return `True` before you continue.** If either returns `False`, stop and show me the copy command's output. This copy is what makes the template available later in Start Here.

## 5. Start your own Git history

```powershell
git init -b main
```

`git init` starts Git tracking in this folder. `-b main` names your first branch `main`. A branch is a line of saved work; you'll use `main` for this portfolio. [Git initialization reference](https://git-scm.com/docs/git-init).

Tell Git who is making the changes:

```powershell
git config user.name "YOUR NAME"
git config user.email "YOUR GITHUB NOREPLY ADDRESS"
```

- `git config` changes a Git setting for this repository.
- `user.name` sets the author name on your commits.
- `user.email` sets the commit email. Use the exact `noreply` address you copied earlier.
- These settings label your commits. GitHub sign-in happens through the browser prompt when Git needs access.

Check the saved values:

```powershell
git config --get user.name
git config --get user.email
```

`--get` reads a setting without changing it. Check that both values are yours. [Commit email reference](https://docs.github.com/en/account-and-profile/how-tos/email-preferences/setting-your-commit-email-address).

## 6. Personalize your introduction

```powershell
code .
```

`code` opens VS Code. The dot means **open this folder**, which should be `it-support-portfolio`.

Open `README.md`, add your name, and write one or two sentences about your interests and training. Keep the example notice while sample entries are still listed. Press **Ctrl+S** to save and **Ctrl+Shift+V** to preview the Markdown.

## 7. Save your first commit

Return to PowerShell:

```powershell
git status
```

`status` shows your branch and which files have changes. You should be on `main`, with files waiting for their first commit.

```powershell
git add .
```

`add` selects files for the next commit; this is called **staging**. The dot selects changes under the current folder. The starter's `.gitignore` keeps archive and raw-evidence folders out of normal staging.

```powershell
git diff --cached --stat
```

`diff` shows changes. `--cached` selects the staged changes, and `--stat` shows a short summary by file. Review that list before saving. Keep private ticket details and credentials out of your portfolio.

```powershell
git commit -m "Start my IT support portfolio"
```

`commit` saves the staged version in your local history. `-m` supplies its message, and the quoted text describes this saved version. You now have your first local commit.

## 8. Create your own repository on GitHub

In your browser, open [GitHub's new repository page](https://github.com/new). Use these settings:

| Setting | What to choose |
| --- | --- |
| Owner | Your GitHub username. |
| Repository name | `it-support-portfolio` |
| Visibility | **Private**, while you prepare your work. |
| Template | None. |
| Add README, .gitignore, or license | Leave all of these off. Your local files are ready to upload. |

Click **Create repository**. Keep the new repository empty so your first push can upload the history you already created locally. If GitHub says the repository already exists, stop and show me so we can use the work you've already started. [Repository creation reference](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository).

Leave the repository page open. Return to this guide for the commands below; you'll refresh that page after uploading.

## 9. Connect your repository and upload

Return to PowerShell, still inside `it-support-portfolio`. Replace `YOUR-USERNAME` with **your GitHub username** before running:

```powershell
git remote add origin https://github.com/YOUR-USERNAME/it-support-portfolio.git
```

| Part | What it does |
| --- | --- |
| `git remote add` | Saves a connection to an online repository. |
| `origin` | Names that connection so later commands can use it. |
| `https://github.com/YOUR-USERNAME/it-support-portfolio.git` | Identifies the repository you just created under your account. |

This connects your local portfolio to its GitHub destination. It doesn't upload files yet. If Git reports that `origin` already exists, stop and show me the output of the next command before changing it. [Connection and upload reference](https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github#adding-a-local-repository-to-github-using-git).

```powershell
git remote -v
```

`remote` lists your online connections. `-v` displays their full addresses. Both `origin` lines should point to **your GitHub account's `it-support-portfolio` repository**. Check this before pushing.

```powershell
git push -u origin main
```

| Part | What it does |
| --- | --- |
| `push` | Uploads your local commits. |
| `-u` | Remembers this connection for later pulls and pushes. |
| `origin` | Selects your own GitHub repository. |
| `main` | Selects the branch to upload. |

If Git requests sign-in again, complete the browser sign-in using your GitHub account, as you did when cloning ITC3.

After the push finishes, return to your repository page in the browser and refresh it. Confirm that the repository is under your username and your personalized README appears.

```powershell
git status
```

You should see a clean working tree and a branch that's up to date with `origin/main`. Setup is complete. Continue with [Write your first entry](START-HERE.md) for the everyday copy, edit, commit, and push routine.

If a tool isn't recognized after installation, close the whole terminal window and reopen PowerShell. If any other command fails, keep its message and show me where you stopped.
