# Contributing to Xfce Notes

Thank you for considering a contribution!

This repository contains user-written notes about the Xfce desktop environment. Contributions should help improve clarity, organization, or completeness of information.

## 🔗 Submodule Integration & Attribution

Please note that this repository is designed to be used as a **Git submodule** within my [Jekyll website](https://github.com/nozomi-75/nozomi-75.github.io). As such, its content may be rendered or embedded directly into the site.

To ensure proper credit, when your contribution is merged into this project, your name (or preferred handle) will be added to the [`authors.yml`](https://github.com/nozomi-75/nozomi-75.github.io/blob/main/_data/authors.yml) file in the main site repository. This way, your contributions will be visibly attributed wherever applicable on the site.

If you have a preferred display name and/or link you'd like included, feel free to mention it in your pull request or open an issue.


## 📋 Contribution Guidelines

### ✅ You Can:
- Add new notes about Xfce tools, plugins, or config tips.
- Improve formatting or fix typos.
- Organize content into logical sections.
- Update outdated information (please cite if possible).

### ❌ Please Avoid:
- Adding non-Xfce content (e.g., unrelated DEs or apps).
- Adding speculation without context or disclaimers.
- Uploading large binaries or screenshots (unless requested).

## 🧰 How to Contribute

1. **Fork** the repository.
2. Create a **new branch** for your change.
3. Make your changes.
4. Commit with a clear message.
5. **Open a pull request**.

## 📄 Style Tips

- Refer to it as "Xfce".
- Use clear, concise Markdown.
- Refer to [Chirpy's](https://github.com/cotes2020/jekyll-theme-chirpy/tree/master/_posts) documentations.
- Wrap code snippets in triple backticks:

  ```
  xfconf-query -c xfwm4 -p /general/theme -s "Adwaita"
  ```

## 📑 Attribution Tips

- **Always cite the source** if you include or paraphrase content from, but not limited to:
  - Wiki pages (e.g., Arch Wiki, Ubuntu Wiki)
  - Blog posts or forums
  - Official Xfce documentation
- You can include the citation as:
  - An in-text citation
  - A footnote-style link
  - A link (i.e. to the project)

## 💬 Questions?

You may contact the repository owner for your general questions related to this project. Otherwise, please open an issue if you're unsure whether something belongs here.
