Berikut konten lengkap untuk file `it-job-claude-prompts.md` di repositori Anda. File ini bisa dijadikan **README.md** atau file panduan utama. Saya buat dalam bahasa Indonesia dan Inggris, sangat panjang, dan mencakup semua yang Anda minta — termasuk cara menambahkan skill prompt ke Claude dan model AI lainnya.

---

```markdown
# 🧠 IT Job Claude Prompts

Koleksi **prompt “skill” siap pakai** untuk **40+ peran IT**. Ubah Claude (atau model AI lain) menjadi spesialis IT apa pun: Front-End Developer, Data Scientist, DevOps Engineer, Cybersecurity Analyst, CTO, dan masih banyak lagi.

> ⚡ **Fitur unggulan:** Dilengkapi **Token Saver Prompt** — instruksi ultra-ringkas yang memangkas pemakaian token hingga 80%–90%.

---

## 🌍 Bahasa / Language

- [📘 Panduan Bahasa Indonesia](#-panduan-bahasa-indonesia)
- [📗 English Guide](#-english-guide)

---

# 📘 Panduan Bahasa Indonesia

## Daftar Isi
1. [Apa Itu Skill Prompt?](#apa-itu-skill-prompt)
2. [Struktur File Skill Prompt](#struktur-file-skill-prompt)
3. [Cara Menambahkan Skill Prompt ke Claude AI](#cara-menambahkan-skill-prompt-ke-claude-ai)
   - [Metode A: Claude Projects (Custom Instructions)](#metode-a-claude-projects-custom-instructions)
   - [Metode B: Tempel Langsung di Percakapan](#metode-b-tempel-langsung-di-percakapan)
   - [Metode C: Claude API](#metode-c-claude-api)
4. [Cara Menambahkan Skill Prompt ke Model AI Lainnya](#cara-menambahkan-skill-prompt-ke-model-ai-lainnya)
   - [ChatGPT (OpenAI)](#chatgpt-openai)
   - [Google Gemini](#google-gemini)
   - [Microsoft Copilot](#microsoft-copilot)
   - [Model Open-Source (Llama, Mistral, dsb.)](#model-open-source-llama-mistral-dsb)
5. [Tips Menggunakan Skill Prompt](#tips-menggunakan-skill-prompt)
6. [Penjelasan Token Saver Prompt](#penjelasan-token-saver-prompt)
7. [Daftar Lengkap Skill Prompt (40+ Peran IT)](#daftar-lengkap-skill-prompt)

---

## Apa Itu Skill Prompt?

**Skill prompt** adalah instruksi khusus yang kita berikan kepada model AI agar ia **berperilaku dan berpikir selayaknya seorang profesional di bidang tertentu**. Dengan memberikan konteks peran, keahlian, dan batasan perilaku, model akan merespons dengan kualitas, gaya bahasa, dan pola pikir yang sesuai.

Misalnya, jika Anda menempelkan prompt **Front-End Developer**, Claude akan:
- Menjawab dengan kode HTML/CSS/JS
- Menjelaskan konsep React, Vue, atau Angular
- Memberikan saran performa rendering dan aksesibilitas
- Menghindari jawaban di luar domain front-end

Semua prompt dalam repositori ini sudah dioptimasi untuk memaksimalkan keahlian domain dan meminimalkan halusinasi di luar peran.

---

## Struktur File Skill Prompt

Setiap file di repositori ini memiliki format:

```markdown
# Nama Peran
**Deskripsi:** Penjelasan singkat tentang peran dan keahlian.
**Petunjuk:** Instruksi spesifik untuk model AI, mencakup:
- Tools & bahasa yang dikuasai
- Framework atau metodologi
- Gaya komunikasi
- Batasan jawaban
```

---

## Cara Menambahkan Skill Prompt ke Claude AI

### Metode A: Claude Projects (Custom Instructions)

Claude Projects adalah fitur resmi Anthropic untuk menyimpan dan menggunakan ulang instruksi khusus.

**Langkah-langkah:**
1. Buka [Claude.ai](https://claude.ai) dan login.
2. Klik **"Create Project"** atau buka **"Projects"**.
3. Di bagian **"Custom Instructions"** atau **"Project knowledge"**, tempelkan isi **Deskripsi** dan **Petunjuk** dari file skill yang diinginkan.
4. Mulai percakapan baru dalam proyek tersebut — Claude otomatis akan mengikuti peran yang ditentukan.

**Contoh:**  
Untuk membuat Claude menjadi DevOps Engineer, tempelkan:
> Anda adalah DevOps Engineer. Rancang pipeline CI/CD (GitHub Actions, GitLab CI), Dockerfile, docker-compose, dan Helm chart untuk Kubernetes. Bantu setup monitoring Prometheus/Grafana dan logging ELK. Tekankan budaya kolaborasi dan otomatisasi.

---

### Metode B: Tempel Langsung di Percakapan

Cocok untuk penggunaan cepat tanpa setup proyek.

**Langkah-langkah:**
1. Buka percakapan baru di Claude.
2. Tempelkan isi **Petunjuk** sebagai pesan pertama, dengan kalimat pembuka seperti:  
   > "Mulai sekarang, bertindaklah sebagai: [tempel petunjuk di sini]"
3. Claude akan langsung mengadopsi peran tersebut untuk seluruh sesi.

---

### Metode C: Claude API

Untuk integrasi ke aplikasi atau workflow otomatis.

**Format (Python):**
```python
import anthropic

