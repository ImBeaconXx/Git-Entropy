# Git-Entropy (WIP)
> Stop guessing where your technical debt is. Data-driven refactoring for modern teams.

[中文說明](./README.zh-TW.md) | [License](./LICENSE) | [Architecture](#)

### 📊 The Problem
Static analysis (like SonarQube) finds "bad code," but it doesn't find "painful code." If a complex function hasn't been touched in 3 years, it's not debt—it's an artifact. If a simple function is changed 50 times a month, it's a bottleneck.

**Git-Entropy** combines **Code Churn** and **Structural Complexity** to find the "Entropy" of your files.

### 🧠 The Core Logic
We calculate the **Entropy Score** using a time-decayed churn model:

$$Entropy = \left( \sum_{i=1}^{n} e^{-\lambda (t_{now} - t_i)} \right) \times \text{Complexity}(f)$$

- **$\lambda$ (Decay Factor):** Recent commits carry more weight.
- **Complexity:** Calculated via **Tree-sitter** incremental parsing (not just Regex) to detect nesting depth and cyclomatic complexity.

### 🛠️ Proposed Tech Stack
- **Engine:** Rust (built with `git2-rs`) for blindingly fast log traversal.
- **Parsing:** `tree-sitter` for language-agnostic AST analysis.
- **UI:** A zero-dependency TUI (Terminal UI) and an optional D3.js treemap export.

### 🚀 Roadmap
- [ ] Git log traversal engine (Rust)
- [ ] Tree-sitter integration for Rust/JS/Go
- [ ] Interactive CLI Dashboard
- [ ] CI/CD Github Action integration

*This project is currently in the **RFC (Request for Comments)** stage. I’d love to hear your thoughts on the scoring algorithm!*

> Note on Language: English is not my native language. I’ve done my best to communicate the technical concepts clearly. If you find any typos or awkward phrasing, feel free to open a PR—I’d appreciate it!
