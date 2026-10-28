# Clip Studio

Give it a video. Get back a transcript, chapters, titles, and short clips ready
for TikTok, Reels or Shorts — trimmed, reframed and captioned.

Everything happens on your own computer. Your videos never get uploaded to us.
There is no account to make, no key to ask for, and we never charge you
anything.

---

## Before you start, you need two things

**1. The right computer**

| You have | Can you run it? |
|---|---|
| Mac with Apple silicon (M1, M2, M3, M4) | **Yes** — version 0.4.0 |
| Windows 10 or 11 | Not yet |
| Linux on a 64-bit PC | Not yet |
| Older Intel Mac | Not yet |

Not sure if your Mac is Apple silicon? Click the Apple menu → **About This
Mac**. If the chip says "M" and a number, you're good.

**Windows and Linux people:** sorry — not yet. Each version has to be built on
the kind of computer it runs on, and there's no Windows or Linux machine to
build on at the moment. Ask Sid and he'll tell you when there is. The older
0.3.6 builds you might find in the releases list need a licence key that is no
longer being handed out, so don't bother with those.

**2. A Claude Pro or Max subscription**

The app uses *your* Claude account to do the thinking. It does not come with
one, and there's no free tier that works. If you don't have Claude Pro or Max,
the app will install and run but the clip-finding won't.

You'll also want about **1.5 GB of free space**, plus room for your videos.

You do *not* need to install Python, ffmpeg, yt-dlp or anything else. They come
bundled inside.

---

## Step 1 — Install it

Open the **Terminal** app. (Press ⌘ + Space, type "terminal", hit Enter.)

Copy this whole line, paste it in, and press Enter:

```sh
curl -fsSL https://github.com/Sidharth004/clip-studio-releases/releases/latest/download/install.sh | sh
```

It downloads about 250 MB and checks the file arrived intact. It does not ask
for your password and does not change anything outside your own folders.

**Now close Terminal and open a fresh one.** This matters. The window you just
typed in doesn't know about the new app yet.

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
To get past the warning, right-click the app and choose **Open**.

---

## Step 3 — Connect your Claude account

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

## Step 4 — Make some clips

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

You're in the old terminal window. Open a fresh one. You can also type the full
path: `~/.local/bin/clip-studio`

**The video plays but the picture is black**

Your browser can't display that video format. Disconnect the file and let the
app download it again.

**"Claude is not signed in" partway through**

Run `claude auth login` in a terminal, then try the step again.

**The download gives a 404 or "not found" error**

Your Mac is probably an Intel one — those aren't supported yet. Click the Apple
menu → **About This Mac** and check whether the chip starts with "M".

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
| Videos, transcripts, clips | `~/Library/Application Support/Clip Studio` |
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