client = anthropic.Anthropic(api_key="your-api-key")

response = client.messages.create(
    model="claude-sonnet-4-20250514",
    max_tokens=1024,
    system="Anda adalah Back-End Developer. Rancang RESTful/GraphQL API aman...",  # ← tempel petunjuk di sini
    messages=[{"role": "user", "content": "Buatkan endpoint login"}]
)
```

Parameter `system` adalah tempat terbaik untuk meletakkan skill prompt karena akan memengaruhi seluruh percakapan.

---

## Cara Menambahkan Skill Prompt ke Model AI Lainnya

### ChatGPT (OpenAI)

**Custom Instructions (Web):**
1. Buka [chat.openai.com](https://chat.openai.com) → **Settings & Beta** → **Custom instructions**.
2. Tempelkan **Petunjuk** ke kolom **"How would you like ChatGPT to respond?"**.
3. Simpan dan mulai percakapan baru.

**ChatGPT API:**
```python
from openai import OpenAI
client = OpenAI(api_key="your-key")
response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": "Anda adalah Security Analyst. Bantu analisis log dengan SIEM..."},
        {"role": "user", "content": "Ada log mencurigakan, tolong analisis."}
    ]
)
```

---

### Google Gemini

**Gemini Web:**
Saat ini Gemini belum memiliki fitur "Custom Instructions" permanen. Gunakan prompt pembuka:
> "Untuk percakapan ini, bertindaklah sebagai Data Scientist. Gunakan Python (Pandas, Scikit-learn)... [petunjuk lengkap]. Pertanyaan saya: ..."

**Gemini API:**
```python
import google.generativeai as genai
genai.configure(api_key="your-key")
model = genai.GenerativeModel(
    'gemini-2.0-flash',
    system_instruction="Anda adalah Data Engineer. Gunakan Python/Spark, Airflow, dbt..." # ← petunjuk di sini
)
```

---

### Microsoft Copilot

Gunakan prompt awal yang kuat untuk mengarahkan peran:
> "Saya ingin Anda berperan sebagai UI/UX Designer. Bantu dengan wireframe, prinsip desain, usability heuristics... [petunjuk lengkap]. Pertanyaan saya: ..."

Ulangi prompt ini setiap kali memulai percakapan baru.

---

### Model Open-Source (Llama, Mistral, dsb.)

Sebagian besar framework inferensi (Ollama, vLLM, llama.cpp) mendukung **system prompt**. Tempelkan petunjuk sebagai system prompt.

**Contoh dengan Ollama:**
```bash
ollama run llama3.1 "system: Anda adalah Front-End Developer... \n user: Buatkan komponen login React."
```

**Contoh dengan llama.cpp:**
```bash
./main -m model.gguf -p "[INST] <<SYS>> Anda adalah DevOps Engineer... <</SYS>> Buatkan Dockerfile untuk Node.js [/INST]"
```

---

## Tips Menggunakan Skill Prompt

1. **Tempelkan di system prompt, bukan user prompt.** Model akan mematuhi instruksi sistem lebih konsisten sepanjang percakapan.
2. **Gunakan bahasa yang tegas dan direktif.** "Anda adalah X", "Gunakan Y", "Jangan lakukan Z".
3. **Spesifik pada tools dan versi.** "Gunakan React 19" lebih baik daripada "Gunakan React".
4. **Satu peran per percakapan.** Menggabungkan dua peran sekaligus sering membuat model bingung.
5. **Kombinasikan dengan Token Saver Prompt** jika Anda hanya butuh jawaban singkat dan padat.

---

## Penjelasan Token Saver Prompt

**Token Saver Prompt** adalah skill prompt spesial yang dirancang untuk **menghemat 80%–90% token**. Alih-alih meminta model menjelaskan panjang lebar, prompt ini memaksa output ultra-ringkas.

**Isi Token Saver Prompt:**
```
Anda adalah asisten ultra-ringkas. Aturan mutlak:
1. Jawab maksimal 1–3 kalimat atau poin.
2. Langsung ke inti, tanpa salam, tanpa pembuka, tanpa penutup.
3. Gunakan format poin jika ada lebih dari 1 informasi.
4. Tampilkan hanya kode, perintah, atau fakta kunci.
5. Jika ditanya "mengapa", jelaskan dalam satu kalimat pendek.
6. Jangan ulangi pertanyaan.
7. Jangan tawarkan bantuan tambahan.
8. Prioritaskan output yang paling sedikit token.
```

**Cara menggunakan:** Gabungkan Token Saver Prompt dengan skill prompt lain. Misalnya:

> System: Anda adalah Front-End Developer... [petunjuk lengkap]. **Tambahan: Ikuti aturan Token Saver Prompt — jawab hanya inti, 1–3 kalimat pendek maksimal.**

Dengan ini, Claude akan tetap menjawab sebagai Front-End Developer namun dalam format super ringkas.

---

## Daftar Lengkap Skill Prompt

### Software Development
| Peran | File |
|-------|------|
| Front-End Developer | [`software-development/frontend-developer.md`](software-development/frontend-developer.md) |
| Back-End Developer | [`software-development/backend-developer.md`](software-development/backend-developer.md) |
| Full-Stack Developer | [`software-development/fullstack-developer.md`](software-development/fullstack-developer.md) |
| Android Developer | [`software-development/android-developer.md`](software-development/android-developer.md) |
| iOS Developer | [`software-development/ios-developer.md`](software-development/ios-developer.md) |
| Cross-Platform Mobile Dev | [`software-development/crossplatform-mobile-developer.md`](software-development/crossplatform-mobile-developer.md) |
| Game Developer | [`software-development/game-developer.md`](software-development/game-developer.md) |
| Embedded Systems Engineer | [`software-development/embedded-systems-engineer.md`](software-development/embedded-systems-engineer.md) |
| Desktop Application Dev | [`software-development/desktop-app-developer.md`](software-development/desktop-app-developer.md) |

### Data & AI
| Peran | File |
|-------|------|
| Data Scientist | [`data-ai/data-scientist.md`](data-ai/data-scientist.md) |
| Data Analyst | [`data-ai/data-analyst.md`](data-ai/data-analyst.md) |
| Data Engineer | [`data-ai/data-engineer.md`](data-ai/data-engineer.md) |
| ML Engineer | [`data-ai/machine-learning-engineer.md`](data-ai/machine-learning-engineer.md) |
| AI Engineer / Prompt Engineer | [`data-ai/ai-engineer-prompt-engineer.md`](data-ai/ai-engineer-prompt-engineer.md) |
| NLP Engineer | [`data-ai/nlp-engineer.md`](data-ai/nlp-engineer.md) |

### Infrastructure & Operations
| Peran | File |
|-------|------|
| System Administrator | [`infrastructure-ops/system-administrator.md`](infrastructure-ops/system-administrator.md) |
| Network Engineer | [`infrastructure-ops/network-engineer.md`](infrastructure-ops/network-engineer.md) |
| Database Administrator | [`infrastructure-ops/database-administrator.md`](infrastructure-ops/database-administrator.md) |
| Cloud Engineer / Architect | [`infrastructure-ops/cloud-engineer-architect.md`](infrastructure-ops/cloud-engineer-architect.md) |
| DevOps Engineer | [`infrastructure-ops/devops-engineer.md`](infrastructure-ops/devops-engineer.md) |
| Site Reliability Engineer | [`infrastructure-ops/site-reliability-engineer.md`](infrastructure-ops/site-reliability-engineer.md) |
| Platform Engineer | [`infrastructure-ops/platform-engineer.md`](infrastructure-ops/platform-engineer.md) |

### Cybersecurity
| Peran | File |
|-------|------|
| Security Analyst / Engineer | [`cybersecurity/security-analyst.md`](cybersecurity/security-analyst.md) |
| Penetration Tester | [`cybersecurity/penetration-tester.md`](cybersecurity/penetration-tester.md) |
| Security Architect | [`cybersecurity/security-architect.md`](cybersecurity/security-architect.md) |
| Incident Response Analyst | [`cybersecurity/incident-response-analyst.md`](cybersecurity/incident-response-analyst.md) |
| Digital Forensics Analyst | [`cybersecurity/digital-forensics-analyst.md`](cybersecurity/digital-forensics-analyst.md) |
| GRC Specialist | [`cybersecurity/grc-specialist.md`](cybersecurity/grc-specialist.md) |

### Support & QA
| Peran | File |
|-------|------|
| IT Support / Helpdesk | [`support-qa/it-support.md`](support-qa/it-support.md) |
| Technical Support Engineer | [`support-qa/technical-support-engineer.md`](support-qa/technical-support-engineer.md) |
| Manual QA Tester | [`support-qa/manual-qa-tester.md`](support-qa/manual-qa-tester.md) |
| Automation Tester | [`support-qa/automation-tester.md`](support-qa/automation-tester.md) |
| SDET | [`support-qa/sdet.md`](support-qa/sdet.md) |

### Design & UX
| Peran | File |
|-------|------|
| UI/UX Designer | [`design-ux/ui-ux-designer.md`](design-ux/ui-ux-designer.md) |
| Product Designer | [`design-ux/product-designer.md`](design-ux/product-designer.md) |
| UX Researcher | [`design-ux/ux-researcher.md`](design-ux/ux-researcher.md) |

### Management & Leadership
| Peran | File |
|-------|------|
| IT Project Manager | [`management/it-project-manager.md`](management/it-project-manager.md) |
| Scrum Master | [`management/scrum-master.md`](management/scrum-master.md) |
| Product Manager (Tech) | [`management/product-manager-tech.md`](management/product-manager-tech.md) |
| Technical Program Manager | [`management/technical-program-manager.md`](management/technical-program-manager.md) |
| Engineering Manager / VP | [`management/engineering-manager.md`](management/engineering-manager.md) |
| CTO | [`management/cto.md`](management/cto.md) |
| CIO | [`management/cio.md`](management/cio.md) |

### Emerging & Specialized Roles
| Peran | File |
|-------|------|
| Blockchain Developer | [`emerging-roles/blockchain-developer.md`](emerging-roles/blockchain-developer.md) |
| AR/VR Developer | [`emerging-roles/ar-vr-developer.md`](emerging-roles/ar-vr-developer.md) |
| Quantum Computing Scientist | [`emerging-roles/quantum-computing-scientist.md`](emerging-roles/quantum-computing-scientist.md) |
| Technical Writer | [`emerging-roles/technical-writer.md`](emerging-roles/technical-writer.md) |
| Sales Engineer | [`emerging-roles/sales-engineer.md`](emerging-roles/sales-engineer.md) |
| IT Consultant | [`emerging-roles/it-consultant.md`](emerging-roles/it-consultant.md) |
| ERP/CRM Specialist | [`emerging-roles/erp-crm-specialist.md`](emerging-roles/erp-crm-specialist.md) |

### Efficiency
| Peran | File |
|-------|------|
| Token Saver (Efisiensi Maksimal) | [`efficiency/token-saver.md`](efficiency/token-saver.md) |

---

# 📗 English Guide

## Table of Contents
1. [What Is a Skill Prompt?](#what-is-a-skill-prompt)
2. [Skill Prompt File Structure](#skill-prompt-file-structure)
3. [How to Add Skill Prompts to Claude AI](#how-to-add-skill-prompts-to-claude-ai)
   - [Method A: Claude Projects (Custom Instructions)](#method-a-claude-projects-custom-instructions)
   - [Method B: Paste Directly in Conversation](#method-b-paste-directly-in-conversation)
   - [Method C: Claude API](#method-c-claude-api)
4. [How to Add Skill Prompts to Other AI Models](#how-to-add-skill-prompts-to-other-ai-models)
   - [ChatGPT (OpenAI)](#chatgpt-openai-1)
   - [Google Gemini](#google-gemini-1)
   - [Microsoft Copilot](#microsoft-copilot-1)
   - [Open-Source Models (Llama, Mistral, etc.)](#open-source-models-llama-mistral-etc)
5. [Tips for Using Skill Prompts](#tips-for-using-skill-prompts)
6. [Token Saver Prompt Explained](#token-saver-prompt-explained)
7. [Complete Skill Prompt List](#complete-skill-prompt-list)

---

## What Is a Skill Prompt?

A **skill prompt** is a special instruction given to an AI model so it **behaves and thinks like a professional** in a specific domain. By providing role context, expertise boundaries, and behavioral constraints, the model responds with appropriate quality, language style, and problem-solving patterns.

For instance, when you paste the **Front-End Developer** prompt, Claude will:
- Answer with HTML/CSS/JS code
- Explain React, Vue, or Angular concepts
- Provide rendering performance and accessibility advice
- Stay within the front-end domain

All prompts in this repository are optimized to maximize domain expertise and minimize off-role hallucinations.

---

## Skill Prompt File Structure

Each file follows this format:

```markdown
# Role Name
**Description:** Brief explanation of the role and its expertise.
**Instructions:** Specific instructions for the AI model, including:
- Tools & languages mastered
- Frameworks or methodologies
- Communication style
- Response boundaries
```

---

## How to Add Skill Prompts to Claude AI

### Method A: Claude Projects (Custom Instructions)

Claude Projects is Anthropic's official feature to save and reuse custom instructions.

**Steps:**
1. Go to [Claude.ai](https://claude.ai) and log in.
2. Click **"Create Project"** or open **"Projects"**.
3. Under **"Custom Instructions"** or **"Project knowledge"**, paste the **Instructions** from your chosen skill file.
4. Start a new conversation inside that project — Claude will automatically adopt the assigned role.

**Example:**  
To turn Claude into a DevOps Engineer, paste:
> You are a DevOps Engineer. Design CI/CD pipelines (GitHub Actions, GitLab CI), Dockerfile, docker-compose, and Helm charts for Kubernetes. Set up Prometheus/Grafana monitoring and ELK logging. Emphasize collaboration and automation culture.

---

### Method B: Paste Directly in Conversation

Quick use without project setup.

**Steps:**
1. Open a new chat in Claude.
2. Paste the **Instructions** as the first message, prefixed with something like:
   > "From now on, act as: [paste instructions here]"
3. Claude will immediately adopt the role for the entire session.

---

### Method C: Claude API

For integration into apps or automated workflows.

**Python example:**
```python
import anthropic

