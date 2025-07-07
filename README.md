# Westminster Standards JSON

> **Disclaimer:** This README is vibe-coded. It aims for clarity and utility, not strict formality.

This package provides structured JSON data for the Westminster Standards, including the Westminster Larger Catechism and the Westminster Shorter Catechism. The data is intended for use in applications, research, or study tools that require programmatic access to these historic Christian documents.

## Contents

JSON files are organized by catechism (`larger` and `shorter`) and by the level of included references:
- Files with full questions, answers, and references
- Files with questions and answers, but no references
- Files mapping footnote numbers to Scripture references

### File Descriptions

#### Larger Catechism
- **no_references**: Questions and answers, with clause breakdowns and footnotes, but no Scripture references.
- **with_references**: Full questions and answers, with clause breakdowns, footnotes, and inline Scripture references for each clause.
- **references**: A mapping of footnote numbers to their corresponding Scripture references and texts.

#### Shorter Catechism
- **main**: Full questions and answers, with clause breakdowns, footnotes, and inline Scripture references for each clause.
- **no_references**: Questions and answers, with clause breakdowns and footnotes, but no Scripture references.
- **references**: A mapping of footnote numbers to their corresponding Scripture references and texts.

## Data Structure

### Catechism Files (with or without references)
Each catechism file is an array of objects, one per question:

```json
{
  "number": 1,
  "question": "What is the chief end of man?",
  "answer": "Man’s chief end is to glorify God, and to enjoy him forever.",
  "clauses": [
    {
      "text": "Man’s chief end is to glorify God,",
      "footnote": 1,
      "references": [
        {
          "reference": "Psalm 86",
          "text": "..."
        }
      ]
    },
    ...
  ]
}
```
- The `references` field is present only in files with references.
- In `*_no_references.json` files, the `references` field is omitted.

### References Files
Each references file is a mapping from footnote number to an array of Scripture references:

```json
{
  "1": [
    {
      "reference": "Psalm 86",
      "text": "..."
    },
    ...
  ],
  ...
}
```

## Usage

You can use these files in your application by importing or loading the JSON data as needed. Example in JavaScript/TypeScript:

```js
const catechism = require('./catechisms/shorter/westminster_shorter_catechism.json');
console.log(catechism[0].question); // "What is the chief end of man?"
```

## License

This data is provided for public use. Please credit the source if used in published works or applications. 