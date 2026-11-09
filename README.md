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
