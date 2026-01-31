# personalwebsite
Wei-Lu's personal website
# Personal Portfolio Website (WordPress on AWS Lightsail)

This repository documents a reproducible setup for deploying a personal portfolio website using WordPress on AWS Lightsail.  
Goal: a single-page Home that contains Bio + CV PDFs + key info + a project list, where each project links to a detail page with downloadable PDFs.

---

## 1) Target Website Structure (Information Architecture)

### Home (single-page)
Home contains the following sections (top → bottom):
1. Short Bio + key info
2. Projects list (overview grid/list)
3. CV / Resume PDFs (download buttons)
4. Contact

### Project detail pages
Each project has its own detail page including:
- Title
- description
- Key links (e.g., paper, demo, GitHub)
- PDF download(s)
- Images / screenshots (optional)

---

## 2) Deployment Approach

### Baseline
- Hosting: AWS Lightsail
- Deployment method: Lightsail **WordPress blueprint** (managed baseline)
- OS: Linux/Unix (provided by blueprint)
- Web stack and database: pre-installed by blueprint

Why blueprint:
- Fastest path to a working WordPress site
- Mature ecosystem (themes/plugins)
- Minimal manual server setup for a beginner
- Focus on reproducible provisioning + site configuration

---

## 3) Provisioning / Bootstrap (From 0 to a working website)

### Milestone A: Create the instance
- Create a Lightsail instance using WordPress blueprint
- Choose the smallest plan for initial learning (e.g., $5/month)
- Confirm the default WordPress page is accessible via Public IP

**Acceptance criteria**
- From 0 → website is publicly accessible
- No manual SSH installation steps required to see the default WordPress page

### Milestone B: Admin access and basic setup
- Log into `/wp-admin`
- Set the homepage to the custom Home page
- Choose a theme suitable for a one-page portfolio + project detail pages

**Acceptance criteria**
- Able to edit Home sections
- Able to create one sample project detail page

### Milestone C: Stability and basic ops
- Attach a Static IP (avoid IP changes after reboot)
- Enable HTTPS (later step once the site is stable)

**Acceptance criteria**
- Site remains reachable after reboot (stable address)
- HTTPS plan documented (or enabled)

---

## 4) CI/CD and DevOps Plan (Planned)

This project aims to practice DevOps concepts beyond “just deploying a website”.

### Phase 1 (current): Reproducible provisioning and configuration
- Document infrastructure choices (Lightsail blueprint, plan, region)
- Document WordPress configuration steps (theme, pages, project template)
- Keep a clear checklist for rebuilding in a new AWS account

### Phase 2 (next): Automation
Potential automation directions (choose one after the instance is available):
- Snapshot-based backup/restore strategy (Lightsail snapshots)
- Infrastructure template (CloudFormation) to recreate the baseline resources
- Deployment automation for assets (e.g., PDFs/images) if needed
