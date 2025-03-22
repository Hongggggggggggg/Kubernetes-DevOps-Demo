# 使用 eclipse-temurin:20-jdk 作為基礎映像，並將此階段命名為 builder
FROM eclipse-temurin:20-jdk AS builder

# 設定工作目錄為 /usr/src/app
WORKDIR /usr/src/app

# 複製與 Gradle 相關的檔案 (gradle 包含開頭為 gradle 的檔案、build.gradle 以及 settings.gradle)
COPY gradle* build.gradle settings.gradle* ./

# 複製 gradle 資料夾到容器中
COPY ./gradle ./gradle

# 為 gradlew 指令加上執行權限
RUN chmod +x ./gradlew

# 執行預設的 Gradle 任務（可能會下載依賴或初始化設定）
RUN ./gradlew

# 執行 Gradle 任務以快取依賴，將所有所需的 jar 檔案下載下來
RUN ./gradlew downloadRepos

# 複製專案中的所有檔案到工作目錄
COPY . .

# 複製 pb 資料夾至 proto 資料夾，提供 protobuf 定義檔
COPY ./pb ./proto

# 再次確認 gradlew 有執行權限（以防 COPY 過程中權限改變）
RUN chmod +x ./gradlew

# 執行 Gradle 任務，產生可執行的發行版，並指定 protoSourceDir 參數
RUN ./gradlew installDist -PprotoSourceDir=./proto

# 使用 eclipse-temurin:20-jre 作為最終運行映像，並命名此階段為 release
FROM eclipse-temurin:20-jre AS release

# 設定工作目錄
WORKDIR /usr/src/app

# 從 builder 階段複製整個 /usr/src/app 資料夾到此映像中
COPY --from=builder /usr/src/app ./

# 設定環境變數 AD_PORT 為 9099
ENV AD_PORT 9099

# 定義容器啟動時要執行的命令，此處指定應用程式的可執行檔路徑
ENTRYPOINT [ "./build/install/opentelemetry-demo-ad/bin/Ad" ]
