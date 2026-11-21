<!-- Animated hero. Upload hero.svg next to this README (same folder / repo root).
     One-file alternative (no extra upload): replace the line below with
     <img src="https://capsule-render.vercel.app/api?type=venom&color=0:070d1b,50:0f2547,100:0b4a63&height=240&section=header&text=Your%20Name&fontSize=56&fontColor=f8fafc&animation=twinkling&desc=AI%20Engineer%20%26%20Data%20Scientist" width="100%"> -->
<img src="hero.svg" width="100%" alt="Eslam Mohamed - AI Engineer and Data Scientist">

<br/>

I turn raw data into models that run in production. My work centers on **retrieval-augmented generation, NLP and predictive modeling**, with a strong focus on evaluation and reliability.

<p>
<a href="https://linkedin.com/in/YOUR_USERNAME"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
<a href="https://kaggle.com/YOUR_USERNAME"><img src="https://img.shields.io/badge/Kaggle-20BEFF?style=flat&logo=kaggle&logoColor=white" alt="Kaggle"/></a>
<a href="https://huggingface.co/YOUR_USERNAME"><img src="https://img.shields.io/badge/Hugging%20Face-FFD21E?style=flat&logo=huggingface&logoColor=black" alt="Hugging Face"/></a>
<a href="mailto:you@example.com"><img src="https://img.shields.io/badge/Email-30363D?style=flat&logo=gmail&logoColor=white" alt="Email"/></a>
</p>

<p align="center">
  <a href="#impact">Impact</a> &nbsp;·&nbsp;
  <a href="#architecture-in-practice">Architecture</a> &nbsp;·&nbsp;
  <a href="#how-i-build">Code</a> &nbsp;·&nbsp;
  <a href="#selected-work">Work</a> &nbsp;·&nbsp;
  <a href="#technical-stack">Stack</a> &nbsp;·&nbsp;
  <a href="#experience--credentials">Experience</a> &nbsp;·&nbsp;
  <a href="#contact">Contact</a>
</p>

<br/>

## Impact

<table align="center">
<tr>
<td align="center" width="25%"><h2>00+</h2><sub>ML projects delivered</sub></td>
<td align="center" width="25%"><h2>00K</h2><sub>documents processed</sub></td>
<td align="center" width="25%"><h2>00%</h2><sub>answer accuracy on eval set</sub></td>
<td align="center" width="25%"><h2>&lt; 0s</h2><sub>average response time</sub></td>
</tr>
</table>

<sub>Replace the zeros with your real numbers. Even two or three honest figures make a profile far more credible.</sub>

<br/>

## Architecture in practice

A production retrieval-augmented assistant I built and run, from message to grounded answer:

```mermaid
flowchart LR
    U([User on Telegram]) --> API[FastAPI<br/>webhook]
    API --> Q[(Redis<br/>queue)]
    Q --> W[Celery worker]
    W --> R[Retriever<br/>pgvector similarity search]
    R --> P[Prompt builder<br/>context + question]
    P --> L[LLM]
    L --> A([Answer with sources])

    D[Documents<br/>PDF / DOCX] --> I[Ingestion<br/>chunk + embed]
    I --> V[(PostgreSQL<br/>pgvector)]
    V --> R
```

<br/>

## How I build

Clean, typed, testable code. A simplified view of the retrieval step:

```python
def answer(question: str, k: int = 5) -> Answer:
    """Embed the question, retrieve the closest chunks, answer only from them."""
    query_vec = embed(question)

    chunks = db.execute(
        "SELECT content, source FROM chunks ORDER BY embedding <=> %s LIMIT %s",
        (query_vec, k),
    ).fetchall()

    context = "\n\n".join(c.content for c in chunks)
    reply = llm.generate(PROMPT.format(context=context, question=question))

    return Answer(text=reply, sources=[c.source for c in chunks])
```

**Evaluation snapshot** &nbsp;<sub>(example format, put your own measured results)</sub>

