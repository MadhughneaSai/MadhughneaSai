# Create a GitHub profile README folder with a README.md and a quick HOW_TO_USE.md,
# then zip it for the user to download.

import os, textwrap, zipfile, io, json, pathlib

root = "/mnt/data/madhughnea-github-readme"
os.makedirs(root, exist_ok=True)
assets_dir = os.path.join(root, "assets")
os.makedirs(assets_dir, exist_ok=True)

username_placeholder = "YOUR_GITHUB_USERNAME"
linkedin_placeholder = "https://www.linkedin.com/in/YOUR-LINKEDIN"
portfolio_placeholder = "https://YOUR-PORTFOLIO.example"
resume_placeholder = "https://YOUR-RESUME-LINK.pdf"

readme = f"""\
<!--
Profile README for Madhughnea Sai
Create a public repo named {username_placeholder}/{username_placeholder}. The README.md at the repo root
is rendered on your GitHub profile.
-->
<h1 align="center">🌟 Madhughnea Sai</h1>
<p align="center">
  Bridging systems, AI, and scalable software. <br/>
  MS in Computer Science at Indiana University Bloomington, May 2025.
</p>

<p align="center">
  <a href="mailto:amadhughneasai@gmail.com"><img src="https://img.shields.io/badge/Email-amadhughneasai%40gmail.com-red"/></a>
  <a href="{linkedin_placeholder}"><img src="https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin"/></a>
  <a href="https://github.com/{username_placeholder}"><img src="https://img.shields.io/badge/GitHub-{username_placeholder}-black?logo=github"/></a>
  <a href="{portfolio_placeholder}"><img src="https://img.shields.io/badge/Portfolio-visit-success"/></a>
  <a href="{resume_placeholder}"><img src="https://img.shields.io/badge/Resume-PDF-informational"/></a>
  <img src="https://komarev.com/ghpvc/?username={username_placeholder}&color=grey" alt="profile views"/>
</p>

---

### 🔭 What I build

- **C++ Chess Engine** - bitboards and magic bitboards for attack generation, full legal move generation including en passant, castling, promotions. Iterative deepening with alpha-beta, transposition tables, MVV-LVA ordering. Perft-tested to depth 6 with 100% rules compliance and 95% branch pruning efficiency. gRPC server-streaming API consumed via Envoy and gRPC-Web for live best-move updates.  
  _Repo: add your link here_

- **Order Management Service (C++ + gRPC)** - CRUD with list views that support paging, filters, sort. Streams live order updates without polling. Robust CMake build that auto-generates protobuf code, clean server and client targets, safe concurrency and graceful shutdown.  
  _Repo: add your link here_

- **High-volume Job Postings Ingestion** - Selenium with rotating VPN/proxy pools and CAPTCHA solving to collect and normalize thousands of postings per day. Mapped data into MySQL and reused team validation/dedupe. Kept ~500k records up to date on schedule.  
  _Repo: add your link here_

---

### 💼 Experience

**Software Engineer, Y Stem and Chess** — May 2025 to Present  
- Built a production-grade chess analysis stack described above.  
- Designed a gRPC streaming API that powers a live frontend over Envoy and gRPC-Web.  
- Verified engine correctness with perft benchmarks and fixed edge cases in pinned pieces and castling rights.

**Software Developer, Central Indiana Corporate Partnership** — Jul 2024 to Dec 2024  
- Selenium ingestion with rotating proxies and CAPTCHA solving, cutting manual entry by about 50 percent while keeping latency predictable.  
- Ingested results into a production MySQL database, mapped fields, reused validation and de-dupe steps, and scheduled refreshes to keep ~500k records current.  
- Monitored GitLab CI/CD pipelines with MSTest suites on merges and nightlies and turned failures into tracked tickets for Agile sprints.

**Software Analyst Intern, JPMorgan** — Jun 2022 to Jul 2022  
- Implemented a circular buffer in C++ for low-latency order storage and retrieval.  
- Optimized an exponential weight future pricing model from ~100 ns to ~80 ns via precomputation and cache-friendly data access.  
- Wrote unit tests and documentation and closed Jira tickets.

---

### 🎓 Education

**Indiana University Bloomington** — Master’s in Computer Science, Aug 2023 to May 2025 — GPA 3.7/4.0  
Relevant coursework: Data Structures and Algorithms, Systems and Security, Software Engineering, Computer Networks

**Vellore Institute of Technology** — Bachelor’s in Computer Science and Engineering, Jul 2019 to Jun 2023 — GPA 3.5/4.0  
Relevant coursework: Operating Systems, Digital Logic and Design, Computer Architecture, Parallel and Distributed Computing, Networks and Communication, Database Management Systems, Information Security Management

---

### 🧰 Toolbox

<p>
  <!-- Languages -->
  <img src="https://img.shields.io/badge/C%2B%2B-00599C?logo=c%2B%2B&logoColor=white" />
  <img src="https://img.shields.io/badge/C-283593?logo=c&logoColor=white" />
  <img src="https://img.shields.io/badge/Java-007396?logo=java&logoColor=white" />
  <img src="https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white" />
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black" />
  <img src="https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white" />
  <img src="https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white" />
  <img src="https://img.shields.io/badge/R-276DC3?logo=r&logoColor=white" />
  <img src="https://img.shields.io/badge/Bash-4EAA25?logo=gnubash&logoColor=white" />
  <br/>
  <!-- Frameworks -->
  <img src="https://img.shields.io/badge/gRPC-000000?logo=grpc&logoColor=white" />
  <img src="https://img.shields.io/badge/React-20232a?logo=react&logoColor=61DAFB" />
  <img src="https://img.shields.io/badge/Angular-DD0031?logo=angular&logoColor=white" />
  <img src="https://img.shields.io/badge/Spring-6DB33F?logo=spring&logoColor=white" />
  <img src="https://img.shields.io/badge/Node.js-339933?logo=node.js&logoColor=white" />
  <img src="https://img.shields.io/badge/Express-000000?logo=express&logoColor=white" />
  <img src="https://img.shields.io/badge/Raylib-000000?logo=raylib&logoColor=white" />
  <br/>
  <!-- Databases -->
  <img src="https://img.shields.io/badge/MySQL-4479A1?logo=mysql&logoColor=white" />
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white" />
  <br/>
  <!-- DevOps and Tools -->
  <img src="https://img.shields.io/badge/AWS-232F3E?logo=amazon-aws&logoColor=white" />
  <img src="https://img.shields.io/badge/Docker-2496ED?logo=docker&logoColor=white" />
  <img src="https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes&logoColor=white" />
  <img src="https://img.shields.io/badge/Git-F05032?logo=git&logoColor=white" />
  <img src="https://img.shields.io/badge/GitLab-FC6D26?logo=gitlab&logoColor=white" />
  <img src="https://img.shields.io/badge/CMake-064F8C?logo=cmake&logoColor=white" />
  <img src="https://img.shields.io/badge/gTest-4A9EA1?logo=googletest&logoColor=white" />
  <img src="https://img.shields.io/badge/pytest-0A9EDC?logo=pytest&logoColor=white" />
  <img src="https://img.shields.io/badge/Postman-FF6C37?logo=postman&logoColor=white" />
  <img src="https://img.shields.io/badge/Jira-0052CC?logo=jira&logoColor=white" />
  <img src="https://img.shields.io/badge/VS%20Code-007ACC?logo=visual-studio-code&logoColor=white" />
  <img src="https://img.shields.io/badge/Agile-3DDC84?logo=pinboard&logoColor=white" />
</p>

---

### 🧪 Publications

- **A Neural Network Based Approach to Find Solutions to Diffusion Equations: Resolving Overfitting Issues Using Various Regularization Methods in Neural Networks** — SYNASC 2022, IDASCN 2022

---

### 📈 GitHub stats

<p align="center">
  <img src="https://github-readme-stats.vercel.app/api?username={username_placeholder}&show_icons=true" height="150"/>
  <img src="https://github-readme-streak-stats.herokuapp.com/?user={username_placeholder}" height="150"/>
</p>
<p align="center">
  <img src="https://github-readme-stats.vercel.app/api/top-langs/?username={username_placeholder}&layout=compact" height="150"/>
</p>

---

### 🔗 Quick links
- Portfolio: {portfolio_placeholder}
- LinkedIn: {linkedin_placeholder}
- GitHub: https://github.com/{username_placeholder}
- Email: amadhughneasai@gmail.com
- Phone: +1-930-237-0706

> Operating principles: Observe → Guess → Idempotent by default → Ship small, learn fast
"""

