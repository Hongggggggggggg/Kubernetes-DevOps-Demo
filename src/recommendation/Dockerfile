# 使用 Python 3.12 的 slim 版映像檔（Bookworm 版本）
FROM python:3.12-slim-bookworm

# 設定工作目錄為 /usr/src/app
WORKDIR /usr/src/app

# 將 requirements.txt 複製到容器中
COPY requirements.txt ./

# 更新 apt 資料庫並安裝 gcc、python3-dev 與 build-essential
# 這些工具提供編譯 C/C++ 擴充套件所需的環境
RUN apt-get update && apt-get install -y \
    gcc \
    python3-dev \
    build-essential

# 更新 pip 至最新版
RUN pip install --upgrade pip

# 根據 requirements.txt 安裝所有 Python 依賴套件
RUN pip install -r requirements.txt

# 複製專案中所有檔案到容器的工作目錄
COPY . .

# 設定容器啟動時執行的指令，啟動 recommendation_server.py
ENTRYPOINT ["python", "recommendation_server.py"]
