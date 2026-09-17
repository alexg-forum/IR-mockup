# IR-mockup

Support code for Forum's IR GTM engine. First piece: the document
ingestion layer that feeds the "IR Thought Leadership Report" Claude skill.

## The split

Two separate pieces, kept separate on purpose:

1. **The report skill** — already built, lives as a Claude skill inside the
   "IR Go To Market Project," not in this repo. It drafts the actual
   thought-leadership reports from whatever reference material is
   available to it. This part is working and stays a prompt, not code.
2. **The fetch-and-classify layer** — this repo, not yet built. Real code
   that pulls reference documents from wherever they actually live,
   classifies them, and lands them somewhere the skill can be pointed at.

Reasoning for the split: drafting logic is a fast-iterating prompt and
should stay one; fetching and classifying documents from an external
system is deep integration work, which is where it's worth being real
code instead of a prompt.

## Status

Not yet built. Still open, before writing the fetch code:

- **Data source.** Not decided yet. Candidates raised so far: SharePoint
  (already connected, and where the reference documents currently live),
  Azure Blob Storage / ADLS Gen2, and Microsoft Fabric. No Azure or Fabric
  access is provisioned yet.
- **Credentials.** None available yet for any of the above.
- **Where classified output lands.** Not decided yet — needs to be
  somewhere the skill can actually read from.

## Explicit non-goals for this step

- Not building an end-to-end "IR team asks, it fetches, then generates the
  report" pipeline. That would be a separate, bigger build (a real app
  calling Claude outside of chat) that hasn't been scoped.
- Not touching the report-drafting logic itself — that stays in the
  Claude skill.
