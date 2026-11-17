# AI-Assisted Development Notes

## Overview

This standalone documentation project explains a responsible workflow for using AI in simulated enterprise transaction/data troubleshooting exercises. It is a beginner-to-intermediate learning example, not a claim of production, SAP, or professional support experience. AI helped create these examples; I am responsible for reviewing, running, and understanding code before presenting it as my work.

The AI-assisted development foundation of the Technical Interview Foundation Portfolio: a reusable review and validation workflow, rather than an AI application.

## Language Notes

This repository uses English as the primary technical language.

Short Traditional Chinese and conversational Malaysian Malay notes are included to support learning and interview revision.

Technical terms are intentionally kept in English where commonly used in the industry.

Traditional Chinese:
繁中備註主要用來快速理解和複習技術概念，部分常用技術詞會保留英文。

Bahasa Melayu:
Nota BM guna gaya yang biasa ditutur di Malaysia supaya lebih senang faham dan explain masa interview. Istilah technical yang biasa digunakan akan kekal dalam English.

See [AI-Assisted Development Learning Notes](LEARNING_NOTES.md) for concise revision of review, debugging, test cases, and responsible AI use.

## Why This Project Exists

Make the human review process visible: define a problem, question suggestions, reproduce mistakes, and check a correction. The aim is to explain how AI assistance can be used responsibly while retaining ownership of understanding and validation.

## Business / Technical Scenario

An AI suggestion for counting repeated transaction IDs contains an ordering bug. A small synthetic example exposes the incorrect assumption without requiring private data, a live model, or access to a production system.

## Skills Demonstrated

- Clear problem definition and context-rich technical prompts.
- Code review, debugging, and checking assumptions.
- Test-case design, edge-case reasoning, and input contracts.
- Security/dependency review and honest documentation of AI assistance.

## Architecture / Data Flow

```text
Problem + synthetic context
  -> AI suggestion (reviewed as a hypothesis)
  -> human code review -> normal/edge-case checks
  -> correction -> documented evidence and limitations
```

This is a documented development workflow, not a deployed AI service or an automated agent.

## How It Works

1. **Define the problem:** state the incorrect behaviour and desired result.
2. **Gather context:** collect synthetic sample inputs, relevant code, errors, and constraints.
3. **Ask for approaches:** request options and assumptions before accepting a solution.
4. **Review generated code:** trace the logic and check unfamiliar API behaviour.
5. **Test the implementation:** compare actual results with independently chosen expectations.
6. **Test edge cases:** include missing, malformed, duplicate, and boundary inputs.
7. **Validate security and data handling:** keep credentials and sensitive records out of prompts; check file access and output handling.
8. **Refactor where necessary:** simplify names and control flow without hiding the reasoning.
9. **Document the final solution:** explain behaviour, limits, and validation evidence.

### Appropriate uses

AI can help with brainstorming, boilerplate generation, explaining unfamiliar errors, debugging assistance, test case generation, refactoring ideas, and documentation. Suggestions are hypotheses until reviewed and tested. I do **not** blindly copy AI-generated code. I remain responsible for understanding the code and checking the result.

Start with the [debugging example](debugging-example.md), [prompt example](prompt-example.md), and [validation checklist](validation-checklist.md). The debugging example is deliberately constructed to demonstrate a common mistake; it is not a fabricated history of a real incident.

AI is used to accelerate development, not replace understanding.

> 繁中備註：AI 可以幫忙加快 coding，但不能取代理解。產生的 code 仍要自己 review、測試和驗證。
>
> 🇲🇾 BM: AI boleh cepatkan coding, tapi tak ganti pemahaman kita. Code yang AI bagi masih kena review, test dan verify sendiri.

> 繁中備註：先定義問題與預期結果，再 review、測試和驗證 AI 建議；AI 不能取代自己的理解。
>
> ENG: Define the problem and expected result, then review, test, and validate AI suggestions without outsourcing understanding.
>
> BM: Tentukan masalah dan expected result dulu, kemudian review, test dan verify cadangan AI. Kita masih kena faham sendiri.

## How to Run

No service, API key, or dependency installation is required to read this repository.

1. Read [prompt-example.md](prompt-example.md) for the problem and constraints.
2. Trace the flawed and corrected functions in [debugging-example.md](debugging-example.md).
3. Optionally copy only the corrected Python block into a Python 3 session and run its five assertions, without the `-O` option. This is a manual snippet check, not a test runner supplied by this repository.
4. Use [validation-checklist.md](validation-checklist.md) to review a suggestion before accepting it. Its unchecked boxes are a reusable template, not a completed audit.

> 繁中備註：先讀 prompt 和 debugging 範例；若要驗證，只複製 corrected Python 區塊執行，不要開啟 `-O`。
>
> ENG: Read the prompt and debugging example; optionally run only the corrected Python block without `-O`.
>
> BM: Baca prompt dan contoh debugging dulu. Kalau nak verify, run blok Python yang corrected sahaja tanpa `-O`.

## Example Investigation

For IDs `A, B, A`, expect one later duplicate occurrence. The flawed function adds each ID to a set before checking membership, returning 3. The correction checks membership before adding the ID and treats missing IDs separately. The example is deliberately constructed for teaching; it is not a claimed production incident or transcript of an actual model response.

