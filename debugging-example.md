# Debugging an AI Suggestion

## Problem

Count repeated transaction IDs in a CSV export. The following is a deliberately flawed example of a plausible AI suggestion:

```python
def count_duplicates(rows):
    seen = set()
    duplicates = 0
    for row in rows:
        transaction_id = row["transaction_id"]
        seen.add(transaction_id)
        if transaction_id in seen:
            duplicates += 1
    return duplicates
```

The ID is added before membership is checked, so every row is counted. It also treats missing IDs as valid identifiers.

## Reproduce and isolate

For `A, B, A`, the expected count of later occurrences is 1. The flawed function returns 3. Tracing the set after the first `add()` reveals the ordering bug. A blank ID needs a separate validation issue, not duplicate classification.

## Corrected version

```python
def count_duplicates(rows):
    seen = set()
    duplicates = 0
    for row in rows:
        transaction_id = (row.get("transaction_id") or "").strip()
        if not transaction_id:
            continue
        if transaction_id in seen:
            duplicates += 1
        seen.add(transaction_id)
    return duplicates


assert count_duplicates([]) == 0
assert count_duplicates([{"transaction_id": "A"}]) == 0
assert count_duplicates([{"transaction_id": "A"}, {"transaction_id": "B"},
                         {"transaction_id": "A"}]) == 1
assert count_duplicates([{"transaction_id": "A"}] * 3) == 2
assert count_duplicates([{}, {"transaction_id": " "}]) == 0
```

This assumes rows are dictionaries and IDs are strings or None, as they are in a CSV reader. An arbitrary external API would need a stronger input contract.

## Validate and prevent

Check empty input, unique IDs, repeated IDs, three occurrences, and missing IDs. The metric is later occurrences, not the number of distinct duplicated IDs or the total number of rows in duplicate groups. In a complete CSV validator, report missing IDs separately from duplicate detection. Preserve these cases when changing the logic.

Another poor assumption is that successful numeric parsing proves a financial amount is valid: `Decimal('NaN')` and `Decimal('Infinity')` parse successfully. Check `is_finite()` before comparing amounts.
