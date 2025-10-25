# 🔴 Big Red Button — Context + Screenshot Logger (Web App)  
> *“Because sometimes the only context is: I panicked and clicked the red thing.”* 🧠💥

Welcome to the tiniest productivity upgrade since “rename file to final_v9_REALLY_FINAL.docx.”  
This web app gives you a **Big Red Button** in your browser that will:

- 📸 **Grab a full‑screen screenshot** (desktop capture).  
- 📝 Ask for your **Context** (or accept what you typed already).  
- 🕒 Stamp a **timestamp** (because your auditor friend loves receipts).  
- 🧾 Append everything to a **2‑column Word table**: **Left = Context+time**, **Right = Screenshot**.  
- 🔁 **Auto‑roll** to new files after 90 entries (`ContextShots (2).docx`, etc.).  
- 🌐 **Website Poller** (optional): enter a URL + interval → headless browser snaps it on schedule and logs it, too.

It’s like a dashcam for your workflow, but with fewer car metaphors and more “oh right, *that’s* what I was doing.” 🚗➡️🖥️

---

## 🧪 What’s inside? (Features at a glance)

- 🔴 **Big Red Button** — click to capture the desktop after a small delay (so you can Alt‑Tab with dignity).  
- ⏳ **Configurable delay** — set your seconds in the UI; we remember it because we care.  
- 📚 **Word doc output** — a single table that keeps your evidence tidy and your future self grateful.  
- 🤝 **Thread‑safe writes** — manual captures and the website poller won’t trip over each other.  
- 🕵️ **Auditor‑approved vibes** — timestamped context + screenshot = immaculate paper trail. (Hi auditors! We see you 👋. Please stop asking for “one more sample,” it’s 4:59 pm.)  
- 🧰 **Cross‑platform** — Windows/macOS/Linux (desktop capture via MSS on Win/Linux; `screencapture` on macOS).  
- 🌍 **Headless website screenshots** — point at a URL, pick an interval, let it rain PNGs into your doc.

---

## ⚙️ Install (pick your shell flavor)

```bash
python -m venv venv
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate
```

Install deps:
```bash
pip install flask python-docx mss selenium webdriver-manager
```

> 🔧 First website-capture run will download a matching ChromeDriver. Have Chrome/Chromium installed and internet available.

---

## ▶️ Run it

```bash
python big_red_context_shot_cross.py
```
Your browser will open to `http://127.0.0.1:8788` with two sections:
1) **Manual Desktop Capture** — type Context, set Delay, click **CAPTURE & LOG**.  
2) **Website Poller (Headless)** — enter URL + Interval seconds → **START POLLER**. Use **STOP POLLER** to end.

There’s also a **Quick Test: One‑off Website Screenshot** — for that instant “does it work?” satisfaction. 🎯

---

## 🕹️ Usage flow (Manual)

1. Type your **Context**.  
2. Set **Delay before capture** (e.g., `2.0`).  
3. Alt‑Tab to your target app/window, compose yourself, fix your posture.  
4. Click **CAPTURE & LOG** → we wait, snapshot, and append to your Word file.

**Where’s my file?**  
We write to `~/Documents/ContextShots.docx` and roll over to `ContextShots (2).docx`, `(3)`, … as needed.

---

## 🧾 Output format

The Word document is a two‑column table:

| Context (with timestamp) | Screenshot |
|---|---|
| `2025-10-25 09:42:17 — Debugging: "Why is CPU at 437% on a toaster?"` | *(screenshot image)* |

- Images are auto‑scaled to the right column.  
- The context cell stores **timestamp + your text** — neat, searchable, and suspiciously professional.

---

## 🔐 Permissions (macOS folks)

- **Screen Recording** → System Settings » Privacy & Security » Screen Recording (grant for your Terminal/Python).  
If your first screenshot is black, that’s macOS being shy. Give it a pat (and a permission). 🫣

---

## 🩹 Troubleshooting (a.k.a. “Why, computers?”)

- **Windows:** `ModuleNotFoundError: No module named 'exceptions'`  
  You installed the wrong package. Fix it:  
  ```bash
  pip uninstall -y docx
  pip install --upgrade python-docx
  ```

- **Windows/Linux (MSS):** TypeError about `BufferedWriter`  
  You’re on an MSS version that wants a **path string**. This app uses `to_png(..., output=str(path))`, so you’re golden. Grab the latest script if needed.

- **Website screenshots don’t appear**  
  - Ensure **Chrome/Chromium** is installed.  
  - First run needs internet to fetch **chromedriver**.  
  - Some sites block headless captures; try the **Quick Test**. If blocked, we can add a non‑headless option.

- **Word says the doc is in use**  
  Close it in Word. We’re good, but not *time‑travel good*. 🕳️⏳

---

## ❓ FAQ (Frequently Accused Questions)

**Q: Can I choose which monitor to capture?**  
A: Currently it grabs the virtual full desktop. Per‑monitor capture is coming the moment my coffee finishes loading. ☕️

**Q: Can I tag entries or add categories?**  
A: Yes! We can add a tags column or auto‑prefix contexts. Tell me your taxonomy dreams. 🏷️

**Q: Can the website poller save to a separate doc?**  
A: Easy. We can auto‑name as `ContextShots-SITES-YYYY-MM-DD.docx` or per‑URL docs.

**Q: Will this satisfy our auditors?**  
A: It gives you **timestamped evidence** with neat context in a Word doc. Auditors love that.  
   (Hi again, auditors. We made extra columns just for you. Please stop asking for screenshots of screenshots. 🙏📑😂)

---

## 🧠 Under the hood

- **Flask** powers the local web UI.  
- **python‑docx** writes `.docx` like a polite robot.  
- **MSS** captures desktop on Windows/Linux; **`screencapture`** does it on macOS.  
- **Selenium + webdriver‑manager** drive headless Chrome for website screenshots.  
- Writes to Word are **locked** so manual and automated captures don’t step on each other’s toes. 👣

---

## 📝 Changelog (highlights)

- **2025‑10‑25** — UI tweak: context field won’t bully the seconds box; added responsive stacking.  
- **2025‑10‑24** — Website Poller + Quick Test route; better status in UI (last saved/error/time).  
- **2025‑10‑23** — Cross‑platform capture stabilized; fixed Windows path/`to_png` quirks.  
- **2025‑10‑22** — Web‑only glory; removed desktop drama.  
- **2025‑10‑21** — Added configurable pre‑capture delay.  
- **2025‑10‑20** — Initial release. Button very red. Spirits high. 🎉

---

## 📜 License

Pick your favorite permissive license (MIT/BSD/Apache‑2.0). Or call Legal and we’ll send snacks while they decide. 🍪📞

---

## 🙌 Credits

You, glorious button‑clicker.  
Also: Flask, python‑docx, MSS, Selenium, your GPU fan, and the unsung hero known as “screenshots_folder_final_final.” 💼💨
