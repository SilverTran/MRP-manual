# CẨM NANG HƯỚNG DẪN SỬ DỤNG HỆ THỐNG ERP / MRP (NEOBAGS V25.02)

> **Hệ thống:** NEOBAGS ERP/MRP V 25.02  
> **Dành cho:** Merchandiser (Đơn hàng), Kỹ thuật/R&D (BOM), Quản lý Sản xuất & Kế hoạch (Planning/PMC), Mua hàng (Purchasing), Quản lý Kho (Warehouse), Giám đốc & Quản trị viên (Admin).  
> **Bản xem trực quan (Web tương tác):** Mở file [`index.html`](file:///D:/SVG/AI_Agent/manual/MRP/index.html) trực tiếp bằng trình duyệt.  
> **Chính sách bảo mật:** Toàn bộ đường dẫn URL nội bộ được ẩn và thay thế bằng định danh chuẩn: *"Cổng thông tin hệ thống MRP nội bộ"*. Hệ thống chặn 100% công cụ tìm kiếm và AI Crawler.

---

## 1. MỤC LỤC TỔNG QUAN

1. [Tổng quan Kiến trúc & Chu trình Dữ liệu Khép kín (End-to-End Flow)](#1-tổng-quan-kiến-trúc--chu-trình-dữ-liệu-khép-kín)
2. [Đăng nhập & Làm quen Giao diện Tiếng Anh (Dark Theme)](#2-đăng-nhập--làm-quen-giao-diện-tiếng-anh)
3. [Phân hệ 1: F/G (Finished Goods) - Quản lý Đơn hàng & BOM](#3-phân-hệ-1-fg-finished-goods---quản-lý-đơn-hàng--bom)
   - 3.1. Quản lý Đơn hàng Khách hàng (`F/G › Buyer order`)
   - 3.2. Quản lý Đơn hàng Tạm tính (`F/G › Temp order`)
   - 3.3. Danh sách Định mức Vật tư (`F/G › BOM-List`)
   - 3.4. Quản lý Chi tiết Định mức Kỹ thuật (`F/G › BOM-Manage`)
   - 3.5. Quản lý Giao hàng & Xuất hàng Thành phẩm (`F/G › Shipment`)
   - 3.6. Quản lý Tồn kho Thành phẩm (`F/G › Stock`)
4. [Phân hệ 2: MATERIAL - Quản lý Nguyên Phụ Liệu, Mua Hàng & Kho](#4-phân-hệ-2-material---quản-lý-nguyên-phụ-liệu-mua-hàng--kho)
   - 4.1. Tính toán Nhu cầu & Đặt mua Vật tư (`MATERIAL › Manage PO` - Trọng tâm MRP)
   - 4.2. Theo dõi Trạng thái Đơn mua Vật tư (`MATERIAL › PO Status`)
   - 4.3. Nhập kho Nguyên phụ liệu (`MATERIAL › Inbound`)
   - 4.4. Xuất kho Cấp phát Sản xuất (`MATERIAL › Outbound`)
   - 4.5. Quản lý Tồn kho & Định giá Tài sản Kho (`MATERIAL › Inventory`)
5. [Phân hệ 3: PRODUCTION - Kế hoạch Sản xuất & Giám sát Chuyền](#5-phân-hệ-3-production---kế-hoạch-sản-xuất--giám-sát-chuyền)
   - 5.1. Lập Lịch Sản xuất & Xếp Chuyền (`PRODUCTION › Schedule-Manage`)
   - 5.2. Lịch Thời gian biểu Trực quan (`PRODUCTION › Schedule-Timetable`)
   - 5.3. Bảng Giám sát Năng suất Từng giờ (`PRODUCTION › Dashboard-Table`)
   - 5.4. Biểu đồ Năng suất & Giám sát Chuyền Thời gian thực (`PRODUCTION › Dashboard-Chart & Line monitor`)
   - 5.5. Theo dõi Sản lượng Mã hàng & Khối (`PRODUCTION › ITEM-Bar & ITEM-Block`)
   - 5.6. Báo cáo Sản lượng & Thống kê Hàng lỗi (`PRODUCTION › Hourly output & Top defect`)
6. [Phân hệ 4: TOOLS - Công cụ Tiện ích & Trình chiếu Xưởng](#6-phân-hệ-4-tools---công-cụ-tiện-ích--trình-chiếu-xưởng)
7. [Phân hệ 5: CONFIG - Thiết lập Hệ thống & Quy chuẩn Xưởng](#7-phân-hệ-5-config---thiết-lập-hệ-thống--quy-chuẩn-xưởng)
8. [Phân hệ 6: CODE - Master Data (Danh mục Dùng chung)](#8-phân-hệ-6-code---master-data-danh-mục-dùng-chung)
9. [Phân hệ 7: ADMIN - Quản trị Người dùng & Phân quyền](#9-phân-hệ-7-admin---quản-trị-người-dùng--phân-quyền)
10. [Bảng Tra cứu Nút bấm & Quy chuẩn Màu sắc](#10-bảng-tra-cứu-nút-bấm--quy-chuẩn-màu-sắc)
11. [Bảng Từ điển Thuật ngữ Chuyên ngành ERP/MRP May mặc](#11-bảng-từ-điển-thuật-ngữ-chuyên-ngành-erpmrp-may-mặc)
12. [Ma trận Sự cố & Hướng dẫn Xử lý Lỗi Nghiệp vụ (FAQ)](#12-ma-trận-sự-cố--hướng-dẫn-xử-lý-lỗi-nghiệp-vụ-faq)

---

## 1. TỔNG QUAN KIẾN TRÚC & CHU TRÌNH DỮ LIỆU KHÉP KÍN

Hệ thống NEOBAGS ERP/MRP vận hành theo chu trình sản xuất công nghiệp khép kín, trong đó dữ liệu của mỗi phân hệ là mắt xích liên kết trực tiếp với phân hệ tiếp theo:

```
[1. KHÁCH HÀNG & KINH DOANH]
   │ Nhận Buyer PO, Style, Color, Qty, ETD, FOB/CMT
   ▼
[2. F/G: BUYER ORDER] (/fg/manage-order)
   │ Tạo mã đơn hàng nội bộ (NEO PO#)
   │ Tải lên hoặc liên kết Định mức vật tư
   ▼
[3. F/G: BOM-MANAGE] (/fg/bom-manage)
   │ Thiết lập chi tiết R/M: Vải (Fabric), Phụ liệu (Trim), Đóng gói (Packing)
   │ Định mức tiêu hao (Consumption), Đơn giá mua (Unit Price), Nhà cung cấp
   ▼
[4. MATERIAL: MANAGE PO - MRP ENGINE] (/material/manage-po)
   │ 1. Tính toán Tổng nhu cầu: Cons(BOM) + Tỷ lệ hao hụt (Loss %)
   │ 2. Cân đối Tồn kho sẵn có: Assign Inventory để bù trừ
   │ 3. Tạo Đơn mua vật tư: Make PO -> Sinh mã Material PO#
   │ 4. Tính toán Chi phí: Unit Price, Thuế Tax, Phí Handling, Phụ phí Surcharge
   ▼
[5. MUA HÀNG & KHO VẬT TƯ]
   ├── [MATERIAL: INBOUND] (/material/inbound): Nhập kho vật tư theo đợt giao (Delivery)
   ├── [MATERIAL: INVENTORY] (/material/inventory): Quản lý tồn theo Location, tính giá trị USD
   └── [MATERIAL: OUTBOUND] (/material/outbound): Xuất cấp phát cho xưởng theo Lệnh sản xuất
   ▼
[6. PRODUCTION: SCHEDULE & GIÁM SÁT]
   ├── [Schedule-Manage] (/Production/ScheduleManage): Phân bổ PO vào Chuyền (Line), In tem QR
   ├── [Dashboard-Table] (/Production/DashboardTable): Theo dõi sản lượng từng giờ (DT1 -> DT8)
   └── [Line Monitor & Top Defect]: Kiểm soát tỷ lệ lỗi QC và tiến độ xuất xưởng
   ▼
[7. F/G: SHIPMENT & STOCK] (/FG/Shipment & /FG/Stock)
   │ Đóng gói (Packed), Kiểm kim (X-Ray), Xuất hàng (Shipped) và Đối soát công nợ
```

---

## 2. ĐĂNG NHẬP & LÀM QUEN GIAO DIỆN TIẾNG ANH

- **Địa chỉ truy cập:** Mở *Cổng thông tin hệ thống MRP nội bộ*.
- **Bước 1:** Tại màn hình đăng nhập, nhập **User ID** và **Password**.
- **Bước 2:** Bấm nút đăng nhập. Sau khi xác thực thành công, hệ thống tự động chuyển về trang điều khiển trung tâm: `F/G › Manage Order`.
- **Đặc điểm giao diện thực tế:**
  - **Giao diện Tối (Dark Theme):** Tông nền đen xám than `#1a1c1e`, chữ trắng tương phản cao, dịu mắt khi vận hành ca dài tại xưởng và văn phòng.
  - **Thanh Header trên cùng:**
    + Góc trái: Logo `ERP`, phiên bản `V 25.02 - NEOBAGS`, và đường dẫn breadcrumb trang hiện tại.
    + Khu vực trung tâm: 7 Menu điều hướng thả xuống (F/G, PRODUCTION, MATERIAL, TOOLS, CONFIG, CODE, ADMIN).
    + Góc phải: Đồng hồ điện tử nhảy giây thời gian thực `[HH : MM : SS]`.

---

## 3. PHÂN HỆ 1: F/G (FINISHED GOODS) - QUẢN LÝ ĐƠN HÀNG & BOM

### 3.1. Quản lý Đơn hàng Khách hàng (`F/G › Buyer order`)
- **Đường dẫn Menu (Breadcrumb):** `F/G ▶ Buyer order` (Đường dẫn: `/fg/manage-order`)
- **Mục đích:** Tiếp nhận đơn hàng chính thức từ khách hàng, tạo mã đơn hàng nội bộ `NEO PO#`, quản lý sản lượng đặt, số lượng đã đóng gói, tồn kho thành phẩm và theo dõi tiến độ xuất hàng.

#### A. Bảng giải thích chi tiết các nút bấm
| Tên Nút Bấm | Màu Sắc | Vị Trí | Chức Năng Nghiệp Vụ | Khi Nào Cần Bấm? |
| :--- | :--- | :--- | :--- | :--- |
| **+ Add PO** | Xanh lá | Thanh công cụ trái | Mở modal nhập thủ công đơn hàng mới | Khi có đơn hàng mới từ khách hàng cần tạo mã NEO PO# đơn chiếc |
| **Add PO (Excel)** | Xanh dương | Cạnh nút Add PO | Mở giao diện tải lên file Excel để nhập hàng loạt PO | Khi tiếp nhận đơn hàng lớn gồm nhiều mã PO / hợp đồng từ Buyer |
| **Template** | Vàng cam | Thanh công cụ | Tải file mẫu Excel chuẩn để điền đơn hàng | Khi cần chuẩn bị dữ liệu Excel trước khi import vào hệ thống |
| **ACTIVE / ARCHIVE / ALL** | Dropdown viền xám | Giữa thanh công cụ | Lọc trạng thái đơn hàng (Đang chạy, Đã lưu trữ, Tất cả) | Dùng để lọc nhanh danh sách đơn hàng cần xử lý |
| **Search** | Xám đen | Cạnh ô tìm kiếm | Thực thi tìm kiếm theo từ khóa đã gõ | Khi cần tìm theo mã NEO PO#, Style, Buyer, Color |
| **btnDisplayUI** (Bánh răng) | Xanh ngọc | Góc phải công cụ | Tùy biến ẩn/hiển thị các cột trên bảng dữ liệu | Khi cần thu gọn màn hình để chỉ xem các cột trọng tâm |
| **D/L AR** | Vàng cam | Tiêu đề cột thao tác | Tải xuống báo cáo kế toán / tiến độ các PO được tick chọn | Khi cần kết xuất dữ liệu đối soát tiến độ và tài chính |
| **ARCHIVE** | Xám viền | Mỗi dòng đơn hàng | Chuyển đơn hàng vào trạng thái lưu trữ (hoàn tất) | Khi PO đã hoàn thành xuất hàng và chốt thanh toán |
| **DEL** | Đỏ | Mỗi dòng đơn hàng | Xóa đơn hàng khỏi hệ thống | Chỉ dùng khi tạo nhầm đơn hàng (chưa phát sinh BOM/Mua hàng) |
| **COPY** | Xanh dương | Mỗi dòng đơn hàng | Sao chép thông tin đơn hàng để tạo PO tương tự | Khi có đơn hàng lặp lại quy cách với PO cũ |

#### B. Cấu trúc các cột dữ liệu
- `LAST MODIFIED` / `USER ID`: Thời gian và mã người sửa gần nhất.
- `NEO PO#`: Mã định danh đơn hàng sản xuất của xưởng (Khóa chính liên kết xuyên suốt).
- `BUYER`: Tên khách hàng / Nhãn hàng (AC, CW, DJ, HS, JW...).
- `BUYER PO #`: Mã PO gốc của khách hàng phát hành.
- `SPLIT PO#`: Mã tách đợt giao nếu đơn hàng được chia nhiều lần xuất.
- `STYLE CODE` / `STYLE NAME`: Mã kiểu dáng và Tên sản phẩm.
- `SEASON` / `COLOR`: Mùa hàng (ví dụ: SP26, FA25) và Tên mã màu sắc.
- `① ORDER QTY`: Tổng số lượng đặt hàng theo hợp đồng.
- `② PACKED`: Số lượng đã qua đóng gói hoàn chỉnh.
- `②-③+④ STOCK`: Tồn kho thành phẩm sẵn sàng giao.
- `③ SHIPPED`: Số lượng thực tế đã xuất hàng lên xe/container.
- `①-③ BAL(SHIP)`: Số lượng còn nợ chưa xuất hàng (Balance = Order - Shipped).
- `FOB` / `CMT`: Đơn giá xuất khẩu FOB hoặc đơn giá gia công CMT.
- `ETD`: Ngày dự kiến xuất hàng (Estimated Time of Departure).
- `BOM`: Trạng thái định mức vật tư gắn với PO (kèm icon liên kết sang BOM).

#### C. Nguồn gốc dữ liệu & Bước tiếp theo
- **Dữ liệu sinh ra từ đâu?** Được nhập từ Đơn đặt hàng của Buyer (PO Sheet / Purchase Contract) hoặc import từ file Excel của bộ phận Merchandiser.
- **Hoàn tất thì làm gì tiếp theo?** Chuyển sang màn hình `F/G › BOM-Manage` để lập định mức vật tư chi tiết cho mã hàng đó.

---

### 3.2. Quản lý Đơn hàng Tạm tính (`F/G › Temp order`)
- **Đường dẫn Menu (Breadcrumb):** `F/G ▶ Temp order` (Đường dẫn: `/fg/temp-order`)
- **Mục đích:** Lưu trữ các đơn hàng dự thảo, đơn hàng chào mẫu (Sample Order) hoặc đơn hàng chưa chốt số lượng chính thức, giúp Merchandiser tính thử định mức vật tư trước khi ký hợp đồng chính thức.

---

### 3.3. Danh sách Định mức Vật tư (`F/G › BOM-List`)
- **Đường dẫn Menu (Breadcrumb):** `F/G ▶ BOM-List` (Đường dẫn: `/fg/bom-list`)
- **Mục đích:** Tra cứu, quản lý phiên bản Revision, tải lên hàng loạt và điều phối định mức kỹ thuật sản phẩm.

#### A. Bảng nút bấm tác vụ
| Tên Nút Bấm | Màu Sắc | Vị Trí | Chức Năng Nghiệp Vụ | Khi Nào Cần Bấm? |
| :--- | :--- | :--- | :--- | :--- |
| **Upload BOM** | Xanh lá | Thanh công cụ | Tải file Excel BOM kỹ thuật lên hệ thống | Khi phòng Kỹ thuật/R&D đã hoàn thiện bảng BOM trên file mẫu |
| **Template BOM** | Vàng cam | Thanh công cụ | Tải file Excel mẫu BOM trắng tiêu chuẩn | Khi cần mẫu file để nhập định mức sản phẩm mới |
| **D/L** (Download) | Vàng | Header cột tác vụ | Xuất các bản ghi BOM đã chọn ra file Excel | Khi cần gửi bảng BOM cho Merchandiser hoặc khách hàng duyệt |
| **DEL** (Delete) | Đỏ | Header cột tác vụ | Xóa hàng loạt các BOM được tick chọn | Khi muốn xóa các bản nháp BOM không sử dụng |
| **MANAGE** | Xanh ngọc / Cyan | Cột thao tác từng dòng | Mở trang biên tập chi tiết định mức BOM | Bấm để vào màn hình cấu hình chi tiết vật tư của mã hàng |

#### B. Cấu trúc các cột bảng BOM-List
- `LAST MODIFIED` / `USER ID` / `USER NAME` / `GROUP`: Dấu vết người biên soạn và cập nhật.
- `BUYER`: Nhãn hàng khách hàng.
- `STYLE CODE` / `STYLE NAME`: Mã thiết kế và Tên sản phẩm balo/túi xách.
- `COLOR NAME`: Tên phối màu của sản phẩm.
- `REVISION`: Phiên bản định mức (V_1, V_2, FINAL...). Giúp kiểm soát chặt chẽ lịch sử thay đổi vật tư.
- `REMARK`: Ghi chú kỹ thuật.

---

### 3.4. Quản lý Chi tiết Định mức Kỹ thuật (`F/G › BOM-Manage`)
- **Đường dẫn Menu (Breadcrumb):** `F/G ▶ BOM-Manage` (Đường dẫn: `/fg/bom-manage?RID={BOM_ID}`)
- **Mục đích:** Khai báo chi tiết 100% nguyên phụ liệu cấu thành nên sản phẩm túi xách/balo: loại vải chính, vải lót, chỉ may, khóa kéo, đầu kéo, nhãn mác, thùng carton, keo dán...

#### A. Công tắc chuyển đổi chế độ biên tập: Checkbox "EDIT" (CỰC KỲ QUAN TRỌNG)
> 🔒 **CƠ CHẾ BẢO VỆ DỮ LIỆU ĐỊNH MỨC:**  
> Nhằm chống việc người dùng vô tình bấm nhầm làm thay đổi sai lệch định mức kỹ thuật hoặc đơn giá vật tư, **mặc định hệ thống khóa cứng 100% bảng BOM ở trạng thái Chỉ Xem (Read-only)**.

- **Vị trí Checkbox `EDIT`:** Nằm trên thanh công cụ (Toolbar) trên cùng, ngay bên phải nút màu vàng `D/L BOM` và bên trái nhãn Model sản phẩm.
- **Tên phần tử:** `<input type="checkbox" name="chkEditBOM"> EDIT`
- **Ý nghĩa & Hành vi khi tick vào Checkbox `EDIT`:**
  1. **Kích hoạt chế độ biên tập (Edit Mode):** Chuyển toàn bộ bảng định mức từ trạng thái khóa sang trạng thái cho phép chỉnh sửa.
  2. **Thay đổi trên Thanh công cụ:**
     - Các nút mặc định (`Open BOM`, `+ CREATE NEW BOM`, `Basic info`, `D/L BOM`, `Search`) lập tức **BỊ ẨN ĐI**.
     - Xuất hiện 2 nút chức năng mới: **`✔ SAVE`** (Xanh lá - Lưu thay đổi vào CSDL) và **`CANCEL`** (Xám - Hủy bỏ chỉnh sửa, hỏi xác nhận `Are you sure?` rồi trả lại trạng thái ban đầu).
  3. **Mở khóa chỉnh sửa trực tiếp (Inline Editing):**
     - Cột **`CONS`** (Định mức tiêu hao): Mở khóa thành ô nhập liệu cho phép gõ trực tiếp số định mức mới.
     - Cột **`U/PRICE`** (Đơn giá): Mở khóa cho phép click vào số để cập nhật giá mua mới.
     - Cột **`CURRENCY`**: Mở khóa thành dropdown chọn loại tiền tệ (USD, VND, CNY).
     - Cột **`REMARK (BOM)`**: Mở khóa cho phép nhập ghi chú vị trí chi tiết trên sản phẩm.
  4. **Kích hoạt công cụ Thêm & Xóa vật tư:**
     - Tại cột `R/M NAME`: Xuất hiện thêm nút bấm màu xanh lá **`+ Add R/M`** để tra cứu và chèn thêm nguyên phụ liệu vào BOM.
     - Cột tác vụ ngoài cùng bên phải **`DEL`** hiện ra:
       + Xuất hiện nút đỏ **`DEL`** trên tiêu đề cột.
       + Xuất hiện checkbox tiêu đề **`chkAllItem`** (tick để chọn tất cả 100% các dòng vật tư trong bảng).
       + Xuất hiện checkbox con **`chkItem`** tại từng dòng vật tư để tick chọn xóa từng dòng riêng lẻ.

#### B. Bảng nút bấm tác vụ trong màn hình BOM-Manage
| Tên Nút Bấm / Checkbox | Màu Sắc | Vị Trí | Chức Năng Nghiệp Vụ | Khi Nào Cần Bấm? |
| :--- | :--- | :--- | :--- | :--- |
| **Checkbox [ ] EDIT** | Ô checkbox viền xanh | Toolbar đầu trang | **Mở khóa toàn bộ bảng BOM sang chế độ chỉnh sửa (Edit Mode)** | **Bắt buộc tick đầu tiên** nếu muốn thêm vật tư, sửa CONS, sửa giá hoặc xóa dòng. |
| **✔ SAVE** | Xanh lá | Xuất hiện khi tick EDIT | Lưu toàn bộ danh mục và định mức vừa sửa vào hệ thống | Bắt buộc bấm sau khi đã hoàn tất chỉnh sửa định mức. |
| **CANCEL** | Xám | Xuất hiện khi tick EDIT | Hủy bỏ chế độ sửa, hoàn tác dữ liệu về ban đầu | Bấm khi không muốn lưu các thay đổi vừa gõ nhầm. |
| **+ Add R/M** | Xanh lá | Header cột R/M Name (khi tick EDIT) | Mở popup tra cứu danh mục để gán thêm mã vật tư vào BOM | Bấm để bổ sung thêm vải, khóa, nhãn vào sản phẩm. |
| **Checkbox [ ] chkAllItem** | Checkbox | Header cột DEL (khi tick EDIT) | Tự động tick chọn tất cả các dòng vật tư trong bảng | Dùng khi muốn chọn hàng loạt tất cả các dòng để xóa. |
| **Checkbox [ ] chkItem** | Checkbox | Từng dòng cột DEL (khi tick EDIT) | Đánh dấu chọn riêng dòng vật tư này để xóa | Tick vào các dòng vật tư thừa, sau đó bấm nút đỏ DEL. |
| **DEL** | Đỏ | Header cột DEL (khi tick EDIT) | Xóa toàn bộ các dòng vật tư đã tick chọn | Bấm để thực thi xóa các dòng đã chọn. |
| **NewBasic info / Basic info** | Xanh dương | Toolbar đầu trang (khi chưa tick EDIT) | Mở popup xem/sửa thông tin chung: Style, Buyer, Season, Color | Dùng khi cần cập nhật thông tin chung của sản phẩm. |
| **D/L BOM** | Vàng cam | Toolbar đầu trang (khi chưa tick EDIT) | Tải toàn bộ cấu trúc định mức BOM ra file Excel | Dùng khi cần gửi bảng BOM cho Merchandiser hoặc khách hàng duyệt. |
| **Color Selector** | Dropdown | Đầu trang | Chuyển đổi qua lại giữa các phiên bản màu sắc (Colorways) | Khi sản phẩm có nhiều màu (Đen, Hồng, Navy...) dùng chung khung BOM. |

#### C. Cấu trúc bảng định mức chi tiết
1. `CATEGORY`: Phân nhóm vật tư (Fabric: Vải chính/lót, Trim: Khóa/đầu kéo/chỉ, Packing: Thùng/băng keo/túi PE, Other...).
2. `R/M CODE`: Mã nguyên phụ liệu định danh hệ thống (Nền đỏ đậm: RMF..., RMT..., RMP...).
3. `R/M NAME`: Tên kỹ thuật của nguyên phụ liệu.
4. `SPECIFICATION`: Quy cách chi tiết (Ví dụ: Khổ 58", Độ dày 210D/3P, Bản rộng 25mm...).
5. `COLOR`: Màu sắc quy định của vật tư.
6. `CONS`: Định mức tiêu hao cho 1 đơn vị sản phẩm (Consumption).
7. `UNIT`: Đơn vị tính (YDS, M, PCS, CON, SET, ROLL...).
8. `BUYER`: Khách hàng chỉ định nguồn gốc vật tư.
9. `U/PRICE` / `CURRENCY`: Đơn giá mua dự toán và loại tiền tệ (USD, VND, CNY).
10. `SUPPLIER`: Tên nhà cung cấp được chỉ định cho vật tư này.
11. `REMARK (BOM)`: Vị trí sử dụng trên sản phẩm (Ví dụ: Thân trước, Quai đeo, Lớp lót...).

#### C. Nguồn gốc dữ liệu & Bước tiếp theo
- **Dữ liệu sinh ra từ đâu?** Do phòng Kỹ thuật / R&D bóc tách từ tài liệu kỹ thuật (Tech Pack) của Buyer.
- **Hoàn tất thì làm gì tiếp theo?** Dữ liệu BOM sau khi bấm `SAVE` sẽ được động bộ sang phân hệ `MATERIAL › Manage PO` để động cơ MRP tính toán nhu cầu mua hàng.

---

### 3.5. Quản lý Giao hàng & Tồn kho Thành phẩm (`F/G › Shipment` & `F/G › Stock`)
- **Shipment (`/FG/Shipment`):** Lập kế hoạch đóng container, in Packing List, xuất hóa đơn xuất xưởng và cập nhật số lượng `Shipped`.
- **Stock (`/FG/Stock`):** Quản lý tồn kho thành phẩm đã hoàn thành nhưng chưa đến ngày ETD xuất xưởng hoặc tồn kho lưu trữ.

---

## 4. PHÂN HỆ 2: MATERIAL - QUẢN LÝ NGUYÊN PHỤ LIỆU, MUA HÀNG & KHO

### 4.1. Tính toán Nhu cầu & Đặt mua Vật tư (`MATERIAL › Manage PO` - TRỌNG TÂM MRP)
- **Đường dẫn Menu (Breadcrumb):** `MATERIAL ▶ Manage PO` (Đường dẫn: `/material/manage-po`)
- **Mục đích:** Đây là **trái tim của hệ thống MRP**. Động cơ tính toán sẽ đối chiếu giữa: (Số lượng đặt của đơn hàng) × (Định mức BOM) + (% Hao hụt) - (Tồn kho sẵn có) để ra Số lượng cần đặt mua thực tế, tính toán chi phí và phát hành đơn mua gửi nhà cung cấp.

#### A. Bộ lọc & Công cụ đầu trang
- **Dropdown Nhóm:** Chọn xem gom theo Đơn hàng (`Group by NEO PO`) hoặc gom theo Nhà cung cấp (`Group by Supplier`).
- **Dropdown Lọc NEO PO#:** Chọn mã đơn hàng cần chạy thuật toán MRP.
- **+ Create new EtC MATERIAL PO:** Tạo PO mua các vật tư phát sinh ngoài BOM gốc.

#### B. Cấu trúc Bảng tính toán nhu cầu MRP đa tầng
Bảng dữ liệu được tổ chức theo 6 khối nghiệp vụ chuẩn quốc tế:

1. **Khối Ⓐ ORDER INFORMATION (Thông tin Đơn hàng):**
   - `MATERIAL PO #`: Mã đơn đặt hàng vật tư được hệ thống cấp phát (Kèm nút `DEL PO` màu đỏ).
   - `NEO PO#`: Mã đơn hàng sản xuất nội bộ liên kết.
   - `STATUS (INFO)`: Nút `INFO` xanh lá xem trạng thái tiến độ phê duyệt đơn mua.

2. **Khối MATERIAL INFORMATION (Thông tin Vật tư):**
   - Nút `+ ADD MATL` (Xanh lá): Bổ sung thêm mã vật tư mới vào PO mua hàng.
   - Nút `MAKE PO` (Xanh lá) & Checkbox: Tick chọn các vật tư cùng một NCC để tạo đơn đặt hàng chính thức.
   - `SUPPLIER` / `COUNTRY`: Tên và quốc gia của nhà cung cấp.
   - `GROUP` / `CODE` / `NAME`: Nhóm (F/T/P/O), mã và tên nguyên phụ liệu.
   - `SPECIFICATION` / `COLOR`: Quy cách kỹ thuật và màu sắc.

3. **Khối Ⓑ BOM CONSUMPTION (This CONTRACT only) - Tiêu hao theo Hợp đồng:**
   - `① CONS.(BOM) (BEFORE)`: Định mức tiêu hao gốc lấy từ BOM kỹ thuật.
   - `CONS.(BOM) (AFTER)` (Kèm nút `UPDATE` xanh lá): Định mức thực tế được phép điều chỉnh cho đơn hàng này.
   - `② LOSS %` (Kèm nút `SET` xanh lá): Tỷ lệ phần trăm hao hụt sản xuất (Ví dụ: Vải chính 3%, Chỉ may 5%).
   - `③ = ① + ② CONS.(LOSS)`: Tổng định mức tiêu hao sau khi cộng hao hụt.

4. **Khối Ⓒ GLOBAL PO QTY INFO (Tổng hợp nhu cầu & Tồn kho khả dụng):**
   - `① CONS.(LOSS)`: Tổng khối lượng vật tư cần cho toàn bộ sản lượng đơn hàng.
   - `ASSIGN`: Khối lượng vật tư đã được gán/giữ chỗ từ các kho sẵn có.
   - `INVENTORY`: Tồn kho vật lý khả dụng hiện có thể huy động.

5. **Khối Ⓔ MATERIAL PURCHASE ORDER (Chi tiết Đơn đặt mua vật tư):**
   - `① ORDER QTY` (Kèm nút `SET` xanh lá): Số lượng thực tế chốt gửi đặt hàng cho NCC.
   - `② ASSIGN` (Kèm nút `SET` xanh lá): Số lượng bù trừ từ kho nội bộ.
   - `③ UNIT PRICE` (Kèm nút `RESET` cam): Đơn giá mua thỏa thuận với NCC.
   - `④ = ① * ③ TOTAL`: Tổng tiền vật tư chưa thuế.
   - `⑤ TAX` (Nút `SET`): Tiền thuế GTGT hoặc thuế nhập khẩu.
   - `⑥ HANDLING` (Nút `SET`): Phí bốc dỡ, lưu kho, thông quan.
   - `⑦ SURCHARGE` (Nút `SET`): Phụ phí hàng gấp, phí cước phát sinh.
   - `AMOUNT` (Nút `SET DECIMAL` xanh dương): Tổng giá trị thanh toán cuối cùng của đơn mua.
   - `SHIPPER & CONSIGNEE`: Đơn vị vận chuyển và Kho nhà máy tiếp nhận.
   - `PO DATE`, `TARGET DATE`, `ETA`, `ETD`: Ngày lập đơn, Ngày hẹn giao, Ngày tàu đến cảng, Ngày hàng về đến xưởng (đều có nút `SET` đồng loạt).

6. **Khối Ⓔ DELIVERY (Theo dõi Tiến độ Giao hàng & Nhập kho):**
   - `① IN`: Số lượng thực tế đã nhập kho qua cổng Inbound.
   - `Ⓔ① - ① BAL`: Số lượng NCC còn nợ chưa giao đủ (Balance).
   - `STATUS (MATERIAL)`: Trạng thái tiến độ: Chờ giao, Đang giao một phần, Đã hoàn tất.

#### C. Quy trình thao tác 4 bước đặt hàng vật tư
- **Bước 1:** Chọn mã `NEO PO#` cần tính toán tại thanh lọc trên cùng.
- **Bước 2:** Kiểm tra định mức tiêu hao, bấm nút `SET` tại cột `LOSS %` để áp tỷ lệ hao hụt phù hợp cho từng chủng loại vật tư.
- **Bước 3:** Kiểm tra cột `INVENTORY`. Nếu kho còn dư, bấm nút `SET` tại `ASSIGN` để trừ tồn kho. Số lượng còn thiếu sẽ tự động kết xuất sang cột `ORDER QTY`.
- **Bước 4:** Tick chọn các dòng vật tư cần mua cùng một nhà cung cấp, bấm nút **MAKE PO** (màu xanh lá) để hệ thống sinh mã `MATERIAL PO#` và cập nhật đơn giá, ngày giao hàng `ETA`.

---

### 4.2. Quản lý Tồn kho & Định giá Tài sản Kho (`MATERIAL › Inventory`)
- **Đường dẫn Menu (Breadcrumb):** `MATERIAL ▶ Inventory` (Đường dẫn: `/material/inventory`)
- **Mục đích:** Kiểm soát tổng thể tồn kho nguyên phụ liệu, đối soát tồn sổ sách và tồn thực tế đếm được, phân bổ theo vị trí giá kệ và định giá tổng tài sản kho theo USD.

#### A. Thanh công cụ & Bộ lọc
- **Lọc Trạng thái:** Dropdown `NOT ZERO` (Mặc định chỉ hiển thị các mã còn tồn kho > 0 để tránh rối mắt) hoặc chọn xem toàn bộ danh mục.
- **Lọc Thời gian:** Xem tồn hiện tại `TODAY` hoặc lùi ngày để xem tồn quá khứ.
- **Lọc Vị trí:** Dropdown `[ LOCATION ]` để lọc xem tồn của từng dãy kệ/kho bãi cụ thể.
- **Nút DOWN XLS** (Xanh lá): Xuất toàn bộ báo cáo tồn kho ra tệp Excel phục vụ kiểm kê.
- **Nút Refresh** (Xám đen): Cập nhật số liệu tức thì.

#### B. Cấu trúc các cột số liệu tồn kho
1. `MATERIAL INFORMATION`: Nhóm vật tư (GROUP), Mã R/M, Tên, Quy cách, Màu, Đơn vị tính (UNIT).
2. `IN (Nhập lũy kế)`: Tổng số lượng đã nhập qua Inbound, chia thành hàng theo Hợp đồng `[CONTRACT]` và hàng dùng chung `[N/A]`.
3. `IN BALANCE`: Khối lượng hàng đã xuất PO mua nhưng đang trên đường vận chuyển chưa về kho.
4. `OUT (Xuất lũy kế)`: Tổng số lượng đã xuất kho cấp cho các chuyền may.
5. `PHYSICAL INVENTORY`: Số lượng tồn kho thực tế đếm được tại kệ (Dữ liệu kiểm kê thực tế).
6. `INVENTORY`: Số lượng tồn kho sổ sách có thể sử dụng (Sẵn sàng cấp phát hoặc Assign cho PO mới).
7. `① * STD PRICE AMOUNT(USD)`: Giá trị tồn kho quy đổi ra tiền USD (Số lượng tồn × Đơn giá tiêu chuẩn Standard Price). Cột này dùng để báo cáo tài chính kho định kỳ.
8. `HISTORY`: Nút xem bảng sao kê chi tiết lịch sử từng lần Nhập - Xuất - Chuyển kho của mã vật tư đó.

---

### 4.3. Nhập kho Nguyên Phụ Liệu (`MATERIAL › Inbound`)
- **Đường dẫn Menu (Breadcrumb):** `MATERIAL ▶ Inbound` (Đường dẫn: `/material/inbound`)
- **Mục đích:** Tiếp nhận lô hàng giao từ nhà cung cấp, ghi nhận số lượng thực tế nhận được theo từng mã `MATERIAL PO#`, gắn vị trí kệ kho và cộng tồn vào hệ thống.

#### A. Bảng nút bấm tác vụ
| Tên Nút Bấm | Màu Sắc | Vị Trí | Chức Năng Nghiệp Vụ | Khi Nào Cần Bấm? |
| :--- | :--- | :--- | :--- | :--- |
| **UPLOAD EXCEL** | Xanh dương | Đầu trang | Nhập danh sách phiếu nhập kho nhanh từ file Excel | Khi nhập lô hàng lớn gồm hàng trăm mã phụ liệu cùng lúc |
| **DOWNLOAD EXCEL** | Vàng cam | Đầu trang | Tải file Excel mẫu phiếu nhập kho | Khi cần mẫu chuẩn để thủ kho làm biên bản nhận hàng |
| **APPLYING INBOUND NOW** | Xanh lá | Đầu trang | **Chốt ghi sổ nhập kho chính thức** | **Bắt buộc bấm sau khi kiểm tra xong số lượng** để tăng tồn kho hệ thống |
| **+ ADD** | Xanh lá | Cạnh cột PO# | Thêm dòng vật tư cần nhập | Khi nhập bổ sung từng mã hàng lẻ |
| **DEL** | Đỏ | Cột cuối mỗi dòng | Xóa dòng vật tư khỏi phiếu nhập | Khi nhập nhầm dòng hoặc nhà cung cấp chưa giao mã đó |

#### B. Quy trình nhập kho 4 bước
- **Bước 1:** Nhập mã `MATERIAL PO#` vào dòng nhập. Hệ thống sẽ tự động điền các thông tin: Nhà cung cấp, Tên vật tư, Quy cách, Số lượng đã đặt mua `ORDER QTY` và Số lượng còn thiếu `BALANCE QTY`.
- **Bước 2:** Kiểm đếm hàng thực tế tại cửa kho, nhập số lượng nhận vào cột **DELIVERY QTY**.
- **Bước 3:** Tại cột **LOCATION**, chọn vị trí giá kệ mà thủ kho sẽ xếp vật tư vào (Ví dụ: Kệ A1-02, Kho Vải K1...).
- **Bước 4:** Kiểm tra tổng thể và bấm nút màu xanh lá **APPLYING INBOUND NOW**. Hệ thống sẽ tự động tăng số lượng tồn trong `MATERIAL › Inventory` và giảm công nợ giao hàng trên `MATERIAL › Manage PO`.

---

### 4.4. Xuất kho Cấp phát Sản xuất (`MATERIAL › Outbound`)
- **Đường dẫn Menu (Breadcrumb):** `MATERIAL ▶ Outbound` (Đường dẫn: `/material/Outbound`)
- **Mục đích:** Xuất cấp nguyên phụ liệu từ kho cho các chuyền may hoặc xưởng cắt theo lệnh sản xuất.

#### A. Bảng nút bấm tác vụ
- **+ ADD/EDIT STYLE** (Xanh lá): Chọn mã hàng và đơn hàng cần xuất vật tư.
- **UPLOAD EXCEL** (Xanh dương): Tải file danh sách xuất kho hàng loạt.
- **DOWNLOAD EXCEL** (Vàng cam): Tải mẫu phiếu xuất kho Excel.
- **APPLYING OUTBOUND NOW** (Xanh lá): **Chốt xuất kho chính thức**, tự động trừ tồn kho hệ thống và ghi nhận chi phí sản xuất cho đơn hàng.

---

## 5. PHÂN HỆ 3: PRODUCTION - KẾ HOẠCH SẢN XUẤT & GIÁM SÁT CHUYỀN

### 5.1. Lập Lịch Sản xuất & Xếp Chuyền (`PRODUCTION › Schedule-Manage`)
- **Đường dẫn Menu (Breadcrumb):** `PRODUCTION ▶ Schedule-Manage` (Đường dẫn: `/Production/ScheduleManage`)
- **Mục đích:** Phân bổ các đơn hàng `NEO PO#` vào từng chuyền may (Line), xác định ngày bắt đầu - ngày kết thúc, giao chỉ tiêu sản lượng và in mã QR công đoạn (Bundle Tag / Travel Ticket).

#### A. Bảng nút bấm tác vụ
| Tên Nút Bấm | Màu Sắc | Vị Trí | Chức Năng Nghiệp Vụ | Khi Nào Cần Bấm? |
| :--- | :--- | :--- | :--- | :--- |
| **Update Filter** | Xám đen | Đầu trang | Làm mới danh sách kế hoạch theo điều kiện lọc | Khi muốn tải lại bảng kế hoạch chuyền mới nhất |
| **Settings** (Bánh răng) | Xanh ngọc | Đầu trang | Cấu hình ẩn/hiển thị cột bảng kế hoạch | Dùng khi cần giao diện làm việc tối giản |
| **QR** | Xanh dương | Header cột QR | **In hàng loạt phiếu mã QR công đoạn sản xuất** | Bấm sau khi tick chọn các đơn hàng chuẩn bị đưa lên chuyền may |
| **Schedule** | Xanh lá | Từng dòng đơn hàng | Mở hộp thoại phân bổ lịch sản xuất chi tiết | Bấm để chọn chuyền may (Line), ngày Start, ngày End, chỉ tiêu Qty |

#### B. Cấu trúc bảng kế hoạch sản xuất
- `PO INFORMATION`: Mã NEO PO#, Khách hàng (BUYER), Style Code, Style Name, Màu, Số lượng đặt (ORDER QTY).
- `SCHEDULE`:
  + `START`: Ngày chuyền bắt đầu vào hàng.
  + `END`: Ngày dự kiến chuyền may hoàn tất đơn hàng.
  + `QTY`: Số lượng chỉ tiêu giao cho chuyền trong đợt này.
  + `LINE`: Tên chuyền may tiếp nhận (Line 1, Line 2, Line 3...).
  + `PROCESS`: Công đoạn phụ trách (Cutting: Cắt, Sewing: May, Assembly: Lắp ráp/Hoàn thiện).
- `SUM OUTPUT-LINE`: Sản lượng lũy kế mà chuyền may đã hoàn thành thực tế.
- `SUM OUTPUT-ETC`: Tiến độ qua các công đoạn phụ trợ:
  + `QC`: Số lượng qua kiểm tra chất lượng đạt.
  + `X-RAY`: Số lượng đã qua máy rà kim loại an toàn.
  + `PACKING`: Số lượng đã đóng gói vào thùng carton.
  + `SHIPMENT`: Số lượng đã bốc xếp lên xe xuất hàng.

---

### 5.2. Bảng Giám sát Năng suất Từng Giờ (`PRODUCTION › Dashboard-Table`)
- **Đường dẫn Menu (Breadcrumb):** `PRODUCTION ▶ Dashboard-Table` (Đường dẫn: `/Production/DashboardTable`)
- **Mục đích:** Màn hình điều hành tác nghiệp thời gian thực của Quản đốc xưởng và Tổ trưởng chuyền. Giám sát chi tiết sản lượng đạt được của từng chuyền may qua từng giờ làm việc trong ngày (DT1 đến DT8 + Tăng ca), phát hiện ngay hiện tượng nghẽn chuyền hoặc tỷ lệ phế phẩm tăng cao.

#### A. Bộ điều khiển đầu trang
- **Pick a date (Datepicker):** Chọn ngày cần theo dõi (Mặc định là ngày hôm nay).
- **Update filter:** Bấm để cập nhật lại số liệu ghi nhận theo thời gian thực từ các máy quét mã QR tại xưởng.

#### B. Cấu trúc bảng theo dõi năng suất theo giờ
1. `LINE` / `PROCESS`: Tên chuyền may và công đoạn.
2. `NEO PO INFORMATION`: Thông tin đơn hàng đang chạy trên chuyền (PO#, Style, Color, ETD).
3. `SCHEDULE`: Ngày bắt đầu, Ngày kết thúc và Tổng sản lượng kế hoạch.
4. `TOTAL (Lũy kế toàn đơn)`:
   - `OUTPUT (QTY/RATE)`: Tổng sản lượng chuyền đã làm được từ đầu đơn đến nay và Tỷ lệ % đạt so với hợp đồng.
   - `DEFECT (QTY/RATE)`: Tổng số lượng sản phẩm lỗi và Tỷ lệ phế phẩm % lũy kế.
5. `TODAY (Chỉ số trong ngày được chọn)`:
   - `TARGET`: Chỉ tiêu sản lượng ban giám đốc giao cho ngày hôm nay.
   - `OUTPUT (QTY/RATE)`: Sản lượng thực tế đạt được hôm nay và Tỷ lệ % hoàn thành mục tiêu ngày.
   - `DEFECT (QTY/RATE)`: Số sản phẩm lỗi phát sinh hôm nay và Tỷ lệ lỗi %.
6. `HOURLY OUTPUT(%) (Theo dõi 8 khung giờ sản xuất chuẩn)`:
   - **DT1:** Khung giờ 1 (07:30 - 08:30)
   - **DT2:** Khung giờ 2 (08:30 - 09:30)
   - **DT3:** Khung giờ 3 (09:30 - 10:30)
   - **DT4:** Khung giờ 4 (10:30 - 11:30)
   - **DT5:** Khung giờ 5 (12:30 - 13:30)
   - **DT6:** Khung giờ 6 (13:30 - 14:30)
   - **DT7:** Khung giờ 7 (14:30 - 15:30)
   - **DT8:** Khung giờ 8 (15:30 - 16:30)
   - **EXTRA:** Khung giờ làm thêm tăng ca (Overtime sau 16:30).

---

### 5.3. Các Màn hình Trực quan Hóa Khác của Phân hệ Sản xuất
- **Schedule-Timetable (`/Production/ScheduleTimeTable`):** Biểu đồ Gantt trực quan biểu diễn tiến độ các đơn hàng trên các chuyền theo trục thời gian tuần/tháng.
- **Dashboard-Chart (`/Production/DashboardChart`):** Đồ thị trực quan hóa đường cong năng suất (Target vs Actual) và biểu đồ phân bổ sản lượng các xưởng.
- **Line monitor (`/Production/LineMonitor`):** Giao diện màn hình lớn (Large Screen) chuyên dùng treo trên các tivi đầu chuyền để công nhân tự theo dõi tiến độ từng phút.
- **Top defect (`/Production/TopDefect`):** Báo cáo Pareto thống kê các nguyên nhân lỗi may/nguyên phụ liệu xuất hiện nhiều nhất để bộ phận QA/QC có biện pháp khắc phục.

---

## 6. PHÂN HỆ 4: TOOLS - CÔNG CỤ TIỆN ÍCH & TRÌNH CHIẾU XƯỞNG

1. **Broadcast (`/Tool/Broadcast`):** Cho phép Quản đốc hoặc Ban giám đốc soạn thông báo điều hành để hiển thị tức thì trên toàn bộ màn hình máy tính của người dùng hoặc màn hình tivi chuyền xưởng.
2. **Rotate page (`/Tool/RotatePage`):** Cấu hình tự động xoay lật tuần tự giữa các trang Dashboard (Ví dụ: 30 giây chiếu Dashboard Table, 30 giây chiếu Biểu đồ Chart, 30 giây chiếu Báo cáo Top Defect) trên các TV giám sát trung tâm.
3. **Raw data (Web) (`/Tool/RawDataWeb`):** Truy xuất trích xuất dữ liệu gốc phục vụ việc phân tích chuyên sâu của phòng Kế hoạch và Ban kiểm soát nội bộ.

---

## 7. PHÂN HỆ 5: CONFIG - THIẾT LẬP HỆ THỐNG & QUY CHUẨN XƯỞNG

1. **Line (`/config/line`):** Khai báo danh mục chuyền may, công đoạn, số lượng lao động thiết kế trên từng chuyền.
2. **Work hours (`/config/work-hours`):** Cấu hình khung giờ làm việc chuẩn (DT1 đến DT8), giờ nghỉ trưa và giờ tăng ca áp dụng theo quy chế công ty.
3. **Chart (`/config/chart`):** Cài đặt các ngưỡng cảnh báo màu (Xanh: Đạt tiến độ > 95%, Vàng: Cảnh báo chậm 80-95%, Đỏ: Báo động chậm < 80%).
4. **Defect (`/config/defect`):** Danh mục bảng mã lỗi QC may mặc chuẩn quốc tế (Lỗi đường chỉ, Lỗi mũi kim, Lỗi lệch nhãn, Lỗi bẩn dầu máy...).

---

## 8. PHÂN HỆ 6: CODE - MASTER DATA (DANH MỤC DÙNG CHUNG)

### 8.1. Quản lý Danh mục Nguyên phụ liệu gốc (`CODE › R/M`)
- **Đường dẫn Menu (Breadcrumb):** `CODE ▶ R/M` (Đường dẫn: `/code/rm`)
- **Mục đích:** Đây là **Từ điển Master Data nguyên phụ liệu dùng chung cho toàn bộ nhà máy**. Mọi loại vải chính, vải lót, chỉ may, khóa kéo, nhãn mác, băng dính hay thùng carton trước khi được đưa vào Định mức BOM hoặc Đặt mua đều phải được khai báo mã chuẩn tại màn hình này.

#### A. Quy tắc phân nhóm vật tư (Category Code)
- `F (Fabric)`: Tất cả các loại vải chính, vải lót, vải phối, lưới, mút xốp eva.
- `T (Trim)`: Phụ liệu may mặc (Dây kéo, đầu khóa kéo, băng dính Velcro, chỉ may, nút bấm, móc kim loại, dây dệt quai túi).
- `P (Packing)`: Vật tư đóng gói (Thùng carton, túi nilon PE/PP, hạt hút ẩm Silica gel, băng keo niêm phong, nhãn mã vạch barcode).
- `O (Other)`: Các loại hóa chất phụ trợ, dầu máy, keo dán, vật tư tiêu hao phụ xưởng cắt/may.

#### B. Bảng nút bấm tác vụ trên màn hình CODE › R/M
| Tên Nút Bấm | Màu Sắc | Vị Trí | Chức Năng Nghiệp Vụ | Khi Nào Cần Bấm? |
| :--- | :--- | :--- | :--- | :--- |
| **+ Add R/M** | Xanh lá | Thanh công cụ | Mở popup khai báo 01 mã nguyên phụ liệu mới vào từ điển | Khi có mã vải, phụ liệu mới về xưởng chưa từng có trong hệ thống. |
| **UPLOAD EXCEL** | Xanh dương | Thanh công cụ | Nạp danh sách hàng loạt nguyên phụ liệu từ file Excel | Khi nhận dự án mới cần nhập hàng trăm mã phụ liệu cùng lúc vào Master Data. |
| **Template R/M** | Vàng cam | Thanh công cụ | Tải file mẫu Excel chuẩn để điền dữ liệu R/M | Trước khi bấm UPLOAD EXCEL, tải file mẫu này về để điền đúng định dạng cột. |
| **D/L Excel** | Vàng cam | Thanh công cụ | Xuất toàn bộ từ điển danh mục R/M ra tệp Excel | Dùng khi cần gửi bảng tra cứu mã vật tư cho phòng Mua hàng hoặc Kỹ thuật. |
| **EDIT** | Xanh ngọc / Cyan | Từng dòng vật tư | Mở popup chỉnh sửa thông tin kỹ thuật, quy cách hoặc đơn giá chuẩn | Khi cần sửa Tên, Đơn vị tính (YDS/M/PCS), Nhà cung cấp hoặc Standard Price. |
| **DEL** | Đỏ | Từng dòng vật tư | Xóa mã nguyên phụ liệu khỏi hệ thống | Chỉ xóa được khi mã R/M này **chưa từng được đưa vào bất kỳ BOM nào**. |

#### C. Cấu trúc thông tin bắt buộc khi khai báo mã R/M mới
- `Category`: F (Fabric), T (Trim), P (Packing) hoặc O (Other).
- `R/M Code`: Mã định danh duy nhất (VD: `RMF-00124`, `RMT-00512`, `RMP-00031`). Không được trùng lặp.
- `R/M Name`: Tên tiếng Anh kỹ thuật của vật tư (VD: *Polyester 600D PU2 Coating, Nylon Coil Zipper #5*).
- `Specification`: Quy cách chi tiết (Khổ rộng 58", Độ dày dệt, Kích thước răng khóa, Trọng lượng gsm...).
- `Color / Color Code`: Tên màu hoặc mã màu Pantone/Colorway chỉ định của khách hàng.
- `Unit`: Đơn vị đo lường chuẩn: **YDS** (Yard), **M** (Mét), **PCS** (Cái/Chiếc), **CON** (Cuộn chỉ), **SET**, **ROLL**.
- `Standard Price (USD)`: Đơn giá tiêu chuẩn quy đổi ra USD để hệ thống tự động định giá tổng tài sản kho (Inventory Valuation).
- `Supplier`: Nhà cung cấp mặc định hoặc đối tác sản xuất vật tư đó.

### 8.2. Các Danh mục Master Data Khác
1. **Category/Style/Color (`/code/category-style-color`):** Danh mục ngành hàng balo, mã kiểu dáng (Style) và bảng mã màu (Colorways) chuẩn hóa của doanh nghiệp.
2. **Exchange unit (`/code/exchange-unit`):** Bảng hệ số quy đổi đơn vị tính (Yard sang Mét, Mét sang PCS, Cuộn sang Mét...) phục vụ tính toán tự động trong BOM và Kho.
3. **Buyer (`/code/buyer`):** Danh mục khách hàng quốc tế (Mã viết tắt, Tên đầy đủ, Quốc gia, Điều khoản thanh toán).
4. **Site Management (`/code/matl-consignee`):** Địa điểm các nhà máy, xưởng thành viên và thông tin đơn vị nhận hàng (Consignee).
5. **Matl. supplier (`/code/matl-supplier`):** Danh bạ đối tác nhà cung cấp nguyên phụ liệu trong và ngoài nước.
6. **Location (`/code/location`):** Hệ thống mã hóa tọa độ giá kệ trong kho bãi (Dãy, Kệ, Tầng, Ô).

---

## 9. PHÂN HỆ 7: ADMIN - QUẢN TRỊ NGƯỜI DÙNG & PHÂN QUYỀN

1. **Account (`/admin/account`):** Tạo mới tài khoản, phân quyền thao tác (Xem, Sửa, Duyệt PO, Xóa) cho từng vị trí nhân sự (Merchandiser, Planner, Warehouse, Admin).
2. **Profile (`/admin/account/edit`):** Đổi mật khẩu cá nhân, cập nhật email và số điện thoại liên hệ.
3. **Logout (`/logout`):** Đăng xuất an toàn khỏi hệ thống khi kết thúc phiên làm việc.

---

## 10. BẢNG TRA CỨU NÚT BẤM & QUY CHUẨN MÀU SẮC

Hệ thống tuân thủ quy chuẩn mã màu Bootstrap chuẩn hóa để người dùng nhận diện ngay bản chất thao tác:

| Màu Sắc Nút Bấm | Các Nút Thực Tế Điển Hình | Ý Nghĩa Nghiệp Vụ | Lưu Ý Quan Trọng |
| :--- | :--- | :--- | :--- |
| **XANH LÁ** | `+ Add PO`, `Upload BOM`, `SAVE`, `MAKE PO`, `APPLYING INBOUND NOW`, `APPLYING OUTBOUND NOW`, `Schedule` | **Tạo mới / Lưu / Thực thi / Chốt sổ** | Đây là các nút làm phát sinh hoặc xác nhận thay đổi dữ liệu chính thức vào hệ thống. |
| **XANH DƯƠNG** | `NewBasic info`, `UPLOAD EXCEL`, `QR`, `COPY`, `PRINT PO` | **Mở biểu mẫu / Nhập tệp / In ấn** | Dùng để mở popup khai báo, đọc file mẫu hoặc kích hoạt in ấn / tem mã QR công đoạn. |
| **XANH NGỌC** | `btnDisplayUI`, `Settings`, `MANAGE`, `EDIT` | **Tùy biến hiển thị / Quản trị chi tiết** | Mở bảng quản trị chi tiết của dòng hoặc bật tắt ẩn/hiển thị các cột của bảng. |
| **VÀNG CAM** | `Template`, `Template BOM`, `DOWNLOAD EXCEL`, `D/L AR`, `D/L PO` | **Tải mẫu tệp / Xuất báo cáo dữ liệu** | An toàn 100%, chỉ tải file dữ liệu về máy cá nhân, không làm thay đổi hệ thống. |
| **ĐỎ NGUY HIỂM** | `DEL`, `DEL PO`, `RESET`, `CANCEL PO` | **Xóa bản ghi / Hủy bỏ đơn mua / Xóa dòng** | **CỰC KỲ CẨN TRỌNG!** Dữ liệu sau khi xóa sẽ không thể khôi phục. Chỉ bấm khi có phê duyệt. |
| **XÁM ĐEN** | `Search`, `Update Filter`, `Refresh` | **Tìm kiếm / Làm mới số liệu** | Giúp tải lại trạng thái dữ liệu mới nhất mà các người dùng khác vừa cập nhật. |

---

## 11. BẢNG TỪ ĐIỂN THUẬT NGỮ CHUYÊN NGÀNH ERP/MRP MAY MẶC

| Thuật Ngữ Tiếng Anh | Nghĩa Nghiệp Vụ Tiếng Việt | Ứng Dụng Trong Hệ Thống |
| :--- | :--- | :--- |
| **F/G (Finished Goods)** | Thành phẩm hoàn chỉnh | Nhóm phân hệ quản lý sản phẩm hoàn thiện, đơn hàng xuất khẩu. |
| **R/M (Raw Materials)** | Nguyên phụ liệu thô | Vải chính, vải lót, chỉ may, khóa kéo, nhãn mác, băng keo, thùng... |
| **NEO PO#** | Mã đơn hàng sản xuất nội bộ | Mã số xuyên suốt liên kết giữa Đơn hàng, Định mức, Mua hàng và Chuyền may. |
| **BUYER PO#** | Mã đơn hàng gốc của khách hàng | Mã số hợp đồng do khách hàng quốc tế phát hành cho nhà máy. |
| **BOM (Bill of Materials)** | Bảng định mức kỹ thuật sản phẩm | Danh sách toàn bộ các loại vật tư tiêu hao để may thành 1 chiếc túi xách/balo. |
| **CONS (Consumption)** | Định mức tiêu hao | Số lượng vật tư cần dùng cho 1 đơn vị thành phẩm (VD: 0.85 YDS vải/túi). |
| **LOSS %** | Tỷ lệ hao hụt | Tỷ lệ phần trăm dự phòng hao phí trong quá trình cắt, may hoặc lỗi sợi. |
| **ASSIGN** | Gán tồn kho (Cấp phát trước) | Bù trừ số lượng vật tư sẵn có trong kho vào đơn hàng mới để không phải mua thêm. |
| **INBOUND** | Nghiệp vụ Nhập kho | Quá trình tiếp nhận hàng từ NCC về kho và ghi nhận tăng tồn kho. |
| **OUTBOUND** | Nghiệp vụ Xuất kho | Quá trình xuất cấp vật tư từ kho giao cho chuyền may sản xuất. |
| **BAL (Balance)** | Số lượng dư nợ / Còn thiếu | Số lượng hàng khách đặt chưa giao hoặc số lượng vật tư NCC chưa giao đủ. |
| **PHYSICAL INVENTORY** | Tồn kho vật lý thực tế | Số lượng đếm thực tế khi thủ kho đi kiểm kê tại các giá kệ. |
| **STD PRICE (Standard Price)** | Đơn giá tiêu chuẩn | Đơn giá danh nghĩa quy chuẩn dùng để định giá tổng tài sản tồn kho ra USD. |
| **LINE** | Chuyền sản xuất / Chuyền may | Tổ đội công nhân may chịu trách nhiệm hoàn thiện đơn hàng theo lịch. |
| **DT1 – DT8 (Daily Time 1..8)** | 8 Khung giờ làm việc chuẩn | Giờ theo dõi sản lượng định kỳ trong ngày (07:30 đến 16:30). |
| **ETD (Est. Time of Departure)** | Ngày dự kiến xuất hàng | Hạn chót xuất xưởng đóng container để giao cho hãng tàu/khách hàng. |
| **ETA (Est. Time of Arrival)** | Ngày dự kiến hàng đến kho | Hạn chót nhà cung cấp phải giao nguyên phụ liệu về đến nhà máy. |

---

## 12. MA TRẬN SỰ CỐ & HƯỚNG DẪN XỬ LÝ LỖI NGHIỆP VỤ (FAQ)

### Sự cố 1: Sau khi tạo đơn hàng mới, vì sao không tính toán được vật tư trong `MATERIAL › Manage PO`?
- **Nguyên nhân:** Đơn hàng `NEO PO#` đó chưa được liên kết với bản ghi định mức BOM nào, hoặc BOM đang ở trạng thái chưa lưu (`Draft`).
- **Cách khắc phục:** 
  1. Vào `F/G › BOM-Manage`, kiểm tra xem Style Code của PO đã có BOM chưa.
  2. Khai báo đầy đủ danh sách vật tư và bấm nút **SAVE** màu xanh lá.
  3. Quay lại `MATERIAL › Manage PO`, chọn lại mã `NEO PO#` từ dropdown, hệ thống sẽ tự động nạp bảng tiêu hao.

### Sự cố 2: Đã nhập kho ở màn hình Inbound nhưng tồn kho trong `MATERIAL › Inventory` không tăng?
- **Nguyên nhân:** Người dùng mới chỉ gõ số lượng vào cột `DELIVERY QTY` nhưng quên chưa bấm nút xác nhận chốt sổ.
- **Cách khắc phục:** 
  1. Kiểm tra lại màn hình `MATERIAL › Inbound`.
  2. Bắt buộc bấm nút màu xanh lá **APPLYING INBOUND NOW** trên thanh công cụ. Khi có thông báo thành công, số lượng mới chính thức được ghi sổ vào kho.

### Sự cố 3: Nút `MAKE PO` trong `MATERIAL › Manage PO` bị mờ (disabled) không bấm được?
- **Nguyên nhân:** Người dùng chưa tick chọn các ô checkbox ở đầu dòng vật tư, hoặc các dòng vật tư được tick thuộc các Nhà cung cấp (Supplier) khác nhau.
- **Cách khắc phục:** 
  1. Mỗi mã `MATERIAL PO#` chỉ phát hành cho một Nhà cung cấp duy nhất.
  2. Dùng bộ lọc lọc theo từng Nhà cung cấp, sau đó tick chọn các dòng cần mua của NCC đó. Nút **MAKE PO** sẽ sáng lên để bấm.

### Sự cố 4: Chuyền may đã làm xong hàng nhưng trên `PRODUCTION › Dashboard-Table` cột Output hiển thị bằng 0?
- **Nguyên nhân:** Công nhân hoặc tổ trưởng chưa quét mã QR công đoạn (Travel Ticket) tại trạm kiểm đếm, hoặc ngày trên bộ lọc Datepicker đang chọn khác với ngày sản xuất thực tế.
- **Cách khắc phục:**
  1. Kiểm tra lại bộ lọc ngày tại ô **Pick a date**, đảm bảo chọn đúng ngày hôm nay và bấm **Update filter**.
  2. Kiểm tra bộ phận kiểm đếm xem mã QR in từ màn hình `Schedule-Manage` đã được quét qua máy đọc QR hay chưa.

---
*Tài liệu được biên soạn và bảo mật nội bộ. Tuyệt đối không sao chép hoặc phân phối ra ngoài doanh nghiệp.*
