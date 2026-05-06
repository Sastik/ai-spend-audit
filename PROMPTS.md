# 🤖 PROMPTS.md

This document contains all prompts used for the AI-generated summary feature, along with the reasoning behind their design and iterations.

---

## 📌 Purpose of AI in This Project

AI is used **only for generating a personalized summary** of the audit results.

It is **not used** for:

* Pricing calculations
* Audit logic
* Recommendations

This ensures:

* Deterministic and verifiable outputs
* Financial accuracy
* Consistency in results

---

## 🧠 Final Prompt (Production)

```text id="final-prompt"
You are a financial analyst helping a startup optimize its AI tool spending.

Based on the audit data below, write a concise (80–120 words), clear, and professional summary.

The summary should:
- Highlight key overspending areas
- Mention total potential savings (monthly and yearly)
- Suggest general optimization direction (downgrade, switch tools, etc.)
- Be honest: if savings are low, say the spending is already efficient

Avoid:
- Technical jargon
- Repeating raw numbers excessively
- Making unsupported claims

Audit Data:
{{audit_data}}

Write the summary in a tone suitable for a startup founder.
```

---

## 🧪 Prompt Iterations & Learnings

---

### ❌ Version 1 (Rejected)

```text id="v1-prompt"
Analyze this AI tool usage and suggest improvements:
{{audit_data}}
```

**Problems:**

* Too vague → inconsistent outputs
* Sometimes hallucinated recommendations
* No control over tone or length

---

### ❌ Version 2 (Rejected)

```text id="v2-prompt"
Act as an AI expert and optimize this usage:
{{audit_data}}
```

**Problems:**

* Overly generic responses
* Ignored financial context
* Focused on features instead of cost

---

### ✅ Version 3 (Improved)

Added:

* Role definition (“financial analyst”)
* Clear structure
* Output constraints

Result:

* More relevant and focused summaries

---

### ✅ Final Version (Used)

Enhancements:

* Word limit (80–120 words)
* Explicit instructions on honesty
* Avoid repetition
* Focus on savings + reasoning

Result:

* Consistent, readable summaries
* Better alignment with product goal

---

## ⚙️ Input Structure

The `{{audit_data}}` passed to the model is structured JSON:

```json id="input-structure"
{
  "total_monthly_savings": 120,
  "total_annual_savings": 1440,
  "tools": [
    {
      "name": "ChatGPT",
      "current_cost": 60,
      "recommended_cost": 20,
      "savings": 40,
      "reason": "Team plan overkill for 2 users"
    }
  ]
}
```

---

## 🔄 Fallback Strategy

Since LLM APIs can fail or return inconsistent output:

Fallback summary is used when:

* API request fails
* Response is empty or malformed

---

### 🛟 Fallback Template

```text id="fallback"
Your current AI tool usage shows potential savings of approximately ${{monthly}} per month and ${{yearly}} annually. 

Some tools may be over-provisioned for your team size or use case. Consider reviewing plan tiers and exploring alternative tools to optimize costs.

Overall, your setup can be improved with a few targeted adjustments.
```

---

## ⚠️ Challenges Faced

1. **Inconsistent tone**

   * Fixed by defining role + audience

2. **Hallucinated recommendations**

   * Solved by restricting AI to summary only

3. **Too verbose responses**

   * Controlled via word limit

4. **Formatting issues**

   * Cleaned via post-processing (trim, validation)

---

## 🧠 Key Learnings

* AI works best when given **clear constraints and structure**
* Financial logic should remain **rule-based and deterministic**
* Prompt specificity directly impacts output quality
* Fallbacks are essential for production reliability

---

## 🚀 Future Improvements

* Fine-tuned prompts based on real user feedback
* Structured output (JSON → formatted UI)
* Multi-tone summaries (technical vs non-technical)
