# Appendices, Linux, Macos, Windows ...

> Blender Python API Essentials reference. Original prose; identifiers preserved verbatim.

## Overview

Covers: Appendices; Linux; macOS; Windows; Creating a Dynamic Extensions Repository; Creating an Extensions Repository; Working Limits; Getting Started; Building the Manual; Editing the Manual; Local Editing; Installing Dependencies; Installation on Linux; Installation on macOS; Installation on Windows; Pull Requests; Commit Guidelines; Contribute Documentation.

## Appendices

The Appendices chapter gives more detailed explanations of certain Blender tools that typical usage may not require.

## Linux

Linux quick start: open a terminal, change to Blender's install directory, and run it:
```text
cd <install-dir>
./blender
```
If Blender is on your PATH (typically when installed via a distribution package), just run `blender`. Depending on your desktop environment, installing Blender may add a desktop icon or a menu entry, and many environments offer a "Run in terminal" option (the docs show configuring the KDE menu icon to start Blender from a terminal, and a screenshot of Blender launched from a Linux terminal with its text output).

## macOS

macOS quick start: open the Terminal app and run the executable inside the app bundle:
```text
cd /Applications/Blender.app/Contents/MacOS
./Blender
```
If you do this often, add that directory to your PATH: open a Terminal, run `sudo nano /etc/paths`, enter your password, go to the file's bottom, add /Applications/Blender.app/Contents/MacOS, press Ctrl-X to quit, and Y to save — a new terminal will then accept `Blender`. On macOS, ".app" applications are really folders that Finder shows as files, so to get terminal output you must point at the executable inside, which lives at ./Blender.app/Contents/MacOS/Blender (start a terminal from Applications ▸ Utilities). With Blender in the Applications folder you can run `/Applications/Blender.app/Contents/MacOS/Blender`.

## Windows

Windows quick start: open the Command Prompt, change to Blender's install directory, and run it:
```text
cd c:\<install-dir>
blender
```
You can also add Blender's folder to the system PATH to avoid changing directory each time. On Windows the Console Window (the Command Prompt) first opens as a separate desktop window, then the main Blender window appears and the console is toggled off; show it again via Window ▸ Toggle System Console. To start Blender from the command line, open a Command Prompt (press OSKey-R, type cmd) and find the executable — an installer install puts it at C:\Program Files\Blender Foundation\Blender\blender.exe. The docs show the Console Window right after startup and again later after opening a file, with the relevant messages.

## Creating a Dynamic Extensions Repository

A dynamic extensions repository serves a smaller JSON file holding only the latest version of the extensions compatible with the query parameters; it's only relevant when a repository holds multiple versions of multiple extensions, and for small or personal repositories a static repository is simpler and recommended. Listing: set one up by following the static-repository steps, since the format and listing are identical. Query parameters: when fetching the listing, Blender passes "platform" and "blender_version" so only compatible extensions are listed, sent as query-URL parameters — the base URL `https://extensions.blender.org/api/v1/extensions/` becomes, for example, `https://extensions.blender.org/api/v1/extensions/?blender_version=4.2.0&platform=linux-x64`. Access token: a repository may require authentication, so the user can give it an access token that Blender sends in an Authorization header:
```text
curl -i https://extensions.blender.org/api/v1/extensions/ \
-H "Accept: application/json" \
-H "Authorization: Bearer abc29832befb92983423abcaef93001"
```

## Creating an Extensions Repository

