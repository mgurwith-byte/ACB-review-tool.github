# Cognitive Burden Medication Review

Static GitHub Pages app for reviewing pasted medication lists for anticholinergic burden and other cognition-relevant medicines in older adults.

## What the app does

The current version of the app:
- calculates Anticholinergic Cognitive Burden (ACB) scores from the loaded ACB dataset,
- shows the total cumulative ACB score,
- separates strongly anticholinergic medicines from lower-scoring medicines that contribute additively,
- flags benzodiazepines, z-drugs, other sedatives, and opioids as cognition / alertness / falls-risk medicines even when ACB scoring is low,
- recognises some medicines even when dose or formulation text is included,
- provides spelling suggestions for some unrecognised entries,
- keeps optional STOPP prompts in a collapsible section at the bottom,
- generates report-ready GP text,
- adds an MDT prompt when psychotropic medication is present, so that psychotropics can be discussed in the MDT meeting before asking the GP to take action.

## Important clinical logic

This is a review aid, not a prescribing decision tool.

The app deliberately separates several concepts:
- **Anticholinergic burden**: based on medicines present in the loaded ACB dataset.
- **Other cognitive-risk medicines**: benzodiazepines, z-drugs, sedatives, antipsychotics, tricyclics, sedating antidepressants, gabapentinoids, and opioids may still be clinically important even if they do not drive a high ACB total.
- **STOPP prompts**: shown as contextual review prompts only; they are not intended to declare a definite STOPP breach without clinical context such as indication, dose, duration, renal function, diagnosis, and falls risk.
- **Psychotropic medicines**: where psychotropics are part of the flagged output, the generated GP paragraph adds wording that they should be discussed in the MDT meeting before asking the GP to take action.

## GP output behaviour

The GP paragraph is designed to distinguish between different scenarios:
- strong ACB-positive medicines,
- raised cumulative ACB from multiple lower-scoring medicines,
- sedative / opioid cognitive-risk medicines even when ACB-positive medicines are absent,
- possible misspellings,
- unrecognised medicines,
- genuinely negative recognised results.

This is intended to avoid misleading wording such as saying there are no medicines of concern when a benzodiazepine or other cognition-relevant psychotropic has actually been detected.

## Files required

Place these in the repository root:
- `index.html`
- `.nojekyll`
- `README.md`

Place these in `data/`:
- `acb-dataset.json`
- `recognised-unscored.json`
- `stopp_relevant_medicines_uk.json`

## Expected data files

### `acb-dataset.json`
Primary medicine list used for ACB scoring. Entries should include a medicine name, aliases where available, and either a top-level score or an ACB score inside a `scales.acb.score` structure.

### `recognised-unscored.json`
Recognised UK medicines that the app should match even where no ACB score is currently assigned. This reduces false “not recognised” outputs.

### `stopp_relevant_medicines_uk.json`
Contextual STOPP review prompts for medicines or classes where further review may be appropriate.

## User workflow

1. Paste one medicine per line, or paste a comma-separated list.
2. Select **Analyse medicines**.
3. Review the summary bar, result cards, and optional STOPP prompts.
4. Copy the generated GP/report paragraph if needed.

## Matching behaviour

The app supports:
- generic names,
- some brand names and aliases,
- partial normalisation of formulations and dose text such as `donepezil 10 mg` or patch wording,
- limited spelling suggestions using approximate matching.

If a medicine is not recognised, the app now says it was not recognised in the current dataset rather than implying the medicine does not exist.

## Interface notes

- Light and dark mode are supported.
- The app is a static client-side HTML file with JavaScript and no server-side processing.
- The copy button copies the generated GP paragraph only.
- STOPP prompts are hidden by default inside a collapsible section.

## Hosting on GitHub Pages

1. Create a repository.
2. Upload `index.html`, `.nojekyll`, `README.md`, and the `data/` folder.
3. In GitHub, open **Settings -> Pages**.
4. Set the source to deploy from the main branch root.
5. Save and wait for publication.

## Limitations

- Recognition depends on the medicines present in the local JSON files.
- A medicine not recognised by the app may still be clinically important.
- A medicine not listed with an ACB score is not necessarily free of cognitive or sedative burden.
- STOPP prompts are contextual and should not be used without clinical review.
- The generated text supports review and communication, but should not replace prescribing judgement or MDT discussion.
