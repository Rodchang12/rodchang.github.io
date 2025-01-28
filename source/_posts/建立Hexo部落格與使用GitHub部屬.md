---
title: 建立Hexo部落格與使用GitHub部屬
date: 2025-01-16 14:29:35
tags:
  - Hexo
  - 部落格
categories:
  - 技術
---

## 1. 關於建立部落格
在2024年開始接觸前端技術，在實體與線上課程的學習中設立了不同的目標去挑戰，並使用了 Notion 跟 HackMD 作學習筆記，經過這段時間的累積，建立自己的部落格來存放自己的筆記是更好的選項，而在眾多的平台選擇了 Hexo。

Hexo 是一個基於 Node.js 的靜態部落格框架，由於 Hexo 是使用指令來做開發，並在配合 GitHub Pages 進行部屬，可以同時練習指令與 GitHub 版本控制。

Hexo 是使用 MarkDown 撰寫格式，同時也須熟悉 Git 指令與 npm 的知識，可以參考下方連結教學。


* [MarkDown 語法大全](https://hackmd.io/@eMP9zQQ0Qt6I8Uqp2Vqy6w/SyiOheL5N/%2FBVqowKshRH246Q7UDyodFA)
* [Git 教學 - 為你自己學 Git](https://gitbook.tw/)
* [npm 基本常用指令](https://seanacnet.com/npm/npm-common-commands/)

## 2. 環境準備

### 2.1 安裝必要工具
在開始之前，請確保你的電腦已安裝以下工具：
* [Nodejs](https://nodejs.org/en/) : 建議使用最新的 LTS 版本
* [Git](https://git-scm.com/) : 版本控制
* [GitHub 帳號](https://github.com/) : 用於存放部落格原始碼與靜態頁面
* [Visual Studio Code](https://code.visualstudio.com/) : 編輯器，也可以用自己習慣的 IDE 來編輯。

**本文版本環境**
* 作業系統： Windows10 X64
* Nodejs:：v20.18.2 LTS
* IDE：VS Code

**Hexo 版本**
* hexo: 7.3.0
* hexo-cli: 4.3.2

### 2.2 檢查安裝

可以使用輸入以下指令在終端機確認是否安裝成功：
```bash
node -v   # 確認 Node.js 版本
git --version  # 確認 Git 版本
```

確認上述兩個工具安裝好後，接下來就可以開始安裝Hexo了。


## 3. 安裝與初始化 Hexo

### 3.1 安裝 Hexo CLI
依照 [Hexo官方文件](https://hexo.io/zh-tw/docs/#%E5%AE%89%E8%A3%9D) 指示，在終端機中執行以下指令 : 


```bash
npm install -g hexo-cli
```

### 3.2 初始化 Hexo 專案
``` bash
hexo init my-blog # 建立 my-blog 資料夾
cd my-blog # 切換到專案資料夾
npm install # 下載所需要的套件
```

### 3.3 啟動本地伺服器
在本地啟動 Hexo 的伺服器 :
```bash
hexo server
```

打開瀏覽器在網址輸入 `http://localhost:4000`，就會看到Hexo出現在瀏覽器上囉。

## 4. GitHub Page 準備事項

### 4.1 設定 GitHub 儲存庫 ( repository )

1. 在 GitHub 建立一個新的儲存庫( repository ) ，建議使用 `<github-username>.github.io`
例如 : `Rodchang12.github.io`
![image](https://hackmd.io/_uploads/SJ6bGcx_Je.png)

* 名稱可以設立自己的使用者名稱或是暱稱，記得 `.github.io` 要加上去。
* 權限設定為 `Public` (公開)。
* 其他不用更動，按下綠色按鈕( Create repository )即可建立。

2. 複製 GitHub Repository 的連結
![image](https://hackmd.io/_uploads/Sy2BqjedJl.png)

### 4.2 在 Hexo 專案資料夾中設定
1. `._config.yml` 設定爲以下調整 : 
```yaml=
# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
  type: git
  repo: 前面複製的 Github Repository 網址 
 #repo: https://github.com/usuename/username.github.io.git
  branch: master # 預設分支名稱
  message:
```
參考 : [Hexo官方文件](https://hexo.io/zh-tw/docs/one-command-deployment#Git)

2. 安裝[部署外掛](https://github.com/hexojs/hexo-deployer-git) : 
```bash
npm install hexo-deployer-git --save
```
3. 將 Hexo 產生的網站內容上傳到 GitHub : 
```bash
hexo clean && hexo deploy
```

4.重新整理 Github 的 repository ，確認是否上傳內容成功 
* 進入右側的 `Deployments` :
![image](https://hackmd.io/_uploads/r1B5k2lO1l.png)
* 輸入上面的網址或點擊連結 : 
![image](https://hackmd.io/_uploads/HkCDg2gu1l.png)
* 就可以看到 Hexo 的網站順利地架在 Github 的 Page 上囉，預設主題會是 `Landscape`
![image](https://hackmd.io/_uploads/SyLB-hgd1x.png)


## 5. 撰寫與管理文章
### 5.1 建立新文章
```bash
hexo new "第一篇文章"
```
而文章會新增在目錄的 `source/_posts/<文章名稱>.md`。
附檔名為 `.md`，開啟檔案會發現這是一個「Markdown」檔。

### 5.2 文章格式
* 開頭基本資訊 : 
```yaml
---
title: 我的第一篇文章
date: 2025-01-24 12:00:00
categories: 
    - 技術筆記
tags: 
    - Hexo
    - Blog
---
```

* 文章內容 : 
```yaml=
## 標題
第一行文字...
第二行...

### 次標題
插入圖片
![圖片說明](image.png)
```
* 更多 `MarkDown` 語法請參考 : [MarkDown 語法大全](https://hackmd.io/@eMP9zQQ0Qt6I8Uqp2Vqy6w/SyiOheL5N/%2FBVqowKshRH246Q7UDyodFA)



### 5.3 在本地端預覽文章
```bash
hexo generate
hexo server
```


## 6. 進階設定
### 6.1 更換 Hexo 主題
Hexo 在建立後會有預設主題，可以在 [Hexo Themes](https://hexo.io/themes/) 找到喜歡的主題，並按照說明安裝。
![image](https://hackmd.io/_uploads/SJGGNnxOkx.png)
本文選擇使用[NexT](https://github.com/next-theme/hexo-theme-next)這套主題，接下來所需的步驟是

* 安裝 NexT 主題樣式
```bash
npm install hexo-theme-next
```

* 開啟 `._config.yml` 檔案，更改 `theme`設定 : 
```bash
theme: next
```

* 在本機端啟動 Hexo 伺服器，確認是否套用到 NexT 主題樣式的網站 !
```bash
hexo server
```

### 6.2 設定自訂網域
其實上述步驟已經足夠讓自己的 Blog 免費地架在網路上了，美中不足的就只是網址就會是呈現 <github_username>.github.io 的格式。
如果你有自己的網域，可以在 GitHub Pages 設定 CNAME 來綁定網域名稱。