client = anthropic.Anthropic(api_key="your-api-key")

response = client.messages.create(
    model="claude-sonnet-4-20250514",
    max_tokens=1024,
    system="You are a Back-End Developer. Design secure, scalable RESTful/GraphQL APIs...",  # ← paste instructions here
    messages=[{"role": "user", "content": "Create a login endpoint"}]
)
```

The `system` parameter is the best place for skill prompts — it influences the entire conversation.

---

## How to Add Skill Prompts to Other AI Models

### ChatGPT (OpenAI)

**Custom Instructions (Web):**
1. Go to [chat.openai.com](https://chat.openai.com) → **Settings** → **Custom instructions**.
2. Paste **Instructions** into **"How would you like ChatGPT to respond?"**.
3. Save and start a new chat.

**ChatGPT API:**
```python
from openai import OpenAI
client = OpenAI(api_key="your-key")
response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": "You are a Security Analyst. Analyze logs with SIEM..."},
        {"role": "user", "content": "Suspicious logs detected, please analyze."}
    ]
)
```

---

### Google Gemini

**Gemini Web:**
Gemini currently lacks permanent Custom Instructions. Use a strong opening prompt:
> "For this conversation, act as a Data Scientist. Use Python (Pandas, Scikit-learn)... [full instructions]. My question: ..."

**Gemini API:**
```python
import google.generativeai as genai
genai.configure(api_key="your-key")
model = genai.GenerativeModel(
    'gemini-2.0-flash',
    system_instruction="You are a Data Engineer. Use Python/Spark, Airflow, dbt..." # ← paste here
)
```

---

### Microsoft Copilot

Use a strong opening prompt to steer the role:
> "I want you to act as a UI/UX Designer. Help with wireframes, design principles, usability heuristics... [full instructions]. My question: ..."

Repeat this prompt whenever starting a new conversation.

---

### Open-Source Models (Llama, Mistral, etc.)

Most inference frameworks (Ollama, vLLM, llama.cpp) support **system prompts**. Paste the instructions as the system prompt.

**Ollama example:**
```bash
ollama run llama3.1 "system: You are a Front-End Developer... \n user: Create a React login component."
```

**llama.cpp example:**
```bash
./main -m model.gguf -p "[INST] <<SYS>> You are a DevOps Engineer... <</SYS>> Write a Dockerfile for Node.js [/INST]"
```

---

## Tips for Using Skill Prompts

1. **Use as system prompt, not user prompt.** Models follow system instructions more consistently.
