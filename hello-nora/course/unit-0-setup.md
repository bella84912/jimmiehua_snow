# Unit 0｜環境建置 + 品牌資料建置

> 這個單元完成後，你的 Claude 會說中文、知道你的品牌，而且有完整的安全防護。
<p align="left">
  <img src="../images/empty.png" alt="Hello Nora AI 行銷團隊" width="600">
</p>
---

## 📖 這份課程的小圖示（先認識一下）

整套課程的小圖示都固定一個意思，看到就知道是什麼：

| 圖示 | 意思 |
|:--:|---|
| 🔒 | 需要 Claude 付費版才能用的功能 |
| ⚠️ | 要注意、容易出錯的地方 |
| ✏️ | 要複製、貼給 Claude 的指令 |
| 🆓 | 免費版（claude.ai 網頁版）的做法 |
| ✅ | 完成後該看到的結果／驗收 |

---

## 你會得到什麼

- Claude Code 在你的電腦上跑起來，全程中文
- 一份讓所有 AI 夥伴都能讀懂你品牌的「共用大腦」
- 安全防護就位，AI 不會誤刪你的檔案

---

## 先搞清楚：你要走哪條安裝路線？

每個人情況不同，先對號入座，照你那一列走就好：

| 你是哪一種？ | 走哪條路 | 進階功能（裝完核心再回來看） |
|---|---|---|
| **Claude 免費版**（claude.ai 網頁版） | 走 **[免費版專區](../free-version/)**：下載 5 個 zip、一個個上傳。**這個單元的安裝指令你可以跳過。** | 免費版不能自動發文／拉數據，MCP 類進階功能用不到 |
| **Claude 付費版** → **快速簡單的安裝方式** | 照下面 **Step 4 的方法 B**（拖給 Claude 裝，Mac／Windows 都適用），或方法 A（一個指令） | • 自動發 FB／IG → Unit 7<br>• 貼文排進 Google 日曆 → 進階串接教學<br>• Canva 生圖 → Unit 3<br>• 自動拉廣告數據 → Jack ＋ Meta Ads MCP |
| **Claude 付費版** → **按照影片步驟一條一條安裝** | 跟著安裝教學影片，從這個 Unit 0 開始照步驟做，每個單元帶你裝好對應的夥伴 | 同上 |

> 💡 進階功能（MCP）都等你把核心團隊裝好、用順之後再回來弄，不急著一開始就接。

---

## 🎙️ 推薦工具：Typeless

> 裝了這個，整個課程從「打指令」變成「跟 AI 說話」。

你不需要一直打字。Typeless 是一個語音輸入工具——你說話，它幫你把話轉成精準的文字，直接貼進 Claude Code。

不管是跟 Nora 說「幫我排這週的貼文」，還是叫 Leon「做一個 Landing Page」，**開口說就好，不用打字**。

### 下載

