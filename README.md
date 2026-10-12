# Trang điều hành nhóm – Hệ thống NVQS

Cấu trúc: `index.html` (giao diện + logic), `style.css` (màu sắc, bố cục), `README.md`. Không cần cài đặt. Đồng bộ realtime bằng Firebase Realtime Database (miễn phí), đưa lên web bằng git + GitHub Pages.

## 1. Bật đồng bộ realtime (làm một lần)
1. Vào https://console.firebase.google.com → **Add project**.
2. **Build → Realtime Database → Create database** (chọn khu vực gần nhất).
3. Tab **Rules**, dán nội dung sau rồi **Publish**:
```json
{ "rules": { "teams": { "$team": { ".read": true, ".write": true } } } }
```
4. **Project settings → Your apps → Web (</>)** → đăng ký app, sao chép `firebaseConfig`.
5. Mở `index.html`, dán các giá trị vào hằng `CFG` (phải có `databaseURL`).

## 2. Đưa lên web bằng git
```bash
git init
git add .
git commit -m "Trang điều hành nhóm NVQS"
git branch -M main
git remote add origin https://github.com/<tai-khoan>/<ten-repo>.git
git push -u origin main
```
Trên GitHub: **Settings → Pages → Branch: main, thư mục / (root) → Save**. Sau 1–2 phút, trang có địa chỉ `https://<tai-khoan>.github.io/<ten-repo>/`. Mỗi lần sửa code chỉ cần `git add . && git commit -m "..." && git push`.

## 3. Cách dùng
- Cả nhóm mở cùng địa chỉ, nhập **cùng mã nhóm**, chọn vai của mình.
- **Họ tên thành viên** → nhập → **Cập nhật**: mọi chỗ “Nhóm trưởng/TV1/TV2” đổi theo trên máy cả nhóm.
- Bấm vào một việc để đổi trạng thái, ghi chú, báo vướng mắc. Người khác thấy ngay.
- Nhóm trưởng: đánh giá Đạt / Yêu cầu làm lại (bắt buộc ghi nhận xét), giao lại việc, xóa việc thêm.
- **+ Giao thêm nhiệm vụ**: thêm việc mới vào giai đoạn bất kỳ.

## Lưu ý
- Chưa nhập cấu hình Firebase thì trang chạy **chế độ thử** (chỉ đồng bộ giữa các tab cùng máy).
- Chưa có đăng nhập tài khoản: ai biết địa chỉ trang và mã nhóm đều xem và sửa được. Hãy đặt mã nhóm khó đoán.
- Cấu hình Firebase đặt trong code công khai là bình thường; an toàn dựa vào mã nhóm và Rules ở trên.
