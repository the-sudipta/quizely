# Project Memory: Lifetime Interactive Quiz Generator

## 1. Executive Summary & Vision
The **Lifetime Interactive Quiz Generator** is an open-source, zero-overhead educational tool designed to empower students and educators to generate interactive practice exams instantly. 

### Core Philosophy:
* **Zero Cost & High Accessibility:** Built strictly as a single-file application (`.html`) requiring no backend servers, API keys, or databases. It can be hosted entirely for free on static hosting platforms (e.g., GitHub Pages) or run completely offline.
* **Privacy by Design:** All data processing happens entirely inside the user's browser via client-side JavaScript (`FileReader` API). Quiz questions never leave the user's local machine.
* **Frictionless Workflow:** No registration, login, or user management. Users simply download a standard tabular template (CSV), fill it out using Excel or Google Sheets, and upload it to the tool to begin practicing.

---

## 2. System Architecture & User Flow

[1. User Downloads Template] ---> [2. Edits in Excel/Google Sheets]
|
v
[4. Dynamic UI Generation] <--- [3. Uploads .csv to index.html]
|
v
[5. Interactive Testing & Real-time Scoring] <--- [6. State Reset / Loop]


1. **Template Retrieval:** The application provides an explicit trigger to generate and download a pre-formatted RFC 4180-compliant CSV template via data URI generation.
2. **Ingestion & Parsing:** The local browser ingests the student's CSV file. A specialized state-machine text parser evaluates the content line by line to map rows into organized memory objects.
3. **Dynamic DOM Manipulation:** The tool reads the parsed data arrays and dynamically overwrites the DOM container with styled quiz questions, options, and event tracking parameters.
4. **Interactive Assessment:** Upon form submission, the engine validates the selected elements against stored answer coordinates, triggers clear CSS conditional styling classes (`.correct` / `.incorrect`), calculates percentage metrics, and switches operational states.

---

## 3. Current Technical Implementation

The project has advanced from a basic string-splitting utility to a robust standalone production prototype.

### Key Milestones Completed:
* **RFC 4180 Compliant State-Machine Parser:** Implemented a robust token-skipping tokenizer (`parseCSVLine`) to handle text entries wrapped in double quotes. This ensures the app safely parses text containing complex internal punctuation, multi-clause sentences, and raw numbers with commas (e.g., `5,400` or `RAID 1, a sudden power failure...`) without distorting the layout.
* **Responsive Mobile-First UI/UX:** Styled using standard CSS Custom Properties (`:root`) with a deep purple/indigo theme theme. It includes clear hover mechanics, distinct padding profiles for prolonged reading sessions, and `:active` CSS transformation matrices to scale clicked elements smoothly.
* **State Management Lifecycle:** * **Setup State:** Prompts file downloads and handles file ingestion inputs.
  * **Exam State:** Dynamically renders content and intercepts form submissions.
  * **Review State:** Evaluates options, locks radio buttons from further interaction, injects accessibility/color-coded feedback, and renders scrolling target score sheets.
  * **Reset Stream:** Wipes memory states and rolls the UI cleanly back to the Setup State without a browser refresh.

---

## 4. Current File Anatomy

The core deliverable exists inside a single `index.html` divided into three distinct operational paradigms:

1. **HTML Structure (`<body>`):**
   * `.setup-zone`: Configuration block containing download triggers and file selection handlers.
   * `#quiz-form`: Active playground tracking field inputs dynamically populated on demand.
   * `#result-box`: Contextual statistics card revealed strictly at validation endpoints.

2. **CSS Design Architecture (`<style>`):**
   * Leverages custom semantic tokens (`--primary`, `--success`, `--error`) for effortless brand shifting.
   * Employs `.correct` and `.incorrect` UI modifiers to handle dual-color grading for instant validation.

3. **JavaScript Engine (`<script>`):**
   * `parseCSVLine(text)`: Evaluates embedded structural boundaries. Escapes nested structural tokens smoothly.
   * `parseCSVText(text)`: Builds clean array models, automatically truncating title metadata and raw headers.
   * `renderQuiz()`: Compiles literal block parameters into semantic HTML inputs.
   * `addEventListener('submit')`: Evaluates student inputs, updates state flags, and returns percentage outcomes.
   * `resetQuiz()`: Wipes local component states cleanly.

---

## 5. Future Roadmap & Extension Vector Points

CODEX or any subsequent development loop can build on this foundation using these potential enhancement paths:
* **Persistent Progress Tracking:** Integrate browser `localStorage` or `IndexedDB` to securely store past performance scores, letting students track improvement over time without external databases.
* **Timer Mechanics:** Add an overall exam timer or per-question stopwatch component to simulate real-world testing environments.
* **Question Randomization:** Introduce a client-side Fischer-Yates shuffle method to randomize the presentation order of questions and answer options upon ingestion.
* **Flexible Format Support:** Upgrade the interface to smoothly accept multiple formats, such as structured JSON files or raw copy-and-paste text blocks.