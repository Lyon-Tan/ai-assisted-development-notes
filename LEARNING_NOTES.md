# AI-Assisted Development Learning Notes

Short revision notes for the simulated examples in this repository. The [README](README.md) remains the main professional explanation.

## AI-assisted coding and responsible AI use

AI is used to accelerate development, not replace understanding. It can suggest approaches, boilerplate, tests, and documentation; the developer remains responsible for the result.

> 🇹🇼 繁中備註：AI 可以加快 coding、產生 test case 和整理文件，但不能取代理解。最後仍要自己看懂、測試和驗證。
>
> 🇲🇾 BM: AI boleh cepatkan coding, buat test case dan bantu dokumentasi. Tapi kita masih kena faham, test dan verify sendiri; AI tak ganti pemahaman kita.

## Hallucination and incorrect assumptions

A hallucination may be a convincing but invented API or explanation. An incorrect assumption may use a real API with the wrong business rule. Verify unfamiliar behaviour and state the expected result before accepting generated code.

> 🇹🇼 繁中備註：hallucination 可能是看起來合理、實際不存在的 API 或說法；錯誤假設也可能是 API 用對了，卻套錯業務規則。兩種都要驗證。
>
> 🇲🇾 BM: Hallucination boleh jadi API atau penerangan yang nampak betul tapi sebenarnya direka. Assumption salah pula boleh guna API sebenar dengan business rule yang salah. Dua-dua kena semak.

## Code review

Review AI-generated code for logic, assumptions, failure behaviour, and readability. Trace a small example line by line; convincing formatting does not prove correctness.

> 🇹🇼 繁中備註：code review 要看邏輯、假設和出錯時的行為。用小例子逐步追蹤，不要因為 code 看起來整齊就認定正確。
>
> 🇲🇾 BM: Masa code review, semak logic, assumption dan apa jadi kalau input salah. Trace satu contoh kecil; code nampak kemas tak bermaksud mesti betul.

## Debugging

Reproduce the failure, isolate the smallest cause, fix it, and rerun the check. In the [debugging example](debugging-example.md), checking set membership after adding the ID incorrectly counts every row as a duplicate.

> 🇹🇼 繁中備註：debugging 先重現問題，再找出最小原因。這個例子先把 ID 加進 set 才檢查，會讓每一筆都被算成重複。
>
> 🇲🇾 BM: Untuk debugging, reproduce masalah dulu, kemudian cari punca kecil yang boleh diuji. Dalam contoh ni, ID dimasukkan ke set sebelum check, jadi semua row dikira duplicate.

## Test cases and edge cases

A test case states input and an independently chosen expected result. Edge cases include empty input, blank IDs, three repeats, zero, malformed amounts, and non-finite numbers. Passing only a normal example is insufficient.

> 🇹🇼 繁中備註：test case 要先定義輸入和預期結果。edge cases 包括空資料、空白 ID、多次重複和特殊數值；正常範例通過還不夠。
>
> 🇲🇾 BM: Test case kena ada input dan expected result yang ditentukan sendiri. Cuba edge case macam input kosong, ID blank, banyak repeat dan amount pelik; satu contoh biasa lulus belum cukup.

## Input validation and dependency assumptions

Validate headers, required fields, types, and business rules. Confirm the runtime version and required libraries; do not assume an AI-suggested function exists or a package is already installed.

> 🇹🇼 繁中備註：input validation 要查欄位、型別和規則；dependency assumptions 也要確認，包括版本和套件是否存在，不能只相信 AI 的建議。
>
> 🇲🇾 BM: Check header, field wajib, type dan rules input. Semak juga versi runtime dan library; jangan anggap function yang AI cadang memang ada atau package tu dah install.

## Security review

Review prompts and code for exposed credentials, private data, unsafe file writes, and unnecessary dependencies. Use minimal synthetic examples here and keep real secrets out of prompts and Git.

> 🇹🇼 繁中備註：security review 要查機密資料、危險寫檔和不必要的 dependency。這裡用模擬資料；真實 credentials 不要放進 prompt 或 Git。
>
> 🇲🇾 BM: Security review kena tengok credentials, data peribadi, file write yang berisiko dan dependency yang tak perlu. Guna data simulasi; jangan letak secret sebenar dalam prompt atau Git.