| Metric | Result | How it is measured |
|:--|:--:|:--|
| Retrieval hit rate @5 | 00% | Relevant chunk present in top 5 results |
| Answer faithfulness | 00% | Claims supported by retrieved context |
| Refusal on out-of-scope questions | 00% | Declines instead of inventing an answer |
| p95 latency | 0.0 s | End to end, message to reply |

<br/>

## Selected work

| Project | What it does | Stack |
|:--|:--|:--|
| [**TeleDesk**](https://github.com/YOUR_USERNAME/teledesk) | Support assistant that answers customer questions from a company's own documents | FastAPI, PostgreSQL + pgvector, Celery, Redis, Gemini |
| [**Project Two**](https://github.com/YOUR_USERNAME/project-two) | Problem solved, approach, and the measured result | PyTorch, Transformers |
| [**Project Three**](https://github.com/YOUR_USERNAME/project-three) | Problem solved, approach, and the measured result | Pandas, scikit-learn, XGBoost |
| [**Project Four**](https://github.com/YOUR_USERNAME/project-four) | Problem solved, approach, and the measured result | TensorFlow, OpenCV |

<br/>

## Technical stack

<table>
<tr><td width="22%"><b>Languages</b></td><td>Python, SQL, R, JavaScript</td></tr>
<tr><td><b>Machine learning</b></td><td>PyTorch, TensorFlow, scikit-learn, XGBoost, Hugging Face Transformers</td></tr>
<tr><td><b>LLM systems</b></td><td>RAG, embeddings, vector search, prompt design, evaluation</td></tr>
<tr><td><b>Data</b></td><td>Pandas, NumPy, PostgreSQL, Redis, Power BI</td></tr>
<tr><td><b>Engineering</b></td><td>FastAPI, Celery, Docker, Git, Linux, CI/CD</td></tr>
</table>

<p>
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://skillicons.dev/icons?i=python,pytorch,tensorflow,sklearn,pandas,numpy,fastapi,postgres,redis,docker,git,linux&perline=12&theme=dark">
  <img src="https://skillicons.dev/icons?i=python,pytorch,tensorflow,sklearn,pandas,numpy,fastapi,postgres,redis,docker,git,linux&perline=12&theme=light" alt="Stack icons">
</picture>
</p>

<br/>

## GitHub activity

<p>
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api?username=YOUR_USERNAME&show_icons=true&theme=dark&hide_border=true&bg_color=0d1117&count_private=true&include_all_commits=true">
  <img height="170" src="https://github-readme-stats.vercel.app/api?username=YOUR_USERNAME&show_icons=true&theme=default&hide_border=true&count_private=true&include_all_commits=true" alt="GitHub stats">
</picture>
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://github-readme-stats.vercel.app/api/top-langs/?username=YOUR_USERNAME&layout=compact&theme=dark&hide_border=true&bg_color=0d1117&langs_count=6">
  <img height="170" src="https://github-readme-stats.vercel.app/api/top-langs/?username=YOUR_USERNAME&layout=compact&theme=default&hide_border=true&langs_count=6" alt="Top languages">
</picture>
</p>

<br/>

## Experience & credentials

| Period | Role | Focus |
|:--|:--|:--|
| 2025 – Present | **Role title**, Company or Freelance | What you built and the measurable impact |
| 2023 – 2025 | **Role title**, Company | What you built and the measurable impact |
| 2019 – 2023 | **Degree**, University | Field of study, notable thesis or project |

**Certifications:** Machine Learning Specialization (DeepLearning.AI) · Data Science Professional Certificate · *add yours*

<br/>

## Contact

Open to freelance projects, collaborations and full-time roles.

<p>
  <a href="https://linkedin.com/in/YOUR_USERNAME"><img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
  <a href="https://t.me/YOUR_USERNAME"><img src="https://img.shields.io/badge/Telegram-26A5E4?style=for-the-badge&logo=telegram&logoColor=white" alt="Telegram"/></a>
  <a href="mailto:you@example.com"><img src="https://img.shields.io/badge/Email-30363D?style=for-the-badge&logo=gmail&logoColor=white" alt="Email"/></a>
</p>
