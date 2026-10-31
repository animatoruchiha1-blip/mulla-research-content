# Research Papers Directory

This directory stores individual structured JSON files for research papers published in the **Mulla Research Library**.

---

## File Naming Convention

Each research paper must be saved as a separate JSON file named with its unique Research ID:

```
research/
├── RES-0001.json
├── RES-0002.json
├── RES-0003.json
└── RES-0004.json
```

---

## Publication Status & Public Visibility

Every paper contains a `"status"` field:

- `"status": "published"` — **Live & Visible**: The paper appears in the public library, categories, search results, and homepage.
- `"status": "draft"` — **Hidden / Work-in-Progress**: The paper is strictly ignored by the public website and will not be displayed anywhere.
- `"status": "archived"` — **Archived**: Hidden from regular public discovery.

---

## Publishing Workflow

1. Copy [`templates/research-template.json`](../templates/research-template.json).
2. Name your new file (e.g., `RES-0001.json`).
3. Fill in your research metadata, abstract, and content.
4. Set `"status": "published"`.
5. Commit and push to the `main` branch.
6. The website will automatically detect and display the paper.
