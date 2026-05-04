# WuangWuang Chat

Giao diện chat có xác thực người dùng, lưu lịch sử hội thoại và tích hợp mô hình ngôn ngữ qua Ollama.

## 👤 Thông tin sinh viên

- Họ tên: **Trần Công Quang**
- MSSV: **24120221**
- Trường: **Đại học Khoa học Tự nhiên**
- Môn Học: **Tư Duy Tính Toán**

## 📌 Giới thiệu đồ án

Đồ án xây dựng hệ thống chat gồm **backend FastAPI** và **frontend Streamlit**.  
Người dùng đăng ký/đăng nhập (email hoặc Google), lịch sử chat được lưu trên Firestore, và trả lời được sinh bởi mô hình chạy qua **Ollama**.

## 🚀 Features

- Lightweight chat UI
- **User authorization before chatting**
- **Save and load chat data**
- Stores chat history in session state
- Easy to extend with any AI or backend API

## 🧰 Yêu cầu

- Python 3.x
- Streamlit
- Các dependencies trong `requirements.txt`
- Ollama (nếu muốn dùng LLM local)

## 🧱 Cấu trúc dự án

```
chatbot-page-wuang/
├─ backend/                 # FastAPI
├─ frontend/                # Streamlit UI
├─ .streamlit/secrets.toml  # Firebase + Google OAuth config
├─ .env                     # OLLAMA_HOST, OLLAMA_MODEL
├─ requirements.txt
```

## ⚙️ Cài đặt

```bash
cd chatbot-page-wuang
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
pip install fastapi uvicorn
```

## 🔐 Cấu hình secrets

File bắt buộc:
```
.streamlit\secrets.toml
```

File này chứa:
- `[firebase_client]`
- `[firebase_admin]`
- `[google-login]`

> Nếu chạy từ thư mục `frontend`, hãy đảm bảo có `frontend\.streamlit\secrets.toml` hoặc chạy từ root để Streamlit tự tìm đúng file.

## 🤖 Cấu hình Ollama

`.env` (ở root):
```
OLLAMA_HOST=http://localhost:11434
OLLAMA_MODEL=llama3.2:1b
```

Chạy Ollama:
```bash
ollama serve
ollama pull llama3.2:1b
```

## ▶️ Hướng dẫn chạy

Mở **2 terminal** trong thư mục `chatbot-page-wuang`.

### 1) Chạy Backend (FastAPI)
```bash
cd chatbot-page-wuang
.venv\Scripts\Activate.ps1
$env:OLLAMA_HOST="http://localhost:11434"
$env:OLLAMA_MODEL="llama3.2:1b"
python -m uvicorn backend.app.main:app --reload --port 8000
```

Kiểm tra nhanh:
```
http://localhost:8000/health
```

### 2) Chạy Frontend (Streamlit)
```bash
cd chatbot-page-wuang
.venv\Scripts\Activate.ps1
streamlit run frontend\app.py
```

Mở trình duyệt:
```
http://localhost:8501
```

## 🛠️ Troubleshooting nhanh

- **Lỗi StreamlitSecretNotFoundError**: chạy từ root repo hoặc đảm bảo `frontend\.streamlit\secrets.toml` tồn tại.
- **Không truy cập được `localhost:8000`**: backend chưa chạy hoặc bị crash do thiếu secrets.
- **Chat lỗi 500**: Ollama chưa chạy hoặc sai `OLLAMA_HOST`.

## 🎬 Video Demo

Xem video demo: [https://youtu.be/42ebPqrAQf8?si=PN5JxtC84FKEaYLH](https://youtu.be/42ebPqrAQf8?si=PN5JxtC84FKEaYLH)

