# Unit 7｜串接 Meta，讓 Maya 直接幫你發文

> 這個單元完成後，Maya 排好的貼文行事曆可以一鍵發到你的 Facebook 粉絲專頁和 Instagram。
<p align="left">

  <img src="../images/metasteup.png" alt="Hello Nora AI 行銷團隊" width="600">

</p>
> 🔍 **這跟 Jack 那個「看廣告數據」不是同一件事**：Jack 用的是 Meta 官方免費 MCP（貼個網址、登入就好，只負責「讀數據」）；**這個單元是「發文」**——要自己建一個 App、拿 Token，步驟比較多。兩件事各走各的，別搞混。

---

## 你會解鎖的能力

| 功能 | 說明 |
|------|------|
| **FB 自動排程 ／ IG 即時發** | Maya 排完行事曆：**FB** 可指定未來時間自動排程（設好就走，電腦關了 Meta 也會幫你發）；**IG 只能「現在發」**——IG 的 API 不支援「排到未來自動發」，要定時自動發只有 FB 做得到 |
| **留言回覆（半自動）** | 設定回覆規則，你在線時 Maya 幫你一次回完留言。⚠️ 這是半自動、不是 24 小時無人值守——電腦關了就不會跑，要全天自動回得用 ManyChat／Meta 內建工具 |
| **競品廣告分析** | 查任意品牌在 Meta 廣告庫的在投廣告，拿來做競品研究 |
| **過往貼文表現分析** | 拉出你自己的貼文數據（觸及、互動率），讓 Maya 分析哪種內容最有效 |

> ⚠️ **前置需求：**
> - Claude Pro 訂閱（約 US$20/月，實際以官方公告為準）
> - **Facebook 粉絲專頁**（不支援個人帳號）
> - **你必須是這個粉絲專頁的「管理員」**，也會是等一下自己建的那個 App 的管理員（兩個都是你本人，沒問題）
> - Instagram **商業帳號**，並連結到上面的粉絲專頁
>
> 💡 **不用送 Meta 審核、不用上架 App**：你建的 App 一直留在「開發模式」就好。開發模式下，這個 App 只能操作「**你自己有管理員權限的粉專**」——剛好就是你要發文的那個，所以完全夠用，不需要走 App Review 那套繁瑣流程。

> ⚠️ **先講安全：自動化要「像真人」，別像機器人。** 透過 API 自動發文、自動回覆很方便，但 Meta 會盯「異常行為」——短時間狂發、罐頭式秒回大量留言、頻率高到不像人，都可能被判定為濫用，輕則限流、重則**封鎖粉專或停用 App**。安全用法：
> - 發文**排程分散**，別一次灌爆、別幾秒一篇
> - 自動回覆**設少數幾個情境**（例如問價格才回），不要每則留言都自動回
> - 重要的、對外的內容，**發出前讓 Maya 先給你確認**，不要全自動放生
> - 這是你的主要資產，寧可慢一點、穩一點

---

## Step 1：建立 Meta 開發者帳號

