# AI-Assisted Development Notes

This standalone documentation project explains a responsible workflow for using AI in simulated enterprise transaction/data troubleshooting exercises. It is a beginner-to-intermediate learning example, not a claim of production, SAP, or professional support experience. AI helped create these examples; I am responsible for reviewing, running, and understanding code before presenting it as my work.

## Language Notes

This repository uses English as the primary technical language.

Short Traditional Chinese and conversational Malaysian Malay notes are included to support learning and interview revision.

Technical terms are intentionally kept in English where commonly used in the industry.

Traditional Chinese:
繁中備註主要用來快速理解和複習技術概念，部分常用技術詞會保留英文。

Bahasa Melayu:
Nota BM guna gaya yang biasa ditutur di Malaysia supaya lebih senang faham dan explain masa interview. Istilah technical yang biasa digunakan akan kekal dalam English.

See [AI-Assisted Development Learning Notes](LEARNING_NOTES.md) for concise revision of review, debugging, test cases, and responsible AI use.

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

AI is used to accelerate development, not replace understanding.

> 🇹🇼 繁中備註：AI 可以幫忙加快 coding，但不能取代理解。產生的 code 仍要自己 review、測試和驗證。
>
> 🇲🇾 BM: AI boleh cepatkan coding, tapi tak ganti pemahaman kita. Code yang AI bagi masih kena review, test dan verify sendiri.

## Quick Interview Revision

### Why review AI-generated code?

English: AI can invent APIs or make incorrect assumptions; review logic and verify unfamiliar behaviour before accepting a suggestion.

> 🇹🇼 繁中備註：AI 可能捏造 API 或做出錯誤假設；看起來合理的答案仍要確認邏輯和行為。
>
> 🇲🇾 BM: AI boleh reka API atau buat assumption salah. Walaupun nampak meyakinkan, kena semak logic dan verify behaviour dulu.

### What should tests cover?

English: Define expected results independently and test normal inputs, edge cases, malformed data, and failure behaviour.

> 🇹🇼 繁中備註：先自己定義預期結果，再測正常輸入、edge cases、錯誤格式和失敗情況。
>
> 🇲🇾 BM: Tentukan expected result sendiri, kemudian test input biasa, edge case, format salah dan apa jadi bila proses gagal.

### What does responsible use include?

English: Keep private data out of prompts, review dependencies and file access, and explain which checks were actually performed.

> 🇹🇼 繁中備註：不把私人資料放進 prompt；確認 dependency 和檔案操作，並誠實說明實際做過哪些驗證。
>
> 🇲🇾 BM: Jangan letak data peribadi dalam prompt. Semak dependency dan akses file, kemudian jelaskan check yang memang dah dibuat.

## Interview questions and answers

**How do you know AI-generated code is correct?** Review the assumptions, run it on known examples, check edge cases, and compare outputs with expectations that were not copied from the implementation.

**What should stay out of prompts?** Credentials, tokens, personal records, and confidential business data unless an explicitly approved environment and policy permit them. Use minimal synthetic examples here.

**What if an AI answer looks convincing but is wrong?** Reduce it to a reproducible case, check authoritative documentation when needed, correct the code, and retain the regression case.

**How do you describe AI use honestly?** Explain what AI suggested, what I reviewed and changed, and which checks I actually ran. Do not claim independent authorship or understanding I have not earned.
