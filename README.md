# vue3_gcs_demo

此專案示範如何使用 **Vue 3** 及 **Vite** 建立具備 PWA 功能（可發送通知）的手機網頁，並將產出檔案部署到 **Google Cloud Storage** (GCS)。

專案原始碼位於 `pwa-demo` 資料夾，下列說明如何建置與部署。

## 開發環境

```bash
cd pwa-demo
npm install
npm run dev
```

## 產生靜態檔案

```bash
npm run build
```

建置完成後會在 `pwa-demo/dist` 目錄產生靜態檔，將此目錄內容上傳至 GCS 以啟用靜態網站即可。

在 GCS 建立 Bucket 後，記得於 **網站設定** 中指定首頁與404頁面（通常為 `index.html`），即可透過網址存取 PWA。
