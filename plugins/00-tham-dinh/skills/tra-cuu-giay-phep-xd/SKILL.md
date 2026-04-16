---
name: tra-cuu-giay-phep-xd
description: "Tra cứu giấy phép xây dựng (GPXD) và hồ sơ xin phép cho công trình tại Việt Nam — quy trình, hồ sơ, cơ quan cấp phép."
allowed-tools:
  - WebSearch
  - WebFetch
  - Write
  - Edit
  - Read
  - Bash
user-invocable: true
---

# /tra-cuu-giay-phep-xd — Tra Cứu Giấy Phép Xây Dựng

Tra cứu thông tin giấy phép xây dựng (building permit), quy trình cấp phép, và hồ sơ yêu cầu cho một công trình hoặc địa chỉ cụ thể tại Việt Nam.

## Sử Dụng

```
/tra-cuu-giay-phep-xd [địa chỉ hoặc mô tả công trình]
```

## Khi Bắt Đầu

Hỏi: **địa chỉ + loại công trình + quy mô** (số tầng, diện tích ước tính). Sau đó nghiên cứu.

## Quy Trình

### 1. Xác Định Cơ Quan Cấp Phép

| Quy mô công trình | Cơ quan cấp GPXD | Căn cứ |
|---|---|---|
| Công trình cấp I, cấp đặc biệt | Sở Xây dựng | Luật XD 50/2014, Điều 103 |
| Công trình cấp II–IV, nhà ở riêng lẻ | UBND quận/huyện | Luật XD 50/2014, Điều 103 |
| Công trình trong KCN, KCX | Ban quản lý KCN | NĐ 15/2021/NĐ-CP |

### 2. Kiểm Tra Miễn Phép

Các công trình miễn GPXD (Luật XD 50/2014, Điều 89, sửa đổi bởi Luật 62/2020, Điều 89a):
- Nhà ở riêng lẻ ≤ 7 tầng trong dự án đã phê duyệt quy hoạch chi tiết
- Công trình bí mật nhà nước, công trình tạm phục vụ thi công
- Công trình sửa chữa, cải tạo không thay đổi kết cấu chịu lực, công năng, quy mô

### 3. Tra Cứu Trực Tuyến (nếu có)

- Cổng dịch vụ công quốc gia: [dichvucong.gov.vn](https://dichvucong.gov.vn)
- Cổng dịch vụ công cấp tỉnh (tùy địa phương)
- Web search: `"giấy phép xây dựng" + "[địa chỉ]" + "[quận]"`

### 4. Hồ Sơ Yêu Cầu

Liệt kê hồ sơ xin GPXD theo NĐ 15/2021/NĐ-CP, Điều 43–46:

**Nhà ở riêng lẻ:**
- Đơn xin GPXD (mẫu)
- Bản sao GCNQSDĐ (sổ đỏ)
- Bản vẽ thiết kế: mặt bằng, mặt cắt, mặt đứng, móng (2 bộ)
- Ảnh hiện trạng

**Công trình khác:**
- Tất cả các mục trên, cộng thêm:
- Hồ sơ thiết kế cơ sở đã thẩm định
- Thẩm duyệt PCCC (fire safety approval) — QCVN 06:2021/BXD
- Đánh giá tác động môi trường (ĐTM) nếu thuộc diện bắt buộc
- Chứng chỉ hành nghề của chủ nhiệm thiết kế

### 5. Thời Gian & Chi Phí

| Loại | Thời gian xử lý | Lệ phí |
|---|---|---|
| Nhà ở riêng lẻ | 15 ngày làm việc | Theo quy định UBND tỉnh |
| Công trình khác | 30 ngày làm việc | Theo quy định UBND tỉnh |
| Gia hạn GPXD | 15 ngày | — |

## Định Dạng Đầu Ra

```markdown
---
tieu-de: "Tra cứu GPXD — [Địa chỉ / Công trình]"
ngay: [YYYY-MM-DD]
dia-chi: "[Địa chỉ đầy đủ]"
ky-nang: tra-cuu-giay-phep-xd
---

# Tra Cứu Giấy Phép Xây Dựng — [Địa Chỉ]

## Tổng Quan
| Thông số | Giá trị |
|---|---|
| Loại công trình | [...] |
| Cơ quan cấp phép | [...] |
| Miễn phép? | [Có / Không — lý do] |
| Thời gian dự kiến | [...] ngày làm việc |

## Hồ Sơ Yêu Cầu
[Checklist chi tiết]

## Quy Trình
[Các bước tuần tự]

## Nguồn
## Khoảng Trống & Lưu Ý
```

## Quy Tắc

- **Trích luật có số hiệu.** "NĐ 15/2021/NĐ-CP, Điều 43" — không ghi "nghị định về xây dựng".
- **Không khẳng định "đủ điều kiện cấp phép."** Ghi "theo quy định, hồ sơ cần bao gồm..."
- **Tuyên bố miễn trừ bắt buộc.**