A third-party site can support Blender extensions in several ways, from simplest to most involved: Static (host one static JSON file listing all the repository's packages), Dynamic (serve the JSON on demand per Blender version and platform), or Platform (fork the entire Extensions Website to make your own). Tags and translations: if you plan to use tags other than the Blender Extensions Platform's, submit a pull request to tags.py so they can appear translated inside Blender.

## Working Limits

Working limits. Space: object and vertex positions aren't clamped, but larger values grow steadily less precise. A table of scale versus accuracy: at 10, 1/1,048,576th; at 100, 1/131,072nd; at 1,000, 1/16,384th; at 10,000, 1/1,024th; at 100,000, 1/128th; and at 1,000,000, 1/16th. As a rough rule, values within -5,000 to +5,000 (a 10,000 range) are usually reliable, since single-precision floating-point math is used internally. Time: a scene currently allows at most 1,048,574 frames, giving continuous shots of 12 hours 8 minutes at 24 fps, 11 hours 39 minutes at 25 fps, 9 hours 42 minutes at 30 fps, and 4 hours 51 minutes at 60 fps; in practice a finished work usually combines many scenes, so this cap doesn't limit total length. Text fields: fixed-length strings are used internally (for data-block names, modifiers, vertex groups, UV layers, and so on); some common limits are directory 767, file-name 255, file-path 1023, and identifier 63, and because of multi-byte encoding some Unicode characters consume more than one ASCII character.

## Getting Started

Welcome — this section guides contributing to the Blender manual, which is written in reStructuredText (RST), a straightforward markup language well suited to technical documentation; you can edit it online or with your local text editor, with all contributions managed through a collaborative workflow on Blender's development platform, projects.blender.org. The two editing options are: Online Editing (contribute straight from your browser using Blender's online editor — the simplest, fastest method, ideal for quick edits and corrections) and Local Editing (edit the manual files on your computer with a plain text editor, synced with the online version through a repository so your local edits stay current, and able to build and preview your edits before you submit). Tip: local editing is recommended for larger contributions, major rewrites, or when you need to preview before submitting.

## Building the Manual

Converting the RST files into HTML pages is simple: open a terminal or Command Prompt in the ~/blender-manual directory and run:
```text
make
```
(On Windows you can just open make.bat to run the command without typing it in the Command Prompt.) This is the command to use when building the docs — other commands are listed by `make help` — and it converts the RST files to HTML, opens your default browser to the result, then keeps running to watch for RST changes and refresh the HTML as needed. The built pages can also be browsed manually under ~/blender-manual/build/html (e.g. open build/html/index.html for the home page). The first build (or after major changes) may take several minutes, but later changes take only a few seconds.

## Editing the Manual

You modify the manual by editing local text files kept in sync with the online ones via a repository, from which the server updates the online manual. The manual is written in reStructuredText (RST), editable in a plain text editor, and for a local preview you build the RST source into HTML. Update: first bring your local copy up to date with `make update`. Writing: edit the .rst files in the manual folder with any text editor, checking the Writing Style Guide for conventions and the Markup Style Guide for the RST language. Bigger changes: before adding or overhauling a section, check carefully that it doesn't already exist (the docs can be disorganized, with duplicated or oddly placed sections — if you find one, file an issue and optionally include a revision), and before any edit that isn't simple and plainly justified (such as moving folders), verify with a manual maintainer that it fits the community's vision, since otherwise someone may already be working on that section, it may be scheduled for deletion, or it may be due for a planned Blender change — communicating early and often keeps the environment productive and the manual better. Getting help: pose questions about functionality to the Blender developers for that area, or ask in the unofficial user support channel's #docs or #blender-coders channel in Chat; Blender also has module owners (developer and artist members) responsible for designing and maintaining assigned areas (see the module pages). Preview: build the manual to view changes (you can build just the chapter you edited for speed), opening the generated .html files under build/html in your browser or refreshing an open page. Upload: when happy, upload the changes to the online manual — at first by submitting patches for review and feedback, and later committing directly, as detailed in the next section.

## Local Editing

The guides below help you set up your editing environment and walk through the contribution process.

## Installing Dependencies

This section documents how to install the software that generates the manual; the installation differs per operating system, with instructions written for each.

## Installation on Linux

This guide covers installing dependencies, downloading the repository, and setting up the build environment. Installing dependencies — run the command for your Linux distribution in a terminal. Debian/Ubuntu:
```text
sudo apt-get install python3 python3-pip git git-lfs
git lfs install --skip-repo
```
Redhat/Fedora:
```text
sudo dnf install python python-pip git git-lfs
git lfs install --skip-repo
```
Arch Linux:
```text
sudo pacman -S python python-pip git git-lfs
git lfs install --skip-repo
```
Downloading the repository — check out the Blender Manual's repository (this may take a few minutes by connection speed):
```text
cd ~
git clone https://projects.blender.org/blender/blender-manual.git
```
Setting up the build environment — open a Terminal, enter the folder git clone made, and install dependencies:
```text
cd ~/blender-manual
make setup
```
Re-run `make setup` now and then to keep dependencies current. It automatically creates a virtual environment to avoid touching the system Python (per PEP 668):
```text
python3 -m venv .venv
.venv/bin/pip install -r requirements.txt
```
and the Sphinx command is then at `.venv/bin/sphinx-build`.

