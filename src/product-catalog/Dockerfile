# 使用 golang:1.22-alpine 作為基底映像，並將此階段命名為 builder，用於編譯應用程式
FROM golang:1.22-alpine AS builder

# 設定容器內的工作目錄為 /usr/src/app
WORKDIR /usr/src/app

# 將專案的所有檔案複製到容器內的工作目錄中
COPY . .

# 根據 go.mod 檔案下載所有所需的依賴套件
RUN go mod download

# 編譯 Go 應用程式，輸出可執行檔命名為 product-catalog，存放在目前工作目錄中
RUN go build -o product-catalog ./

# 使用輕量級的 alpine 映像建立運行階段，並將此階段命名為 release
FROM alpine AS release

# 設定運行階段容器內的工作目錄為 /usr/src/app
WORKDIR /usr/src/app

# 複製本地的 products 資料夾到容器內的 products 資料夾（例如存放靜態資源或設定檔）
COPY ./products ./products

# 從 builder 階段複製編譯完成的 product-catalog 可執行檔到目前工作目錄
COPY --from=builder /usr/src/app/product-catalog ./

# 暴露容器運行時所使用的網路埠，由環境變數 PRODUCT_CATALOG_PORT 指定
ENV PRODUCT_CATALOG_PORT 9080

# 設定容器啟動時預設執行的命令，啟動 product-catalog 應用程式
ENTRYPOINT [ "./product-catalog" ]
