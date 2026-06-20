# 🌳 The Arboreal Sage

A **chatbot with memory** that acts as a calm, nature‑inspired guide for personal goal‑setting, journaling, and mindful planning.

Built with Python (Flask) and vanilla HTML/CSS/JS – no heavy frameworks needed.

---

## ✨ Features

- **🎯 Multi‑Step Workflows** – structured sessions:
  - *The Daily Dig* – set a main objective, identify obstacles, and plant a “seed” action.
  - *The Reflection* – process a challenge, find its positive “sunlight”, and grow an insight.
- **🧠 Persistent Memory** – remembers your name, objectives, and workflow answers within a session.
- **🤖 AI Integration** – uses OpenAI’s GPT (optional) or a clever **mock AI** that stays in character – works completely offline.
- **🎨 Themed Interface** – comes with a warm, earthy palette (Valiant Poppy, Bulget Violet) – easily customizable.

---

## 🚀 Quick Start

### Prerequisites

- Python 3.8 or higher
- `pip` (Python package manager)

### 1. Project Structure

Make sure your project looks like this:

```
arboreal-sage/
├── app.py
├── frontend.html
├── .env (optional)
└── README.md (you are here)
```

### 2. Install Dependencies

```bash
pip install flask flask-cors python-dotenv
```

*(If you want real OpenAI, also run `pip install openai`, but it’s **not required**.)*

### 3. Run the Backend

```bash
python app.py
```

The Flask server will start on `http://localhost:5000`.

### 4. Open Your Browser

Visit **`http://localhost:5000`** – the frontend is served directly from the same port.

*If you prefer to serve the frontend separately, see the “Advanced” section below.*

---

## 🔧 Configuration (Optional)

Create a `.env` file in the project root:

```env
OPENAI_API_KEY=sk-...       # Optional – leave empty to use mock AI
SESSION_SECRET=your-secret-key   # For session security
```

If you **don’t** set `OPENAI_API_KEY`, the app will use a built‑in mock AI – it still replies in the Sage’s voice and supports all workflows.

---

## 🧭 Usage Guide

### First Visit

You’ll see a welcome overlay asking for your name. The Sage will remember it.

### Main Chat

- Type any message for a free‑form conversation.
- Use the **quick‑action buttons** below the chat:
  - **🌱 The Daily Dig** – starts the goal‑setting workflow.
  - **🍂 The Reflection** – starts the journaling workflow.
  - **🌳 Check on my root** – asks about your last set objective.

### Workflows

Once a workflow starts, the Sage will ask a series of questions.  
Just reply naturally – the bot will guide you step by step.

After completing a workflow, the Sage will generate a personalized **Seed** or **Growth Point** using AI (or the mock).  
Your answers are saved as memories.

### Memory

The Sage remembers:
- Your name
- Your last main objective (set via Daily Dig)
- Answers from completed workflows

Ask *“How did my objective take root?”* or click the **Check on my root** button to recall it.

---

## 🛠 Advanced Setup (Separate Frontend/Backend)

If you prefer running the frontend on a different port (e.g. for development):

1. **Comment out** these two routes in `app.py` (add `#` before `@app.route`):
   ```python
   # @app.route('/')
   # def serve_frontend():
   #     return open('frontend.html', encoding='utf-8').read()
   ```

2. Restart the Flask backend (`python app.py`).

3. In a **new terminal**, start a static server:
   ```bash
   python -m http.server 3000
   ```

4. Open `http://localhost:3000` – the HTML will be served from there.

5. Make sure `frontend.html` has `API_BASE = 'http://localhost:5000/api'` (it already does).

---

## 🎨 Customizing the Color Theme

The frontend uses CSS custom properties.  
Edit the `:root` block in `frontend.html`:

```css
:root {
  --color-bg-primary: #572F48;   /* main background */
  --color-bg-secondary: #4E4C5E; /* chat bubbles, header */
  --color-accent: #CF4A4D;       /* buttons, highlights */
  --color-text-primary: #FFA67A; /* main text */
  --color-text-secondary: #817965; /* timestamps, subtle text */
}
```

You can replace these with your own hex colours.

---

## 🐛 Troubleshooting

| Issue | Solution |
|-------|----------|
| **`FileNotFoundError: frontend.html`** | Make sure `frontend.html` is in the same folder as `app.py`. |
| **`UnicodeDecodeError`** | Your `frontend.html` may contain special characters – the app now forces UTF‑8, so re‑save the file as UTF‑8. |
| **CORS errors** | The backend already allows `localhost:3000`. If you use a different port, update the `CORS()` line in `app.py`. |
| **Mock AI replies feel repetitive** | That’s expected – the mock follows a template. For richer responses, add your own `OPENAI_API_KEY`. |

---

## 🧪 Testing the Workflows

- **Start Daily Dig** → answer *objective*, then *obstacle* → the AI suggests a *seed*.
- **Start Reflection** → answer *challenge*, then *sunlight* → the AI suggests a *growth point*.
- Use **Check on my root** to recall your objective at any time.

---

## 📜 License

This project is open‑source under the MIT License.

---

##  Credits

Built  using Flask, vanilla JS, and a lot of tree metaphors.

---

Enjoy your journey with the Arboreal Sage – may your roots grow deep and your branches reach high. 🌳
