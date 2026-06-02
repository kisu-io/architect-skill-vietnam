---
name: mo-hinh-khoi-tich-3d
description: "Tạo mô hình 3D tương tác khối tích xây dựng cho phép (buildable envelope) dựa trên thông số quy hoạch — sử dụng Three.js, xuất HTML."
allowed-tools:
  - Write
  - Edit
  - Read
  - Bash
user-invocable: true
---

# /mo-hinh-khoi-tich-3d — Mô Hình Khối Tích Xây Dựng 3D

Tạo file HTML tương tác hiển thị khối tích xây dựng tối đa cho phép trên lô đất, dựa trên thông số quy hoạch đã phân tích.

## Sử Dụng

```
/mo-hinh-khoi-tich-3d [tham chiếu báo cáo quy hoạch hoặc thông số thủ công]
```

Ví dụ:
- `/mo-hinh-khoi-tich-3d` (sau khi đã chạy `/phan-tich-quy-hoach-vn`)
- `/mo-hinh-khoi-tich-3d lô 20x30m, MDXD 60%, 12 tầng, lùi trước 6m, lùi bên 3m`

## Khi Bắt Đầu

1. Kiểm tra xem đã có báo cáo từ `/phan-tich-quy-hoach-vn` trong thư mục làm việc chưa
2. Nếu có: đọc thông số từ báo cáo, xác nhận với người dùng
3. Nếu không: yêu cầu các thông số tối thiểu sau đây:

| Thông số bắt buộc | Ví dụ |
|---|---|
| Kích thước lô đất (D × R) | 20 m × 30 m |
| Mật độ xây dựng tối đa (MDXD) | 60% |
| Tầng cao tối đa | 12 tầng |
| Chiều cao tầng (mặc định 3,3 m) | 3,3 m |
| Khoảng lùi trước | 6 m |
| Khoảng lùi bên (trái, phải) | 3 m |
| Khoảng lùi sau | 3 m |

Thông số tùy chọn: khoảng lùi tầng trên (nếu khác tầng trệt), tầng hầm, podium.

## Tạo Mô Hình

Tạo file HTML sử dụng Three.js (r128 từ CDN: `https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js`).

### Các Thành Phần

1. **Lô đất** — mặt phẳng màu xám nhạt, hiển thị kích thước D × R
2. **Khối tích cho phép** — khối hộp bán trong suốt (xanh dương, opacity 0.3) thể hiện vùng xây dựng được phép sau khoảng lùi
3. **Khoảng lùi** — vùng đệm màu đỏ nhạt (opacity 0.15) xung quanh khối tích
4. **Chỉ giới đường đỏ** — đường đỏ phía trước lô đất
5. **Nhãn** — hiển thị thông số: MDXD, tầng cao, chiều cao, khoảng lùi
6. **Bảng thông tin** — panel HTML overlay góc trên trái hiển thị tất cả thông số

### Tính Toán Khối Tích

```
chieu_rong_xd = chieu_rong_lo - khong_lui_trai - khong_lui_phai
chieu_dai_xd = chieu_dai_lo - khong_lui_truoc - khong_lui_sau
dt_chiem_dat = chieu_rong_xd × chieu_dai_xd

// Kiểm tra MDXD
mdxd_thuc_te = dt_chiem_dat ÷ dt_lo × 100
if mdxd_thuc_te > mdxd_toi_da:
    // Thu nhỏ khối tích cho phù hợp MDXD
    he_so = (mdxd_toi_da × dt_lo) ÷ dt_chiem_dat
    dt_chiem_dat = dt_chiem_dat × he_so

chieu_cao = tang_cao × chieu_cao_tang
dt_san = dt_chiem_dat × tang_cao
hssd = dt_san ÷ dt_lo
```

### Tương Tác

- **Xoay:** kéo chuột trái (OrbitControls — tự viết, không dùng module import)
- **Zoom:** cuộn chuột
- **Di chuyển:** kéo chuột phải
- **Hover:** hiển thị thông số khi di chuột vào khối tích

### Bảng Thông Tin (HTML Overlay)

```
┌─────────────────────────────┐
│ KHỐI TÍCH XÂY DỰNG         │
│ Lô đất: 20,0 × 30,0 m     │
│ DT lô: 600 m²              │
│ MDXD: 60%                  │
│ DT chiếm đất: 360 m²       │
│ Tầng cao: 12 tầng          │
│ Chiều cao: 39,6 m          │
│ DT sàn tổng: 4.320 m²      │
│ HSSDĐ: 7,2 lần             │
│ Khoảng lùi: T6/B3/P3/S3 m │
└─────────────────────────────┘
```

(T = trước, B = bên trái, P = bên phải, S = sau)

## Đầu Ra

Ghi vào: `./mo-hinh-khoi-tich-[dia-chi-slug].html`

File HTML phải:
- Tự chứa (self-contained), chỉ phụ thuộc CDN Three.js
- Có responsive design (hoạt động trên cả desktop và tablet)
- Hiển thị đơn vị mét (m), m², tầng
- Có tiêu đề và địa chỉ rõ ràng
- Ghi nguồn: "Thông số theo [QH 1/500 / QCVN 01:2021/BXD]"
- Ghi tuyên bố miễn trừ ở footer

## Quy Tắc

- **Hệ mét.** Tất cả kích thước bằng mét, diện tích bằng m².
- **Dấu phẩy thập phân.** `3,3 m` không phải `3.3 m` (trong text hiển thị tiếng Việt).
- **Trình bày tính toán.** Bảng thông tin phải hiển thị cả đầu vào và kết quả.
- **OrbitControls tự viết.** Không import từ Three.js examples (không hỗ trợ). Viết logic xoay/zoom/pan trực tiếp.
- **KHÔNG dùng CapsuleGeometry** — không có trong r128.
