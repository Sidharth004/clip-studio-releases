# Clip Studio

Give it a video. Get back a transcript, chapters, titles, and short clips ready
for TikTok, Reels or Shorts — trimmed, reframed and captioned.

Everything happens on your own computer. Your videos never get uploaded to us.
There is no account to make, and we never charge you anything.

---

## Before you start, you need three things

**1. The right computer**

| You have | Which version you get |
|---|---|
| Mac with Apple silicon (M1, M2, M3, M4) | **0.3.7** — the newest |
| Windows 10 or 11 | 0.3.6 — one version behind |
| Linux on a 64-bit PC | 0.3.6 — one version behind |
| Older Intel Mac | Not supported yet |

Not sure if your Mac is Apple silicon? Click the Apple menu → **About This
Mac**. If the chip says "M" and a number, you're good.

**Windows and Linux people:** the newest version is Mac-only at the moment.
Each version has to be built on the kind of computer it runs on, and the
Windows and Linux ones aren't ready yet. You can still install 0.3.6 — the
instructions below tell you how, and it works fine. You just won't have the
most recent fixes.

**2. A Claude Pro or Max subscription**

The app uses *your* Claude account to do the thinking. It does not come with
one, and there's no free tier that works. If you don't have Claude Pro or Max,
the app will install and run but the clip-finding won't.

**3. A licence key**

Ask Sid for one. It's a short code that looks like `PHfbdVQhpvvl5g5stxg8Kt1`.
Without it the app opens, but every AI step stays locked.

You'll also want about **1.5 GB of free space**, plus room for your videos.

You do *not* need to install Python, ffmpeg, yt-dlp or anything else. They come
bundled inside.

---

## Step 1 — Install it

### On a Mac

Open the **Terminal** app. (Press ⌘ + Space, type "terminal", hit Enter.)

Copy this whole line, paste it in, and press Enter:

```sh
curl -fsSL https://github.com/Sidharth004/clip-studio-releases/releases/latest/download/install.sh | sh
```

It downloads about 250 MB and checks the file arrived intact. It does not ask
for your password and does not change anything outside your own folders.

**Now close Terminal and open a fresh one.** This matters. The window you just
typed in doesn't know about the new app yet.

### On Windows

Open **PowerShell**. (Press the Windows key, type "powershell", hit Enter.)

Paste these **two** lines and press Enter:

```powershell
$env:CLIP_STUDIO_VERSION = "v0.3.6"
irm https://github.com/Sidharth004/clip-studio-releases/releases/download/v0.3.6/install.ps1 | iex
```

The first line is what gets you 0.3.6, the newest Windows build. Leave it out
and the install will fail with a "not found" error, because the very latest
release is Mac-only right now.

**Now close PowerShell and open a fresh one.**

If Windows says it won't run scripts, paste this first, then try again:

```powershell
Set-ExecutionPolicy -Scope Process Bypass -Force
```

### On Linux

Open a terminal and paste this:

```sh
curl -fsSL https://github.com/Sidharth004/clip-studio-releases/releases/download/v0.3.6/install.sh | CLIP_STUDIO_VERSION=v0.3.6 sh
```

The `v0.3.6` bits are what gets you the newest Linux build. Without them the
install fails with a "not found" error, because the very latest release is
Mac-only right now.

Then open a fresh terminal.

To get the "choose a file" button working, install `zenity` or `kdialog` first.
Without one you can still type file paths by hand.

---

## Step 2 — Start it

In your fresh terminal window, type:

```sh
clip-studio
```

Your web browser opens on its own. That's the app.

**Two things will look alarming the first time. Both are normal.**

*It takes about 20 seconds to start.* Your computer scans new programs once.
After that it opens in under a second.

*Your computer warns you the app is unsafe.* This is because the app isn't
"code-signed" — a certificate that costs hundreds of dollars a year. The
installer checks the download's fingerprint instead, which does the same job.
To get past the warning:

- **Mac** — right-click the app, choose **Open**.
- **Windows** — click **More info**, then **Run anyway**.
- **Linux** — nothing to dismiss.

---

## Step 3 — Paste in your licence key

The first screen asks for it. Paste the code Sid gave you and press Enter.

