<div align="center">

<img src="./assets/neofetch.svg" alt="neofetch-style intro card for Vivansh Garg" width="100%"/>

<br/>

<a href="mailto:vivanshgarg05@gmail.com"><img src="https://img.shields.io/badge/-email-0d1117?style=for-the-badge&logo=gmail&logoColor=f5a623" alt="Email"/></a>
<a href="https://www.linkedin.com/in/vivansh-garg/"><img src="https://img.shields.io/badge/-linkedin-0d1117?style=for-the-badge&logo=linkedin&logoColor=f5a623" alt="LinkedIn"/></a>
<a href="https://repoatlas-iqbu.onrender.com"><img src="https://img.shields.io/badge/-live_demo-0d1117?style=for-the-badge&logo=render&logoColor=f5a623" alt="RepoAtlas live demo"/></a>
<img src="https://komarev.com/ghpvc/?username=Vivansh-07&label=visitors&color=f5a623&style=for-the-badge" alt="Profile views"/>

</div>

<br/>

```console
vivansh@github:~$ cat about.txt
```

> Hi, I'm **Vivansh Garg**, a **B.Tech CSE (Data Science)** student at **Manipal University Jaipur**, graduating **2028**.
> I like projects where the honest answer matters more than the flashy one: **measure it, ablate it, test it, then ship it.**
> Lately that means catching voice-clone fraud mid-call, finding what *actually* helps retrieval, auditing data for hidden bias, and mapping how codebases hold together.

<br/>

```console
vivansh@github:~$ git log --oneline --graph projects/
```

