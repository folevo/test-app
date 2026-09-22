# Quiz CLI

An interactive command-line quiz game for practicing programming knowledge.

## Project overview

Quiz CLI is a Node.js terminal application that loads category-based questions from a local JSON file and guides a player through an interactive quiz. Players choose a category and question count, answer numbered multiple-choice prompts, receive immediate feedback and explanations, and see a final score with a review of incorrect answers.

### Core capabilities

- Presents JavaScript Basics, Node.js Fundamentals, and General Programming question categories.
- Supports all available questions or, where available, three- and five-question sessions.
- Randomizes question order for each quiz session with the Fisher–Yates shuffle algorithm.
- Validates numeric menu selections and supports replaying after results are displayed.
- Shows ANSI-styled terminal output, a progress bar, score-based feedback, and incorrect-answer review.

### Technology stack

- **Runtime:** Node.js 18 or later
- **Language:** JavaScript using ECMAScript modules
- **Built-in Node.js APIs:** `node:fs/promises`, `node:path`, `node:url`, and `node:readline`
- **Question storage:** Local JSON (`data/questions.json`)
- **Dependencies:** No external runtime dependencies are declared

## Setup instructions

### Prerequisites

Install [Node.js](https://nodejs.org/) version 18.0.0 or newer. npm is included with standard Node.js installations.

### Install and run

```bash
git clone <repository-url>
cd test-app
npm install
npm start
```

`npm install` is safe even though the manifest declares no external packages; it prepares the project through npm. The application can also be started directly:

```bash
node index.js
```

### Environment configuration

No environment variables or `.env` file are required. Questions are read from `data/questions.json` relative to the application entry point.

### Test command

The package manifest provides the following command:

```bash
npm test
```

It runs Node.js’s built-in test runner (`node --test`). No test files are currently present in the repository.

## Usage examples

Start the quiz:

```bash
npm start
```

A typical interactive session follows this pattern:

```text
Choose a category:

  1. JavaScript Basics
  2. Node.js Fundamentals
  3. General Programming

Your choice (enter number): 1

How many questions?

  1. All questions
  2. 3 questions
  3. 5 questions

Your choice (enter number): 2
```

For each question, enter the displayed number for the desired answer. Invalid selections are rejected until a valid option is supplied. At the end of the session, answer `y` at the replay prompt to begin another quiz or any other response to exit.

```text
Would you like to play again? (y/n): y
```

## File structure

```text
.
├── data/
│   └── questions.json     # Categories, multiple-choice options, answers, and explanations
├── src/
│   ├── colors.js          # ANSI terminal styling helpers
│   ├── input.js           # Readline prompts, menu selection, confirmation, and pause helpers
│   └── quiz.js            # Quiz state, question flow, scoring, progress, and results
├── index.js               # Executable application entry point and main interaction loop
├── package.json           # Project metadata, Node.js requirement, and npm scripts
└── README.md              # Project documentation
```

## Other details

- The project is configured as an ES module package through `"type": "module"` in `package.json`; use `import`/`export` syntax for project modules.
- `index.js` derives its directory from `import.meta.url`, allowing it to locate `data/questions.json` without relying on the shell’s current working directory.
- The application reads its question bank asynchronously at startup. If the JSON file cannot be read or parsed, it reports the error and exits with status code `1`.
- A question object contains `question`, `options`, `answer`, and optional `explanation` fields. The `answer` value is a zero-based index into `options`.
- Terminal coloring uses ANSI escape codes implemented locally in `src/colors.js`; no color library is installed.
- Quiz results are maintained only in memory for the current session. The application does not persist scores or user answers.
