# 🤖 MyAIRep — Personal AI Profile Chatbot

> An AI-powered chatbot that represents **Akilan Pandiyan** in professional conversations.  
> Built with **OpenAI GPT-4o-mini** and **Gradio** — always available to answer questions on your behalf.

---

## 🚀 Live Demo

👉 **[Try it here → huggingface.co/spaces/apandiyan1/MyAIRep](https://huggingface.co/spaces/apandiyan1/MyAIRep)**

---

## 💡 What It Does

- Answers questions about career history, skills, and professional background
- Reads from a personal LinkedIn profile PDF and a written summary
- Captures interested visitors' **name and email** for follow-up via Pushover notification
- Logs **unknown or off-topic questions** so they can be reviewed later
- Steers conversations toward meaningful professional engagement
- Stays strictly on-topic — career and professional questions only

---

## 🛠️ Tech Stack

| Layer | Tool |
|---|---|
| LLM | OpenAI GPT-4o-mini |
| UI | Gradio ChatInterface |
| PDF Parsing | pypdf |
| Notifications | Pushover API |
| Deployment | Hugging Face Spaces |
| Environment | python-dotenv |

---

## 📁 Project Structure

```
career-digital-twin/
├── app.py                             # Main chatbot application
├── requirements.txt                   # Python dependencies
├── README.md                          # Project documentation
├── .env.example                       # Environment variable template
├── me/
│   ├── Profile.pdf                    # LinkedIn profile exported as PDF
│   └── summary.txt                    # Personal career summary
└── my_profile_chatbot.ipynb           # Original development notebook
```

---

## ⚙️ How It Works

The agent is powered by two custom tools:

**`record_user_details`**
> Captures a visitor's name, email, and conversation notes. Sends an instant Pushover notification when someone expresses interest in getting in touch.

**`record_unknown_question`**
> Logs any off-topic or unanswerable question for later review — so nothing gets missed.

The system prompt constrains the agent strictly to career and professional topics, ensuring it always stays on-brand and professional.

```
Visitor asks a question
        ↓
GPT-4o-mini reads Profile.pdf + summary.txt
        ↓
Decides: Answer it  OR  Use a tool
        ↓
record_user_details     record_unknown_question
(captures contact)      (logs the question)
        ↓
Pushover notification sent to Akilan
```

---

## 🖥️ Running Locally

**1. Clone the repository**
```bash
git clone https://github.com/akilanpandiyan/my_profile_ai_chatbot
```

**2. Create and activate a virtual environment**
```bash
python -m venv venv
source venv/bin/activate        # Mac/Linux
venv\Scripts\activate           # Windows
```

**3. Install dependencies**
```bash
pip install -r requirements.txt
```

**4. Set up your environment variables**
```bash
cp .env.example .env
```
Then open `.env` and fill in your credentials:
```
OPENAI_API_KEY=your_openai_key
PUSHOVER_TOKEN=your_pushover_token
PUSHOVER_USER=your_pushover_user_key
```

**5. Add your profile files**
- Export your LinkedIn profile as PDF → save as `me/Profile.pdf`
- Write a short career summary → save as `me/summary.txt`

**6. Run the app**
```bash
python app.py
```

---

## ☁️ Deploying to Hugging Face Spaces

```bash
gradio deploy
```

> ⚠️ Add your secrets in **Space Settings → Repository Secrets**:
> - `OPENAI_API_KEY`
> - `PUSHOVER_TOKEN`
> - `PUSHOVER_USER`

---

## 🔐 Environment Variables

| Variable | Description |
|---|---|
| `OPENAI_API_KEY` | Your OpenAI API key |
| `PUSHOVER_TOKEN` | Your Pushover app token |
| `PUSHOVER_USER` | Your Pushover user key |

> Never commit your `.env` file. It is listed in `.gitignore` for safety.

---

## 📸 Screenshot

> *(Add a screenshot of your Gradio chatbot in action here)*

---

## 🧠 What I Learned Building This

- How to design an AI agent personality using system prompts
- How to build custom tool schemas in JSON format for LLM function calling
- How to write a `handle_tool_calls` dispatcher to route the right tool at runtime
- How to parse PDF content and inject it into an LLM context window
- How to deploy a Gradio app to Hugging Face Spaces

---

## 👤 Author

**Akilan Pandiyan**  
AI Engineer | Building Multi-Agent Systems  
📍 Long Beach, California

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/akilanpandiyan/)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=flat-square&logo=github&logoColor=white)](https://github.com/akilanpandiyan)
[![Hugging Face](https://img.shields.io/badge/HuggingFace-FFD21E?style=flat-square&logo=huggingface&logoColor=black)](https://huggingface.co/spaces/apandiyan1/MyAIRep)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
