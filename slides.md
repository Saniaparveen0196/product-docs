---
marp: true
theme: default
paginate: true
class: lead
# Global custom CSS for the presentation
style: |
  /* -- Custom theme variables -- */
  :root {
    --brand: #0b6cf6;
    --accent: #0ec8a0;
    --text: #0f1724;
    --muted: #6b7280;
    --code-bg: rgba(15, 23, 36, 0.06);
  }

  /* Page background and font defaults */
  section {
    font-family: "Inter", "Segoe UI", Roboto, -apple-system, "Helvetica Neue", Arial;
    color: var(--text);
    line-height: 1.45;
    padding: 48px;
  }

  /* Title styling */
  h1 {
    color: var(--brand);
    letter-spacing: -0.02em;
  }

  /* Footer area (email + small print) */
  .slide-footer {
    position: absolute;
    right: 24px;
    bottom: 12px;
    font-size: 12px;
    color: var(--muted);
    display: flex;
    gap: 12px;
    align-items: center;
  }

  /* Code blocks */
  pre code {
    background: var(--code-bg);
    padding: 12px;
    border-radius: 8px;
    display: block;
    overflow-x: auto;
  }

  /* Fancy callout */
  .callout {
    border-left: 4px solid var(--accent);
    padding: 12px 16px;
    background: rgba(14, 200, 160, 0.06);
    border-radius: 6px;
    color: var(--text);
  }

  /* Math size */
  .katex {
    font-size: 1.05em;
  }

---

<!-- Title slide -->
# Product Documentation — WidgetFlow
_A concise, maintainable product docs slide deck (Marp)_

**Author:** Technical Writing Team  
**Contact:** 24f2003458@ds.study.iitm.ac.in

<div class="slide-footer">
  <span>24f2003458@ds.study.iitm.ac.in</span>
</div>

---

<!-- Slide with background image -->
<!-- Use inline HTML attributes to ensure a background image appears in many Marp renderers -->
<section style="background-image: url('https://images.unsplash.com/photo-1542744173-8e7e53415bb0?auto=format&fit=crop&w=1600&q=60'); background-size: cover; background-position: center;">
  
  <h2 style="color: white; text-shadow: 0 2px 8px rgba(0,0,0,0.6);">Product Overview</h2>
  <p style="color: white; text-shadow: 0 1px 6px rgba(0,0,0,0.5); max-width: 60%;">
    WidgetFlow is a microservice-based platform for real-time metric aggregation, alerting, and dashboards.
  </p>

  <div class="slide-footer" style="color: rgba(255,255,255,0.9);">
    <span>24f2003458@ds.study.iitm.ac.in</span>
  </div>
</section>

---

# Goals & Audience

- Provide **maintainable** docs kept in Git.
- Enable automated delivery: HTML, PDF, PPTX exports via Marp CLI / GitHub Actions.
- Audience: developers, SREs, product managers.

---

# How to maintain in Git

1. One Markdown file per major document: `slides.md`, `user-guide.md`, `api.md`.
2. Use branches for major updates: `feature/upgrade-auth`.
3. Use PR templates and CI checks (linter + Marp build) to validate exports.

```yaml
# sample GitHub Action (brief)
name: Build slides
on: [push, pull_request]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Install Marp CLI
        run: npm i -g @marp-team/marp-cli
      - name: Render slides
        run: marp slides.md --pdf --html
