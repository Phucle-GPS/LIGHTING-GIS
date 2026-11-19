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
| base.json | Bản đồ nền (bản dự phòng, không nén) |
| pack.gz | Dữ liệu trụ, cáp, tủ, ký hiệu, khung (nén gzip) |
| base.gz | Bản đồ nền nén gzip – app dùng file này |
| sw.js | Bộ nhớ đệm offline (chỉ lưu bản nén) |
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

## Bản nhẹ cho điện thoại
- `index.html` chỉ còn ~330 KB; dữ liệu nằm trong `pack.gz` (~0,8 MB) và `base.gz` (~2,4 MB).
- Bộ nhớ đệm trên máy chỉ giữ bản nén (~3,5 MB thay vì ~10 MB trước đây); bản cũ tự xóa khi mở app phiên bản mới.

## Chọn đối tượng kiểu CAD
- Bấm chỗ trống → bấm góc đối diện: kéo sang phải = chọn trọn trong khung, sang trái = chọn giao. Esc hủy. Shift + bấm để cộng thêm.
- Nhiều đối tượng chồng nhau: bấm lại đúng chỗ để chọn lần lượt.

## Xuất bản vẽ tủ lớn
- Tủ vừa 1 khung A3 tỉ lệ 1/1000: xuất bản vẽ có khung như trước.
- Tủ lớn hơn khung: không tách bản – xuất 1 bản vẽ tổng thể tỉ lệ 1/1000 (đúng tọa độ VN-2000), khung tên đặt bên phải để người dùng sao chép và tự cắt.

## Sửa đối tượng vẽ như AutoCAD (grip)
- Bấm chọn nét vẽ → hiện ô vuông xanh (grip). Kéo ô, hoặc bấm ô (ô đỏ) rồi bấm điểm mới: kéo dãn đầu mút/đỉnh, dời (ô giữa/tâm), đổi bán kính (ô góc phần tư).
- Nhiều nét chung một điểm được kéo cùng nhau. Esc hủy, Ctrl+Z hoàn tác. Nhấp đúp nét vẽ → bảng thuộc tính.
- Enter / Space: đang có lệnh → kết thúc; không có lệnh → lặp lại lệnh vừa dùng.

## Lệnh con như AutoCAD
- Các lựa chọn trong [ ] hiện thành nút bấm phía trên dòng lệnh (hoặc gõ chữ trong ngoặc).
- PL: A cung (A góc · CE tâm · R bán kính · S điểm thứ 2 · D hướng · L về đoạn thẳng · CL khép bằng cung), L dài, W rộng, H nửa rộng, C khép, U hoàn tác.
- REC: F bo góc, W rộng nét, R xoay, D kích thước. C: 2P, 3P, D đường kính.
- Khi lệnh sửa hỏi chọn đối tượng: ALL tất cả, P lần chọn trước, L vừa vẽ, W cửa sổ, C giao, R bớt, A thêm.
- Vẽ/chép xong, đối tượng mới được chọn sẵn (có grip) để M, CO, RO, SC… ngay không cần chọn lại.

## Bảng lệnh AutoCAD 2D (F1)
- F1 mở bảng lệnh theo nhóm (Vẽ, Hiệu chỉnh, Kích thước & chữ, Lớp & khối, Đo đạc, Chiếu sáng, Phím) có ô tìm kiếm; bấm dòng để chạy lệnh.
- Gõ vài chữ ở dòng lệnh sẽ hiện gợi ý (↑ ↓ chọn rồi Enter, hoặc Tab để điền).
- Lệnh mới: SPL, PO (điểm – thêm trụ dùng TRU), J, S (STRETCH – lưu dùng Ctrl+S), AL, DAN, DCO, ST, T, B, I, BE, LAYISO, LAYON, AA, Ctrl+P.

## Định vị trên bản đồ (vị trí của tôi)
- Mở app (sau khi đăng nhập) app tự lấy GPS và đưa bản đồ về chỗ người dùng đang đứng: chỉ hiện chấm xanh và vòng sai số, không bật tủ, trụ, đèn nào, không mở danh sách tủ.
- Nút ◎ dưới nút +/− (và nút "Định vị" ở bảng trái): quay về vị trí của tôi và bám theo khi di chuyển; kéo bản đồ thì thôi bám; bấm ◎ khi đang bám để bật la bàn (điện thoại).
- Thẻ góc dưới trái: "Vị trí của tôi", tọa độ, sai số. Bấm × để tắt định vị.
- Cần mở app qua https (GitHub Pages) và cho phép quyền "Vị trí" trên trình duyệt.
