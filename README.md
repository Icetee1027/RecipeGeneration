# 食譜生成器 API

這是一個使用 Go 和 Gemini AI 開發的食譜生成器 API。

## 功能

- 接收前端傳送的設備和食材資訊
- 使用 AI 生成食譜
- 回傳標準化的食譜格式

## 安裝

1. 複製專案：
```bash
git clone [repository-url]
cd recipe-generator
```

2. 安裝依賴：
```bash
go mod download
```

3. 設置環境變數：
```bash
cp .env.example .env
# 編輯 .env 檔案，填入您的 Gemini API 金鑰
```

## 運行

```bash
go run main.go
```

## API 端點

### 生成食譜

- **URL**: `/generate-recipe`
- **方法**: `POST`
- **請求格式**:
```json
{
    "equipment": [
        {
            "name": "平底鍋",
            "type": "鍋具",
            "size": "中型",
            "material": "不鏽鋼"
        }
    ],
    "ingredients": [
        {
            "name": "油",
            "type": "食材",
            "amount": "2湯匙",
            "unit": "湯匙"
        }
    ],
    "preference": {
        "cooking_method": "煎",
        "doneness": "中等熟"
    }
}
```

- **回應格式**:
```json
{
    "dish_name": "菜名",
    "dish_description": "菜餚描述",
    "recipe": [
        {
            "step": "步驟說明",
            "time": "所需時間",
            "temperature": "溫度",
            "description": "描述",
            "doneness": "熟度（如果適用）"
        }
    ]
}
```

## 使用 Docker

```bash
docker build -t recipe-generator .
docker run -p 8080:8080 recipe-generator
``` 