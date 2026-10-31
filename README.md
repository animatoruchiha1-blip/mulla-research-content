# Mulla Research Content Repository
### Dedicated Structured Knowledge Store for Mulla Research Library

**Repository Owner:** `animatoruchiha1-blip`  
**Repository Name:** `mulla-research-content`  
**Target Branch:** `main`  
**Visibility:** Private  
**Platform Owner / Lead Researcher:** Mulla Md Anas Ahemad  
**Website:** [Mulla Research Library](https://mulla-research-library.vercel.app)

---

## 1. Overview

This private repository functions as the **database-free metadata and content store** for the **Mulla Research Library** digital knowledge platform.

Instead of utilizing centralized SQL or NoSQL database servers, all research papers, abstracts, bibliographies, categories, and site configurations are stored as version-controlled JSON documents. The Next.js website fetches and serves this data dynamically using the GitHub REST API and GitHub Contents API.

---

## 2. Repository Structure

```
mulla-research-content/
│
├── research/                  # Individual research publication JSON files
│   ├── RES-0001.json
│   ├── RES-0002.json
│   └── README.md
│
├── indexes/                   # Fast lookup indexes
│   ├── research-index.json    # Catalog of all research items
│   └── categories.json        # Academic category taxonomy
│
├── settings/                  # Global website settings & configuration
│   └── website.json
│
├── schemas/                   # Formal JSON Schema validation
│   └── research-schema.json
│
├── templates/                 # Reusable research paper template
│   └── research-template.json
│
├── .gitignore                 # Excludes local/OS/credential files
└── README.md                  # Comprehensive operating documentation
```

---

## 3. Step-by-Step Publishing Workflow

Managing research is handled directly through GitHub without touching website source code or accessing an administrative panel.

### Step 1: Upload PDF & Cover Image to Vercel Blob
1. Log in to your [Vercel Dashboard](https://vercel.com/dashboard).
2. Open your `mulla-research-library` project.
3. Click the **Storage** tab and select your **Vercel Blob** store.
4. Upload:
   - Your research paper document (PDF format, up to 30 MB).
   - Your research cover image (JPEG, PNG, or WebP, up to 8 MB).
5. Copy the resulting public HTTPS URLs for both files.

### Step 2: Create Research JSON File on GitHub
1. Open this repository: [`animatoruchiha1-blip/mulla-research-content`](https://github.com/animatoruchiha1-blip/mulla-research-content).
2. Navigate into the `research/` directory.
3. Click **Add file** > **Create new file**.
4. Name the file using the standard identifier format, e.g., `RES-0001.json`.

### Step 3: Populate the Research Metadata
Paste the template from [`templates/research-template.json`](templates/research-template.json) and fill in your details:

```json
{
  "id": "RES-0001",
  "title": "How AI Can Help Grow a Business",
  "slug": "how-ai-can-help-grow-a-business",
  "author": "Mulla Md Anas Ahemad",
  "category": "Artificial Intelligence",
  "description": "A comprehensive research report about AI in business automation and growth.",
  "abstract": "This research investigates how modern artificial intelligence and automated reasoning architectures accelerate enterprise workflows, optimize commercial ledger reconciliation, and reduce operational overhead.",
  "keywords": [
    "Artificial Intelligence",
    "Business",
    "Automation",
    "Machine Learning"
  ],
  "coverImage": "https://your-blob-store.public.blob.vercel-storage.com/covers/ai-growth.jpg",
  "pdfUrl": "https://your-blob-store.public.blob.vercel-storage.com/papers/how-ai-can-help-grow-a-business.pdf",
  "publishedAt": "2026-10-31",
  "status": "published",
  "featured": true
}
```

### Step 4: Set Publication Status
- To publish immediately: set `"status": "published"`.
- To save as a draft without public visibility: set `"status": "draft"`.

### Step 5: Commit to `main`
Click **Commit changes...**, write a commit message (e.g., `feat(research): publish RES-0001`), and commit directly to the `main` branch.

### Step 6: Live Reflection
The website dynamically queries GitHub and displays your new publication within 60 seconds (or immediately if a webhook is configured).

---

## 4. Maintenance & Operations

### How to Edit an Existing Paper
1. Navigate to `research/RES-XXXX.json` in GitHub.
2. Click the pencil icon (**Edit this file**).
3. Modify any field (e.g. improve the abstract, update the PDF URL, or change tags).
4. Commit your changes to `main`. The live website will refresh automatically.

### How to Unpublish a Paper (Draft Mode)
1. Open the target JSON file in `research/`.
2. Change `"status": "published"` to `"status": "draft"`.
3. Commit to `main`. The paper will immediately disappear from the public website while remaining safely preserved in your repository.

### How to Permanently Delete a Paper
1. In `research/`, open the target JSON file.
2. Click the trash can icon (**Delete this file**).
3. Commit the deletion to `main`.

### How to Add a New Category
1. Open [`indexes/categories.json`](indexes/categories.json).
2. Append a new category object:
   ```json
   {
     "id": "cat-new",
     "name": "New Category Name",
     "slug": "new-category-name",
     "description": "Clear academic description of this research discipline.",
     "iconName": "BookOpen",
     "color": "#245B91"
   }
   ```
3. Commit to `main`.

---

## 5. Webhook Configuration for Instant Live Updates

For instantaneous cache invalidation upon pushing commits, set up a GitHub webhook:

1. In this repository, go to **Settings** > **Webhooks** > **Add webhook**.
2. **Payload URL:** `https://your-production-domain.vercel.app/api/revalidate`
3. **Content type:** `application/json`
4. **Secret:** Enter your `GITHUB_WEBHOOK_SECRET` (configured in your Vercel project environment variables).
5. **Which events would you like to trigger this webhook?**: Select **Just the push event**.
6. Ensure **Active** is checked, then click **Add webhook**.

---

## 6. Security Principles

1. **Private Repository:** Keep this repository private to protect draft research and private metadata.
2. **Server-Side Token Access:** The public website accesses this repository exclusively through server-side Next.js route handlers and server components. The `GITHUB_TOKEN` is never exposed to browser clients.
3. **No Database Dependencies:** Eliminates SQL injection, database downtime, connection pool saturation, and operational costs.
4. **Draft Confidentiality:** The website strictly checks `status === 'published'`. Draft papers cannot be accessed or viewed by URL guessing.

---

## 7. Platform Owner & Mentors

**Platform Owner:**  
Mulla Md Anas Ahemad  
AI Researcher | I.Com (Intermediate in Commerce) | Software Development | Cyber Security  

**Mentors & Inspirations:**
- **Golam Sir** (*UDAAN SCIENCE ACADEMY*) — Science and Logical Thinking Mentor
- **Shams Sir** (*CODES COOL*) — Coding and Development Mentor
- **Manoj Sir** (*BHADRAK COMMERCE ACADEMY*) — Commerce Mentor

**Motto:**  
> *"Learn Continuously. Think Logically. Research Deeply. Create Meaningfully."*
