Please rewrite this repository’s README

Requirements:
1. Keep it concise, practical, and specific to the current repo.
2. Replace any copied/incorrect content from other repos.
3. Explain the repo structure, not just list folders.
4. Use the exact section order and headings below.
5. Use real file/folder names from this repo (verify before writing).
6. Keep Markdown clean and readable.

Required README structure:

# <repo_name>

<1-2 sentence summary of what this ETL repo does and what domain it serves>

## How This Repo Is Structured

- Briefly explain the ETL layers used in this repo (Bronze/Silver/Gold as applicable).
- Explain what each layer is responsible for in this specific project.
- Add a short 3-step high-level data flow.

## Repository Layout

- Add a `text` code block tree showing the real current structure.
- Include key top-level files, notebooks, and SQL layer folders/files.

## Key Files And Responsibilities

- Bullet list of important files/folders and what each does.
- Include notebooks, sql layer directories, project config, and dependencies file.

## Data Sources

Add a Markdown table with these columns:
| Source | Type | Main Data Used Here | Lands In | Notes |

- Include all major upstream sources used by the repo (DBs, blob/static files, etc.).
- Mention important table/file names where helpful.
- Explain where each source lands (Bronze/Silver/Gold or transformation stage).

## Static Inputs

- List static files/paths if the repo uses them.
- If none exist, write: “No static input files are currently documented.”

## Downstream Usage

- List known downstream consumers (e.g., Power BI datasets, reverse ETL targets).
- If unknown, write: “Downstream consumers are not currently documented.”

Style rules:
- Do not invent sources, files, or consumers.
- If something is uncertain, mark it as “to be confirmed”.
- Keep wording direct and operational (for analysts/engineers).
- Preserve existing factual details that are correct, but fix wording/grammar.