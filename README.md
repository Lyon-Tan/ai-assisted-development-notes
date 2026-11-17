# AI-Assisted Development Notes

This standalone documentation project explains a responsible workflow for using AI in simulated enterprise transaction/data troubleshooting exercises. It is a beginner-to-intermediate learning example, not a claim of production, SAP, or professional support experience. AI helped create these examples; I am responsible for reviewing, running, and understanding code before presenting it as my work.

## Workflow

1. **Define the problem:** state the incorrect behaviour and desired result.
2. **Gather context:** collect synthetic sample inputs, relevant code, errors, and constraints.
3. **Ask for approaches:** request options and assumptions before accepting a solution.
4. **Review generated code:** trace the logic and check unfamiliar API behaviour.
5. **Test the implementation:** compare actual results with independently chosen expectations.
6. **Test edge cases:** include missing, malformed, duplicate, and boundary inputs.
7. **Validate security and data handling:** keep credentials and sensitive records out of prompts; check file access and output handling.
8. **Refactor where necessary:** simplify names and control flow without hiding the reasoning.
9. **Document the final solution:** explain behaviour, limits, and validation evidence.

## Appropriate uses

AI can help with brainstorming, boilerplate generation, explaining unfamiliar errors, debugging assistance, test case generation, refactoring ideas, and documentation. Suggestions are hypotheses until reviewed and tested. I do **not** blindly copy AI-generated code. I remain responsible for understanding the code and checking the result.

Start with the [debugging example](debugging-example.md), [prompt example](prompt-example.md), and [validation checklist](validation-checklist.md). The debugging example is deliberately constructed to demonstrate a common mistake; it is not a fabricated history of a real incident.

## Interview questions and answers

**How do you know AI-generated code is correct?** Review the assumptions, run it on known examples, check edge cases, and compare outputs with expectations that were not copied from the implementation.

**What should stay out of prompts?** Credentials, tokens, personal records, and confidential business data unless an explicitly approved environment and policy permit them. Use minimal synthetic examples here.

**What if an AI answer looks convincing but is wrong?** Reduce it to a reproducible case, check authoritative documentation when needed, correct the code, and retain the regression case.

**How do you describe AI use honestly?** Explain what AI suggested, what I reviewed and changed, and which checks I actually ran. Do not claim independent authorship or understanding I have not earned.
