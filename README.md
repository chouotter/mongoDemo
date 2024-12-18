# Student Hub 專案
這是一個前後端分離的專案（基於MVC架構）。

### 功能
* Create: 新增資料
* Read: 查詢資料
* Update: 更新資料
* Delete: 刪除資料

### 安裝與執行指引
#### 環境需求
* 前端開發 : React + ts
* 後端開發 : Node.js + Express
* 資料庫 : MongoDB
* API測試 : PostMan
* 安裝套件 : npm

#### 瀏覽應用
在瀏覽器中打開 http://localhost:5173 來使用應用。

### API 規格說明
#### API 基本資訊
* Base URL : /api/v1/user/
* 格式 : JSON
#### 查詢學生資料(Read)
* GET 方法
* 描述 : 根據學生的缺席次數、姓名或座號查詢資料。

#### 新增學生資料(Create)
* POST 方法
* 描述 : 新增一筆學生資料。

(請求參數)
* Body :
```typescript
{
    "userName": "tkuim1234",
    "name": "王大明",
    "department": "資訊管理學系",
    "grade": "6",
    "class": "g",
    "Email": "min@gmail.com"
}
```

(回應)
* 成功 : 
```typescript
{
    "code": 200,
    "message": "",
    "body": {
        "userName": "tkuim1234",
        "name": "王大明",
        "department": "資訊管理學系",
        "grade": "6",
        "class": "g",
        "Email": "min@gmail.com"
        "_id": "6759b6c52927e07a0ddeb599",
        "__v": 0
    }
}
```

* 失敗 : 
```typescript
{
  "code": 403,
  "message": ""
}
```

#### 刪除學生資料(Delete)
* DELETE 方法
* 根據帳號刪除學生資料。

(請求參數)
* Body :
```typescript
{
  "userName": "tkuim1234"
}
```

(回應)
* 成功 : 
```typescript
{
  "code": 200,
  "message": "刪除成功",
  "body": {
    "userName": "tkuim1234"
  }
}
```

* 失敗 : 
```typescript
{
  "code": 400,
  "message": "用戶名是必需的"
}
```

#### 更新學生資料(Update)
* PUT 方法
* 根據帳號更新學生名字。

(請求參數)
* Body :
```typescript
{
  "userName": "tkuim1234",
  "name": "王大明"
}
```

(回應)
* 成功 : 
```typescript
{
  "code": 200,
  "message": "更新成功",
  "body": {
    "userName": "tkuim1234",
    "name": "王大明"
  }
}
```

* 失敗 : 
```typescript
{
  "code": 400,
  "message": "userName 和 name 是必需的參數"
}
```

### 架構圖 : 展示前端、後端、資料庫及其互動
![架構圖](image.png)

### 流程圖：描述 CRUD 功能的操作流程。
#### 流程圖
![流程圖](image-1.png)

#### 流程解說
1. 使用者操作前端界面 : 使用者在 React 前端界面上提交表單或點擊按鈕（新增、查詢、更新或刪除學生資料）。
2. 前端處理請求 : 前端透過 Fetch，向後端 Express 伺服器發送 HTTP 請求（如 POST、GET、PUT、DELETE）。
3. 後端路由匹配 : 後端根據請求的路徑和方法，在路由層 (Route) 找到對應的控制器方法。
4. 控制器處理請求邏輯 : 控制器 (Controller) 接收請求，調用服務層 (Service)，執行業務邏輯（如驗證學生資料、格式化數據等）。
5. 服務層與數據模型交互 : 服務層負責與數據模型 (Model) 交互，進行資料庫操作（如新增、查詢、更新或刪除）。
6. 數據模型與 MongoDB 交互 : 數據模型 (Model) 使用 Mongoose 與 MongoDB 進行資料交互，完成對數據庫的增、刪、改、查操作。
7. 結果返回 : 最終結果從數據庫返回給控制器，再經由路由層返回給前端。
8. 前端界面更新 : 前端接收後端的回應數據，更新界面顯示。