It should say **active** with a number of days remaining.

If it says something else, see *When your licence won't accept* below.

---

## Step 4 — Connect your Claude account

A setup screen shows you what's missing. ffmpeg and yt-dlp are already built
in, so usually Claude is the only row that needs anything.

Click **Install** or **Sign in**. A terminal window opens so you can watch it
work. Then leave it alone — it closes by itself when it's done.

*Nothing seemed to happen?* The terminal it opened is probably hiding behind
your browser window.

To change accounts later, click the **claude CLI ready** button in the top bar.
Note the difference between the two exits there:

- **Disconnect** — stops just this app from using Claude.
- **Sign out everywhere** — signs you out of Claude on your whole computer,
  including other tools. Use the first one unless you really mean the second.

---

## Step 5 — Make some clips

Paste a YouTube link and press **Add**. The app pulls the captions, tidies up
the transcript, then writes a summary, chapters and titles.

Then it **stops and asks you what you're looking for**. Something like *"only
the founder's hot takes, skip the product updates"*. It asks first because
finding clips is the expensive part, and guessing wrong wastes your Claude
allowance.

**Please start with a short video.** Every step uses up some of your Claude
allowance. A three-hour podcast as your first try is a big bite.

To actually edit a clip, the app needs the video file, not just the captions:

- **Choose a file…** — if you already have it. The app reads it where it sits
  and doesn't copy it.
- **Download from YouTube** — if you don't.

Then press **✂ Edit** on any clip to trim it, reframe it to vertical, add
captions and export.

---

## Useful commands

| Type this | What it does |
|---|---|
| `clip-studio` | start the app |
| `clip-studio update` | get the newest version |
| `clip-studio --check` | list what's installed and what's missing |
| `clip-studio --port 9000` | use a different port, if something clashes |
| `clip-studio uninstall` | remove the app — **your videos and clips stay put** |

---

## When something goes wrong

**"command not found"**

You're in the old terminal window. Open a fresh one. On a Mac you can also type
the full path: `~/.local/bin/clip-studio`

**The video plays but the picture is black**

Your browser can't display that video format. Disconnect the file and let the
app download it again.

**"Claude is not signed in" partway through**

Run `claude auth login` in a terminal, then try the step again.

**The download gives a 404 or "not found" error**

On Windows or Linux, this almost always means you left out the `v0.3.6` part of
the command. Go back to your install step and copy the whole thing.

On a Mac, it means your Mac is too old — the Intel ones aren't supported yet.

### When your licence won't accept

| It says | What it means | What to do |
|---|---|---|
| **active** | All good. | Nothing. |
| **Enter a licence key** | No key saved yet. | Paste the code Sid gave you. |
| **has not been confirmed yet** | The app can't reach the licence server to check your key. | Check your internet. If it still fails, tell Sid — the problem is on his end, not yours. |
| **has not been confirmed for 7 days** | It worked before, but the app hasn't been able to re-check for a week. | Get back online and restart the app. If that doesn't fix it, tell Sid. |
| **withdrawn** | Your key was turned off. | Ask Sid. |
| **The trial ended** | Your key ran out. | Ask Sid for a new one. |

---

## You're testing this — so please tell Sid

This is a test build. Things will break. That's the point.

When something goes wrong, the three things most worth sending:

1. **What you were doing** when it happened.
2. **What it said** — a screenshot is perfect.
3. **Your version and setup** — run `clip-studio --check` and send the output.

---

## Where your stuff is kept

| What | Where |
|---|---|
| Videos, transcripts, clips | **Mac** `~/Library/Application Support/Clip Studio`<br>**Windows** `%LOCALAPPDATA%\Clip Studio`<br>**Linux** `~/.local/share/clip-studio` |
| Clips you export | `Documents/Clipping` |

Uninstalling the app leaves all of it alone. It's yours.

---

## Your privacy

Your videos and transcripts stay on your computer. There is no server of ours
for them to go to.

Claude runs through your own signed-in account. That means nobody else sees your
work and nobody else is billed for it. The only thing that leaves your machine
is what Claude Code sends to Anthropic on your behalf — exactly the same as when
you use Claude Code yourself.

---

*This page is for downloads only. The source code lives in a private repo.*
