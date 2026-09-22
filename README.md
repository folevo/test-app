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