howto = f"""# How to use

1) Find your GitHub username. Example: if your profile is https://github.com/octocat the username is **octocat**.
2) Create a new public repository named exactly **{username_placeholder}**. Replace this placeholder with your username.
   - In GitHub, click "New" and set the Repository name to **your-username**. Check "Public".
   - Example: if your username is `octocat`, create `octocat/octocat`.
3) Copy `README.md` from this folder into that repository.
4) Replace placeholders inside README.md:
   - `{username_placeholder}` with your actual username
   - `{linkedin_placeholder}` with your LinkedIn URL
   - `{portfolio_placeholder}` with your portfolio URL if you have one
   - `{resume_placeholder}` with a link to your resume PDF (or remove the badge)
5) Commit and push. Visit your profile page to see the README render.
6) Optional: replace the project repo links, add screenshots in the `assets/` folder, and reference them with relative paths like `./assets/screenshot.png`.

Tips:
- Keep the README concise and visual. Shields.io badges and short bullet points help recruiters skim.
- Use GitHub "Pinned" repositories to highlight your top projects.
"""

with open(os.path.join(root, "README.md"), "w", encoding="utf-8") as f:
    f.write(readme)

with open(os.path.join(root, "HOW_TO_USE.md"), "w", encoding="utf-8") as f:
    f.write(howto)

# Create a zip archive
zip_path = "/mnt/data/madhughnea-github-readme.zip"
with zipfile.ZipFile(zip_path, "w", zipfile.ZIP_DEFLATED) as zf:
    for foldername, subfolders, filenames in os.walk(root):
        for filename in filenames:
            full_path = os.path.join(foldername, filename)
            arcname = os.path.relpath(full_path, start=os.path.dirname(root))
            zf.write(full_path, arcname)

zip_path
