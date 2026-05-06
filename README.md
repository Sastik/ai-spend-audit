# 🚀 AI Spend Audit Tool

A free web application that helps startups and developers analyze their AI tool spending, identify cost-saving opportunities, and optimize their usage across tools like ChatGPT, Claude, GitHub Copilot, and more.

This tool provides instant insights into overspending, recommends better plans or alternatives, and estimates potential monthly and annual savings.

---

## 🎯 Who is this for?

* Startup founders
* Engineering managers
* Developers using multiple AI tools
* Teams managing AI SaaS costs

---

## 📸 Screenshots

> Add 3–4 screenshots here after UI is ready

* Landing Page
* Input Form
* Audit Results
* Shareable Report Page

---

## ⚙️ Tech Stack

**Frontend:**

* React (TypeScript)
* Tailwind CSS

**Backend:**

* Python (FastAPI)

**Database:**

* PostgreSQL

**Deployment:**

* Frontend: Netlify
* Backend: Railway

**Email:**

* SMTP (Gmail / Resend alternative)

**LLM:**

* NVIDIA API (with fallback support)

---

## 🧪 Features

* AI tool spend input form (multi-tool support)
* Rule-based audit engine
* Savings calculation (monthly + yearly)
* AI-generated summary
* Email lead capture
* Shareable public audit links

---

## 🚀 Getting Started

### 1. Clone the repo

```bash
git clone https://github.com/your-username/ai-spend-audit.git
cd ai-spend-audit
```

### 2. Setup frontend

```bash
cd frontend
npm install
npm run dev
```

### 3. Setup backend

```bash
cd backend
pip install -r requirements.txt
uvicorn main:app --reload
```

### 4. Environment variables

Create `.env` file:

```env
DATABASE_URL=your_postgres_url
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=your_email
SMTP_PASS=your_password
LLM_API_KEY=your_nvidia_key
```

---

## 🌍 Live Demo

👉 https://your-deployed-url.netlify.app

---

## 🧠 Key Decisions

1. **FastAPI over Node.js**

   * Faster development for APIs and async handling

2. **Rule-based audit instead of AI**

   * More reliable, deterministic, and explainable

3. **Email after value display**

   * Improves conversion rate (user-first design)

4. **LocalStorage for form persistence**

   * Better UX without requiring login

5. **PostgreSQL for structured data**

   * Reliable and scalable for storing audit + leads

---

## 📌 Future Improvements

* Benchmark comparison (industry averages)
* PDF export
* Referral system
* Embedded widget version

---

## 📄 License

MIT License
