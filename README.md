# LIGHTING GIS

Bản đồ chiếu sáng · CSKV Trung tâm (Q1 · Q3 · Bình Thạnh · Phú Nhuận).

## Đăng nhập
- **Đồng đội**: mở link app → nhập *tên đăng nhập + mật khẩu* do quản trị cấp. Máy được ghi nhớ 30 ngày.
- **Quản trị**: bấm *“Quản trị · đăng nhập bằng mã gửi qua Gmail”* → nhập mã 6 số nhận trong Gmail (hiệu lực 10 phút, dùng 1 lần).

## Cài máy chủ (làm 1 lần)
1. Tạo Google Sheet mới (vd: *LIGHTING GIS – Quản trị*).
2. **Tiện ích mở rộng › Apps Script** → xóa nội dung mẫu → dán toàn bộ `Code.gs` → Lưu.
3. Chọn hàm **caiDat** → **Chạy** → cấp quyền (Nâng cao › Đi tới… › Cho phép). Sheet sẽ có 4 trang: TaiKhoan, NhatKy, DuLieu, CaiDat (đã có sẵn 14 tài khoản cũ, giữ nguyên mật khẩu).
4. **Triển khai › Tùy chọn triển khai mới** → loại *Ứng dụng web* · Thực thi với tư cách: **Tôi** · Người có quyền truy cập: **Bất kỳ ai** → Triển khai → sao chép link `.../exec`.
5. Mở `config.js` trên GitHub → dán link vào `api: '...'` → Commit.

Sửa `Code.gs` sau này: **Triển khai › Quản lý bản triển khai › Sửa › Phiên bản mới** (giữ nguyên link).

## Quản lý tài khoản
Trong app (đăng nhập quản trị → mục *Quản lý tài khoản*) hoặc sửa trực tiếp sheet **TaiKhoan**:
- Quyền: Chỉ xem / Chỉnh sửa / Quản trị · Quận: `Q1, Q3, QBT, QPN` hoặc `Tất cả` · Trạng thái: Hoạt động / Khóa.
- Đổi mật khẩu: gõ mật khẩu mới vào cột **Đặt mật khẩu mới** – hệ thống tự mã hóa và xóa ô đó; người dùng phải đăng nhập lại.
- Bật/tắt thư báo khi có người đăng nhập: trong app hoặc trang **CaiDat**.

## Tệp
| Tệp | Nội dung |
|---|---|
| index.html | App (bản đồ + đăng nhập) |
| config.js | Link máy chủ Apps Script |
| base.json | Bản đồ nền |
| app.html | Chuyển hướng link cũ về app |
| sw.js, manifest.json, icon-*.png | Cài như ứng dụng trên điện thoại |

## Lệnh vẽ nhanh (gõ ở dòng lệnh dưới bản đồ, hoặc bấm nút trên thanh công cụ)
| Lệnh | Việc làm |
|---|---|
| `DT 30 G` | Dải trụ: chọn điểm đầu – cuối, tự đặt trụ cách đều ~30 m, tự đặt tên, nối cáp ngầm (`N`: nổi, `K`: không nối) |
| `DIV 5 G` | Chia đoạn thành 5 khoảng đều, đặt trụ + nối cáp |
| `DS HS_1` | Đánh số trụ vẽ mới: bấm lần lượt → HS_1, HS_2… (trụ hiện hữu giữ nguyên số) |
| Kéo bộ đèn | Trụ 2 đèn trở lên: bấm chọn 1 bộ đèn rồi kéo để xoay riêng (hoặc gõ số độ trong khung thông tin) |
| Tự động | Trụ hiện hữu đã được dời sát mép đường và xoay đèn ra mặt đường/hẻm; trụ vẽ mới (TR, DT) cũng tự vào mép |
| `MEP 0.5` | Dời lại trụ vào mép đường gần nhất (giữ bên trái/phải theo tim đường, trụ giữa đường giữ nguyên), cách mép 0,5 m |
| `M` | Dời trụ hoặc tủ điều khiển (chạm tủ → chạm vị trí mới, hoặc gõ X Y / @dx dy) |
| `W` | Chọn vùng nhiều trụ → đổi đèn, nối cáp, đánh số, thống kê, xuất bản vẽ |
| `LD LED` / `NC G` | Đổi loại đèn / nối cáp cho các trụ đang chọn |
| `TK` | Thống kê trụ, đèn, cáp ngầm/nổi – tải bảng Excel |
| `KT` / `IN` | Khung tên (người lập, ngày, SHBV) / xuất bản vẽ khung 1/1000 |
| `LENH` | Tự tạo lệnh tắt (như LISP): `D30 = DT 30 G` |
| `?` | Danh sách tất cả lệnh · Enter trống: lặp lại lệnh vừa dùng |

## Lệnh kiểu AutoCAD (F1 trong app để xem đầy đủ)
- Vẽ: L, C, A, REC, POL, EL, PL, H, BO
- Sửa: CO/CP, M, E, TR, EX, O, RO, SC, F, CHA, MI, AR, X, MA (quét thuộc tính – cả nền bản đồ, trụ, cáp; S: thiết lập; NEN0: trả nền về gốc)
- Quản lý: LA, OP, UN, PR/Ctrl+1, Z, P, RE
- Kích thước & chữ: D, DLI, DAL, DRA, DDI, MT, DT
- Phím: Ctrl+O/S/Z/Y, F1, F2, F3, F7, F8, F9, F10, ESC
- Đổi tên lệnh cũ: thêm trụ = TRU (hoặc PO); dải trụ = DTR; cáp = CN/CG
