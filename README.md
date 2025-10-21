# 🔴 Big Red Button — Context + Screenshot Logger

> For when your brain says “What was I doing?” and your mouse says “PANIC!” 🧠🚨

This tiny tool gives you a **Big Red Button** that will:
1) Grab a **full-screen screenshot** 📸,
2) Ask you politely, “**What is the context?**” 🗣️,
3) Stamp the **date & time** 🕒,
4) Paste everything into a **2-column Word table** 🧾:  
   **Left:** Context (+ timestamp) • **Right:** Screenshot.  
5) Auto-rotate to a new doc after **90 entries** 🔄 (2×90 vibe: 2 columns × up to 90 rows per doc).

It’s like a dashcam for your workflow, except it doesn’t judge you for having 87 Chrome tabs named “New Tab.” 🙈✨

---

## 🧪 Variants

### 1) 🌐 Web Edition (macOS 12.6-friendly) — Recommended
No native GUI shenanigans. Uses a local web page with a **big red button**, macOS `screencapture`, and `python-docx`.

- File: `big_red_context_shot_web.py`
- Creates: `~/Documents/ContextShots.docx` (auto-rolls to `ContextShots (2).docx`, etc.)

**New:** configurable delay **before** the window hides ⏳. Because sometimes you need to move Slack out of frame like a guilty cat. 🐈‍⬛

### 2) 🖥️ Desktop Edition (Tk) — Fancy but picky
Pretty, but some native wheels may demand macOS 12.7 (build 1207) and sulk on 12.6. If you’re on Monterey 12.6, use the Web Edition unless you enjoy dependency roulette. 🎰

---

## ⚙️ Install

Create a virtual environment (strongly encouraged; your future self will send a thank-you email): 💌

```bash
python3 -m venv venv
source venv/bin/activate
```

### 🌐 Web Edition (the smooth one)
```bash
pip install flask python-docx
python big_red_context_shot_web.py
```
Your browser opens to `http://127.0.0.1:8787`. Big red button awaits. 🔴👀

### 🖥️ Desktop Edition (the brave one)
```bash
pip install python-docx mss Pillow
python big_red_context_shot.py
```
If it crashes with something like “macOS 12 (1207) required, have 1206” — that’s the native wheel having a diva moment. See Troubleshooting or switch to Web Edition. 💅

---

## 🕹️ Usage (Web Edition)

1. Open the page (it opens automatically). 🌍
2. Type your **Context**. 📝
3. Set **Delay before hiding (seconds)** — default is `2.0`. (Gives you time to arrange windows before the app politely hides your browser.) 🧹
4. Hit **CAPTURE & LOG**. 💥
5. The app waits, hides your frontmost app, takes the screenshot, and appends a row to your Word doc. 📄➡️🖼️

**Pro tip:** Your chosen delay persists after each capture so you don’t have to re-type it. We respect your procrastination preferences. 😌

---

## 🧾 Output Format

The Word file contains a single table:

| Context (with timestamp) | Screenshot |
| --- | --- |
| `2025-10-21 12:34:56 — Investigating “Why is CPU at 437% on a toaster?”` | [screenshot image] |

- Images are scaled to fit the right column. 🔍
- After 90 rows, a fresh document is started automatically. 🆕
- You can rename or move the docs whenever you like; we will happily generate a new one next time. 📦

---

## 🔐 macOS Permissions You’ll See (Once)

- **Screen Recording**: to actually capture the screen (System Settings → Privacy & Security → Screen Recording). 🎥
- **Accessibility** (Web edition only): to let AppleScript send Cmd-H to hide your browser for a clean screenshot. 🫥

If the first screenshot is black, it’s the Screen Recording permission. macOS is shy like that. 🫣

---

## 🛠️ Configuration

### Web Edition
- **Delay before hiding**: Set in the UI (0.0–60.0 seconds). Defaults to **2.0s**. ⏱️
- **Post-hide settle**: Internally ~0.6s to let the UI calm down before snapshot. If you want this tunable too, file a very polite feature request (or shout enthusiastically). 📣

### Desktop Edition
- Go wild and ask for hotkeys, different doc paths, or daily auto-rotation. We can make it happen. 🧞

---

## 🩹 Troubleshooting (a.k.a. “Why is my life like this?”)

- **First screenshot is black**  
  Grant **Screen Recording** to your Terminal/Python app. ✅

- **Browser didn’t hide** (Web)  
  Grant **Accessibility** permission so AppleScript can press Cmd-H for you. 🧑‍⚖️

- **“macOS 12 (1207) required, have 1206”** (Desktop)  
  Native wheels throwing a fit. Use the **Web Edition**, or upgrade macOS, or try Homebrew Python + older wheel pins. 🧊➡️🔥

- **Word says the document is locked**  
  Close it in Word. We’re good, but we’re not “edit your open file through the space-time continuum” good. 🕳️🕰️

- **No `screencapture` command**  
  Are you… on macOS? If yes and it’s missing, we need to talk. 📞

- **Images look huge/tiny**  
  We scale to fit the column. If you want per-row zoom levels, that’s Feature Request #YAGNI-023. 🔎

---

## ❓ FAQ (Frequently Accused Questions)

**Q: Can it capture just one monitor?**  
A: Currently captures the full virtual screen. Multi-monitor finesse can be added—say the word. 🖥️🖥️

**Q: Can it auto-categorize the screenshot?**  
A: Sure, right after it learns to make coffee. (Yes, we can add tags and categories. Ping me.) ☕️🏷️

**Q: Where does it store my data?**  
A: Locally, in your `~/Documents`. No clouds were harmed in the making of this app. ☁️❌

**Q: Is there a keyboard shortcut?**  
A: Desktop Edition supports Return/Space. Web Edition could get a hotkey; just remember browsers have Opinions™. ⌨️🧐

**Q: Will it fix my meeting notes?**  
A: It will at least remember what you were looking at when you decided to take the note. Which is 90% of consulting anyway. 📓😅

---

## 🧠 Nerdy Bits

- **Web Edition:** Flask + `screencapture` + `python-docx` 🧩
- **Desktop Edition:** Tkinter + `mss` + Pillow + `python-docx` 📦
- Word table column widths set to ~3.1" each (best-effort; Word is a diva too). 💃
- Auto-rollover after 90 rows to keep files nimble and your future self sane. 🪄

---

## 📝 Changelog

- **2025-10-21**: Added configurable pre-hide delay in Web Edition. Because you asked nicely. 😊
- **2025-10-20**: Initial release. Button very red. Spirits high. 🔴🎉

---

## 📜 License

Pick your favorite permissive license (MIT/BSD/Apache-2.0). Or go full corporate and call Legal; we’ll wait here with snacks. 🍪📞

---

## 🙌 Credits

You, glorious button-clicker. And the macOS `screencapture` command, which does not get paid enough. 💼💸
