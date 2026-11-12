# CẨM NANG ĐIỆN TỬ VẬN HÀNH HỆ THỐNG ERP / MRP (NEOBAGS V25.02)

Dự án Cẩm nang hướng dẫn sử dụng trực quan kết hợp Trợ lý ảo AI Client-side dành cho hệ thống quản lý sản xuất và hoạch định nhu cầu nguyên phụ liệu (ERP/MRP) của doanh nghiệp may túi xách NEOBAGS.

---

## 1. CẤU TRÚC BỘ TÀI LIỆU & MÃ NGUỒN

```text
D:\SVG\AI_Agent\manual\MRP\
├── index.html          # [CHÍNH] Ứng dụng web Single Page Application tương tác & Chatbot AI
├── manual.md           # [TÀI LIỆU] Cẩm nang chi tiết định dạng Markdown đầy đủ nội dung
├── robots.txt          # [BẢO MẬT] Cấu hình chặn 100% crawler công cụ tìm kiếm và bot AI
├── README.md           # [HƯỚNG DẪN] Hướng dẫn mở trang và kích hoạt GitHub Pages
├── docs/               # [TÀI LIỆU KÈM THEO] Báo cáo khảo sát, ma trận nút bấm, đặc tả luồng
└── pages/              # [GIAO DIỆN THAM CHIẾU] Màn hình khảo sát thực tế (Desktop PC Mode)
```

---

## 2. HƯỚNG DẪN MỞ & SỬ DỤNG TRANG CẨM NANG

- **Cách 1: Xem trực tiếp offline không cần server:**
  - Nhấp đúp chuột vào file `index.html` hoặc mở bằng bất kỳ trình duyệt web hiện đại nào (Chrome, Edge, Firefox, Brave...).
  - Toàn bộ giao diện, bảng tra cứu và Chatbot AI đều chạy độc lập client-side 100% mà không phụ thuộc vào internet hay backend máy chủ ngoài.

- **Cách 2: Phím tắt & Tính năng tương tác:**
  - `Ctrl + K`: Đưa con trỏ nhanh vào thanh tìm kiếm toàn cục.
  - Các nút lọc vai trò (Merchandiser, Kỹ thuật, Mua hàng, Kho, Kế hoạch, Admin) giúp thu gọn nội dung hiển thị theo đúng nhiệm vụ.
  - Nhấp vào biểu tượng 💬 ở góc dưới bên phải để mở Trợ lý ảo AI MRP có sẵn 30+ chủ đề nghiệp vụ, nhận diện câu hỏi ngữ cảnh đa lượt.

---

## 3. CHÍNH SÁCH BẢO MẬT & BẢO VỆ DỮ LIỆU NỘI BỘ

1. **Không chứa URL nội bộ:** Mọi liên kết hệ thống thực tế đều được chuẩn hóa thành *"Cổng thông tin hệ thống MRP nội bộ"*.
2. **Chặn thu thập dữ liệu tự động:**
   - Thẻ Meta trong `index.html`: `<meta name="robots" content="noindex, nofollow, noarchive, nosnippet, noimageindex">`
   - File `robots.txt` chặn toàn bộ: Googlebot, Bingbot, GPTBot, ClaudeBot, PerplexityBot, CCBot, Bytespider, Applebot.

---

## 4. HƯỚNG DẪN KHỞI TẠO GIT & TRIỂN KHAI GITHUB PAGES

Khi bạn muốn đưa cẩm nang lên GitHub để chia sẻ nội bộ qua GitHub Pages:

### Bước 1: Khởi tạo Git repository trong thư mục `manual/MRP`
```bash
cd D:\SVG\AI_Agent\manual\MRP
git init
git add .
git commit -m "feat: release interactive MRP manual V25.02 with smart client-side chatbot"
```

### Bước 2: Liên kết với Remote Repository trên GitHub
```bash
# Thay <USERNAME> và <REPO_NAME> bằng kho lưu trữ của bạn
git remote add origin https://github.com/<USERNAME>/<REPO_NAME>.git
git branch -M main
git push -u origin main
```

### Bước 3: Kích hoạt GitHub Pages
1. Truy cập vào Repository trên GitHub: **Settings** ➔ **Pages**.
2. Tại mục **Build and deployment** ➔ **Source**, chọn: `Deploy from a branch`.
3. Tại mục **Branch**, chọn `main` và thư mục `/ (root)`, sau đó bấm **Save**.
4. Sau khoảng 1-2 phút, trang web cẩm nang của bạn sẽ hoạt động tại địa chỉ:
   `https://<USERNAME>.github.io/<REPO_NAME>/`
