# 四年級上學期 期中考複習（康軒版）

網站：https://kckuo-ai.github.io/midterm-4a/

| 科目 | 期中考範圍 | 重點整理 | 練習卷 |
|---|---|---|---|
| 自然 | 第一單元 地表的靜與動、第二單元 水生生物與環境（p.10–71），可切換全冊一到四單元 | [science/notes.html](science/notes.html) | [science/quiz.html](science/quiz.html) |
| 社會 | 第一單元 家鄉的自然環境、第二單元 家鄉的傳統住屋與器物（p.6–51），可切換全冊一到五單元 | [social/notes.html](social/notes.html) | [social/quiz.html](social/quiz.html) |

## 檔案結構

```
index.html              首頁
assets/style.css        共用樣式（與 midterm-3a 相同）
assets/quiz.js          共用作答程式（與 midterm-3a 相同）
assets/notes-4a.css     四上重點頁的額外樣式（階層圖、手機版表格卡片、圖的顏色）
science/notes.html      自然 重點整理
science/quiz.html       自然 練習卷
science/quiz-data.js    自然 題庫
social/…                社會（同上）
science.html、social.html  舊網址，會自動轉到新的重點整理頁
```

## 範圍切換

- 頁面上方的「期中考（一、二單元）／全冊」按鈕會記在瀏覽器裡：自然用 `sci4a-scope`，社會用 `soc4a-scope`，重點整理和練習卷共用同一個設定。
- 重點整理頁：期中不考的內容用 `<div class="later">` 包起來；目錄連結和表格列也可以加 `class="later"`。
- 練習卷：題目加 `later: true` 代表不在期中考範圍，只在「全冊」出現；整個大題都不考時，在大題加 `later: true`。

## 新增題目

在 `quiz-data.js` 對應大題的 `items` 加一筆即可：

| 題型 | `type` | 寫法 |
|---|---|---|
| 是非 | `tf` | `{ q: '題目', a: '○', exp: '解析', page: 'p.20' }`（答案是 `○` 或 `✕`） |
| 選擇 | `mc` | `{ q: '題目', opts: ['甲', '乙', '丙', '丁'], a: 2, exp: '', page: 'p.20' }`（`a` 從 1 開始；選項前不用寫 ①②③④） |
| 活用（多選） | `multi` | `{ q: '題目', opts: [...], a: [1, 3], exp: '', page: '' }` |
| 配合 | `match` | 大題要有 `labels` 和 `shared`；題目寫 `{ q: '…', a: 'B' }` |
| 勾選 | `check` | `{ scene: '情境一：…', q: '…', a: '✓' }`（答案是 `✓` 或 `✕`；`scene` 只寫在每個情境的第一題） |

其他欄位：`u` 是單元標籤（例如 `'第三單元'`、`'課堂補充'`），只在「全冊」題目旁邊顯示；`page` 是課本頁碼，交卷後顯示在解析後面。
