# 多益考前複習

多益 TOEIC L&R 考前練習網站：Part 2 應答問題（瀏覽器語音朗讀）、Part 5 句子填空、Part 6 段落填空、Part 7 閱讀理解、高頻單字卡和錯題本，每題附中文解析。題目裡的英文單字點一下就會跳出中文、詞性和說明，可以收進生字本再用單字卡複習。手機優先、純靜態（單一 HTML，CSS 和 JS 都寫在檔內），不需要建置工具或後端。

網址：<https://kungmengchien.uk/toeic-review/>

> 本站題目為自編練習題，非 ETS 官方試題。TOEIC 為 ETS 的註冊商標，本站與 ETS 無關。

## 檔案

| 檔案 | 用途 |
|---|---|
| `index.html` | 整個網站。第一個 `<script>` 是點字查詢的詞庫（`DICT`、`PHRASES`）；第二個 `<script>` 最上面是題庫（`P5`、`P2`、`P6`、`P7`、`VOCAB` 常數） |
| `favicon.svg`、`apple-touch-icon.png` | 瀏覽器分頁與「加到主畫面」圖示 |
| `og.png` | 分享連結時的預覽圖（1200×630）；換圖時要改 `index.html` 裡 `og.png?v=` 的版本 |
| `notes/handoff.md` | 原始交接文件（含新增題目的格式），**只留在本機，不上傳**（見 `.gitignore`） |

題目的 `id` 不要改：錯題本用 id 記錄，改了會讓使用者已存的錯題對不上。

練習紀錄和生字本只存在使用者自己的瀏覽器（localStorage key `toeic-review-v1`），不收集任何資料。

## 點單字查中文

- 可以點的地方：Part 5 題目、Part 6/7 文章和題目、Part 2 文字稿、答完題後的選項，以及單字卡背面的例句。作答前的選項不能點，點了就是作答。
- 詞庫在第一個 `<script>`：`DICT` 的鍵是原形（小寫），值是 `[詞性, 中文, 說明, 顯示寫法（可省略）]`。複數、過去式、-ing、比較級會自動對回原形；不規則變化寫在 `FORMS`；片語寫在 `PHRASES`，其他寫法寫在 `PH_ALIAS`；人名、地名寫在 `NAMES`，這些字不能點。
- 生字本的鍵就是詞庫的鍵，改名或刪掉詞條會讓使用者存過的字消失，所以不要改既有的鍵。
- 新增題目後，在瀏覽器主控台執行 `dictMissing()`，會列出還沒收進詞庫的字。沒收錄的字點了會顯示「還沒收進詞庫」和 Yahoo 字典的連結。

## 本機預覽

```powershell
python -m http.server 8920 --bind 127.0.0.1 --directory D:/Claude/Claude-work/toeic-review
```

然後打開 <http://127.0.0.1:8920/>。
