# Write your first entry

Complete [Windows setup](WINDOWS-SETUP.md) first. Then use this same routine for each ticket or XP Cyber write-up. Your working folder is **it-support-portfolio**.

[Windows setup, step 4](WINDOWS-SETUP.md#4-create-your-portfolio-and-copy-the-starter-files) copies the starter files from `ITC3` into `it-support-portfolio`. That includes `WRITEUP-TEMPLATE.md` and the `write-ups` folder. Creating an empty portfolio folder doesn't put those files there; complete the copy before using this guide.

## 1. Open your portfolio and get the latest changes

In Windows PowerShell, run each line separately:

```powershell
Set-Location "$env:USERPROFILE\GitHub\it-support-portfolio"
git status
git pull --ff-only
```

- `Set-Location` moves into your portfolio. `$env:USERPROFILE` is your Windows user folder.
- `git status` shows your branch and any unfinished changes. If you have changes from a previous session, keep them and ask me to help finish that work first.
- `git pull` downloads changes from your own GitHub repository. `--ff-only` applies them only when Git can move forward without combining separate histories. If it stops with an error, show me the message.

## 2. Make a new write-up from the template

First check that the setup files are in your current portfolio folder:

```powershell
Test-Path .\WRITEUP-TEMPLATE.md -PathType Leaf
Test-Path .\write-ups -PathType Container
```

`Test-Path` checks whether something exists. `Leaf` checks for a file; `Container` checks for a folder. **Both results should be `True`.** If either is `False`, stop here and check the copy in [Windows setup, step 4](WINDOWS-SETUP.md#4-create-your-portfolio-and-copy-the-starter-files) with me before changing any existing work.

Now create your new entry:

```powershell
Copy-Item .\WRITEUP-TEMPLATE.md .\write-ups\my-first-ticket.md
```

`Copy-Item` uses the existing `WRITEUP-TEMPLATE.md` to **create** `my-first-ticket.md` inside `write-ups`. The new file doesn't need to exist beforehand. `.\` means the current folder. Choose a **new filename each time**, such as `printer-connection.md`, so you keep your previous work. Use a descriptive name rather than a real ticket number.

```powershell
code .
```

`code` opens VS Code, and the dot opens your whole portfolio folder. Open the new file inside `write-ups`.

## 3. Write a short explanation

Aim for **100–200 words**. Use your own words to explain the problem, what you found, your approach, the result, and the skills you practiced. Read the [printer example](write-ups/printer-offline.md) or [XP Cyber example](write-ups/xp-cyber-customer-support.md) to see the expected detail.

For XP Cyber, describe your reasoning and outcome without commands, exact settings, or solution steps. Keep the setting accurate, credit help you received, and say when a result wasn't confirmed.

You can add a few relevant items from the [framework reference](FRAMEWORK-MAPPINGS.md) to the expandable section. Explain each connection briefly, or remove that section while you focus on the write-up.

Leave out names, private ticket details, system identifiers, and passwords. Screenshots and your own completion report are optional; review them for private information before adding them.

## 4. Link your entry from the README

Open `README.md` and replace a sample row in **Selected work** with your own link, skills, and result. For the filename above, the row follows this pattern:

```markdown
| [My first ticket](write-ups/my-first-ticket.md) | Skills I used | A short description of my result |
```

Change the link text, skills, and result to describe your work. If you used a different filename, change the path too. Save both files with **Ctrl+S** and use **Ctrl+Shift+V** to preview each one.

## 5. Review, commit, and push

Return to PowerShell:

```powershell
git status
git diff
git add README.md write-ups
git diff --cached
```

- `status` lists the changes Git sees.
- `diff` shows changes to tracked files that aren't staged yet.
- `add README.md write-ups` stages your README and write-up changes, including new files and removed samples.
- `diff --cached` shows everything staged for the next commit, including your new write-up. Review this before continuing. Press **Q** if a long diff fills the screen.

```powershell
git commit -m "Add my first troubleshooting write-up"
git push
git status
```

- `commit` saves the staged changes locally. `-m` supplies the message; replace the quoted text with a short description of your entry.
- `push` uploads your commits to the destination set during Windows setup.
- `status` should show a clean working tree and an up-to-date branch.

Open your `it-support-portfolio` repository on GitHub in your browser and refresh the page. Open your new entry from the README to confirm both the upload and the link.

Add another entry when it shows a different skill. As you replace the samples, remove their rows and files; remove the example notice once only your own entries remain. The README and your write-ups are all you need to maintain.