## Installation on macOS

This guide covers installing dependencies, downloading the repository, and setting up the build environment, and relies heavily on command-line tools, assuming little familiarity with the macOS Terminal. Installing dependencies — install or confirm you have PIP, Git, and Git LFS; with Homebrew, run:
```text
python3 -m ensurepip
brew install git git-lfs
git lfs install
```
Downloading the repository — check out the Blender Manual's repository (a few minutes by connection speed):
```text
cd ~
git clone https://projects.blender.org/blender/blender-manual.git
```
Setting up the build environment — open a Terminal, enter the folder git clone made, and install dependencies:
```text
cd ~/blender-manual
make setup
```
Re-run `make setup` periodically to keep dependencies current. It automatically creates a virtual environment to avoid touching the system Python (per PEP 668):
```text
python3 -m venv .venv
.venv/bin/pip install -r requirements.txt
```
and the Sphinx command is then at `.venv/bin/sphinx-build`.

## Installation on Windows

This guide covers installing Python (used to "convert" the source files to HTML), installing Git and downloading the repository, and setting up the build environment. Installing Python — download the Python installation package for Windows (this guide uses version 3.9.x); run the installation wizard, and be sure to enable the "Add Python to PATH" option, which must be on so the make script can build the manual, leaving the other settings at their defaults. Installing Git and downloading the repository — this guide uses the official Git client, though any client works: download and install Git for Windows, then check out the Blender Manual's repository with:
```text
cd ~
git lfs install
git clone https://projects.blender.org/blender/blender-manual.git
```
The download may take a few minutes by connection speed. (With a graphical Git client, just put the repository address in the URL field:)
```text
https://projects.blender.org/blender/blender-manual.git
```
Setting up the build environment — open a Terminal, enter the blender-manual folder git clone just made, and install dependencies:
```text
cd C:\blender-manual
make setup
```
On success you should see this when it finishes:
```text
Successfully installed Jinja2 MarkupSafe Pygments Sphinx docutils sphinx-rtd-theme Cleaning up...
```
Some warnings during setup are harmless, but errors may cause problems. Re-run this command now and then to keep dependencies current. The make setup step automatically creates a virtual environment to avoid touching the system Python (per PEP 668):
```text
python -m venv .venv
.venv/Scripts/pip install -r requirements.txt
```
and the Sphinx command is then at `.venv/Scripts/sphinx-build`.

## Pull Requests

