# Cognitive Risk Dashboard v2

A static GitHub Pages dashboard with broader UK medication recognition and separate evidence badges for ACB, AEC, Beers, and local rules.

## Upload structure

```text
your-repository/
├── index.html
├── .nojekyll
├── README.md
└── data/
    ├── acb-dataset.json
    ├── aec-dataset.json
    ├── beers-rules.json
    ├── local-rules.json
    ├── uk-products.json
    └── medication-schema.json
```

## What is new in v2

- Multiple JSON datasets instead of one combined file.
- Separate evidence badges in the user interface.
- Better UK product recognition, including selected combination products and aliases.
- CSV export and printable review sheet.

## How to publish on GitHub Pages

1. Create a GitHub repository.
2. Upload all files above while preserving the `data/` folder.
3. Open **Settings > Pages**.
4. Choose **Deploy from a branch**.
5. Select `main` and `/ (root)`.
6. Save and wait for the live site URL.

## How to add a medicine

Add a medication object to the most appropriate JSON file in `data/`.

Example:

```json
{
  "name": "example-medicine",
  "aliases": ["example-brand"],
  "scales": {"acb": {"score": 1}},
  "categories": ["local:cns depressant"],
  "badges": ["ACB", "Local rule"],
  "notes": "Example entry.",
  "ingredients": []
}
```

## Important note

This is a review support tool. Any output should be reviewed by the user against the medication record, dose, formulation, duration, co-morbidity, frailty, and current guidance.


## v3 data expansion pack

This package now includes a broader UK-focused set of generic names, brand names, and product aliases across anticholinergic medicines, opioids, benzodiazepines, z-drugs, gabapentinoids, sedating antidepressants, sedating antihistamines, and selected antipsychotics.


## v4 older-adult psychiatry and dementia expansion

This pack further expands recognition for dementia treatments, antipsychotics used in BPSD review, hypnotics, sedating antihistamines, tricyclics, SSRIs with anticholinergic relevance, and UK brand aliases commonly encountered in older-adult psychiatry and dementia practice.