1. 前往 **[developers.facebook.com](https://developers.facebook.com)**
2. 右上角點「開始使用」→ 用你的 Facebook 帳號登入
3. 完成開發者身份驗證（手機號碼驗證即可）

完成後你會進入 Meta for Developers 主控台。

---

## Step 2：建立一個 App

1. 點「我的應用程式」→「建立應用程式」
2. 「使用案例」步驟：點左側「**內容管理（5）**」，勾選這兩個：
   - ✅ **管理粉絲專頁的所有內容**（FB 發文、排程、互動數據）
   - ✅ **管理 Instagram 的訊息和內容**（IG 發文、回覆留言）
3. 填寫：
   - App 名稱：隨便取，例如「我的行銷助手」
   - App 聯絡 Email：填你的 email
4. 點「建立應用程式」

> 💡 **為什麼要選使用案例？** 選了之後，App 才會有「管理粉絲專頁所有內容」這個使用案例，後面 Step 3 才能啟用 `pages_manage_posts` 權限。

---

## Step 3：取得 Facebook 粉絲專頁的 Access Token

這是最關鍵的一步。Token 就是讓 Claude 代你操作粉絲專頁的「鑰匙」。

### 3-1：開啟 Graph API Explorer

1. 左側選單 → 「工具」→「**Graph API Explorer**」
2. 右上角「Meta App」選你剛建立的 App

### 3-2：啟用 pages_manage_posts 權限（必做！）

Graph API Explorer 預設不顯示 `pages_manage_posts`，要先去 App 設定啟用：

1. 回到 App 主控板 → 左側點「**使用案例**」
2. 找到「**管理粉絲專頁所有內容**」→ 點「**自訂**」
3. 在權限清單裡找到並啟用：
   - `pages_manage_posts`（發文 / 排程）
   - `pages_manage_engagement`（回覆留言）
4. 完成後回到 Graph API Explorer，下拉選單就會出現這些權限了

> ⚠️ **避免加入這個已廢棄的權限：** `pages_read_user_content`（Meta v13.0 後已移除，加了會直接擋掉授權）

### 3-3：在 Graph API Explorer 加權限並產生 Token

在 Graph API Explorer 的「權限」區塊，加入以下 6 個：

```
pages_show_list
pages_read_engagement
pages_manage_posts
pages_manage_engagement
pages_manage_metadata
read_insights
```

> **打算也發 Instagram？** 請**再多加這一個**：
> ```
> instagram_content_publish
> ```
> ⚠️ 少了它，之後發 IG 會報 `Application does not have permission (#10)`——不是 Token 壞掉，是這個權限沒帶到，回這步重產 Token 補上即可。（只發 FB 不發 IG 的話可略過。）

點「**Generate Access Token**」→ Facebook 跳出授權視窗 → 允許

### 3-4：用 /me/accounts 取得 Page Token

拿到 User Token 後，在 Explorer 上方輸入框改成：

```
me/accounts
```

點「提交」。回傳結果裡每個粉絲專頁都有一個 `access_token`——**那個就是 Page Token**，有完整發文、管理權限。

### 3-5：換成永久 Token（在你自己的 Terminal 執行）

> 🔒 **安全提醒：App Secret 不要給任何人，包括 AI。以下指令請自己在終端機執行。**

**第一步：換成 60 天長期 User Token**

```bash
curl "https://graph.facebook.com/v25.0/oauth/access_token?grant_type=fb_exchange_token&client_id=【你的App ID】&client_secret=【你的App Secret】&fb_exchange_token=【3-3步的User Token】"
```

> App ID 和 App Secret 在：App 主控板 → 應用程式設定 → 基本資料

**第二步：用長期 User Token 再取一次 Page Token**

```bash
curl "https://graph.facebook.com/v25.0/me/accounts?access_token=【第一步回傳的access_token】"
```

這次回傳的 `access_token` 就是**永久有效的 Page Token**（不會過期，除非你手動撤銷或更改 FB 密碼）。

---

## Step 4：把 Token 存進 Claude

✏️ 在 Claude Code 輸入：

```
/maya-social 幫我建立 Meta 設定檔
```

Maya 會建立 `~/.claude/skills/_brand/meta-config.md`，然後告訴你把 Token 填進哪裡。

> 💡 打開 `_brand/` 只看到 `meta-config.example.md`？那是**範本**——Maya 會照它幫你生成正式的 `meta-config.md`，你不用自己手動建。

✏️ 或是你直接在 Claude Code 貼以下內容，說「幫我安裝」：

```markdown
# Meta API 設定

## Facebook 粉絲專頁
- 粉絲專頁 ID：[在粉絲專頁「關於」頁面找到，或從 Graph API Explorer 查詢]
- Page Access Token：[剛才複製的長期 Token]

## Instagram（如果有的話）
- IG Business Account ID：[從 Graph API 查詢 /{facebook-page-id}?fields=instagram_business_account]
- 同上 Token 可用於 IG

## 設定日期
[填寫日期。這個 Page Token 長期有效、不用每 60 天換；偶爾用 /health-check 確認還活著即可]
```

Claude 會存到 `~/.claude/skills/_brand/meta-config.md`。

---

## Step 5：測試是否成功

✏️ 在 Claude Code 輸入：

```
/maya-social 幫我發一篇 Facebook 測試文，內容是「測試發文，請忽略」，時間設定明天早上 9 點
```

Maya 會：
1. 讀取 `meta-config.md` 裡的 Token 和粉絲專頁 ID
2. 透過 Meta Graph API 建立排程貼文
3. 回報貼文 ID 和預定發文時間

去你的 Facebook 粉絲專頁後台確認，貼文出現在「排定的貼文」就成功了。

---

## Step 6（選用）：Instagram 連動

如果你有 Instagram 商業帳號：

1. 確認 IG 帳號已連結到 Facebook 粉絲專頁
   - 粉絲專頁設定 → 已連結的帳號 → 確認 IG 出現在這裡
2. **先把自己加為 App 測試者（很多人卡在這步）**：到 [Meta 開發者後台](https://developers.facebook.com/apps) → 你的 App → 左側「**應用程式角色 / Roles**」→「**測試人員 / Testers**」→ 新增你自己的 IG／FB 帳號 → 到該帳號的通知接受邀請。
   - ⚠️ **沒做這步，發自己的 IG 會直接報錯 `User must be on whitelist`**（白名單錯誤）。這不是 Token 壞掉，是還沒把自己加進測試者。
3. 用 Graph API Explorer 查詢你的 IG 帳號 ID：
   ```
   GET /{你的粉絲專頁ID}?fields=instagram_business_account
   ```
4. 把 IG 帳號 ID 填進 `meta-config.md` 裡

設定完後，Maya 就能把 IG 貼文「現在發」出去。

> ⚠️ **IG 只能即時發，沒有「排到未來自動發」**：IG 的 API 不像 FB 有未來排程功能（`scheduled_publish_time`），所以「指定時間、你走人讓它自己發」IG 做不到——這是 Meta 自己的限制，不是設定壞掉。要定時自動發，只有 FB 可以。
> ⚠️ IG 發文需要圖片 URL（公開可存取的圖片連結），純文字貼文 IG 不支援。
> ⚠️ 若發文回 `User must be on whitelist` → 回第 2 步把你的帳號加進「測試人員」。
> ⚠️ 若發文回 `Application does not have permission (#10)` → Token 少了 `instagram_content_publish`，回 Step 3-3 重產 Token 把它加上。

---

## 完整自動化流程：Maya + Leon + Meta

> 這是整個課程最完整的自動化場景。裝好 Meta Token（本單元）後就能跑文案排程；配圖由 Leon 出 brief、你用 ChatGPT 生圖（見 Unit 3）。

```
你說一句話：「幫我排這週的 IG 貼文，主題是 [你的主題]，全部發到 Meta」
        ↓
Maya 寫出 7 天貼文行事曆（含文案 + 配圖 brief）
        ↓
Maya 呼叫 Leon：「幫我出這 7 張 IG 圖的 brief」
        ↓
Leon 產出 7 張配圖 brief → 你貼進 ChatGPT 生圖、存成圖片（Canva 可選用來套版／改尺寸）
        ↓
Maya 把 [文案 + 圖片 URL]（FB 再加上排程時間）推進 Meta
        ↓
Facebook 後台出現 7 篇排程貼文；IG 則是你要發的時候「現在發」（IG 不支援排到未來）
```

> 💡 IG 發文需要「公開可存取的圖片 URL」。把生好的圖傳到任何能產生公開連結的地方（你的網站、圖床、雲端公開連結）再給 Maya。

✏️ 在 Claude Code 輸入：

```
/hello-nora 幫我排這週的貼文，主題是 [你的品牌主題]，
每篇請 Leon 出配圖 brief，我生好圖後 FB 排程發布、IG 我要發的時候即時發
```

Nora 會協調 Maya 和 Leon，最後一次確認後推送全部。

---

## ✅ 驗收任務

✏️ 讓 Maya 排一週行事曆，FB 排程、IG 即時發一篇測試：

```
/maya-social 幫我排這週的貼文，主題是 [你的品牌主題]，FB 排程發布，IG 先即時發一篇測試
```

Maya 會：
1. 產出 7 天貼文行事曆
2. 詢問你確認
3. 把 FB 貼文排程推進你的 Facebook 粉絲專頁；IG 即時發一篇

**兩邊都成功才算過關：**
- ✅ **FB**：粉專後台「排定的貼文」出現這週的排程貼文
- ✅ **IG**：成功即時發出一篇（IG 後台**不會**有「排程貼文」是正常的——它本來就只能現在發）

---

## 常見問題

**Q：Token 會過期嗎？60 天到了怎麼辦？**
要看你拿的是哪一種 Token，別搞混：
- **60 天會過期的，是中間那個「長期 User Token」**（Step 3-5 第一步換到的）。
- **但你最後存進 Maya 的是「Page Token」（Step 3-5 第二步用長期 User Token 換到的），這個不會過期**——除非你改 FB 密碼、移除 App、或手動撤銷權限。

所以**只要你有照 Step 3-5 完整做到第二步，存進 `meta-config.md` 的那個 Token 就是長期有效、不用每 60 天換**。
如果哪天真的突然發不出去（例如你改了密碼），就回 Step 3-3 重新產一次 User Token、再跑一遍 Step 3-5 即可。保險起見，**可用 `/health-check` 不定期檢查 Token 還活著沒**。

**Q：為什麼不支援個人 Facebook 帳號？**
Meta API 政策限制，個人帳號無法透過 API 發文，只有「粉絲專頁」才能。

**Q：留言回覆怎麼設定？是 24 小時自動回嗎？**
Token 準備好之後，跟 Maya 說：「幫我設定回覆規則，當有人留言問價格就回 [你的回覆內容]」。
但講清楚：**這是「半自動」，不是 24 小時無人值守**——你在 Claude 這邊請 Maya 跑的時候，她依規則一次把留言回完；**電腦關了、沒在跑的時候不會自動回**。真的要全天候自動回（電腦關著也回），要用 ManyChat 或 Meta 內建的自動回覆工具。

---

## 小提示

> 這個單元是課程裡技術門檻最高的一個。
> 如果 Step 3 卡住，把你看到的錯誤訊息截圖貼給 Maya，她會幫你診斷。

---

> 📜 © 2026 藍諾攝影學院 · **Hello Nora** 付費課程內容 · 僅供購買者個人學習，**禁止轉載／散布／轉售**。完整授權見根目錄 `LICENSE.md`。
<!-- © 藍諾攝影學院 Hello Nora paid course · ref:ELN-HN-2026 · unauthorized redistribution is copyright infringement -->
