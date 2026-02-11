# Discord Bot Token 設定手冊

> 這是一份完整的 Discord Bot Token 取得與設定指南，將帶領你從頭到尾完成 Discord 機器人的建立、Token 取得、以及與 OpenClaw 和聊天群組的綁定。

## 📋 目錄

- [前置準備](#前置準備)
- [第一部分：建立 Discord 應用程式](#第一部分建立-discord-應用程式)
- [第二部分：建立並取得 Bot Token](#第二部分建立並取得-bot-token)
- [第三部分：設定 Bot 權限](#第三部分設定-bot-權限)
- [第四部分：邀請 Bot 到 Discord 伺服器](#第四部分邀請-bot-到-discord-伺服器)
- [第五部分：將 Token 綁定到 OpenClaw](#第五部分將-token-綁定到-openclaw)
- [第六部分：將 Bot 綁定到聊天群組](#第六部分將-bot-綁定到聊天群組)
- [安全性注意事項](#安全性注意事項)
- [常見問題](#常見問題)

---

## 前置準備

在開始之前，請確保你具備以下條件：

- ✅ 有效的 Discord 帳號
- ✅ Discord 伺服器的管理員權限（用於邀請機器人）
- ✅ 已完成 OpenClaw 的基本安裝（參考 [README.md](README.md)）
- ✅ 穩定的網際網路連線

---

## 第一部分：建立 Discord 應用程式

### 步驟 1：前往 Discord Developer Portal

1. 開啟瀏覽器，前往 [Discord Developer Portal](https://discord.com/developers/applications)
2. 使用你的 Discord 帳號登入

![Discord Developer Portal 登入頁面](https://discord.com/assets/developers)

### 步驟 2：建立新的應用程式

1. 點擊右上角的「**New Application**」按鈕
2. 在彈出的視窗中，為你的機器人輸入一個名稱
   - 範例：「OpenClaw Bot」、「我的助理機器人」
3. 閱讀並同意 Discord 的開發者服務條款
4. 點擊「**Create**」按鈕

### 步驟 3：設定應用程式基本資訊

在應用程式的「**General Information**」頁面，你可以：

1. **APP ICON**：上傳機器人的頭像圖片
2. **DESCRIPTION**：填寫機器人的描述（選填）
3. **TAGS**：新增相關標籤（選填）

> 💡 **提示**：這些資訊會在機器人的個人資料中顯示，建議填寫清楚的描述。

---

## 第二部分：建立並取得 Bot Token

### 步驟 4：進入 Bot 設定頁面

1. 在左側選單中，點擊「**Bot**」
2. 如果是第一次建立，點擊「**Add Bot**」按鈕
3. 在確認對話框中，點擊「**Yes, do it!**」

### 步驟 5：取得 Bot Token

1. 在 Bot 設定頁面，找到「**TOKEN**」區塊
2. 點擊「**Reset Token**」按鈕（如果是第一次，會顯示「**Copy**」按鈕）
3. 可能需要輸入你的 Discord 密碼或進行 2FA 驗證
4. Token 會顯示在畫面上，點擊「**Copy**」按鈕複製 Token

> ⚠️ **重要警告**：
> - Token 只會顯示一次！請立即複製並妥善保管
> - **絕對不要**將 Token 公開分享或上傳到 Git 儲存庫
> - 如果 Token 遺失，需要重新生成（舊的 Token 會失效）

### 步驟 6：設定 Bot 基本選項

在同一個 Bot 頁面，建議設定以下選項：

#### Privileged Gateway Intents（特權閘道意圖）

根據你的需求啟用以下選項：

- ✅ **PRESENCE INTENT**：讓機器人看到成員的在線狀態
- ✅ **SERVER MEMBERS INTENT**：讓機器人存取伺服器成員資訊
- ✅ **MESSAGE CONTENT INTENT**：讓機器人讀取訊息內容（**強烈建議啟用**）

> 💡 **OpenClaw 建議配置**：為了讓 OpenClaw 正常運作，請務必啟用「**MESSAGE CONTENT INTENT**」。

#### 其他設定

- **PUBLIC BOT**：如果你希望其他人也能邀請你的機器人，請啟用此選項
- **REQUIRES OAUTH2 CODE GRANT**：一般使用者建議保持關閉

---

## 第三部分：設定 Bot 權限

### 步驟 7：配置 OAuth2 權限

1. 在左側選單中，點擊「**OAuth2**」→「**URL Generator**」
2. 在「**SCOPES**」區塊中，勾選以下選項：
   - ✅ `bot`
   - ✅ `applications.commands`（如果需要使用斜線指令）

### 步驟 8：選擇 Bot 權限

在「**BOT PERMISSIONS**」區塊中，根據 OpenClaw 的需求，建議勾選以下權限：

#### 文字頻道權限（必要）
- ✅ **View Channels**（查看頻道）
- ✅ **Send Messages**（傳送訊息）
- ✅ **Send Messages in Threads**（在討論串中傳送訊息）
- ✅ **Embed Links**（嵌入連結）
- ✅ **Attach Files**（附加檔案）
- ✅ **Read Message History**（讀取訊息歷史記錄）
- ✅ **Add Reactions**（新增反應）
- ✅ **Use Slash Commands**（使用斜線指令）

#### 一般權限（選填）
- ☑️ **Manage Messages**（管理訊息）- 如果需要刪除或編輯訊息
- ☑️ **Mention Everyone**（@everyone 提及）- 如需公告功能
- ☑️ **Use External Emojis**（使用外部表情符號）

### 步驟 9：複製邀請連結

完成權限設定後：
1. 在頁面下方的「**GENERATED URL**」區塊
2. 點擊「**Copy**」按鈕複製產生的邀請連結
3. 保存此連結，稍後用於邀請機器人到伺服器

---

## 第四部分：邀請 Bot 到 Discord 伺服器

### 步驟 10：使用邀請連結

1. 開啟瀏覽器，貼上剛才複製的邀請連結
2. 在下拉選單中，選擇你想要加入機器人的 Discord 伺服器
   - ⚠️ 你必須是該伺服器的管理員或擁有「管理伺服器」權限
3. 檢查並確認機器人請求的權限
4. 點擊「**授權**」或「**Authorize**」按鈕
5. 完成人機驗證（如果系統要求）

### 步驟 11：確認 Bot 已加入

1. 回到你的 Discord 伺服器
2. 在成員列表中，應該能看到你的機器人（顯示為離線狀態是正常的）
3. 機器人的名稱旁會有「🤖 BOT」標籤

---

## 第五部分：將 Token 綁定到 OpenClaw

### 步驟 12：執行 OpenClaw 初始化

如果你還沒有完成 OpenClaw 的初始化，請執行：

```bash
openclaw init
```

### 步驟 13：輸入 Discord Bot Token

在初始化過程中，當系統提示：「**Please enter your Discord Bot Token**」

1. 貼上你在步驟 5 複製的 Bot Token
2. 按下 Enter 鍵確認

![輸入 Bot Token](images/10-openclaw_enter_bot_token.jpg)

### 步驟 14：完成其他 Discord 配置

繼續完成以下配置：

1. **Discord 頻道存取設定**：選擇機器人可以存取的頻道
   
   ![Discord 頻道存取](images/11-openclaw_discord_channel_access.jpg)

2. **配對核准**：確認 Discord 機器人的配對

   ![配對核准](images/12-openclaw_discord_pairing_apporve.jpg)

### 步驟 15：啟動 OpenClaw 服務

完成配置後，啟動 OpenClaw Gateway 服務：

```bash
openclaw gateway start
```

![啟動 Gateway](images/25-openclaw_gateway_start.jpg)

如果一切設定正確，你的機器人應該會：
- 在 Discord 中顯示為「線上」狀態（綠色圓點）
- 能夠回應訊息和指令

---

## 第六部分：將 Bot 綁定到聊天群組

### 步驟 16：設定頻道權限

為了讓機器人在特定頻道中運作，需要設定適當的權限：

#### 方法 A：全伺服器權限（簡單）

1. 確保在邀請機器人時已授予所有必要權限
2. 機器人將能在所有公開頻道中運作

#### 方法 B：特定頻道權限（進階）

1. 在 Discord 中，進入你想要機器人運作的頻道
2. 點擊頻道名稱旁的「⚙️ 編輯頻道」
3. 前往「**權限**」頁面
4. 點擊「**+ 新增成員或身分組**」
5. 搜尋並選擇你的機器人
6. 啟用以下權限：
   - ✅ 查看頻道
   - ✅ 傳送訊息
   - ✅ 讀取訊息歷史記錄
   - ✅ 新增反應
   - ✅ 使用斜線指令
7. 點擊「**儲存變更**」

### 步驟 17：在 OpenClaw 中配置頻道存取

使用 OpenClaw 的配置功能來指定允許的頻道：

```bash
openclaw config discord
```

或者透過 WebUI 管理介面進行配置：

1. 開啟 WebUI（URL 在初始化時會顯示）
2. 前往「**Discord 設定**」
3. 在「**允許的頻道 ID**」中新增頻道 ID

![Discord 頻道存取](images/11-openclaw_discord_channel_access.jpg)

### 步驟 18：如何取得頻道 ID

1. 在 Discord 中，開啟「**使用者設定**」
2. 前往「**進階**」→ 啟用「**開發者模式**」
3. 回到任何頻道，右鍵點擊頻道名稱
4. 點擊「**複製頻道 ID**」
5. 將此 ID 貼到 OpenClaw 的配置中

### 步驟 19：測試機器人

在你配置的頻道中測試機器人：

1. 輸入觸發指令或 @提及機器人
2. 傳送測試訊息，例如：`@OpenClaw Bot 你好`
3. 確認機器人能正確回應

---

## 安全性注意事項

### 🔒 保護你的 Bot Token

**永遠不要：**
- ❌ 將 Token 直接寫在程式碼中
- ❌ 上傳 Token 到 GitHub 或其他公開平台
- ❌ 在 Discord 訊息或論壇中分享 Token
- ❌ 截圖時洩露 Token

**應該這樣做：**
- ✅ 使用環境變數儲存 Token
- ✅ 使用 `.env` 檔案（並加入 `.gitignore`）
- ✅ 定期更換 Token
- ✅ 限制 Token 的權限範圍

### 🔄 如果 Token 洩露怎麼辦？

1. **立即**前往 Discord Developer Portal
2. 進入你的應用程式 → Bot 頁面
3. 點擊「**Reset Token**」
4. 複製新的 Token
5. 在 OpenClaw 中更新 Token：
   ```bash
   openclaw config discord --token <新的Token>
   ```

---

## 常見問題

### Q1: 為什麼機器人顯示離線狀態？

**A:** 可能的原因：

1. **Token 錯誤**：確認複製的 Token 是否正確，沒有多餘的空格
2. **OpenClaw 未啟動**：執行 `openclaw gateway start` 啟動服務
3. **網路問題**：檢查防火牆設定和網路連線
4. **Intent 未啟用**：確認在 Developer Portal 中啟用了必要的 Gateway Intents

**解決方法**：
```bash
# 檢查 Gateway 狀態
openclaw gateway status

# 重新啟動 Gateway
openclaw gateway restart

# 查看日誌
openclaw logs
```

### Q2: 機器人無法讀取訊息內容？

**A:** 需要啟用「Message Content Intent」：

1. 前往 Discord Developer Portal
2. 進入你的應用程式 → Bot 頁面
3. 在「Privileged Gateway Intents」區塊
4. 啟用「**MESSAGE CONTENT INTENT**」
5. 儲存變更
6. 重新啟動 OpenClaw

### Q3: 如何在多個伺服器中使用同一個機器人？

**A:** 只需使用同一個邀請連結，邀請機器人到其他伺服器：

1. 回到 Discord Developer Portal
2. OAuth2 → URL Generator
3. 複製產生的邀請連結
4. 在每個想要新增機器人的伺服器中使用此連結

> 💡 確保在 Bot 設定中啟用了「**PUBLIC BOT**」選項。

### Q4: 機器人可以回應，但無法使用斜線指令？

**A:** 需要配置 Application Commands：

1. 在 OAuth2 設定中，確認勾選了 `applications.commands`
2. 重新生成邀請連結並重新邀請機器人
3. 或者在伺服器設定中調整機器人的權限

### Q5: 如何更改機器人的名稱或頭像？

**A:** 在 Discord Developer Portal 中：

1. 進入你的應用程式
2. 前往「Bot」頁面
3. 更改「USERNAME」或上傳新的「APP ICON」
4. 點擊「Save Changes」

> ⚠️ 機器人名稱每小時只能更改兩次。

### Q6: 機器人在某些頻道中無法運作？

**A:** 檢查頻道權限：

1. 確認機器人有該頻道的「查看頻道」和「傳送訊息」權限
2. 檢查頻道是否被 OpenClaw 的配置排除
3. 確認該頻道不是年齡限制頻道（機器人預設無法存取）

### Q7: Token 遺失了怎麼辦？

**A:** Token 無法找回，只能重新生成：

1. 前往 Discord Developer Portal → Bot
2. 點擊「Reset Token」
3. 複製新的 Token
4. 在 OpenClaw 中更新：
   ```bash
   openclaw init
   # 或
   openclaw config discord
   ```

### Q8: 如何讓機器人只回應特定使用者？

**A:** 在 OpenClaw 的配置中設定白名單：

1. 開啟 WebUI 管理介面
2. 前往「權限設定」
3. 新增允許的使用者 ID
4. 或使用指令：
   ```bash
   openclaw config permissions --whitelist <使用者ID>
   ```

### Q9: 機器人回應速度很慢？

**A:** 可能的原因和解決方法：

1. **API 配額限制**：檢查你使用的 AI 服務的配額
2. **網路延遲**：優化網路連線或更換伺服器位置
3. **系統資源不足**：升級伺服器配置
4. **Gateway 設定**：調整 Gateway 的並發處理數量

### Q10: 如何查看機器人的運行日誌？

**A:** 使用以下指令：

```bash
# 查看即時日誌
openclaw logs --follow

# 查看最近的日誌
openclaw logs --tail 100

# 查看錯誤日誌
openclaw logs --level error
```

---

## 📚 相關資源

- [OpenClaw 完整架設手冊](README.md)
- [Discord Developer Portal](https://discord.com/developers/applications)
- [Discord 開發者文件](https://discord.com/developers/docs)
- [OpenClaw 官方文件](https://openclaw.org)
- [Discord 社群支援](https://discord.gg/openclaw)

---

## 🎉 完成！

恭喜你成功設定 Discord Bot Token 並完成與 OpenClaw 的綁定！

現在你的機器人應該已經：
- ✅ 在 Discord 中顯示為線上狀態
- ✅ 能夠接收和回應訊息
- ✅ 正確綁定到你的 OpenClaw 實例
- ✅ 在指定的聊天群組中正常運作

如有任何問題或需要進一步協助，請參考上方的常見問題或聯繫社群支援。

**祝你使用愉快！** 🤖✨