| | commit | project | what it does | stack |
|:-:|:--|:--|:--|:--|
| 🟠 | `5ih2026` | **[VaaniRakshak](https://github.com/Vivansh-07/VaaniRakshak-AI)** | Real-time call-risk assistant for **voice-cloning fraud**. Combines *voice risk* (is the speech synthetic?) with *action risk* (is the caller pushing a UPI scan, OTP or urgent transfer?) and warns the listener **during** the call. Smart India Hackathon 2026 | `PyTorch` `Whisper` `SSE` |
| 🟠 | `e4a71c2` | **[RepoAtlas](https://repoatlas-iqbu.onrender.com)** | Paste a GitHub repo, get an **interactive dependency map** of its Python modules: PageRank for importance, Louvain for clusters, red halos for circular imports. Plus a Graph Lab for random-graph models. **Live demo ↗** | `FastAPI` `NetworkX` `Cytoscape.js` |
| 🟠 | `0.742nd` | **Hybrid Retrieval QA** | BM25 + dense + Reciprocal Rank Fusion + cross-encoder reranking for **scientific QA on SciFact**. Full ablation with significance tests; a fine-tuned encoder reaches **nDCG@10 0.742**, up from 0.656 for BM25 | `PyTorch` `FAISS` `BEIR` |
| 🟠 | `b1a5v6a` | **Bias-Aware Candidate Auditor** | Flags feature blocks linked to **label corruption** before a model is trained, without being told which columns are sensitive, or **abstains** when the evidence isn't there. Team project, DSE3170 PBL-3 | `Streamlit` `Statistics` `Fairness` |
| ⚪ | `HEAD` | *next big thing* | currently in the oven… | `???` |

<details>
<summary><b>🔍 inside VaaniRakshak</b></summary>

<br/>

```
LISTEN → UNDERSTAND → DETECT → WARN → VERIFY → PREVENT → REPORT
```

- 🎙️ **Voice-authenticity CNN** trained on ASVspoof 2019 LA, wired into a live windowed pipeline
- 🗣️ **Intent detection** for risky requests in **English, Hinglish and Hindi**
- 📈 **Risk engine** with persistence and hysteresis, so it escalates only when the evidence keeps up
- ⚡ **Live events over HTTP + SSE**, plus an upload → warning → verification → call-report interface
- 🧪 **265 tests** with zero third-party dependencies

```
  10.0s  voice 0.71  action 0.00  ->  CAUTION
  12.0s  voice 0.76  action 0.98  ->  HIGH_RISK  [VERIFY_CALLER_BEFORE_PAYMENT]
```
<sub>A suspicious voice alone only reaches <code>CAUTION</code>. It's the <i>"scan this QR and pay right now"</i> that tips it into <code>HIGH_RISK</code>.</sub>

</details>

<details>
<summary><b>🗺️ inside RepoAtlas</b></summary>

<br/>

- **One URL in, a dependency graph out.** Size = PageRank, colour = Louvain community, red halo = circular dependency
- **Modules or packages:** Flask's 82 modules collapse into 20 packages, with package-level cycles
- **Four layouts** (Force, Hierarchy, Rings, Circle), each answering a different question about structure
- **Graph Lab:** Erdős–Rényi, Barabási–Albert and Watts–Strogatz generators with log–log degree plots
- Shareable links, PNG export, deployed on Render

</details>

<details>
<summary><b>📊 inside Hybrid Retrieval QA</b></summary>

<br/>

```
query ─┬─ BM25 (inverted index) ──┐
       │                          ├─► RRF fusion ─► cross-encoder rerank ─► cited answer
       └─ dense bi-encoder + FAISS┘
```

| variant (SciFact test, 300 claims) | nDCG@10 |
|:--|:-:|
| BM25 | 0.656 |
| Dense (MiniLM) | 0.679 |
| RRF fusion | 0.710 |
| **Dense, fine-tuned on SciFact train** | **0.742** |

Paired bootstrap tests show fusion helps only when the two retrievers are of similar strength, and the reranker isn't worth its ~3× latency. 72 tests, a written paper and a side-by-side web demo.

</details>

<details>
<summary><b>⚖️ inside Bias-Aware Candidate Auditor</b></summary>

<br/>

- Cross-fitted **source** and **label** models separate clean population shift from suspicious label behaviour
- Benjamini–Yekutieli correction across feature blocks: it **flags only what survives**, otherwise it abstains
- Streamlit app with a synthetic lab, real-data audits (COMPAS, German Credit, Heart Disease) and live calibration
- On COMPAS with 30% injected corruption, audit-guided reweighting removes most of the over-prediction for the affected group

<sub>Team: Soumya Shradha · Tanishk Gangwar · Yagya Salwan · Vivansh Garg · Guide: Dr. Chirag Joshi</sub>

</details>

<br/>

```console
vivansh@github:~$ ./status --now
```

```diff
+ building   ▰▰▰▰▰▰▱▱▱▱  VaaniRakshak · live call audio + Indian-language model next
+ shipped    ▰▰▰▰▰▰▰▰▰▱  RepoAtlas is live on Render
+ research   ▰▰▰▰▰▰▰▱▱▱  hybrid retrieval: ablations, significance tests, paper
+ learning   ▰▰▰▰▰▱▱▱▱▱  whatever the next project needs
! open to    SWE / ML internships · let's talk → vivanshgarg05@gmail.com
- bugs       ▰▰▰▰▰▰▰▰▰▰  infinite (but fixing them)
```

<br/>

```console
vivansh@github:~$ ls ~/toolbox
```

<p align="center">
  <img src="https://skillicons.dev/icons?i=python,java,cpp,js,html,css,nodejs,react,pytorch,fastapi,docker,latex,git,github,githubactions&perline=8" alt="Toolbox"/>
</p>

<p align="center">
  <code>FAISS</code> · <code>Sentence-Transformers</code> · <code>Whisper</code> · <code>NetworkX</code> · <code>Cytoscape.js</code> · <code>Streamlit</code> · <code>pytest</code> · <code>Render</code>
</p>

<br/>

```console
vivansh@github:~$ gh stats --pretty
```

<p align="center">
  <img height="165" src="https://github-readme-streak-stats.herokuapp.com?user=Vivansh-07&hide_border=true&background=0d1117&ring=f5a623&fire=ff6b6b&currStreakLabel=f5a623&sideLabels=c9d1d9&currStreakNum=c9d1d9&sideNums=c9d1d9&dates=8b949e&stroke=30363d" alt="GitHub streak"/>
</p>

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/Vivansh-07/Vivansh-07/output/snake-dark.svg"/>
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/Vivansh-07/Vivansh-07/output/snake-light.svg"/>
  <img alt="Snake eating my contribution graph" src="https://raw.githubusercontent.com/Vivansh-07/Vivansh-07/output/snake-dark.svg" width="100%"/>
</picture>

<br/>

```console
vivansh@github:~$ fortune
```

<div align="center">

*"First, solve the problem. Then, write the code."* · John Johnson

<sub>⌁ thanks for scrolling this far · <code>exit 0</code> ⌁</sub>

</div>
