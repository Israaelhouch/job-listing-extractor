# Data

## What's here

Five anonymized sample listings in `sample-listings/`, chosen to show the range
of shapes the extractor has to handle:

| File | Language | Why it's here |
|---|---|---|
| `01-fr-salary-stated.txt` | French | Salary in a labelled field: `Salaire proposé 1500 - 2500 TND / Mois` |
| `02-fr-salary-absent.txt` | French | No salary anywhere. Also posted by an agency on behalf of an unnamed client. |
| `03-fr-salary-confidential.txt` | French | `Rémunération proposée : Confidentiel` — the field exists but refuses a value |
| `04-en-salary-annual-usd.txt` | English | Annual salary in USD, buried in prose. Everything else is monthly TND. |
| `05-ar-synthetic.txt` | Arabic | **AI-GENERATED, not a real listing.** See "Arabic" below. |

## The full dataset

26 rows total, held in a private Google Sheet and **not published here**:

- 22 real listings collected by hand
- 4 AI-generated Arabic listings, flagged `synthetic` in a `source` column

Of the 22 real listings:

- 7 state an actual salary figure
- 4 state `Rémunération proposée : Confidentiel`
- the rest state no salary at all

Languages: roughly 16 French, 6 English, 0 Arabic.

The full set is not in this repo because the listings are the hiring companies'
own text, republished from job boards whose terms don't permit redistribution.
Five short anonymized samples are enough to show what the input looks like.

**Sources:** TODO — list the job boards you collected from.

## What was removed

- Phone numbers → replaced with `[PHONE REMOVED]`
- Email addresses → replaced with `[EMAIL REMOVED]`

Company names were **kept**. They're public, and `company` is one of the fields
being extracted — removing them would make the samples useless as examples.

Nothing else was edited. Typos, inconsistent formatting, and duplicated
information were all left in place: the messiness is the thing being tested.

## Arabic

Arabic was in the original scope. It was dropped as a *measured* language after
collection, because Arabic postings turned out to be rare on the Tunisian job
boards sampled — almost everything is French, some English.

Rather than drop it silently, 4 Arabic listings were generated with an AI model
and marked `synthetic` in the dataset.

**These are not evidence.** They were written by a language model, so a language
model reads them unusually easily. Any accuracy figure computed on them measures
model-to-model agreement, not real-world Arabic performance. They are reported
separately from headline results, never merged into an overall number, and
should be replaced if real Arabic listings are found.

## Known limitations

- 7 salary-stating listings means salary accuracy moves in roughly 14-point
  steps. Small changes between prompt versions are noise, not signal.
- All listings were collected on a single day, so any seasonal or
  sector-specific skew in what was being advertised is baked in.
