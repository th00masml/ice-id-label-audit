# ICE-ID within-wave label audit

Audit of the within-wave positives of ICE-ID (Carvalho et al., arXiv:2506.13792)
and of what their noise does to method evaluation. Start with `NOTE-ICE-ID.md`.

## Contents

- `NOTE-ICE-ID.md`: the note.
- `audit/PROTOCOL.md` to `PROTOCOL4.md`: pre-registrations, each written before
  its sample was inspected or its methods scored.
- `audit/RESULTS.md` to `RESULTS4.md`: results for each protocol.
- `audit/audit_sample.jsonl`, `audit/audit2_sample.jsonl`: the 150 audited pairs
  with all evidence, the rule verdict and, where read by hand, the manual verdict
  and its reason. Person IDs and row IDs refer to ICE-ID `people.csv`.
- Code: `run_audit.py` (audit 1), `run_audit2.py` (audit 2), `noise_effect.py`
  (methods vs labels), `splink_within_wave.py` (Splink and the kin-ID check),
  `noise_effect_extra.py` (paired leads, linked shares).
- Cached outputs (`*.json`, `*.npz`) so the numbers can be checked without rerunning.

## Reproduce

    pip install -r requirements.txt
    # download the data: see data/raw/README.md
    python audit/run_audit.py            # audit 1 rules, ~2 min
    python audit/run_audit2.py           # audit 2 rules, ~2 min
    python audit/noise_effect.py         # protocol 3, ~4 min
    python audit/noise_effect_extra.py
    python audit/splink_within_wave.py   # protocol 4, ~10 min

Note: `run_audit.py` and `run_audit2.py` rewrite the sample files from the rules
alone; the manual verdicts in the shipped `*_sample.jsonl` were added afterwards
(see RESULTS.md, RESULTS2.md). Keep a copy before rerunning.

Data: ICE-ID, CC-BY 4.0. Not redistributed here.
