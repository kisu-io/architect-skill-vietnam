---
name: phan-tich-giao-thong
description: "Phân tích giao thông và kết nối hạ tầng cho lô đất tại Việt Nam — đường bộ, GTCC, xe buýt, metro, đường sắt, sân bay, bến xe."
allowed-tools:
  - WebSearch
  - WebFetch
  - Write
  - Read
  - Bash
user-invocable: true
---

# /phan-tich-giao-thong — Phân Tích Giao Thông & Kết Nối

Phân tích khả năng tiếp cận và kết nối giao thông của lô đất, phục vụ đánh giá vị trí và thiết kế giao thông nội bộ. Tương đương skill `mobility-analysis` trong bản gốc.

## Sử Dụng

```
/phan-tich-giao-thong [địa chỉ]
```

Ví dụ:
- `/phan-tich-giao-thong 88 Nguyễn Huệ, Quận 1, TP.HCM`
- `/phan-tich-giao-thong Lô B3, KĐT Vinhomes Ocean Park, Gia Lâm, Hà Nội`

## Khi Bắt Đầu

Hỏi **địa chỉ + tỉnh/thành phố**. Hỏi thêm: "Dự án dự kiến có bao nhiêu căn hộ / văn phòng / chỗ đậu xe?" (để ước lượng nhu cầu giao thông). Sau đó bắt đầu.

## Quy Trình

### 1. Mạng Lưới Đường Bộ

Web search: `"[địa chỉ]" + "giao thông"` và kiểm tra trên OpenStreetMap / Google Maps.

Xác định:
- Đường tiếp giáp: tên đường, lộ giới (m), số làn xe
- Phân loại đường: quốc lộ / tỉnh lộ / đường đô thị / đường nội bộ KĐT
- Tình trạng: đã hoàn thiện / đang thi công / quy hoạch
- Khoảng cách đến đường chính / quốc lộ gần nhất

### 2. Giao Thông Công Cộng (GTCC)

#### a) Xe buýt
Web search: `"xe buýt" + "[khu vực]"` hoặc `"tuyến xe buýt qua" + "[đường]"`

- Các tuyến buýt gần nhất (trong bán kính 500 m)
- Trạm / điểm dừng gần nhất
- Tần suất (giờ cao điểm / thường)
- Nguồn: buyttphcm.com.vn (TP.HCM), transerco.vn (Hà Nội)

#### b) Metro / Đường sắt đô thị
Tình trạng các tuyến metro tại Việt Nam:

| Tuyến | Thành phố | Trạng thái | Dự kiến |
|---|---|---|---|
| Metro số 1 (Bến Thành — Suối Tiên) | TP.HCM | Hoạt động từ 2024 | — |
| Metro số 2 (Bến Thành — Tham Lương) | TP.HCM | Đang xây dựng | ~2030 |
| Metro Nhổn — Ga Hà Nội (tuyến 3) | Hà Nội | Hoạt động một phần | — |
| Metro Nam Thăng Long — Trần Hưng Đạo (tuyến 2) | Hà Nội | Đang xây dựng | ~2030 |

Kiểm tra: khoảng cách đến ga metro gần nhất (hiện hữu hoặc quy hoạch).

#### c) BRT (Bus Rapid Transit)
- Hà Nội: tuyến BRT Kim Mã — Yên Nghĩa
- TP.HCM: tuyến BRT số 1 (quy hoạch)

#### d) Đường sắt quốc gia
- Khoảng cách đến ga tàu hỏa gần nhất
- Tuyến đường sắt tốc độ cao Bắc — Nam (quy hoạch)

### 3. Kết Nối Sân Bay

| Sân bay | Mã IATA | Phục vụ |
|---|---|---|
| Tân Sơn Nhất | SGN | TP.HCM |
| Nội Bài | HAN | Hà Nội |
| Đà Nẵng | DAD | Đà Nẵng, miền Trung |
| Long Thành (đang XD) | — | TP.HCM (dự kiến 2026+) |
| Cam Ranh | CXR | Khánh Hòa |
| Phú Quốc | PQC | Kiên Giang |

