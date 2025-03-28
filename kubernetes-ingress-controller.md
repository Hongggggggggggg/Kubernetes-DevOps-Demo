# 如何在本地設置 Kubernetes 環境
## 本地 Minikube 環境設置

如果您想在本地環境測試應用程式，可以使用 Minikube 來模擬 Kubernetes 集群。以下是設置本地環境的步驟：

### 前置需求

1. 安裝 Minikube
   ```bash
   # macOS (使用 Homebrew)
   brew install minikube
   ```

2. 安裝 kubectl
   ```bash
   brew install kubectl
   ```

3. 啟動 Minikube
   ```bash
   minikube start
   ```

### 啟用 Ingress 插件

在 Minikube 中啟用 Ingress 控制器：

```bash
minikube addons enable ingress
```

確認 Ingress 控制器已成功啟動：

```bash
kubectl get pods -n ingress-nginx
```

### 設置本地域名解析

1. 獲取 Minikube IP 地址：

   ```bash
   minikube ip
   ```
   
   該命令會輸出 Minikube 虛擬機的 IP 地址，例如 `192.168.49.2`

2. 編輯 hosts 檔案：

   ```bash
   sudo nano /etc/hosts
   ```

3. 添加以下條目（使用您實際獲取的 Minikube IP）：

   ```
   192.168.49.2 devops-demo.local
   ```
   
   > **注意**：請將 `192.168.49.2` 替換為執行 `minikube ip` 命令後實際獲取的 IP 地址。

### 部署應用程式與 Ingress

1. 部署您的應用程式服務

2. 應用 Ingress 配置：

   ```bash
   kubectl apply -f kubernetes/frontendproxy/ingress.yaml
   ```

3. 驗證 Ingress 是否已創建：

   ```bash
   kubectl get ingress
   ```

### 使用 Minikube 隧道

1. 在獨立的終端視窗中執行隧道命令：

   ```bash
   minikube tunnel
   ```

   > **重要提示**：該命令需要在獨立終端視窗中執行，並保持運行狀態。這個命令會請求 sudo 權限，因為它需要綁定本地機器的 80/443 端口。

執行 tunnel 命令後，您就可以透過以下網址直接訪問應用程式：

```
http://devops-demo.local
```

無需指定任何端口號，系統會自動將請求路由到 Kubernetes 集群內的適當服務。

### 故障排除

1. 如果無法訪問服務，請確保 minikube tunnel 正在運行
2. 檢查 Ingress 控制器狀態：
   ```bash
   kubectl get pods -n ingress-nginx
   ```
3. 檢查 Ingress 資源配置：
   ```bash
   kubectl describe ingress frontend-proxy
   ```

當您完成測試後，可以按 `Ctrl+C` 停止 Minikube 隧道，並使用以下命令關閉 Minikube：

```bash
minikube stop
```