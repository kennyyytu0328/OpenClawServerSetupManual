# OpenClawServerSetupManual
記錄 OpenClaw 開發工具的安裝與配置歷程

## 基本環境：
Node.js：版本 ≥ 22.0.0

npm：版本 ≥ 9.0.0

Ubuntu：版本 22.04

可用的 AI 模型 (這裡我們使用Gemini OAuth)

## Node.js安裝版本畫面：
![1-download_nodejs](https://github.com/user-attachments/assets/cd4accd7-896a-43be-86ac-11dce7741838)

## 使用官方脚本安装 OpenClaw
curl -fsSL https://openclaw.ai/install.sh | bash

![2-intall_openclaw](https://github.com/user-attachments/assets/1f7f53e0-40da-41c7-a908-e6c33be8da83)

安裝過程會需要一點時間, 請耐心等候.

## 另開一個終端機來安裝 Gemini CLI
$npm install -g @google/gemini-cli

安裝完成後, 輸入 Gemini 執行, 會自動進入Google Account登入頁面, 請選擇有Gemini付費的帳號來登入.
### 如果無法自動進入登入頁面, 你可以照以下步驟：
- 1.獲取金鑰： 在Chrome 瀏覽器中，直接打開 Google AI Studio 並點擊 "Create API Key"。

- 2.直接注入環境變數： 您不需要在終端機執行任何 login 指令，直接輸入：
  
  export GOOGLE_API_KEY="您的金鑰內容"
  
  export GEMINI_API_KEY="您的金鑰內容"

- 3.直接測試執行：
npx @google/gemini-cli -p "Hello Gemini, summarize the current system state."

  如果出現問題, 可以嘗試執行：
  
  NODE_OPTIONS="--no-warnings" npx @google/gemini-cli -p "Hello"

## OpenClaw安裝完成後, 開始進行設定

- 請依照畫面進行操作.
     
![3-openclaw_question1](https://github.com/user-attachments/assets/bb9affd7-affd-4038-b346-dee0f8ce15c7)

![4-openclaw_select_model](https://github.com/user-attachments/assets/80afe9ea-14b0-4468-82b3-7c4122230611)

![5-openclaw_choose_auth](https://github.com/user-attachments/assets/b8d4fd9e-8773-4eef-9687-ada58cb4d054)

### 進行 Google Gemini OAuth流程：
- 1. 畫面中會有一段網址， CTRL+滑鼠右鍵，開啟頁面，直接登入 Google 帳號。 (一樣要有Gemini付費帳號)
- 2. 點擊登入後會跑到空白頁面，不要馬上關掉。把上方網址列整段全部複製起來。
- 3. 回到終端機，把內容貼到終端機裡，按enter。
 
### 如果沒有這個畫面，而是回到命令列，請輸入：
openclaw onboard  
可以再叫起設定流程, 請重新設定。

- 之後選擇要使用的模型, Gemini 3 Flash即可.
  
![6-openclaw_choose_default_model](https://github.com/user-attachments/assets/07a34191-a2bd-4ec0-b7b4-91f43b1c47f4)

- 接下來設定Gateway：
![7-openclaw_gateway_port_bind](https://github.com/user-attachments/assets/d7b2c434-620d-46cd-8590-2c199233b2f0)

- 注意Gateway Token就是設定這個OpenClaw Gateway的密碼, 可以設你自己想要的密碼, 之後會用到.
![8-openclaw_gateway_token](https://github.com/user-attachments/assets/786c3bf1-364f-4e3b-b818-7955eacc5b12)

-  開始設定通訊的方式：
![9-openclaw_config_chat](https://github.com/user-attachments/assets/bda6c8ad-7987-4f96-8376-46fcc51191b6)

- 這裡我們使用Discord通訊, 你需要先在Disocord取得一個Bot Token：
![10-openclaw_enter_bot_token](https://github.com/user-attachments/assets/b78c677d-467a-4c72-acc0-6da6a090f841)
![11-openclaw_discord_channel_access](https://github.com/user-attachments/assets/acd5ec34-e845-4a26-b694-0d4e2b335e7c)

-  設定有人初次進入聊天時, 需要採用Pairing方式來進行認證：
![12-openclaw_discord_pairing_apporve](https://github.com/user-attachments/assets/9478db8d-17bf-4361-b48c-d167c1bddd5c)

-  在這裡決定你要增加的skills有哪些：
![13-openclaw_config_skills](https://github.com/user-attachments/assets/1b54ec97-f816-4473-b52b-0366d510a224)

![14-openclaw_install_skills](https://github.com/user-attachments/assets/4e28af78-7649-4ff5-923e-a8400ccc88f9)

-  這裡會要求你輸入一系列的API KEY, 可以先不提供：
![15-openclaw_other_API_key](https://github.com/user-attachments/assets/65b66c28-22b6-4136-a634-e1bb6cc6f2f5)

-  做Gateway Service的相關啟用：
![16-openclaw_gateway_service_install](https://github.com/user-attachments/assets/eb8705a1-28b2-4b17-b983-ec4d26b90624)

## 這是完成後, OpenClaw 可以使用瀏覽器登入的位置：
![17-openclaw_WebUI_address](https://github.com/user-attachments/assets/076a30ae-f0c6-4e7d-a522-582c0a5f97e5)

這裡會再提示 Gateway Token的儲存位置與取得方式：
![18-openclaw_set_gateway_token](https://github.com/user-attachments/assets/ad4fb6f1-e3d4-45e8-9ebf-583131a0c2c1)

這裡就看要用什麼方式來做初步測試, 1是直接在終端機做, 2是開啟WebUI, 3是先不做.
![19-openclaw_hatch_bot](https://github.com/user-attachments/assets/406a3736-28ab-414b-b8f9-72e3394e0bb6)

## 開啟WebUI 之後, 會看到是在 disconnected 的錯誤：
正常網址會在
http://127.0.0.1:18789/chat?session=main
![20-openclaw_offline](https://github.com/user-attachments/assets/1eb37ecc-c472-4653-9d93-5094f1cb94a8)

需要填入剛剛的Gateway Token到這個欄位.
![21-openclaw_gateway_token_set](https://github.com/user-attachments/assets/9384eea6-fe5d-4f64-a537-025c746e74a3)

填好後, 按下 Connect 鈕, 就會看到 Connected 綠色字出現. 上方也會有 Health OK的標籤.
![22-openclaw_gateway_connect](https://github.com/user-attachments/assets/009dadfb-ae65-450b-a8c1-77d96ebb51d0)

## 新使用者進入聊天時, 跟Bot隨便說一句, Bot會給一組Pairing Code要求認證, 需要在終端機使用這個認證.
![23-openclaw_new_user_approve](https://github.com/user-attachments/assets/cb8a567e-b82b-47ab-a407-03e57e6bf6f4)

## OpenClaw 的關閉方式 
![24-openclaw_gateway_stop](https://github.com/user-attachments/assets/6807a318-5b16-4037-8293-afdf0d75a6f0)
## OpenClaw 的開啟方式
![25-openclaw_gateway_start](https://github.com/user-attachments/assets/48e8ea1b-8fda-4844-816a-d4448c7986ff)

# 進入OpenClaw設定流程
openclaw onboard

# OpenClaw系统檢查
openclaw doctor

# OpenClaw設定檔
cat ~/.openclaw/openclaw.json








 