> 繁中備註：`A, B, A` 應只有 1 次後續重複；錯誤版本因為先加入 set 才檢查，會回傳 3。
>
> ENG: For `A, B, A`, expect one later duplicate; the flawed check-after-add version returns three.
>
> BM: Untuk `A, B, A`, sepatutnya ada satu duplicate yang muncul kemudian. Versi yang tambah ke set sebelum check akan bagi tiga.

## Expected Results

The flawed function returns 3 for `A, B, A`; the corrected function returns 1. The five corrected assertions cover empty input, one unique ID, a repeat, three occurrences, and missing/blank IDs. Passing these examples checks the stated function contract, not every possible input or all generated code.

> 繁中備註：corrected 範例的 5 個 assertions 應通過；這只驗證指定範例，不代表所有 AI code 都正確。
>
> ENG: The five corrected assertions should pass; they validate these examples, not all AI-generated code.
>
> BM: Lima assertion dalam contoh corrected sepatutnya lulus. Ini check contoh tu sahaja, bukan bukti semua code AI betul.

## Troubleshooting / Root Cause Analysis

Define expected behaviour, reproduce the smallest failure, trace the operation order, correct the assumption, and retain a regression example. If the result still differs, check the input contract and runtime/library assumptions before expanding the prompt. Preserve a distinction between evidence and an AI-suggested explanation.

> 繁中備註：先用最小輸入重現問題，追蹤執行順序和假設，再保留能防止問題重現的測試例子。
>
> ENG: Reproduce the smallest failure, trace operation order and assumptions, and retain a regression example.
>
> BM: Reproduce masalah dengan input paling kecil, trace urutan dan assumption, kemudian simpan contoh untuk regression check.

## Limitations

- Documentation and a small Python example only; no live model calls or application backend.
- No structured-output framework, RAG pipeline, tool/function-calling implementation, or evaluation platform.
- The example assumes dictionary rows with string or None IDs; it is not a generic external-input validator.
- A checklist supports review but does not certify security or correctness.
- These examples do not establish professional AI engineering or production experience.

## Interview Talking Points

Explain which task AI can accelerate, which assumptions need review, and how expected results are chosen independently. Describe a concrete correction rather than claiming that AI guarantees correctness.

### Interview questions and answers

**How do you know AI-generated code is correct?** Review the assumptions, run it on known examples, check edge cases, and compare outputs with expectations that were not copied from the implementation.

**What should stay out of prompts?** Credentials, tokens, personal records, and confidential business data unless an explicitly approved environment and policy permit them. Use minimal synthetic examples here.

**What if an AI answer looks convincing but is wrong?** Reduce it to a reproducible case, check authoritative documentation when needed, correct the code, and retain the regression case.

**How do you describe AI use honestly?** Explain what AI suggested, what I reviewed and changed, and which checks I actually ran. Do not claim independent authorship or understanding I have not earned.

## Quick Interview Revision

### Why review AI-generated code?

English: AI can invent APIs or make incorrect assumptions; review logic and verify unfamiliar behaviour before accepting a suggestion.

> 繁中備註：AI 可能捏造 API 或做出錯誤假設；看起來合理的答案仍要確認邏輯和行為。
>
> 🇲🇾 BM: AI boleh reka API atau buat assumption salah. Walaupun nampak meyakinkan, kena semak logic dan verify behaviour dulu.

### What should tests cover?

English: Define expected results independently and test normal inputs, edge cases, malformed data, and failure behaviour.

> 繁中備註：先自己定義預期結果，再測正常輸入、edge cases、錯誤格式和失敗情況。
>
> 🇲🇾 BM: Tentukan expected result sendiri, kemudian test input biasa, edge case, format salah dan apa jadi bila proses gagal.

### What does responsible use include?

English: Keep private data out of prompts, review dependencies and file access, and explain which checks were actually performed.

> 繁中備註：不把私人資料放進 prompt；確認 dependency 和檔案操作，並誠實說明實際做過哪些驗證。
>
> 🇲🇾 BM: Jangan letak data peribadi dalam prompt. Semak dependency dan akses file, kemudian jelaskan check yang memang dah dibuat.

## Role Relevance

These learning examples demonstrate review habits and communication, not delivery of a production AI product.

| Relevant area | Transferable practice demonstrated |
| --- | --- |
| Software Development | Review generated code, explain assumptions, and test a small correction. |
| AI-assisted Engineering | Use AI suggestions with explicit human validation and ownership. |
| Automation | Define repeatable checks before automating a manual task. |
| AI / Data roles | Question data assumptions and distinguish tested behaviour from model claims. |
| Technical Consulting | Communicate scope, uncertainty, validation evidence, and responsible use. |
| Application Development | Practise input contracts and failure reasoning; no application is deployed. |

## Future Improvements

Planned possibilities only; none of the following is implemented:

- Structured output validation against explicit schemas.
- API-based AI integration with controlled inputs and failure handling.
- Retrieval-augmented generation (RAG) over approved reference material.
- Tool/function calling concepts with bounded permissions.
- Evaluation and regression testing using known expected outcomes.
- Prompt injection and other security considerations with adversarial examples.

Start with a small, measurable contract before introducing additional integrations.

## Learning Notes

See [LEARNING_NOTES.md](LEARNING_NOTES.md) for concise English-led explanations with Traditional Chinese and conversational Malaysian Malay revision. AI accelerates development; it does not replace understanding.
