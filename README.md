# ACB Medication Reviewer

Static GitHub Pages site for medication-list review with:
- per-drug ACB scoring where recognised,
- total ACB calculation,
- high cognitive-risk class flags,
- contextual STOPP-relevant prompts,
- misspelling suggestions,
- explicit user review warning.

## Files

- `acb-medication-reviewer.html` — main site file
- `data/stopp_relevant_medicines_uk.json` — contextual UK STOPP-relevant medicine dataset
- `.nojekyll` — recommended for GitHub Pages static hosting
- `docs/test-pack.md` — formal functional test pack
- `tests/sample-test-cases.json` — machine-readable regression cases

## GitHub Pages setup

1. Create a new public repository.
2. Upload `acb-medication-reviewer.html` and the `data` folder to the repository root.
3. Add an empty file named `.nojekyll` to the repository root.
4. In GitHub repository settings, enable Pages from the main branch root.
5. Open the published site URL after deployment.

## Notes

- STOPP prompts are contextual only and should not be presented as automatic breaches.
- Any output must be reviewed by the user.
