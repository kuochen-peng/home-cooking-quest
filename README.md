# Home Cooking Quest｜私房的探索料理

> 一個結合食譜分享、廚藝交流與積分任務系統的料理社群平台

---

## 專案簡介

**Home Cooking Quest** 是一個以「遊戲化」為核心概念設計的料理社群網站。使用者可以：

- 瀏覽官方精選食譜，或以積分解鎖付費食譜
- 在廚藝分享區發表文章、留言互動
- 透過每日簽到、發文、新增食譜等任務累積積分
- 查看個人積分紀錄與收藏食譜
- 管理員可透過後台儀表板管理全站內容

## 功能特色

### 一般使用者

- **首頁** — 輪播橫幅、每日精選食譜、功能介紹區塊
- **精選食譜** — 依類別（中式／日式／西式／甜點／其他）篩選、搜尋食譜，點讚與收藏
- **食譜詳細頁** — 查看食材清單、步驟圖文、營養標示，需積分可解鎖付費食譜
- **廚藝分享** — 發表文章、留言互動、排行榜
- **會員中心** — 個人資料、積分餘額、積分紀錄、收藏食譜列表

### 積分任務系統

| 事件     | 類型 |
| -------- | ---- |
| 每日簽到 | 獲得 |
| 發表文章 | 獲得 |
| 新增食譜 | 獲得 |
| 解鎖食譜 | 消耗 |
| 官方發放 | 獲得 |

---

## 使用技術

| 技術                                                                                      | 版本         | 用途                        |
| ----------------------------------------------------------------------------------------- | ------------ | --------------------------- |
| [Vue 3](https://vuejs.org/)                                                               | ^3.5         | 核心框架（Composition API） |
| [Quasar Framework](https://quasar.dev/)                                                   | ^2.16        | UI 組件庫，支援 PWA         |
| [Vue Router](https://router.vuejs.org/)                                                   | ^4.0         | 前端路由                    |
| [Pinia](https://pinia.vuejs.org/)                                                         | ^3.0         | 狀態管理                    |
| [pinia-plugin-persistedstate](https://prazdevs.github.io/pinia-plugin-persistedstate/)    | ^4.7         | 持久化 store                |
| [Axios](https://axios-http.com/)                                                          | ^1.13        | HTTP 請求                   |
| [VeeValidate](https://vee-validate.logaretm.com/) + [Yup](https://github.com/jquense/yup) | ^4.15 / ^1.7 | 表單驗證                    |
| [Vite](https://vitejs.dev/)                                                               | —            | 建構工具（via Quasar CLI）  |

---

## 專案結構

```
home-cooking-quest_project/
├── back/                          # 後端（Node.js + Express）
│   ├── controllers/               # 業務邏輯控制器
│   │   ├── user.js
│   │   ├── recipe.js
│   │   ├── article.js
│   │   ├── comment.js
│   │   └── mission.js
│   ├── models/                    # Mongoose 資料模型
│   │   ├── user.js                # 含積分紀錄、任務狀態
│   │   ├── recipe.js              # 含食材、步驟、營養標示
│   │   ├── article.js
│   │   ├── comment.js
│   │   └── mission.js
│   ├── routes/                    # API 路由
│   ├── middlewares/               # 中介層（auth、upload）
│   ├── passport/                  # Passport 策略設定
│   ├── cloudinary/                # Cloudinary 設定
│   ├── .env                       # 環境變數（不納入版控）
│   └── index.js                   # 伺服器入口
│
└── home-cooking-quest-quasar/     # 前端（Vue 3 + Quasar）
    ├── src/
    │   ├── pages/                 # 頁面元件
    │   │   ├── IndexPage.vue      # 首頁
    │   │   ├── recipePage.vue     # 精選食譜列表
    │   │   ├── recipeInfo.vue     # 食譜詳細頁
    │   │   ├── articlePage.vue    # 廚藝分享
    │   │   ├── profilePage.vue    # 會員中心
    │   │   ├── loginPage.vue      # 登入
    │   │   ├── registerPage.vue   # 註冊
    │   │   └── admin/             # 後台管理頁面
    │   ├── components/            # 可重用元件
    │   ├── layouts/               # 版面佈局
    │   ├── stores/                # Pinia stores
    │   ├── services/              # API 呼叫封裝
    │   ├── router/                # Vue Router 路由設定
    │   └── boot/                  # Quasar boot 設定
    └── src-pwa/                   # PWA Service Worker
```
