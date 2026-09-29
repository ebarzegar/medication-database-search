# Medication Database Search System

A command-line medication lookup project built with **UNIX Bash**. It searches a fixed-width text database by medication code and displays the matching generic name or dose.

## Why this project

Medication information must be retrieved from the correct field: a code appearing in a dose, name, or inventory column must not count as a medication-code match. This project focuses on precise field extraction, repeatable searches, and user input validation. It is an educational demonstration, **not a clinical decision-support tool**.

## Features

- Searches only the medication-code column, including case-sensitive partial matches.
- Reports every matching record rather than stopping at the first match.
- Lets the user choose generic name or dose for the results.
- Re-prompts after invalid G/D selections and supports repeated searches.
- Handles missing matches, blank search input, and the `ZZZ` exit command.

## Data layout

Each line is a fixed-width record (positions are 1-based):

| Field | Columns | Width |
| --- | --- | ---: |
| Category | 1–4 | 4 |
| Dose | 5–18 | 14 |
| Medication code | 19–26 | 8 |
| Generic name | 27–39 | 13 |
| On-hand inventory | 40–46 | 7 |

The included `sample-data.txt` contains **synthetic demonstration records**, not patient information or the university's supplied dataset.

## Run it

On a Bash-enabled system:

```bash
chmod +x search
./search
```

To use a different file with the same fixed-width layout:

```bash
./search path/to/your-data.txt
```

Enter a code or partial code, then choose `G` for generic name or `D` for dose. Enter uppercase `ZZZ` at the code prompt to quit.

## Implementation

The program reads records without altering the input file, extracts the medication-code substring, and collects all matches in a Bash array. It then validates the requested output type and extracts the corresponding fixed-width field. The original coursework solution used a university-specific data path; this portfolio adaptation accepts an optional path and defaults to the synthetic sample file.

## Project origin and limitations

Adapted from an individual CCPS 393 UNIX programming assignment at Toronto Metropolitan University. This portfolio version includes portability and input-handling improvements. The data and output are demonstrations only; do not use this program for prescribing, dispensing, or clinical decisions.
