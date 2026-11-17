# Validation Checklist

Use this checklist before accepting an AI suggestion. The unchecked boxes are a reusable template, not a claim that validation has already happened.

- [ ] **Logic correctness:** trace representative inputs and verify business rules.
- [ ] **Security:** exclude secrets and personal data; review file writes and unsafe execution.
- [ ] **Edge cases:** test empty input, repeats, zero, negatives, NULL/blank, non-finite numbers, and malformed rows.
- [ ] **Input validation:** check headers, required fields, numeric rules, and timestamps.
- [ ] **Dependency assumptions:** confirm Python version and library availability; avoid needless packages.
- [ ] **Output correctness:** compare report rows and counts with known expectations; explain overlapping issue counts.
- [ ] **Exception handling:** distinguish a bad record from a fatal file/schema failure; return a useful exit code.
- [ ] **Maintainability:** use clear names and small functions; understand every line before presenting it.
- [ ] **SQL semantics:** examine join cardinality, duplicate business keys, NULLs, and reconciliation scope.
- [ ] **Evidence:** record the command, expected result, actual result, and limitations. Claim only checks actually run.
