# Dashboard phân tích biến động giá cổ phiếu ABC-20 (ipywidgets + Voilà)

## Cấu trúc thư mục
| File | Vai trò |
|---|---|
| `app.ipynb` | Notebook chứa toàn bộ dashboard (Voilà sẽ chạy file này) |
| `abc-20.csv` | Dữ liệu (365 phiên × 7 cột, không có dòng tiêu đề) |
| `requirements.txt` | Danh sách thư viện để Render cài |
| `render.yaml` | (tuỳ chọn) cấu hình sẵn cho Render Blueprint |

## Bước 1 – Chạy thử trên máy
```bash
pip install -r requirements.txt
voila app.ipynb
```
Trình duyệt tự mở trang dashboard (mặc định http://localhost:8866). Thử bấm Cập nhật / Đặt lại / Xuất CSV.

## Bước 2 – Đưa lên GitHub
```bash
git init
git add .
git commit -m "Dashboard ABC-20"
git branch -M main
git remote add origin https://github.com/<ten-ban>/abc20-dashboard.git
git push -u origin main
```

## Bước 3 – Deploy lên Render
1. Vào https://render.com → **New +** → **Web Service** → chọn repo vừa push.
2. Điền:
   - **Runtime:** Python 3
   - **Build Command:** `pip install -r requirements.txt`
   - **Start Command:** `voila app.ipynb --port=$PORT --no-browser --Voila.ip=0.0.0.0`
   - **Instance Type:** Free
   - **Environment Variable:** `PYTHON_VERSION` = `3.11.9`
3. Bấm **Create Web Service**, chờ build xong sẽ có link dạng `https://abc20-dashboard.onrender.com`.

(Hoặc chọn **New + → Blueprint** để Render đọc `render.yaml` và tự điền các mục trên.)

## Lưu ý
- Gói Free của Render sẽ "ngủ" sau ~15 phút không có người truy cập; lần mở đầu tiên có thể mất 30–60 giây.
- Mỗi lần mở trang, Voilà chạy lại toàn bộ notebook nên trang cần vài giây để hiện biểu đồ đầu tiên.
- Nếu tài liệu hướng dẫn của thầy có lệnh khác (tên file, Start Command), hãy ưu tiên làm theo tài liệu của thầy.
