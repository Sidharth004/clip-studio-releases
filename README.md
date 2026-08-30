# Clip Studio

Turn a YouTube video into a transcript, chapters, titles and short-form clips —
then trim, reframe, caption and export them.

Everything runs on your own machine. Your video and transcript never leave it,
there is no account with us, and nothing is billed by us.

---

## What you need

| | |
|---|---|
| **A Mac, a PC or a Linux box** | Apple silicon Mac (M1 or later) on macOS 13+ · Windows 10/11 on x64 · Linux on x64 with glibc 2.35+ (Ubuntu 22.04 or newer, Debian 12, Fedora 36+) |
| **A Claude subscription** | Pro or Max. The app uses *your* account |
| **~1.5 GB free** | for the app, plus room for the videos you work on |

Nothing else. Python, ffmpeg, yt-dlp and Deno are all bundled.

Not yet available: Intel Macs, Windows on ARM, and Linux on ARM.

---

## Install — macOS

Open **Terminal** and paste:

```sh
curl -fsSL https://github.com/Sidharth004/clip-studio-releases/releases/latest/download/install.sh | sh
```

Downloads ~222 MB, verifies it, and puts `clip-studio` on your PATH. Nothing is
installed system-wide and it never asks for your password.

If Claude Code is missing it offers to install it — answer `n` to skip.

**Then open a new Terminal.** The one you typed in loaded its PATH before the
installer changed it. (Or use the full path the installer prints.)

## Install — Linux

Open a terminal and paste:

```sh
curl -fsSL https://github.com/Sidharth004/clip-studio-releases/releases/latest/download/install.sh | sh
```

The same command as macOS — it works out which build you need.

**Then open a new terminal**, or run `~/.local/bin/clip-studio` directly.

For the file picker to work, install `zenity` (GNOME) or `kdialog` (KDE). Without
one you can still paste a path by hand; everything else works either way.

## Install — Windows

Open **PowerShell** and paste:

```powershell
irm https://github.com/Sidharth004/clip-studio-releases/releases/latest/download/install.ps1 | iex
```

Downloads ~244 MB and verifies it.

**Then open a new PowerShell window** — the PATH change only applies to windows
opened afterwards.

If it refuses to run scripts, paste this first, then the line above:

```powershell
Set-ExecutionPolicy -Scope Process Bypass -Force
```

---

## First run

```sh
clip-studio
```

Your browser opens by itself.

**The first launch takes about 20 seconds** — your operating system checks new
programs once. Every launch after that is under a second.

You will also see a warning the first time, because the app is not code-signed
(that costs a few hundred dollars a year; the installer verifies the download's
checksum instead):

- **macOS** — right-click the app and choose *Open*, if prompted.
- **Windows** — *"Windows protected your PC"* → **More info** → **Run anyway**.
- **Linux** — nothing to dismiss.

### Connecting Claude

A setup screen appears if anything is missing. ffmpeg and yt-dlp ship with the
app, so Claude is usually the only row needing attention. Click **Install** or
**Sign in** — a terminal opens so you can watch it happen — then leave the
screen alone; it closes itself.

To check or change the account later, click the **claude CLI ready** pill in the
top bar. **Disconnect** stops just this app using Claude. **Sign out everywhere**
signs Claude Code out across the whole machine.

---

## Using it

Paste a YouTube link and press **Add**. The app fetches captions, cleans up the
transcript, then writes a summary, chapters and titles.

Before finding clips it **pauses and asks what you want** — for example *"only
founder hot takes, not product updates"*. Clip-finding costs the most, so it
asks first.

**Start with a short video.** Every stage spends your Claude allowance, and an
hour-long podcast is a big first bite.

To edit a clip you need the video file itself. Either **Choose a file…** (links
it where it sits — nothing is copied) or **Download from YouTube**. Then press
**✂ Edit** on any clip to trim, reframe to 9:16, caption and export.

---

## Commands

| | |
|---|---|
| `clip-studio` | start it |
| `clip-studio update` | get the newest version |
| `clip-studio --check` | what is installed, what is missing |
| `clip-studio --port 9000` | if something else is using the usual port |
| `clip-studio uninstall` | remove the program — **your videos and clips stay** |

---

## If something looks wrong

**`clip-studio: command not found`**
Open a new terminal. On macOS you can also use `~/.local/bin/clip-studio`.

**The video is black but I can hear sound**
The file is in a format your browser cannot display. Disconnect the source and
download it again.

**"Claude is not signed in" during a stage**
Run `claude auth login`.

**Nothing happened when I clicked Install or Sign in**
The terminal it opened is probably behind your browser.

**The download 404s**
There is no build for your machine yet — see *What you need*.

---

## Where your things live

| | |
|---|---|
| Videos, transcripts, clips | macOS `~/Library/Application Support/Clip Studio`<br>Windows `%LOCALAPPDATA%\Clip Studio`<br>Linux `~/.local/share/clip-studio` |
| Exported clips | `Documents/Clipping` on both |

Uninstalling leaves both alone. They are yours.

---

## Privacy

Your video and transcript never leave your machine. Claude runs locally through
your own signed-in account, so nobody else is billed and we store nothing —
there is no server. The only thing that goes out is what Claude Code itself
sends to Anthropic on your behalf, exactly as when you use it directly.

---

*Downloads only. The source lives in a private repository.*
