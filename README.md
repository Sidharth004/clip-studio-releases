# Clip Studio

Turn a YouTube video into a transcript, chapters, title ideas and short-form
clips — then cut and caption those clips — **entirely on your own Mac**.

Nothing is uploaded. No account with us. No subscription to us.

---

## Before you start

You need three things:

| | |
|---|---|
| **An Apple silicon Mac** | macOS 12 (Monterey) or newer, on M1 or later. Intel Macs and Windows are not built yet — see [Which machines](#which-machines) |
| **A Claude subscription** | Pro or Max. The app uses *your* account |
| **~700 MB free** | 143 MB to download, more for the videos you work on |

You do **not** need Python, Homebrew, winget, ffmpeg, yt-dlp or Deno. Every
tool the app uses is bundled with it.

---

## 1. Install

**On a Mac** — open **Terminal** and paste this:

```sh
curl -fsSL https://github.com/Sidharth004/clip-studio-releases/releases/latest/download/install.sh | sh
```

It downloads about 143 MB, checks it arrived intact, and puts a `clip-studio`
command on your PATH. Nothing is installed system-wide and it never asks for
your password or administrator rights.

You may see a note that `~/.local/bin` is not on your PATH. **You can ignore
it** — just use the full path below.

<a id="which-machines"></a>
### Which machines

| | |
|---|---|
| **Apple silicon Mac** (M1 or later) | ✅ available now |
| **Intel Mac** | ❌ not built. The installer says so rather than failing oddly |
| **Windows 10/11** | ⏳ supported by the app, but no build is published yet |

Windows is not a gap in the program — the installer, the build script and the
platform layer are all written and tested against it. The build simply has to be
compiled *on* a Windows machine, which has not happened yet. When it does, a
`clip-studio-windows-x64.zip` appears in the same release and this becomes:

```powershell
irm https://github.com/Sidharth004/clip-studio-releases/releases/latest/download/install.ps1 | iex
```

---

## 2. Start it

```sh
clip-studio
```

On a Mac, if that is not found, use the full path `~/.local/bin/clip-studio`.

Your browser opens by itself.

> **The first launch takes about 20 seconds.** macOS checks new
> programs the first time they run. Every launch after that is under a second.
> Windows may also show a **"Windows protected your PC"** box — click *More
> info*, then *Run anyway*. That appears because the build is not code-signed,
> which costs a few hundred dollars a year; the download's checksum is verified
> by the installer instead.

---

## 3. Connect Claude

On first run you will see a setup screen. Everything except Claude should
already have a tick — `ffmpeg` and `yt-dlp` ship with the app.

For Claude, click the button:

- **Install** — a Terminal opens and installs Claude Code. Wait for it to say
  it is finished.
- **Sign in** — a Terminal opens and your browser asks you to authorise.

Then **leave the setup screen alone**. It notices and closes itself.

Everything happens in a Terminal window you can watch. Nothing is installed
behind your back.

*Why:* the app runs Claude on your machine, using your subscription. It never
sees your password, and nobody else is billed for what you do.

---

## 4. Use it

Paste a YouTube link and press **Add**. The app will:

1. **fetch** the captions
2. **transcript** — clean them up
3. **summary**, **chapters**, **titles**
4. **clips** — but first it *pauses and asks what you want*

That pause is deliberate. Clip-finding costs the most, so it asks for a brief
first — for example *"only founder hot takes and predictions, not product
updates"*.

**Start with a short video**, five or ten minutes. Every stage uses your Claude
allowance, and an hour-long podcast is a big first bite.

### Editing a clip

To cut and export you need the actual video file. In the video's page:

- **Choose a file…** — if you already have it, this links it where it sits.
  Nothing is copied.
- **Download from YouTube** — fetches it.

Then press **✂ Edit** on any clip: trim, reframe to 9:16, add animated
captions, and export.

---

## Commands

| | |
|---|---|
| `clip-studio` | start it |
| `clip-studio update` | get the newest version |
| `clip-studio --check` | what is installed, what is missing |
| `clip-studio uninstall` | remove the program — **your videos and clips stay** |
| `clip-studio --port 9000` | if something else is using the usual port |
| `clip-studio --help` | everything else |

---

## If something looks wrong

**The video box is black but I can hear sound.**
The file uses a video format your browser cannot show. Disconnect the source
and download it again — new downloads use a format every browser plays. As a
quick workaround, Chrome will usually play the old file.

**Nothing happened when I clicked Install or Sign in.**
Look for the Terminal window that opened — it may be behind the browser. If it
says *command not found*, you are on an old version: reinstall with the command
in step 1.

**`clip-studio: command not found`.**
On a Mac, use the full path `~/.local/bin/clip-studio`, or add that folder to
your PATH. On Windows, close the terminal and open a new one — the PATH change
only applies to windows opened after installing.

**"Claude is not signed in" while running a stage.**
Run `claude auth login`.

**The download 404s.**
There is no build published for your machine yet. Only Apple silicon Macs are
covered today — Intel Macs and Windows are not. See
[Which machines](#which-machines).

**Windows says it cannot run scripts.**
Run PowerShell as your normal user and paste:
`Set-ExecutionPolicy -Scope Process Bypass -Force`, then the install line again.

**Everything is slow, or nothing appears for 20 seconds.**
Only the very first launch after installing. Later launches are immediate.

---

## Where your things live

| | |
|---|---|
| Videos, transcripts, clips data | macOS: `~/Library/Application Support/Clip Studio`<br>Windows: `%LOCALAPPDATA%\Clip Studio` |
| Exported clips | `Documents\Clipping` (either) |

Uninstalling does not touch either. They are yours.

---

## Privacy

- Your **video never leaves your Mac**. Not for analysis, not for editing.
- Your **transcript never leaves your Mac**.
- Claude runs **locally**, through your own signed-in account.
- We store nothing, because there is no "we" — there is no server.

The only thing that goes out is what Claude Code itself sends to Anthropic on
your behalf, exactly as when you use it directly.

---

*Downloads only. The source lives in a private repository.*