Khoảng cách + thời gian di chuyển ước tính đến sân bay chính.

### 4. Bến Xe & Đường Thủy

- Bến xe khách liên tỉnh gần nhất
- Bến phà / đường thủy (nếu khu vực ven sông / ĐBSCL)

### 5. Hạ Tầng Phi Cơ Giới

- Vỉa hè: có / không / chất lượng
- Làn xe đạp: rất hiếm tại Việt Nam, ghi nhận nếu có
- Dự án đi bộ / không gian công cộng lân cận

### 6. Đánh Giá Tổng Hợp

Chấm điểm khả năng tiếp cận (thang 5 sao, giải thích):

| Phương tiện | Đánh giá | Ghi chú |
|---|---|---|
| Ô tô / Xe máy | ⭐⭐⭐⭐⭐ | [Mô tả] |
| Xe buýt | ⭐⭐⭐ | [Mô tả] |
| Metro / BRT | ⭐⭐ | [Mô tả] |
| Đi bộ | ⭐⭐⭐ | [Mô tả] |
| Sân bay | ⭐⭐⭐⭐ | [Mô tả] |

**Lưu ý Việt Nam:** Xe máy chiếm 70–80% phương tiện tại đô thị lớn. Thiết kế bãi đậu xe máy quan trọng hơn bãi đậu ô tô ở nhiều dự án.

### 7. Hệ Quả Cho Dự Án

- Số chỗ đậu xe yêu cầu theo QCVN 01:2021/BXD (tùy công năng + quy mô)
- Lối vào / ra: vị trí gợi ý dựa trên đường tiếp giáp
- Bán kính phục vụ GTCC — ảnh hưởng đến tỷ lệ sử dụng xe cá nhân
- Tiềm năng TOD (Transit-Oriented Development) nếu gần ga metro

## Định Dạng Đầu Ra

```markdown
---
tieu-de: "Phân tích giao thông — [Địa chỉ]"
ngay: [YYYY-MM-DD]
dia-chi: "[Địa chỉ đầy đủ]"
ky-nang: phan-tich-giao-thong
---

# Phân Tích Giao Thông & Kết Nối — [Địa Chỉ]

## Tổng Quan

| Thông số | Giá trị |
|---|---|
| Đường tiếp giáp chính | [Tên + lộ giới] |
| GTCC gần nhất | [Loại + khoảng cách] |
| Metro gần nhất | [Ga + khoảng cách + trạng thái] |
| Sân bay | [Tên + khoảng cách + thời gian] |

## Mạng Lưới Đường Bộ
[Chi tiết đường tiếp giáp, phân loại]

## Giao Thông Công Cộng
[Xe buýt, Metro, BRT, đường sắt]

## Kết Nối Sân Bay & Liên Tỉnh
[Sân bay, bến xe, đường thủy]

## Hạ Tầng Đi Bộ & Xe Đạp
[Vỉa hè, làn xe đạp]

## Đánh Giá Tổng Hợp
[Bảng chấm điểm 5 sao]

## Khuyến Nghị Cho Dự Án
[Đậu xe, lối vào/ra, TOD]

## Nguồn
## Khoảng Trống & Lưu Ý
```

## Quy Tắc

- **Đơn vị:** km, m, phút. Theo `don-vi-do-luong.md`.
- **Metro:** luôn ghi rõ trạng thái (hoạt động / đang xây / quy hoạch). Tình trạng thay đổi nhanh — web search để cập nhật.
- **Xe máy là mặc định.** Không áp dụng tiêu chuẩn Walk Score / Transit Score kiểu Mỹ — bối cảnh giao thông VN khác biệt.
- **Tuyên bố miễn trừ bắt buộc.**