This page covers the tooling for contributing and reviewing code. Reviews are a key safeguard for change quality — they help catch bugs, design inconsistencies, and potential maintenance problems, and having your work reviewed also keeps you sharp. (Writers granted commit access can commit to the main repository without forking; see Commit Guidelines if that's you.) One-time setup assumes you've already checked out the manual repository per the install instructions. Fork: go to the Blender repository, click Fork, confirm with the default settings, then add your personal fork as a remote in your local git repository — click SSH for the correct URL and add it like:
```text
git remote add me git@git.blender.org:<username>/blender-manual.git
```
Pushing to the fork needs an SSH key; if you lack ~/.ssh/id_rsa.pub, generate one (works on Linux, macOS, and Git Bash on Windows):
```text
ssh-keygen
```
This makes a private key id_rsa and a public key id_rsa.pub in ~/.ssh — never reveal or send the private key, but the public one is safe to share. Paste the contents of ~/.ssh/id_rsa.pub into your projects.blender.org account settings via "Add Key" (any key name is fine). Workflow: the pull-request workflow is in the Blender Developer's Documentation — some of it targets the main Blender repository, but the workflow is identical for any Blender project. Guidelines for reviewers: the pull-request text should serve as the git commit message (see the guidelines); be explicit about changes to address before committing, without forcing a review iteration; if the PR isn't approved, the author should make another iteration; if the design needs agreement on a task first, put the PR on hold by prefixing the title with WIP:, signaling it isn't ready to merge (no review expected unless the author asks); writers should reply to PRs within 3 working days; add relevant modules/projects to the labels; and encourage new writers to review, since it's a good way to learn and to grow the project. Tips: append .patch to a PR's URL to get its patch file, e.g.:
```text
https://projects.blender.org/blender/blender-manual/pulls/104892.patch
```
Check out a PR into a detached head (leaving no branch behind), e.g.:
```text
git fetch -q origin +refs/pull/104892/head: ; git checkout -qf FETCH_HEAD
```

## Commit Guidelines

Directly submitting changes is limited to people with commit access; once granted, you can commit directly rather than creating a patch file. Make commits from your Git client or the command line — this creates a commit and sends it to the central repository:
```text
git commit -m "This is what I did"
git push
```
Omitting -m "message" prompts you to type the message in a text editor. Tip: always be on the latest revision before committing, since conflicting changes in the latest revision can block a direct commit — update your local repository first (run make update). See also Blender's Git usage guide, and the release-branch documentation for committing to a specific release branch and creating merge commits. Writing a good commit message: when a manual change relates directly to a specific Blender commit, it helps to make the commit title match the Blender commit's, and you're asked to include the hash of the Blender source commit. For example, commit rBM8473 carries a descriptive title plus the hash rBa71d2b260170 — the hash comes from the URL in the Documentation task for an upcoming release. More general changes needn't follow that policy, but should still describe clearly what changed and why; prefixing the title with Cleanup: or Fix: helps for general cleanups or fixes. Good commit messages help administrators track changes and ensure new features are properly documented.

## Contribute Documentation

The Blender Manual is a community-driven effort anyone can contribute to — whether fixing a small spelling mistake or rewriting a whole chapter, your help is most welcome. If you find an error, please report the problem, and get involved in discussions through any of the project Contacts. Where to help: the Documentation Todo List, and Documenting New Features and Changes. Contacts: the Project Page (an overview of the documentation project); the Documentation Forum (forum discussions on writing and translating documentation, covering the user manual, Wiki, release notes, and code docs); Chat (the #docs channel for informal real-time discussion); and the Project Workboard (managing tasks such as bugs, todo lists, and future plans).

## Documentation Todo List

This page lists changes that need to be made to the manual — a great starting place for new contributors — and is auto-generated from any items marked with the `.. todo::` tag. Also check the documentation workboard, which holds larger initiatives, structured work efforts, and priorities.

## Translate Blender

Help bring Blender closer to everyone: by translating Blender's user interface, you let artists and creators everywhere use their own language. No programming is required — only enthusiasm for Blender and translation skill. Come aboard the localization effort and help take Blender worldwide. See the Blender UI Translation Guide for details.

## Adding a Language

This page walks through starting a new translation language. Preparations — if no one has started your target language and you want to create a new set of files for, say, 'fr' (French), first build the environment described in Getting Started, particularly the Installing Dependencies and Building the Manual sections. That foundation lets you create a new translation language from the English source, run make to turn translated po-file text into HTML for local testing, and pull in English-text changes added by other contributors. The examples below show creating a new French file set (language code fr) on Linux; other platforms vary slightly but are mostly the same. Steps: create a Blender ID if you don't have one; log into projects.blender.org and create an issue requesting commit access to push changes to the translation team's central repository; open a console; and change the working directory to the blender-manual directory where the Makefile lives. Trying the make process to create English HTML files — remove any previous build directory:
```text
make clean
```
convert all rst files into pot translation files:
```text
make gettext
```
create HTML files:
```text
make html
```
then view the result locally by opening blender-manual/build/html/index.html. Creating the language entry in the HTML menu — open ./build_files/theme/js/version_switch.js (from the blender-manual subdirectory), find the language table in `var all_langs = {..};`, add the entry `"fr": "Français",` (i.e. `"fr": "Français"`, noting the Unicode characters), then commit and push:
```text
git add ./build_files/theme/js/version_switch.js
git commit -m "HTML: Add French to language menu"
```
```text
git push
```
Generating the file set for the target language — check out the current translation repository:
```text
git clone https://projects.blender.org/blender/blender-manual-translations.git locale
```
This downloads all available language sets into the locale directory (where you'll see the hidden .git subdirectory alongside the language directories), and you add your own set for the language you're translating. From the blender-manual directory, generate the fr file set:
```text
make update_po
```
These files are still English-only, with all msgstr entries blank. Submit the new set to the central repository:
```text
cd locale
git add fr
git commit -m "Initial commit language set of files for French"
```
Tips: for convenience in scripting batch/shell translation and review commands, define two environment variables in .bashrc:
```text
export BLENDER_MAN_EN=$HOME/<path>/blender-manual
export BLENDER_MAN_FR=$BLENDER_MAN_EN/locale
```
Newly generated files contain placeholders for authors, revision dates, and the like; if replacing them is tedious, copy the change_placeholders.sh script from ~/blender-manual/tools/util_maintenance into your local bin directory, replace its values with your details, then after each file change run it to update your personal details and revision date/time and build your language's HTML for browser viewing:
```text
$HOME/bin/change_placeholders.sh $BLENDER_MAN_FR
make -d --trace -w -B -e SPHINXOPTS="-D language='fr'" 2>&1
```

## Contribute

This guide uses French (fr) as an example, but any language code works — replace /fr throughout with your desired language's code. Check the currently available languages on the online translation interface or in the underlying git repository. Simple contribution — the preferred way to contribute translations is the web-based interface, currently hosted on Weblate; suggestions can be contributed without logging in and are reviewed by the translation team before publishing, and Weblate also offers tools like the glossary to improve consistency. Advanced operations — if the web interface doesn't suit you, PO files can be downloaded, edited locally, and uploaded back. Warning: conflicts can arise if updates occur while you edit locally, requiring manual resolution, and direct commits to the translation repository are no longer permitted. Note: uploading or integrating PO files can take several minutes — if a server timeout appears after ten minutes, refresh the page to confirm whether it succeeded. Installing — before translating, confirm the manual builds correctly per Getting Started. Language files — from the manual's root directory run:
```text
make checkout_locale
```
You'll be prompted for the language folder to download (e.g. type fr for French and press Return), which creates a locale/fr subdirectory after downloading. Example directory layout:
```text
blender-manual
|- locale/
|  |- fr/
|  |  |- LC_MESSAGES/
|- manual/
```
Note: with command-line Git, switch to the locale directory for updates rather than the blender-manual directory. Alternatively, download the PO files directly from Weblate via the Files menu on the language's page. PO-file editor — install a PO-file editor to modify the translation files; Poedit is recommended, but others work too. Building with translations — to build the manual with translations applied:
```text
make -e BF_LANG=fr
```
On Windows:
```text
set BF_LANG=fr
make html
```
Editing translation files — the PO files in `LC_MESSAGES` include blender_manual.po (the main user-manual translations) and sphinx.po (a smaller file for the website theme); open them in the PO editor (each entry is a manual section), translate the untranslated strings in the provided input field, then save and upload the modified .po files back to Weblate. Tip: sort entries by source or translation status for easier navigation. Important: build the manual after translating to surface syntax errors, which appear as warnings during the build. Maintenance — keeping track of fuzzy strings: when the manual updates, outdated translations are marked fuzzy; to track them:
```text
make report_po_progress
```
For a detailed report:
```text
python tools/translations/report_translation_progress.py locale/fr/
```
which lists files with fuzzy or empty strings; for more options:
```text
python tools/translations/report_translation_progress.py --help
```
Updating PO files — administrators regularly update PO files to match the latest English manual (typically weekly), and the last update is shown on the Blender Manual Translations project page; translators can update locally with:
```text
make update_po
```
though uploading these to Weblate is not permitted. See also Adding a Language.

## Translate the User Manual

Bring Blender to a global audience: pitch in on the translation effort so the Blender Manual reaches more languages. Fluent in another tongue or just beginning, every bit you add helps — let's build a global community. Maintenance: Adding a Language.
