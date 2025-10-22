# 🔴 Big Red Button — Context + Screenshot Logger (Web Only)

> For when your brain says “What was I doing?” and your mouse says “PANIC!” 🧠🚨  
> This is the **web** edition(s) only: fast, friendly, and allergic to native GUI drama.

This tiny tool gives you a **Big Red Button** in your browser that will:
1) Grab a **full-screen screenshot** 📸,
2) Ask (or accept) your **Context** 📝,
3) Stamp the **date & time** 🕒,
4) Paste everything into a **2‑column Word table** 🧾:  
   **Left:** Context (+ timestamp) • **Right:** Screenshot.  
5) Auto‑rotate to a new doc after **90 entries** 🔄 (`ContextShots (2).docx`, etc.).

It’s like a dashcam for your workflow, except it doesn’t judge you for having 87 Chrome tabs named “New Tab.” 🙈✨

---

## 🧪 Flavors (Both are Web Apps)

### 1) 🌐 Cross‑Platform Web Edition (Windows/macOS/Linux) — **Recommended**
- File: `big_red_context_shot_web.py`
- Uses **MSS** (Windows/Linux) and **`screencapture`** on macOS.
- Lets you set a **Delay before capture** ⏳ so you can Alt‑Tab to the right window first.
- Writes to: `~/Documents/ContextShots.docx`

---

## ⚙️ Install

Create a virtual environment (your future self will applaud): 💌
```bash
python -m venv venv
# Windows:
venv\Scriptsctivate
# macOS/Linux:
source venv/bin/activate
```

### Cross‑Platform Web Edition
```bash
pip install flask python-docx mss
python big_red_context_shot_web.py
```
Your browser opens to `http://127.0.0.1:8788`. Big red button awaits. 🔴👀

---

## 🕹️ Usage

1. Open the page (it opens automatically). 🌍  
2. Type your **Context**. 📝  
3. Set your **Delay** (seconds). ⏱️  
   - Cross‑platform: “Delay before capture.”  
   - macOS: “Delay before hiding,” then a tiny settle, then capture.  
4. Hit **CAPTURE & LOG**. 💥  
5. A row is appended to your Word doc: **Context + timestamp** | **Screenshot**. 📄➡️🖼️

**Pro tip:** Your chosen delay persists after each capture so you don’t have to re‑type it. We respect your procrastination preferences. 😌

---

## 🧾 Output Format

The Word file contains a single table:

| Context (with timestamp) | Screenshot |
| --- | --- |
| `2025-10-21 12:34:56 — Investigating “Why is CPU at 437% on a toaster?”` | [screenshot image] |

- Images are scaled to fit the right column. 🔍  
- After 90 rows, a fresh document starts automatically. 🆕  
- Rename or move the docs whenever you like; we’ll happily generate a new one next time. 📦

---

## 🔐 Permissions You May See

- **macOS Screen Recording**: to actually capture the screen (System Settings → Privacy & Security → Screen Recording). 🎥  
- **macOS Accessibility** (macOS web edition only): to let AppleScript press Cmd‑H and hide the front app. 🫥

If the first screenshot is black on macOS, it’s the Screen Recording permission. macOS is shy like that. 🫣

---

## 🛠️ Troubleshooting (a.k.a. “Why is my life like this?”)

- **Windows error “No module called `exceptions`”**  
  You installed the wrong package. Run:  
  ```bash
  pip uninstall -y docx
  pip install --upgrade python-docx
  ```

- **Windows error “expected str, bytes or os.PathLike object, not BufferedWriter”**  
  Fixed in the latest script: we pass a **file path** to `mss.tools.to_png`, not a file object. Grab the newest version.

- **First screenshot is black (macOS)**  
  Grant **Screen Recording** to your Terminal/Python app. ✅

- **Browser didn’t hide (macOS web edition)**  
  Grant **Accessibility** permission so AppleScript can press Cmd‑H. 🧑‍⚖️

- **Images look huge/tiny**  
  We scale to fit the column. If you want per‑row zoom, that’s Feature Request #YAGNI‑023. 🔎

---

## ❓ FAQ (Frequently Accused Questions)

**Q: Can it capture just one monitor?**  
A: Currently captures the full virtual screen. Multi‑monitor finesse is doable—say the word. 🖥️🖥️

**Q: Can it auto‑tag or categorize?**  
A: Absolutely. We can add tags/categories columns or even per‑row labels. ☕️🏷️

**Q: Where does it store my data?**  
A: Locally, in your `~/Documents`. No clouds were harmed in the making of this app. ☁️❌

**Q: Can I change the output path or auto‑name by date?**  
A: Yes, that’s a quick tweak. Want `ContextShots-YYYY‑MM‑DD.docx`? Easy.

**Q: Will it fix my meeting notes?**  
A: It will at least remember what you were looking at when you decided to take the note. Which is 90% of consulting anyway. 📓😅

---

## 🧠 Nerdy Bits

- **Stack:** Flask + `python-docx` + `mss` (Win/Linux) or `screencapture` (macOS). 🧩  
- Word table column widths set to ~3.1″ each (best‑effort; Word is a diva too). 💃  
- Auto‑rollover after 90 rows to keep files nimble and your future self sane. 🪄

---

## 📝 Changelog

- **2025‑10‑22**: Removed desktop references (web‑only glory). Updated troubleshooting for Windows. 🎯  
- **2025‑10‑21**: Added configurable pre‑capture/pre‑hide delay in web editions. 😊  
- **2025‑10‑20**: Initial release. Button very red. Spirits high. 🔴🎉

---

## 📜 License

Pick your favorite permissive license (MIT/BSD/Apache‑2.0). Or go full corporate and call Legal; we’ll wait here with snacks. 🍪📞

---

## 🙌 Credits

You, glorious button‑clicker. And the unsung heroes: `mss`, `python-docx`, Flask, and the humble `screencapture`. 💼💸
