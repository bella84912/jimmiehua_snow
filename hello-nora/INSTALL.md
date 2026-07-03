# 安裝指引

> 時間抓個底：**裝好整個團隊約 10–15 分鐘**（下載、複製、重開 Claude）；**填品牌資料另花約 10 分鐘**（用 `/brand-setup` 對話式最快，填得好團隊才懂你）。想串自動發文／拉數據等進階功能再各加一點。不急的話可以分兩次做：先裝好、先試玩，品牌資料之後慢慢填。

---

## 前置需求

- **Claude Code** 已安裝（[官方下載](https://claude.com/claude-code)）
- **Mac 或 Windows 都可以**——Claude Code 已原生支援 Windows，**不需要 WSL**
- 一個 Claude 帳號（建議 Claude Pro 以穩定使用全部功能）
- **一個 GitHub 帳號**（沒有就到 [github.com](https://github.com) 免費註冊，1 分鐘）——課程檔案放在私密 repo，我們會用你購買時提供的這個帳號把你邀請進去

---

## Step 0：拿到課程 repo 的下載權限（一定要先做）

課程檔案放在**私密 GitHub repo**，要先被邀請、並**接受邀請**才下載得到。三個動作：

1. 準備一個 **GitHub 帳號**（沒有就到 [github.com](https://github.com) 免費註冊），把帳號名稱／email 回報給藍諾（課程頁面表單，或寄 **service@eleanorfilm.academy**）。
2. 我們發出邀請後，你的 GitHub 通知／信箱會收到一封**邀請信**——點進去按「**Accept invitation**」接受（這步要你自己做，沒按就還沒有權限）。
3. **保持 GitHub 登入狀態**，再打開課程頁面給的 repo 連結。

> ✅ 三步做完就有權限了，往下走 Step 1。
>
> ⚠️ 打開 repo 連結是 **404（找不到頁面）**：最常見原因是**還沒按 Accept invitation**、或沒用被邀請的帳號登入。先確認這兩件事；都做了仍是 404，寄到 **service@eleanorfilm.academy**（附上你的 GitHub 帳號名稱），我們馬上幫你補邀請。

---

## 先搞清楚：你要走哪條安裝路線？

> 下面每條路都要**用你被邀請的 GitHub 帳號登入**，才下載得到私密 repo 的檔案（看到 404 就回 Step 0）。

| 你是哪一種？ | 走哪條路 | 進階功能（裝完核心再回來看） |
|---|---|---|
| **Claude 免費版**（claude.ai 網頁版） | 走 **[免費版專區](free-version/)**：下載 5 個 zip、一個個上傳 | 免費版不能自動發文／拉數據，MCP 類進階功能用不到 |
| **Claude 付費版** → **快速簡單的安裝方式** | 下面 Step 1 的**方法 B**（在 GitHub 按 Download ZIP，再拖給 Claude 裝，Mac／Windows 都適用） | 自動發文／排日曆／拉廣告數據等，見文末「進階功能」 |
| **Claude 付費版** → **按照影片步驟一條一條安裝** | 跟著安裝教學影片，從課程 Unit 0 開始照步驟做 | 同上 |

---

## 安裝步驟

### Step 1：裝好整個團隊（兩種方法選一種，結果一樣完整）

> 兩種方法都要**先用被邀請的 GitHub 帳號登入**。沒登入或邀請還沒生效，下載／clone 會出現 404（回 Step 0 處理）。

**方法 B：下載 ZIP 拖給 Claude 裝（最簡單，Mac／Windows 都適用，不用碰指令）推薦**

1. 確認你**已登入 GitHub**（右上角看得到你的頭像），打開課程給你的 repo 連結。
2. 按頁面上方綠色「**Code**」→「**Download ZIP**」下載整包，雙擊解壓縮。
3. 打開 Claude Code，把解壓縮出的 **hello-nora 資料夾拖進對話框**，貼這句：
   > 「請把這個 hello-nora 資料夾裡 skills 底下的全部內容，複製到我的 Claude 技能資料夾（`.claude/skills/`，沒有就建立），包含 _brand 和所有子資料夾。複製完成後，**請逐一確認 hello-nora、maya-social、leon-design、iris-seo、jack-ads 五位成員和 _brand 都複製成功了，列出來給我看；如果少了哪一個，幫我再複製一次。** 全部到齊後再跟我說「🎉 安裝完成，請完全關閉 Claude Code 再重新打開。開啟後，請輸入 /hello-nora 開始。」」
4. Claude 會自動判斷你的系統、用對的方式複製好，並**當場幫你點名團隊有沒有到齊**。

**方法 A：一個指令（進階，給習慣指令、且 GitHub 已登入授權的人）**

> ⚠️ 私密 repo 的 `git clone` 需要你的電腦先完成 GitHub 登入授權（第一次會跳出登入視窗，照指示登入即可）。不熟指令的話，**直接用方法 B 最穩**。

Mac：

```bash
cd ~/Desktop && git clone https://github.com/eleanorfilm-academy/hello-nora.git && mkdir -p ~/.claude/skills && for s in hello-nora/skills/*; do n=$(basename "$s"); if [ "$n" = "_brand" ] && [ -d ~/.claude/skills/_brand ]; then echo "  ⏭️  _brand 已存在，保留你的品牌資料、跳過不覆蓋"; else cp -r "$s" ~/.claude/skills/; fi; done && printf "\n安裝完成，幫你點名團隊：\n" && ok=1 && for d in hello-nora maya-social leon-design iris-seo jack-ads _brand; do if [ -d ~/.claude/skills/$d ]; then printf "  ✅ %s\n" "$d"; else printf "  ❌ %s 沒裝到\n" "$d"; ok=0; fi; done && if [ $ok = 1 ]; then printf "\n🎉 五位成員都到齊了！請完全關閉 Claude Code 再重新打開，輸入 /hello-nora 你好 就能開始。\n\n"; else printf "\n⚠️ 有成員沒裝到，請把上面整行指令再貼一次；還是不行就改用方法 B（拖檔）。\n\n"; fi
```

Windows（PowerShell，需先裝一次 [Git for Windows](https://git-scm.com/downloads/win)）：

```powershell
cd $env:USERPROFILE\Desktop; git clone https://github.com/eleanorfilm-academy/hello-nora.git; New-Item -ItemType Directory -Force "$env:USERPROFILE\.claude\skills" | Out-Null; Get-ChildItem "hello-nora\skills\*" -Directory | ForEach-Object { if ($_.Name -eq "_brand" -and (Test-Path "$env:USERPROFILE\.claude\skills\_brand")) { "  ⏭️  _brand 已存在，保留你的品牌資料、跳過不覆蓋" } else { Copy-Item $_.FullName "$env:USERPROFILE\.claude\skills\" -Recurse -Force } }; $ok=$true; "`n安裝完成，幫你點名團隊："; foreach ($d in "hello-nora","maya-social","leon-design","iris-seo","jack-ads","_brand") { if (Test-Path "$env:USERPROFILE\.claude\skills\$d") { "  ✅ $d" } else { "  ❌ $d 沒裝到"; $ok=$false } }; if ($ok) { "`n🎉 五位成員都到齊了！請完全關閉 Claude Code 再重新打開，輸入 /hello-nora 你好 就能開始。`n" } else { "`n⚠️ 有成員沒裝到，請把上面整段再貼一次；還是不行就改用方法 B（拖檔）。`n" }
```

> 🩹 **卡關防呆**：
> - 出現 `already exists`（資料夾已存在）→ 先 `rm -rf ~/Desktop/hello-nora` 再重貼整行。
> - Mac 第一次跳「要安裝 Command Line Tools」→ 點安裝、裝完再重貼整行。
> - 出現 `Authentication failed` 或一直要帳密 → 代表 GitHub 授權沒過或還沒被邀請，回 Step 0 確認，或改用方法 B。

裝好後**完全關閉 Claude Code 再重開**。你的技能資料夾（Mac：`~/.claude/skills/`；Windows：`C:\Users\你\.claude\skills\`）會有這些：

```
~/.claude/skills/
├── _brand/           ← 共用品牌資料（你要填）+ FAQ、漏斗表、戰情記錄（節日曆在 maya-social/）
│
├── 五位成員
│   ├── hello-nora/   ← Nora 營運長（輸入 /hello-nora 啟動）
│   ├── maya-social/  ← Maya 社群
│   ├── leon-design/  ← Leon 設計
│   ├── iris-seo/     ← Iris SEO
│   └── jack-ads/     ← Jack 廣告
│
├── 設定 / 精靈
│   ├── brand-setup/   ← 品牌建置精靈（/brand-setup）
│   ├── setup/         ← 防呆設定精靈（/setup）
│   ├── health-check/  ← 設定健康檢查（/health-check）
│   ├── brand-check/   ← 品牌檢查（/brand-check）
│   └── safety-setup/  ← 安全防護設定（/safety-setup）
│
└── 快速指令
    ├── report/        ← 策略彙整報告（/report）
    ├── deck/          ← 客戶成效簡報（/deck）
    ├── ad/            ← 一鍵廣告文案（/ad）
    ├── post/          ← 一鍵社群貼文（/post）
    └── sales/         ← 一鍵銷售信（/sales）
```

> 💡 全部裝好後，你不只有 5 個成員，還有一整套指令（見 [README 的「指令總覽小抄」](README.md)）。

### Step 2：填好你的品牌資料

打開 `_brand/` 底下這 4 個檔填寫（**最簡單**：直接跟 Claude 說「幫我打開品牌資料檔」，它會幫你開）：

- `brand-guide.md` — 品牌規範
- `voice-profile.md` — 語氣檔案
- `product-info.md` — 產品資訊
- `icp.md` — 理想客戶

> 想自己開：Mac 用 `open ~/.claude/skills/_brand/brand-guide.md`；Windows 到 `C:\Users\你\.claude\skills\_brand\` 用檔案總管打開即可。

不知道怎麼填？看 [BRAND-SETUP.md](BRAND-SETUP.md) 的步驟引導。

---

## 驗證安裝（兩關都過才算真的裝好）

### 第 1 關 · 功能驗證：Nora 會不會回你

✏️ 打開 Claude Code，輸入：

```
/hello-nora 你好
```

Nora 跟你打招呼、介紹團隊 → 功能正常。

### 第 2 關 · 完整性驗證：五位成員到齊了嗎

> ⚠️ **這關別跳過**：有時複製只成功一半——Nora 回得了話，但其他成員根本沒進來。光看 Nora 有回應，不代表團隊到齊。

✏️ 最簡單，直接跟 Claude 說：

```
幫我看 ~/.claude/skills/ 裡面有哪些資料夾，確認 hello-nora、maya-social、leon-design、iris-seo、jack-ads 和 _brand 都在
```

Claude 會列出來，六個都在就完全 OK。（用方法 A 一鍵指令的人，畫面上已經幫你點名過 ✅／❌，可略過這關。）

### Plan B：少了東西怎麼救

- **找不到 `/hello-nora` 指令** → ① 確認有複製到 `~/.claude/skills/hello-nora/`；② **完全關閉 Claude Code 再重開一次**（最常見就是忘了重開）。
- **少了某一位成員**（例如清單裡沒有 `leon-design`）→ 跟 Claude 說「幫我把 hello-nora 資料夾裡的 `leon-design` 再複製一次到 `.claude/skills/`」，或乾脆重跑一次安裝（方法 A 重貼整行、方法 B 重拖一次）。
- **資料夾整個是空的** → 多半是 ZIP 沒解壓縮就拖進去了，回 Step 1 重做一次。

---

## Claude 付費版功能（選用）

如果你有 Claude Pro 訂閱，可以額外接這幾個工具來啟用進階功能。**這些都是「選用」，需要你自己去接外部服務，課程不內建**：

| 工具 | 適用夥伴 | 功能 | 怎麼接 |
|-----|-----------|------|------|
| Meta Ads MCP（官方免費） | Jack | 廣告數據自動拉取、看報表 | Meta 官方免費連接器（2026/4 推出、beta 免費、**不用開發者權杖**）：Claude 設定 → 連接器，貼 `https://mcp.facebook.com/ads`。台灣帳號還沒輪到時 `/setup` 會給備案。跟 Jack 說「幫我設定 Meta 廣告數據」會帶你走 |
| Google Ads MCP（進階、選用） | Jack／Iris | 看數據、下載報表 | 跟 Meta 不同，**沒有官方一鍵免費版**：自動拉要開發者權杖、技術門檻較高，且官方免費版只能讀不能改；關鍵字搜尋量目前建議手動查。安裝圖文見 `ADVANCED-google-ads.md` |
| Google Calendar MCP | Nora | 任務自動進你的行事曆 | Claude 連接器，見 `ADVANCED-google-calendar.md` |
| Canva MCP | Leon | 把做好的圖**套品牌版、改尺寸**（後製用，**不是生圖**；生圖請用 ChatGPT）| Canva 連接器（選用）|

> ⚠️ 老實說：Meta 自動拉數據現在用**官方免費 MCP** 就行（不再需要第三方），但**不是裝完團隊就有**，要自己接一下。沒接也完全不影響你用 Jack——把數據貼給他，他一樣幫你分析。
>
> MCP 接法可在 Claude 對話框輸入 `/hello-nora 幫我設定 MCP`，或參考各服務官方文件。

---

## 🗑️ 不想要了？一鍵刪除碼

哪天你不想再把這個團隊留在電腦裡，**複製下面這串「刪除碼」貼進終端機執行**，就會把整個團隊乾乾淨淨移除（只刪這個團隊的資料夾，不會動到你 Claude 的其他東西）。

Mac：

```bash
rm -rf ~/.claude/skills/{_brand,hello-nora,maya-social,leon-design,iris-seo,jack-ads,brand-setup,brand-check,setup,health-check,safety-setup,report,deck,ad,post,sales}
```

Windows（PowerShell）：

```powershell
Remove-Item -Recurse -Force "$env:USERPROFILE\.claude\skills\_brand","$env:USERPROFILE\.claude\skills\hello-nora","$env:USERPROFILE\.claude\skills\maya-social","$env:USERPROFILE\.claude\skills\leon-design","$env:USERPROFILE\.claude\skills\iris-seo","$env:USERPROFILE\.claude\skills\jack-ads","$env:USERPROFILE\.claude\skills\brand-setup","$env:USERPROFILE\.claude\skills\brand-check","$env:USERPROFILE\.claude\skills\setup","$env:USERPROFILE\.claude\skills\health-check","$env:USERPROFILE\.claude\skills\safety-setup","$env:USERPROFILE\.claude\skills\report","$env:USERPROFILE\.claude\skills\deck","$env:USERPROFILE\.claude\skills\ad","$env:USERPROFILE\.claude\skills\post","$env:USERPROFILE\.claude\skills\sales"
```

> 刪完重開 Claude Code，團隊就不在了。想再裝回來，回到本檔 Step 1 重跑一次即可（你的品牌資料若想保留，先把 `_brand/` 從上面那串移掉再執行）。

---

*有問題請到 eleanorfilm.academy 找我們*

---

> 📜 © 2026 藍諾攝影學院 · **Hello Nora** 付費課程內容 · 僅供購買者個人學習，**禁止轉載／散布／轉售**。完整授權見根目錄 `LICENSE.md`。
<!-- © 藍諾攝影學院 Hello Nora paid course · ref:ELN-HN-2026 · unauthorized redistribution is copyright infringement -->
