# Quizely

Quizely is a lifetime interactive quiz generator for students, teachers, and self-learners. It turns a simple CSV file into a polished browser-based practice quiz with instant scoring, review feedback, and unlimited retry attempts.

The app is intentionally built as a single static `index.html` file. There is no backend, no account system, no database, and no API key. Quiz content is parsed locally in the browser, so uploaded questions stay on the user's device.

## Highlights

- Single-file static web app, ready for GitHub Pages.
- Fully client-side CSV upload and parsing.
- RFC 4180-aware parser for quoted commas and escaped quotes.
- Beautiful responsive interface for desktop and mobile study sessions.
- Instant score review with correct, incorrect, and unanswered states.
- Practice again with the same CSV without re-uploading.
- Downloadable CSV template built into the app.
- Privacy-first design with no external services.

## Live Usage

Open `index.html` in a browser or host the repository with GitHub Pages.

1. Download the CSV template from the app.
2. Fill the template in Excel, Google Sheets, LibreOffice, or another spreadsheet tool.
3. Export or save as CSV.
4. Upload the CSV in Quizely.
5. Practice, review your score, and retry as many times as needed.

## CSV Format

Quizely expects this column order:

```csv
Question,Option A,Option B,Option C,Option D,Correct Answer (A/B/C/D)
"Which habit supports long-term memory?",Cramming,Spaced repetition,Skipping review,Reading once,B
```

See [examples/quizely_template.csv](examples/quizely_template.csv) for a ready-to-edit starter file.

## Project Structure

```text
.
|-- index.html
|-- README.md
|-- LICENSE
|-- CITATION.cff
|-- CHANGELOG.md
|-- CONTRIBUTING.md
|-- SECURITY.md
|-- CODE_OF_CONDUCT.md
|-- .gitignore
|-- .nojekyll
|-- docs/
|   `-- PROJECT_DETAILS.md
`-- examples/
    `-- quizely_template.csv
```

## Development

No build step is required.

For a quick local preview:

```bash
python -m http.server 4177
```

Then open `http://127.0.0.1:4177/`.

## Design Principles

- Zero cost: deployable on free static hosting.
- High accessibility: works offline after download.
- Privacy by design: files are processed locally in the browser.
- Student-friendly experience: practice should feel calm, polished, and repeatable.

## Documentation

The full project memory and roadmap live in [docs/PROJECT_DETAILS.md](docs/PROJECT_DETAILS.md).

## License

This project is released under the MIT License. See [LICENSE](LICENSE).