前往 **[typeless.com/downloads](https://www.typeless.com/downloads)**，選你的平台下載（Mac / Windows / iOS / Android 都支援）。

### 使用方式

1. 安裝後，點選啟動按鈕（或設定快捷鍵）
2. 對著麥克風說話
3. Typeless 自動把語音轉成文字，輸出到你目前使用的視窗
4. 回到 Claude Code，你說的話就出現在輸入框裡——按 Enter 送出即可

> 💡 Typeless 會自動過濾「呃」「那個」這類口頭語，讓轉出來的文字乾淨清楚。
>
> ⚠️ **重要：記得把語言變體改成「繁體中文」**——預設可能是簡體中文，轉出來的字會不對。設定路徑：Typeless 偏好設定 → 語言 → 變體 → 選「繁體中文（台灣）」。

---

## Step 1：下載 Claude 桌面 App

> **先把三個名字分清楚，後面才不會找不到東西：**
> - **claude.ai**＝免費的網頁版（用免費版的人走 [免費版專區](https://github.com/eleanorfilm-academy/hello-nora/tree/main/free-version)，這個單元的安裝可跳過）。
> - **Claude 桌面 App**＝下載到電腦的應用程式，這個 Step 1 要裝的就是它。
> - **Claude Code**＝在桌面 App 裡開的一個「工作視窗」，**本課付費版的安裝、指令全都在這裡做**（Step 2 教你打開它）。

前往 [claude.ai/download](https://claude.ai/download)，下載並安裝 Claude 桌面版（Mac / Windows 都有）。安裝完成後，用你的帳號登入。

> **需要 Claude Pro 嗎？**
> Claude 免費版可以試用，但建議搭配 **Claude Pro（約 US$20/月，實際以官方公告為準）** 才能穩定使用所有功能。

---

## Step 2：開啟 Claude Code

打開 Claude 桌面 App 後，開啟 **Claude Code** 視窗（在桌面 App 裡找到 Claude Code 入口點開；若你的版本沒看到，跟著安裝教學影片的畫面找）。

你會看到一個可以輸入指令、跟 Claude 對話的介面——這就是我們整個課程操作的地方。

> **本課會常常請你「完全關閉 Claude Code 再重開」，先學會怎麼做（不是按紅色叉叉）：**
> - **Mac**：左上角選單列點「**Claude**」→「**結束 Claude**」（或按 ⌘Q），再重新打開。
> - **Windows**：右下角工具列的 Claude 圖示按右鍵 →「**結束 / Quit**」，再重新打開。
> 很多「裝好卻沒反應、找不到指令」的狀況，都是因為只縮小、沒有真的結束重開。

---

## Step 3：設定中文語言

Claude Code 預設是英文，這行指令會讓它之後都用中文跟你對話。

✏️ 複製貼上到 Claude Code 視窗，看到確認提示就輸入 `yes`：

```bash
mkdir -p ~/.claude/skills && printf "## 語言\n\n回覆語言：繁體中文\n" >> ~/.claude/CLAUDE.md
```

完成後，**關掉 Claude Code 視窗，再用快捷鍵重新開啟**，讓設定生效。

---

## Step 4：一次裝好整個團隊

> **先決條件：你必須已被邀請進課程的私密 repo。** 課程檔案不是公開的——把你的 **GitHub 帳號**回報給藍諾（課程頁面的表單／service@eleanorfilm.academy），收到 GitHub 邀請信按「**Accept invitation**」接受、並保持 GitHub 登入。**還沒接受邀請就打開下面的連結會是 404，這正常，不是壞掉。**

整個團隊——5 位成員、所有指令、所有工作流、品牌資料範本——一次裝好。下面**兩種方法選一種**，結果一樣完整。

### 方法 B：拖給 Claude 裝（最簡單，Mac／Windows 都適用，不用碰指令）— 最推薦

1. 到 [課程 GitHub](https://github.com/eleanorfilm-academy/hello-nora)，按綠色「**Code**」按鈕 →「**Download ZIP**」下載整包。
2. 找到下載的 zip 檔，**雙擊解壓縮**。
3. 打開 Claude Code，把解壓縮出來的 **hello-nora 整個資料夾拖進對話框**，然後貼這句給它：
   > 「請把這個 hello-nora 資料夾裡 skills 底下的全部內容，複製到我的 Claude 技能資料夾（`.claude/skills/`，沒有就建立），包含 _brand 和所有子資料夾。」
4. Claude 會自動判斷你是 Mac 還是 Windows、用對的方式複製好。完成後**完全關閉 Claude Code 再重開**。

> 這條最穩——你不用懂指令，系統差異交給 Claude 處理。

### 方法 A：一個指令（給習慣複製貼上指令的人）

✏️ **Mac**——複製貼上到 Claude Code，按 Enter：

```bash
cd ~/Desktop && git clone https://github.com/eleanorfilm-academy/hello-nora.git && mkdir -p ~/.claude/skills && for s in hello-nora/skills/*; do n=$(basename "$s"); if [ "$n" = "_brand" ] && [ -d ~/.claude/skills/_brand ]; then echo "  ⏭️  _brand 已存在，保留你的品牌資料、跳過不覆蓋"; else cp -r "$s" ~/.claude/skills/; fi; done && printf "\n安裝完成，幫你點名團隊：\n" && ok=1 && for d in hello-nora maya-social leon-design iris-seo jack-ads _brand; do if [ -d ~/.claude/skills/$d ]; then printf "  ✅ %s\n" "$d"; else printf "  ❌ %s 沒裝到\n" "$d"; ok=0; fi; done && if [ $ok = 1 ]; then printf "\n🎉 五位成員都到齊了！請完全關閉 Claude Code 再重新打開，輸入 /hello-nora 你好 就能開始。\n\n"; else printf "\n⚠️ 有成員沒裝到，請把上面整行指令再貼一次；還是不行就改用方法 B（Download ZIP）。\n\n"; fi
```

> ⚠️ 跳出「要安裝開發者工具 / Command Line Tools」是正常的（代表還沒裝 git）：點「**安裝**」→ 等裝完 → **再貼一次**那行。
> ⚠️ 出現「`already exists`」代表桌面已有舊的 hello-nora：先貼 `rm -rf ~/Desktop/hello-nora` 清掉，再貼一次。
> ⚠️ 出現「`Authentication failed`」或一直要你輸入 GitHub 帳密：代表這台電腦還沒授權私密 repo，或邀請還沒接受——回最上面的先決條件確認，或**直接改用方法 B（Download ZIP）最省事**。

✏️ **Windows**——需先裝一次 [Git for Windows](https://git-scm.com/downloads/win)，然後在 Claude Code 貼這段（PowerShell）：

```powershell
cd ~/Desktop; git clone https://github.com/eleanorfilm-academy/hello-nora.git; New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\skills" | Out-Null; Get-ChildItem "hello-nora\skills\*" -Directory | ForEach-Object { if ($_.Name -eq "_brand" -and (Test-Path "$env:USERPROFILE\.claude\skills\_brand")) { "  ⏭️  _brand 已存在，保留你的品牌資料、跳過不覆蓋" } else { Copy-Item $_.FullName "$env:USERPROFILE\.claude\skills\" -Recurse -Force } }; $ok=$true; "`n安裝完成，幫你點名團隊："; foreach ($d in "hello-nora","maya-social","leon-design","iris-seo","jack-ads","_brand") { if (Test-Path "$env:USERPROFILE\.claude\skills\$d") { "  ✅ $d" } else { "  ❌ $d 沒裝到"; $ok=$false } }; if ($ok) { "`n🎉 五位成員都到齊了！請完全關閉 Claude Code 再重新打開，輸入 /hello-nora 你好 就能開始。`n" } else { "`n⚠️ 有成員沒裝到，請把上面整段再貼一次；還是不行就改用方法 B（Download ZIP）。`n" }
```

> 覺得 Windows 這條麻煩？**直接用上面的方法 B**，不用裝 git、不用碰指令，最省事。

裝好後，不管用哪種方法，都**完全關閉 Claude Code 再重開**，讓它讀到全部技能。

> ✅ 這步把 **Nora、Maya、Leon、Iris、Jack ＋ 所有指令（/setup、/report、/deck、/ad、/post、/sales…）＋ 品牌資料範本 ＋ 所有工作流** 一次裝齊，後面的單元不用再安裝，直接用。

---

## Step 5：建立你的品牌資料

✏️ 輸入：

```
/brand-setup
```

Claude 會開始用中文問你幾個關於品牌的問題，一次一個，大概 10 分鐘可以完成。

如果你有官網或社群頁面，把網址貼給它——Claude 可以直接讀取，幫你自動整理品牌資訊。

> 💡 兩種方式擇一即可：**對話式**（上面的 `/brand-setup`，最輕鬆，約 10 分鐘）；或**自己填**（打開 `_brand/` 4 個檔逐一填，步驟見 [BRAND-SETUP.md](../BRAND-SETUP.md)）。不用兩個都做。

---

## Step 6：驗收品牌資料

問答結束後，✏️ 輸入：

```
/brand-check
```

Claude 會列出剛才建立的 4 份核心品牌檔案（外加選填的 FAQ）、摘要每份內容，讓你確認沒有缺漏。

> 看到 ⚠️ 標記就代表那邊還沒填好，Claude 會告訴你怎麼補。

---

## Step 7：開啟安全防護

`safety-setup` 在 Step 4 已經跟著裝好了，✏️ 直接輸入：

```
/safety-setup
```

Claude 會幫你把 `rm -rf`、`sudo`、`shutdown` 等危險指令加入黑名單，AI 之後不會手滑刪壞你的東西。

> 💡 設完黑名單後，同一個 `/safety-setup` 會**接著問你要不要設「自動允許白名單」**（讓你少按一點「允許」）。那是**進階選用**——這步**設好黑名單就夠了**，白名單想了解再看下面「進階選用」那段，不做完全不影響。

---

## ✅ 驗收任務

完成以下三件事：

- [ ] `/brand-check` 顯示 4 份核心檔案都齊全（FAQ 選填，空著沒關係）
- [ ] `/safety-setup` 顯示黑名單規則已成功加入
- [ ] 中文語言設定生效（Claude 全程用中文回應）

---

## 小提示

> 這份品牌資料是你整個 AI 行銷團隊的共用大腦。
> 填得越清楚，之後每個夥伴給你的東西就越貼近你的品牌風格。
>
> 安全防護不是「以防萬一」——AI 真的有可能在執行任務時誤刪檔案，這層防護一定要有。

---

## 🔓 進階選用：自動允許白名單（非必要，請自行評估風險後再決定）

> ⚠️ **這一段是「選用」，不是必做。** 它能讓你少按很多「允許」、用起來更順手——但因為是**放寬權限**，**有一定風險**，請先看完下面說明、自己評估後再決定要不要做。不想做、或還不確定，**直接跳過完全不影響團隊運作。**

### 前言：這是什麼、為什麼值得單獨講

你用團隊用久了會發現，Claude 三不五時就跳出來問你「要不要允許」——要讀檔、改檔、發文、拉數據，它都會先問過你一次。

- **好處**：安全，每個動作你都看得到、攔得住。
- **壞處**：用熟之後，一直按「允許」很煩，會打斷你的節奏。

「白名單」就是讓你**自己挑一些「信得過、又每天在用」的動作設成自動放行**，這些就不再問、直接做；其他沒挑的照樣會先問你；上面 Step 7 黑名單裡的危險指令則永遠擋掉。一句話——**把煩人的例行確認關掉，把危險的留著擋。** 這是個很實用的設定，所以特別獨立出來講清楚。

### 為什麼說「有風險」、為什麼要你自己決定

放行＝你提前把「同意」交給 AI。雖然黑名單還擋著最危險的那些，但白名單開得越寬，AI 不問你就動手的範圍就越大；萬一它判斷錯，你可能來不及攔。

所以這件事**沒有標準答案，要看你自己**：

- 想要**最安全**、也不嫌每次按允許 → **不用做這段**，維持現狀最穩。
- 覺得**一直按允許很煩、願意換一點便利** → 可以做，但**建議從最輕的程度開始**，用順了再考慮放寬。

### 前提（符合才建議做）

| 前提 | 說明 |
|------|------|
| **已完成 Step 7 黑名單** | 一定要先設好黑名單（危險指令防護），白名單才有「擋危險」這層底。順序不能反。 |
| **你看得懂、也改得回來** | 設定寫在 `~/.claude/settings.json`，之後想關掉，把對應幾行刪掉、重開 Claude 就好。你要能接受「之後可能要自己去調整它」。 |
| **你已評估過、願意承擔** | 這是放寬權限的操作，風險請你自行評估後再決定執行。 |

### 怎麼做

跟設定黑名單同一個工具，✏️ 輸入：

```
/safety-setup
```

跑完黑名單後，它會**主動問你要不要設自動允許**。說要，它會讓你選放行到哪個程度：

- **A. 輕度（最安全，推薦先用這個）**：只自動放行「唯讀」動作——讀你的檔案、上網查資料，完全不會改到任何東西。
- **B. 中度（最實用）**：在 A 之上，再放行團隊每天要做的——改你的品牌資料與草稿、發文／拉廣告數據。改檔、發文不用再一直按允許，但刪除、系統指令還是擋著。
- **C. 自己挑**：你告訴它「哪幾個操作老是跳允許很煩」，它只針對那幾項加。

> 💡 拿不定主意就選 **A 輕度**——它只放行「看」、不放行「改」，幾乎沒有風險，先體驗一下少按允許的順暢感，想放寬之後隨時能再調。

> ⚠️ **不要做「全部自動允許」**（把所有權限都跳過）。那等於 AI 做任何事都不再問你，風險太高，不值得為了省那幾下按鍵冒這個險。

---

> 📜 © 2026 藍諾攝影學院 · **Hello Nora** 付費課程內容 · 僅供購買者個人學習，**禁止轉載／散布／轉售**。完整授權見根目錄 `LICENSE.md`。
<!-- © 藍諾攝影學院 Hello Nora paid course · ref:ELN-HN-2026 · unauthorized redistribution is copyright infringement -->
