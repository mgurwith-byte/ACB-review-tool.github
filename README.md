# Cognitive Risk Dashboard v3

Static GitHub Pages app for pasted medication-list review.

## Add these files

Place these in `data/`:
- `acb-dataset.json`
- `aec-dataset.json`
- `local-rules.json`
- `uk-products.json`
- `stopp_relevant_medicines_uk.json`

## Behaviour

The app now uses a three-state matching model:
- Matched and flagged
- Matched, no current flag
- No flag from current reference set

This wording is intended to avoid implying that an unmatched medicine is invalid or nonexistent.

## Hosting

Upload `index.html` and the `data/` folder to a GitHub repository and enable GitHub Pages.
