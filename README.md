# DevOps 微服務電商應用展示專案

![Last Updated](https://img.shields.io/badge/最後更新-2025年3月29日-blue)

## 目錄
1. [專案介紹](#專案介紹)  
2. [微服務架構](#微服務架構請點擊圖片以放大檢視)  
3. [技術堆疊](#技術堆疊)  
4. [DevOps 流程說明](#devops-流程說明請點擊圖片以放大檢視)  
5. [快速開始](#快速開始)  
6. [程式碼來源](#程式碼來源)

---

## 專案介紹
這是一個電商展示專案，採用多語言微服務（Java、Python、Golang）為核心，結合 **Docker、Kubernetes、GitHub Actions、Argo CD** 等工具，實踐容器化與自動化 **CI/CD** 流程。  
- **電商場景**：展示典型電商應用的複雜度（如訂單管理、商品服務、推薦系統等），驗證微服務架構的彈性與可維運性。  
- **DevOps 與 GitOps**：從程式碼提交、品質檢測、Docker Build & Push，到 Kubernetes 叢集部署與自動更新，展現持續整合（CI）與持續交付（CD）的最佳實踐。

---

## 微服務架構（請點擊圖片以放大檢視）
<img width="919" alt="image" src="https://github.com/user-attachments/assets/7991fa70-dc82-4fff-af3b-7d4591b08e5f" />

#### 本專案由多人協作完成，所有下列服務皆可於此專案中部署與測試。
#### 為方便讀者了解開發分工，特別標示「由本人開發」或「由其他開發者開發」。

### 由本人開發
- **Product-Catalog**：產品目錄服務，管理產品資訊  
- **Ad**：廣告服務，管理平台廣告投放  
- **Recommendation**：產品推薦服務，提供個性化推薦  

### 由其他開發者開發
- **Cart**：購物車服務，處理用戶購物車操作  
- **Checkout**：結帳流程服務，處理訂單生成流程  
- **Payment**：支付處理服務，處理交易與支付流程  
- **Shipping**：配送服務，處理物流和運輸管理  
- **Email**：電子郵件通知服務，負責系統郵件發送  
- **Currency**：貨幣轉換服務，處理多幣種支持  
- **Fraud-Detection**：詐騙檢測服務，識別可疑交易  
- **Image-Provider**：圖片提供服務，管理產品圖片資源  
- **Quote**：報價服務，提供動態定價  
- **Accounting**：會計服務，處理財務與記賬  
- **React-Native-App**：行動裝置前端服務，提供手機端體驗
- **Kafka**：事件訊息佇列服務，實現服務間通信  
- **Load-Generator**：負載測試服務，模擬用戶流量  
- **Prometheus**：時序資料庫，收集和存儲監控指標  
- **Grafana**：資料視覺化儀表板，展示系統指標  
- **OTel-Collector**：OpenTelemetry 收集器，處理遙測資料收集  

---

## 技術堆疊

### 開發語言
- Java  
- Golang  
- Python  

### DevOps 工具
- **容器化**：Docker  
- **協調管理**：Kubernetes  
- **版本控制**：Git / GitHub  
- **CI/CD**：  
  - GitHub Actions（持續整合）  
  - Argo CD（持續部署）

---

## DevOps 流程說明（請點擊圖片以放大檢視）
![DevOps 流程-2025-03-29-113549](https://github.com/user-attachments/assets/2a35aaf3-e947-4f18-b3b6-d5b810d2765b)

### 本專案實現了一站式 CI/CD 自動化流程，從程式碼提交到部署無需人工介入：
1. **開發人員提交代碼**  
   - 將變更推送至 GitHub 儲存庫
   - 提交 Pull Request 
2. **觸發 GitHub Actions**  
   - 執行程式碼品質檢查  
   - 建構容器映像  
   - 推送映像至容器儲存庫  
   - 更新 Kubernetes Deployment 設定檔  
3. **Argo CD 監控映像更新**  
   - 每三分鐘偵測 GitHub 儲存庫的變更  
   - 自動更新 Kubernetes 資源並套用新的部署設定  

---

## 快速開始

### 本地開發環境

1. **複製儲存庫**  
   ```bash
   git clone https://github.com/Hongggggggggggg/devops-demo.git
   cd devops-demo
   ```
2. **使用 Docker Compose 啟動本地環境**  
   ```bash
   docker-compose up
   ```

### Kubernetes 部署

1. **應用 Kubernetes 資源**  
   ```bash
   kubectl apply -f kubernetes/complete-deploy.yaml
   ```
2. **訪問應用程式**  
   ```bash
   kubectl port-forward svc/opentelemetry-demo-frontendproxy 8080:8080
   ```
   在瀏覽器中開啟 [http://localhost:8080](http://localhost:8080)

---

## 程式碼來源

- [opentelemetry.io](https://opentelemetry.io/)
