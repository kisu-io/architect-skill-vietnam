---
name: tra-cuu-dat-dai
description: "Tra cứu thông tin đất đai — quyền sử dụng đất, lịch sử giao dịch, giá đất theo bảng giá UBND tỉnh."
allowed-tools:
  - WebSearch
  - WebFetch
  - Write
  - Read
user-invocable: true
---

# /tra-cuu-dat-dai — Tra Cứu Thông Tin Đất Đai

Tra cứu thông tin đất đai cho mục đích thẩm định, bao gồm quyền sử dụng đất, lịch sử giao dịch (nếu công khai), và giá đất theo bảng giá UBND tỉnh.

## Sử Dụng

```
/tra-cuu-dat-dai [địa chỉ hoặc thông tin thửa đất]
```

## Khi Bắt Đầu

Hỏi **địa chỉ** và hỏi thêm: "Bạn có thông tin từ sổ đỏ (số thửa, tờ bản đồ, mục đích SDĐ, diện tích)?"

## Quy Trình

### 1. Giá Đất Theo Bảng Giá

Web search: `"bảng giá đất" + "[tỉnh/thành]" + "[năm]" + "[tên đường / khu vực]"`

Trích xuất:
- Giá đất (VND/m²) theo vị trí (VT1, VT2, VT3, VT4)
- Năm ban hành bảng giá
- Quyết định UBND tỉnh (số hiệu)

### 2. Thông Tin Pháp Lý Công Khai

- Kiểm tra có công bố quyền sử dụng đất khu vực online không
- Kiểm tra lịch sử giao dịch qua báo chí (đấu giá đất công khai)
- Kiểm tra tranh chấp, khiếu nại (nếu có thông tin công khai)

### 3. Đầu Ra

```markdown
---
tieu-de: "Tra cứu đất đai — [Địa chỉ]"
ngay: [YYYY-MM-DD]
ky-nang: tra-cuu-dat-dai
---

# Tra Cứu Đất Đai — [Địa Chỉ]

## Giá Đất Theo Bảng Giá
| Vị trí | Giá (VND/m²) | Nguồn |
|---|---|---|

## Thông Tin Pháp Lý Công Khai
[Kết quả tra cứu]

## Nguồn
## Khoảng Trống & Lưu Ý
- Thông tin sổ đỏ cá nhân không công khai — cần người dùng cung cấp
- Giá thị trường thường cao hơn bảng giá UBND 3–10 lần
```

## Quy Tắc

- **Bảo mật.** Không lưu trữ thông tin cá nhân chủ sở hữu.
- **Giá là tham khảo.** Luôn ghi "cần thẩm định giá độc lập."
- **Tuyên bố miễn trừ bắt buộc.**
