---
name: tra-cuu-pccc
description: "Phân tích yêu cầu PCCC cho công trình tại Việt Nam — bậc chịu lửa, thoát nạn, hệ thống chữa cháy, thẩm duyệt. Dựa trên QCVN 06:2021/BXD."
allowed-tools:
  - WebSearch
  - WebFetch
  - Write
  - Edit
  - Read
  - Bash
user-invocable: true
---

# /tra-cuu-pccc — Phân Tích Yêu Cầu PCCC

Phân tích yêu cầu Phòng cháy chữa cháy (PCCC — Fire Protection) cho một công trình cụ thể, dựa trên QCVN 06:2021/BXD và các TCVN liên quan.

## Sử Dụng

```
/tra-cuu-pccc [mô tả công trình]
```

Ví dụ:
- `/tra-cuu-pccc tòa nhà văn phòng 15 tầng, Quận 7, TP.HCM`
- `/tra-cuu-pccc chung cư 25 tầng, hỗn hợp thương mại tầng 1-3`

## Khi Bắt Đầu

Hỏi các thông tin tối thiểu (nếu chưa cung cấp):
- Loại công trình (nhà ở / văn phòng / thương mại / hỗn hợp / công nghiệp)
- Số tầng và chiều cao ước tính
- Vị trí (tỉnh/thành)

## Quy Trình

### 1. Xác Định Bậc Chịu Lửa

Theo QCVN 06:2021/BXD, Điều 4.1 và Bảng 4:

| Số tầng / Chiều cao | Bậc chịu lửa tối thiểu |
|---|---|
| ≤ 3 tầng (≤ 9 m) | III–V |
| 4–5 tầng (≤ 18 m) | II–III |
| 6–9 tầng (≤ 28 m) | I–II |
| 10–16 tầng (≤ 50 m) | I |
| > 16 tầng (> 50 m) | I (yêu cầu đặc biệt) |

Ghi rõ giới hạn chịu lửa từng cấu kiện (tường, cột, dầm, sàn, cầu thang) — tham chiếu Bảng 4.

### 2. Phân Tích Thoát Nạn

Theo QCVN 06:2021/BXD, Điều 3.2–3.4 và Bảng 6:

- Số lối thoát nạn tối thiểu mỗi tầng
- Chiều rộng cầu thang thoát nạn (fire escape stairway)
- Chiều rộng hành lang thoát nạn
- Khoảng cách thoát nạn tối đa (hành lang cụt vs hành lang thông)
- Loại buồng thang bộ yêu cầu (thường / N1 không nhiễm khói / N2 áp suất dương / N3)

Ngưỡng quan trọng: **nhà > 28 m** bắt buộc buồng thang bộ không nhiễm khói (smoke-proof stairwell) loại N1.

### 3. Xác Định Hệ Thống Bắt Buộc

Theo QCVN 06:2021/BXD Phụ lục D và TCVN tương ứng:

| Hệ thống | Khi nào bắt buộc | TCVN | CSI Division |
|---|---|---|---|
| Sprinkler tự động | Nhà > 6 tầng hoặc > 1.000 m² sàn/tầng | TCVN 7336:2021 | 21 13 00 |
| Báo cháy tự động | Hầu hết công trình công cộng | TCVN 5738:2021 | 28 31 00 |
| Họng nước chữa cháy | Nhà > 2 tầng công cộng | TCVN 3890:2023 | 21 13 00 |
| Hút khói | Hành lang, tầng hầm, sảnh kín | QCVN 06, Đ.3.8 | 23 00 00 |
| Thang máy chữa cháy | Nhà > 28 m | QCVN 06, Đ.3.5.2 | 14 00 00 |
| Đèn sự cố + biển chỉ dẫn | Mọi công trình | QCVN 12:2014/BXD | 26 00 00 |

### 4. Khoang Ngăn Cháy

Tính diện tích khoang ngăn cháy (fire compartment) tối đa theo QCVN 06:2021/BXD, Bảng 5 — phụ thuộc bậc chịu lửa, công năng, và có/không có Sprinkler.

### 5. Thẩm Duyệt PCCC

Kiểm tra công trình có thuộc diện bắt buộc thẩm duyệt thiết kế PCCC (fire safety approval) theo Luật PCCC 40/2024/QH15, Điều 15:
- Nhà cao ≥ 7 tầng hoặc > 5.000 m² sàn: bắt buộc
- Cơ quan: Phòng/Cục CS PCCC và CNCH — Công an tỉnh/thành

## Định Dạng Đầu Ra

```markdown
---
tieu-de: "Yêu cầu PCCC — [Mô tả công trình]"
ngay: [YYYY-MM-DD]
dia-chi: "[Vị trí]"
ky-nang: tra-cuu-pccc
---

# Yêu Cầu PCCC — [Mô Tả Công Trình]

## Thông Tin Đầu Vào
[Bảng thông số công trình]

## Bậc Chịu Lửa
[Bảng giới hạn chịu lửa từng cấu kiện]

## Thoát Nạn
[Bảng yêu cầu thoát nạn: số lối ra, chiều rộng, khoảng cách]

## Hệ Thống PCCC Bắt Buộc
[Bảng hệ thống + TCVN + mã CSI]

## Khoang Ngăn Cháy
[Diện tích tối đa theo công năng]

## Thẩm Duyệt
[Thuộc diện hay không, cơ quan]

## Nguồn
## Khoảng Trống & Lưu Ý
```

## Quy Tắc

- **Trích QCVN 06:2021/BXD có điều khoản cụ thể.**
- **Mã CSI cho hệ thống kỹ thuật** (theo `dinh-dang-csi.md`).
- **Trình bày giả định rõ ràng** (chiều cao tầng giả định, công năng giả định).
- **Tuyên bố miễn trừ bắt buộc.**
