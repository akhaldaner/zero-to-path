# Dispatcher State

generated_by: dispatcher_ai
generated_at: {{datetime}}
purpose: handover_snapshot
source_of_truth: {{subject}}_map_of_content.md
warning: not a status registry; maps override this file

## Last response

DISPATCHER_RESPONSE
date: {{date}}
confirm: []
needs: []
flags: []
next: []
map_rows:
| artifact_id | Topic | Level | Status | Proposed | Confirmed | Evidence |
|---|---|---|---|---|---|---|

## Handoff

| kind | subject | ref | state | next action |
|---|---|---|---|---|

Allowed `kind` values:

| kind | Meaning |
|---|---|
| `focus` | Current working topic or artifact |
| `debt` | Unclosed practicum or missed block |
| `petition` | Petition waiting for dispatcher confirmation |
| `confirmed` | Confirmed status already inserted into a map |
| `flag` | Risk, imbalance, sequence violation |
| `recall` | Planned interval repetition, especially for language or skill maintenance |