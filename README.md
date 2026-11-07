# 📚 Hướng Dẫn Deploy Sổ Tay Ôn Thi VLDC2 Lên Render (render.com)

Thư mục này (`vldc2-web-deploy/`) chứa toàn bộ mã nguồn web độc lập, sẵn sàng để deploy lên internet miễn phí và sử dụng tức thì trên mọi thiết bị (máy tính, điện thoại, máy tính bảng).

---

## 🌟 1. Cơ Chế Hoạt Động & Độc Lập Cho Từng Máy

- **100% Client-Side (Không xung đột giữa các máy):** Toàn bộ dữ liệu tương tác gồm:
  - 🌙 / ☀️ Chế độ Sáng / Tối (Dark / Light Theme).
  - ⭐ Danh sách công thức và đề mục được đánh dấu sao (Bookmarks).
  - 📝 Sổ tay ghi chú cá nhân (tách theo từng chương và ghi chú chung).
- Toàn bộ dữ liệu trên được lưu trữ độc lập trong `localStorage` của trình duyệt trên máy của mỗi cá nhân.
- **Không chia sẻ trạng thái**: Máy của bạn A lưu ghi chú của bạn A, máy bạn B lưu ghi chú của bạn B, không bao giờ xảy ra xung đột hay lộ dữ liệu lẫn nhau.

---

## 🚀 2. Hướng Dẫn Deploy Lên Render.com (Miễn Phí 100%)

Render cung cấp dịch vụ **Static Site** hoàn toàn miễn phí, băng thông cao, hỗ trợ HTTPS tự động và **không bao giờ bị sleep (ngủ)** sau thời gian không dùng.

### Cách 1: Deploy qua GitHub (Khuyên dùng - Cập nhật tự động)

1. **Khởi tạo và đẩy code lên GitHub:**
   - Mở terminal trong thư mục `vldc2-web-deploy/`:
   ```bash
   cd vldc2-web-deploy
   git init
   git add .
   git commit -m "Khoi tao so tay VLDC2 web deploy"
   git branch -M main
   # Tạo 1 repository mới trên GitHub (ví dụ: vldc2-handbook) rồi liên kết:
   git remote add origin https://github.com/<tai-khoan-cua-ban>/vldc2-handbook.git
   git push -u origin main
   ```

2. **Kết nối với Render:**
   - Đăng nhập vào [Render Dashboard](https://dashboard.render.com).
   - Chọn nút **New +** ở góc trên cùng bên phải -> chọn **Static Site**.
   - Kết nối với tài khoản GitHub của bạn và chọn repository `vldc2-handbook` vừa tạo.

3. **Cấu hình trên Render:**
   - **Name:** `vldc2-handbook` (hoặc tên tùy ý)
   - **Branch:** `main`
   - **Build Command:** *(để trống - không cần build)*
   - **Publish Directory:** `./`
   - Bấm **Create Static Site**.

4. **Hoàn tất:**
   - Render sẽ cấp cho bạn một đường link public miễn phí, ví dụ:  
     `https://vldc2-handbook.onrender.com`
   - Chia sẻ link này cho bạn bè hoặc mở trên điện thoại/laptop để ôn thi mọi lúc mọi nơi!

---

### Cách 2: Deploy bằng Render Blueprint (File `render.yaml`)

Trong thư mục đã có sẵn file `render.yaml`. Khi bạn kết nối repository GitHub với Render, Render sẽ tự nhận diện Blueprint này và cấu hình toàn bộ thông số tự động mà không cần bạn chỉnh tay bất kỳ mục nào.

---

## 💻 3. Chạy Thử Nghiệm Trên Máy Cục Bộ (Local Test)

Trước khi đẩy lên web, bạn có thể kiểm tra trực tiếp:

1. **Cách nhanh nhất:** Click đúp chuột trực tiếp vào file `index.html` để mở trong trình duyệt Chrome, Edge hoặc Cốc Cốc.
2. **Cách chạy server cục bộ:**
   ```bash
   python serve_local.py
   ```
   Trình duyệt sẽ tự động mở trang web tại địa chỉ `http://localhost:8000`.

---

## 📂 4. Cấu Trúc Các File Trong Thư Mục

| Tên File | Chức Năng |
| :--- | :--- |
| `index.html` | Trang web chính: Sổ tay ôn thi VLDC2 (3 chương đầu) kèm bộ lọc, tìm kiếm, lưu trữ cá nhân, MathJax 3 và SVG diagrams |
| `conflict-report.html` | Báo cáo chi tiết xung đột và sai lệch công thức giữa các bản tóm tắt cũ kèm hướng dẫn chuẩn mực |
| `render.yaml` | File cấu hình tự động triển khai Static Site trên nền tảng Render.com |
| `serve_local.py` | Script Python giúp chạy server test nhanh trên localhost:8000 |
| `.gitignore` | Bỏ qua các file rác, file tạm hệ thống khi đẩy lên Git |
| `README.md` | Tài liệu hướng dẫn sử dụng và triển khai (file này) |
