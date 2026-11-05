# VHWS Label — In tem TSC

Web app thiết kế và in tem cho máy in nhiệt TSC. Một file `index.html`, không cần server.

- Link: https://cps-vhws.github.io/vhws-label/
- Hướng dẫn: https://cps-vhws.github.io/vhws-label/#huong-dan

## Thông số mặc định

| | |
|---|---|
| Tem | 40 × 30 mm, 2 tem/hàng |
| Giấy đế | 87 mm = lề 2.5 + tem 40 + khe 2 + tem 40 + lề 2.5 |
| Khe hàng | 3 mm (driver: Media = Gap 3 mm) |
| Driver | Khổ giấy 87 × 30 mm, Portrait |
| Vùng an toàn | 2 mm từ mép tem |

## Cách hoạt động

- In qua driver + hộp thoại in của Chrome/Edge (`@page` = khổ 1 hàng tem, mỗi trang in = 1 hàng).
- Dữ liệu: Excel (.xlsx, sheet đầu) hoặc CSV/dán từ Excel. Mỗi `{Tên cột}` trong mẫu = 1 cột; ghép cột tự khớp theo tên (bỏ dấu).
- Mẫu tem, dữ liệu, mẫu ★ lưu trong trình duyệt (localStorage) của từng máy. Mang sang máy khác: Xuất file / Nhập file mẫu.
- Thư viện qua CDN: JsBarcode 3.11.6, qrcode-generator 1.4.4, SheetJS xlsx 0.18.5 → cần internet.

## Nhật ký thay đổi

- 03/11/2026 · Bản đầu: thiết kế kéo thả, nhập Excel/CSV, 2 tem/hàng
- 03/11/2026 · Hoàn tác (Ctrl+Z), lưu/mở/xuất mẫu tem ★
- 03/11/2026 · Nút In thử 1 hàng
- 03/11/2026 · Khổ giấy đế 87 mm: lề 2.5, khe 2 tem 2 mm, khe hàng 3 mm + sơ đồ cuộn tem
- 03/11/2026 · Giao diện 3 bước (Chọn mẫu → Nhập dữ liệu → In), kéo thả file, gom phần khổ giấy
- 03/11/2026 · Bỏ ô cột số lượng, chỉ giữ Số tem mỗi dòng (in lặp liền nhau)
- 03/11/2026 · Mẫu 3: 2 QR đối xứng, QR lấy từ cột QR
- 03/11/2026 · Tải file Excel mẫu theo đúng các cột của mẫu, ghép cột Excel vào QR/chữ
- 03/11/2026 · Tab Hướng dẫn (yêu cầu máy, driver, vùng an toàn), cảnh báo viền đỏ khi ra ngoài vùng an toàn
- 03/11/2026 · Thanh đầu trang cố định khi cuộn
- 03/11/2026 · Mẫu Tem trắng để tự thiết kế
- 03/11/2026 · Nút + Thêm trường (tự có cột trong file Excel mẫu)
- 03/11/2026 · Icon tab mới: ô vuông 2 hàng VHWS / IN TEM
- 03/11/2026 · Chuyển repo sang CPS-VHWS/vhws-label (link cũ minhthanhbrvt95-web.github.io/tsc-label đã ngừng)
- 03/11/2026 · Cấu hình máy in / loại tem: mặc định TSC TE300 · 40×30 · 2 tem/hàng, lưu thêm cấu hình khác (★), cảnh báo đổi máy/đổi tem
- 03/11/2026 · Nút In / In thử lên thanh trên cùng; Xem trước bản in (cuộn tem thật) dưới khung thiết kế
- 03/11/2026 · Đổi loại phần tử (Chữ / QR / Mã vạch / Khung) ở khung bên phải; chip chèn trường gồm cả trường của mẫu
- 03/11/2026 · Hướng dẫn hộp thoại in: phải chọn máy TSC, không chọn máy A4
- 03/11/2026 · + Thêm trường tự thêm cột vào dữ liệu đang nhập; trường chưa có cột thì chọn "+ Thêm cột … vào dữ liệu"
- 03/11/2026 · Dữ liệu hiện dạng bảng: sửa từng ô, + Thêm dòng, dán nhiều ô từ Excel; ô chữ thô chuyển vào mục "Dán cả bảng"
- 03/11/2026 · Làm lại (Ctrl/⌘+Y, Shift+Ctrl/⌘+Z); phím tắt hoàn tác chạy cả khi đang chọn ô số/ô chọn; icon mới
- 03/11/2026 · Sửa lỗi in tem xoay (Mẫu 2): các trang đầu bị mất dòng dưới do Chrome cắt trang theo khung chưa xoay. Đã kiểm tra in ra PDF cả 3 mẫu: mỗi trang 87×30 mm, đủ nội dung, không trang trắng
- 05/11/2026 · Sửa lỗi in máy TSC bị xoay 90° và dính ngày giờ / link / số trang: bỏ khổ giấy trong `@page` (khổ 87×30 làm Chrome tự chuyển trang ngang), để trình duyệt dùng khổ giấy của driver, hướng dọc. Hướng dẫn in thêm Bố cục = Dọc, Khổ giấy 87×30

## Chưa làm

- In trực tiếp bằng lệnh TSPL (không qua driver) — chỉ cần khi in hàng nghìn tem hoặc bản in bị mờ.
- Đồng bộ mẫu giữa các máy qua mạng (hiện dùng Xuất/Nhập file).
- Chạy offline (nhúng thư viện vào file).
