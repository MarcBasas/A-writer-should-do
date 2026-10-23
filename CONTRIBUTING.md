# Contributing

[English](README.md) · [中文说明](README_zh.md)

## 中文摘要

欢迎修脚本、校正技能规则、补文档。动手前先读英文部分，这里只列会挡住合并请求的几条：

- 问题用 `.github/ISSUE_TEMPLATE/` 里的 Bug 或功能请求模板。中文、英文都可以。
- 改母技能 [`SKILL.md`](SKILL.md) 时，不要把七个现成子技能的旧文件名写回去，除非这个 PR 同时迁移那些目录。两套布局现在是分开的，见 README 的「两套布局」。
- 不要提交整本电子书、未清洗的 HTML，或仍在版权期内的长段原文。种子文本若必须引用，保持短，并在 PR 里说明依据。母技能禁止把原句、人物、情节和独创比喻写进派生技能。
- 不要加入去除 DRM 的步骤或工具。脚本遇到 DRM 就停止，保持这样。
- 本仓库以 MIT 许可发布（见 `LICENSE`，版权人 masterball-w，2026）。不要在贡献里改许可证；要换许可证请先问维护者。
- 提取脚本用 Python 3.8+ 就够。没有测试套件；改 `_text_clean.py` 或 `extract_*.py` 时，请在 PR 里写明你用哪一个你有权使用的小样本手动跑过，以及命令和脚本打印的路径。
- 行为变更写进 `CHANGELOG.md`。若最新一节已是已发布版本，在文件顶部另起 `## [Unreleased]`。只改措辞、不改行为的文档，可以不记。

## What belongs here

This repo is an agent skill plus three ebook extractors. Useful changes:

- A bug in `scripts/extract_epub.py`, `extract_mobi.py`, `extract_azw3.py`, or `scripts/_text_clean.py`, with a small input you are allowed to share or describe.
- A rule in a child skill that contradicts the book that skill names, or a parent-skill step that the files cannot actually perform.
- Documentation that matches the files. The English and Chinese READMEs should stay in step.
- A new `write-like-*` child, if you can say which single book it comes from and which filename layout it uses.

Not useful: a restyled copy of an existing child, a full copyrighted book checked in as `*_fulltext.txt`, or a new analysis dimension that the parent skill does not ask for.

## Before you open a pull request

1. Fork the repo and branch from `main`.
2. Read the parent [`SKILL.md`](SKILL.md) and, if you touch a child, that child's `SKILL.md` and `06-generation-editor.md`.
3. Keep one layout per change. The parent template names `01-world-and-material.md` through `06-generation-and-validation.md`. The seven shipped children use `01-author-spirit.md` through `06-generation-editor.md`. A PR that converts one side should say so in the description and update both READMEs.
4. Do not commit book files, DRM-removal instructions, or long verbatim quotations. A seed passage, if you need one, stays short and structural. The parent skill forbids copying original sentences, names, characters, plots, and original metaphors into a derived skill.
5. The project is MIT, copyright 2026 masterball-w, in [`LICENSE`](LICENSE). Do not change that file in a contribution. Ask the maintainer before any other license.
6. If you change extractor behavior or skill behavior, add a note in [`CHANGELOG.md`](CHANGELOG.md). When the top section is already a released version, add a new `## [Unreleased]` above it. Wording-only doc edits do not need one.
7. There is no test suite and no `requirements.txt`. For a script change, run it on a small file you have the rights to use, and paste the command plus the printed paths into the PR. Python 3.8+ is enough. EPUB uses the standard library. MOBI needs `pip install mobi` or Calibre's `ebook-convert`. AZW3 tries Calibre first.

## Skill edits

- Write rules as actions with a check, in the format the file you are editing already uses. The parent wants input, operation, output, acceptance, and rework. The children use ✅ / ❌ / 💡 / 🤖.
- Do not invent counts. The parent skill says sentence and punctuation numbers have to come from same-function samples. `scripts/` does not contain that measurement script yet; do not fill in fake percentiles.
- One book is one work, one period, and one genre. Say that limit in the child skill's boundary section.
- The AI-pattern list in dimension 6 is a checklist for the agent. Do not describe it as a detector that scores text.
- Save generated essays as `{title}.md` in the working directory. Do not add them to a child folder unless the PR is explicitly a checked-in example, like the existing Zhou Guoping essay.

## Reporting issues

Use the bug report template for a wrong extractor result or a skill step that cannot be followed. Use the feature request template for a missing script or a schema migration. Either language is fine.

Include the file path, what you expected, and what the file or script actually does. For an extractor, include the Python version and whether you used the `mobi` package or `ebook-convert`. Do not attach the copyrighted book.

## Maintainer notes

Commit subjects in this repo are short and often bilingual (`feat:`, `fix(skill):`, `docs(readme):`). Match that. The maintainer reviews content changes to child skills against the named book; a drive-by rewrite of a Literary DNA Summary will not be merged without the evidence the skill file already requires.
