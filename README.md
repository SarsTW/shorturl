# 使用 Google 試算表與 GitHub Pages 建立短網址服務

[本專案](https://github.com/denny0223/0b.sk)示範如何透過 **Google 試算表** 作為資料庫，搭配 **Google Apps Script** 處理邏輯，以及 **GitHub Pages** 託管前端，快速建立短網址服務。

## 功能特色

- **自訂短網址**：可以手動設定短網址代碼來對應長網址。
- **簡易前端**：使用輕量級的 HTML 和 JavaScript 處理網址轉址，並部署在 GitHub Pages 上。
- **方便整合**：使用 Google Apps Script 處理短網址的儲存與查詢。

## 運作原理

1. **Google Apps Script**：
   - `code.gs` 檔案實作後端邏輯。
   - 透過 Google 試算表儲存短網址與對應的原始網址，並提供 JSON API 用於查詢。

2. **前端頁面**：
   - 簡單的 HTML (`404.html`) 用來處理短網址轉址。
   - 使用 JavaScript 呼叫 Google Apps Script 的 API，獲取對應網址並自動跳轉。

3. **GitHub Pages**：
   - 將 `404.html` 上傳到 GitHub Pages，作為動態轉址的前端介面。

## 專案結構

- **code.gs**：用於 Google Apps Script 的後端程式碼。
- **404.html**：簡單的轉址頁面，部署於 GitHub Pages。

## 設定步驟

### 第一步：設定 Google 試算表與 Apps Script

1. 建立 Google 試算表，新增以下欄位：
   - `短網址（Short Code）`：短網址的識別碼（唯一）。
   - `完整網址（Long URL）`：要轉址的目標網址。

2. 在試算表中開啟 Apps Script 編輯器：
   - 將 `code.gs` 的內容貼到編輯器。
   - 將程式部署為網路應用程式，並設定權限為「任何知道連結的人」。

3. 複製網路應用程式的 URL。

### 第二步：設定 GitHub Pages

1. 將專案下載到本地端。
2. 編輯 `404.html`，更新 API URL：
   ```javascript
   const apiUrl = '你的 Google Apps Script 網址?code=' + shortCode;
   ```
3. 將專案推送到 GitHub，並在儲存庫設定中啟用 GitHub Pages。

### 第三步：使用短網址服務

- 使用以下格式存取短網址服務：
  `https://你的 GitHub 使用者名稱.github.io/你的儲存庫名稱/<短網址代碼>`
  例如：`https://your-username.github.io/your-repo/abc123`

## 使用範例

假設短網址代碼為 `abc123`，對應的完整網址為 `https://example.com`：
1. 在 Google 試算表中新增一筆資料，`短網址代碼` 欄位填入 `abc123`，`完整網址` 欄位填入 `https://example.com`。
2. 在瀏覽器中輸入 `https://your-github-username.github.io/your-repo-name/abc123`，即可轉址至 `https://example.com`。

## 注意事項

- 請確保 Google Apps Script 的部署權限設為公開。
- 請確認 GitHub Pages 與 Google Apps Script 均使用 HTTPS，以確保安全性。

---

# URL Shortener with Google Sheets and GitHub Pages

This repository demonstrates how to create a URL shortener using **Google Sheets** as the database, **Google Apps Script** for backend logic, and **GitHub Pages** to host the frontend.

## Features

- **Customizable short URLs**: Define your own short codes for URLs.
- **Simple frontend**: Lightweight HTML and JavaScript for URL redirection, hosted on GitHub Pages.
- **Easy integration**: Utilize Google Apps Script to handle URL storage and lookup.

## How It Works

1. **Google Apps Script**:
   - The `code.gs` script acts as the backend service.
   - It stores short URLs in Google Sheets and provides a JSON API for URL lookup.

2. **Frontend**:
   - A simple HTML page (`404.html`) handles redirection based on the short URL path.
   - The script fetches the target URL from the Google Apps Script API and redirects users.

3. **GitHub Pages**:
   - The `404.html` is hosted on GitHub Pages to handle URL redirection dynamically.

## File Structure

- **code.gs**: Backend logic written in Google Apps Script.
- **404.html**: Frontend redirection page hosted on GitHub Pages.

## Setup

### Step 1: Google Sheets and Apps Script

1. Create a Google Sheet with the following columns:
   - `Short Code`: The unique code for each URL.
   - `Long URL`: The original URL to redirect to.

2. Open the Apps Script editor for the sheet:
   - Paste the content of `code.gs`.
   - Deploy as a web app (ensure access is set to "Anyone with the link").

3. Copy the web app's URL.

### Step 2: GitHub Pages

1. Clone this repository.
2. Update the API URL in `404.html`:
   ```javascript
   const apiUrl = 'YOUR_GOOGLE_APPS_SCRIPT_URL?code=' + shortCode;
   ```
3. Push the repository to GitHub and enable GitHub Pages in the repository settings.

### Step 3: Use Your Shortener

- Navigate to `https://your-github-username.github.io/your-repo-name/<short-code>` to use the shortener.

## Example

For a short URL `abc123` pointing to `https://example.com`:
1. Add `abc123` and `https://example.com` to your Google Sheet.
2. Navigate to `https://your-github-username.github.io/your-repo-name/abc123` to be redirected.

## Notes

- Ensure the Apps Script deployment is publicly accessible.
- Use HTTPS for both the Apps Script and GitHub Pages to ensure secure redirection.
