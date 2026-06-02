---
name: tra-cuu-di-tich
description: "Kiểm tra công trình có nằm trong danh mục di tích lịch sử — văn hóa, khu bảo tồn, hoặc di sản kiến trúc tại Việt Nam không."
allowed-tools:
  - WebSearch
  - WebFetch
  - Write
  - Read
user-invocable: true
---

# /tra-cuu-di-tich — Tra Cứu Di Tích & Di Sản

Kiểm tra công trình hoặc khu vực có thuộc danh mục di tích lịch sử — văn hóa, di sản kiến trúc, hoặc khu bảo tồn tại Việt Nam hay không. Tương đương skill `nyc-landmarks` trong bản gốc.

## Sử Dụng

```
/tra-cuu-di-tich [địa chỉ hoặc tên công trình]
```

## Quy Trình

### 1. Kiểm Tra Di Tích Quốc Gia

Web search: `"di tích" + "[tên công trình / địa chỉ / khu vực]"` trên các nguồn:
- Bộ Văn hóa, Thể thao và Du lịch (Bộ VHTTDL): [bvhttdl.gov.vn](https://bvhttdl.gov.vn)
- Cục Di sản văn hóa
- Danh mục di tích quốc gia (Quyết định công nhận)

Phân loại:
| Cấp | Cơ quan công nhận | Ý nghĩa |
|---|---|---|
| Di tích quốc gia đặc biệt | Thủ tướng Chính phủ | Bảo vệ nghiêm ngặt nhất |
| Di tích quốc gia | Bộ trưởng Bộ VHTTDL | Hạn chế xây dựng trong vùng bảo vệ |
| Di tích cấp tỉnh | UBND tỉnh/thành | Hạn chế tùy quy chế quản lý |

### 2. Kiểm Tra Di Sản UNESCO

Web search: `"UNESCO" + "[tên khu vực]"` — kiểm tra xem có thuộc:
- Di sản Thế giới (World Heritage Site): Hội An, Huế, Vịnh Hạ Long, Mỹ Sơn, Tràng An, Thành Nhà Hồ, Hoàng thành Thăng Long
- Khu dự trữ sinh quyển

### 3. Kiểm Tra Khu Bảo Tồn Kiến Trúc

Một số khu vực có quy chế bảo tồn kiến trúc (không phải di tích chính thức nhưng có hạn chế xây dựng):
- Khu phố cổ Hà Nội (36 phố phường)
- Khu phố cổ Hội An
- Khu biệt thự Pháp tại Hà Nội (quanh Hồ Tây, Ba Đình)
- Khu trung tâm Quận 1, 3 TP.HCM (công trình kiến trúc Pháp thuộc)

### 4. Hệ Quả Xây Dựng

Nếu phát hiện di tích hoặc khu bảo tồn, ghi rõ:
- Vùng bảo vệ I (bất khả xâm phạm) và vùng bảo vệ II (hạn chế)
- Yêu cầu xin ý kiến Bộ VHTTDL / Sở VHTTDL trước khi xây dựng
- Hạn chế chiều cao, mật độ, phong cách kiến trúc
- Tham chiếu: Luật Di sản Văn hóa 28/2001/QH10 (sửa đổi 2009)

## Định Dạng Đầu Ra

```markdown
---
tieu-de: "Tra cứu di tích — [Địa chỉ / Công trình]"
ngay: [YYYY-MM-DD]
ky-nang: tra-cuu-di-tich
---

# Tra Cứu Di Tích & Di Sản — [Địa Chỉ]

## Kết Quả

**Tình trạng: [DI TÍCH QUỐC GIA / KHU BẢO TỒN / KHÔNG PHÁT HIỆN]**

| Hạng mục | Kết quả |
|---|---|
| Di tích quốc gia | [Có / Không] |
| Di tích cấp tỉnh | [Có / Không / Chưa xác định] |
| Di sản UNESCO | [Có / Không] |
| Khu bảo tồn kiến trúc | [Có / Không] |

## Hệ Quả Xây Dựng
[Nếu có di tích: hạn chế, cơ quan cần xin ý kiến]

**Hệ quả:** [Mô tả tác động đến dự án xây dựng]

## Nguồn
## Khoảng Trống & Lưu Ý
```

## Quy Tắc

- **Nếu không phát hiện:** "Không tìm thấy thông tin di tích trong phạm vi tra cứu trực tuyến. Khuyến nghị kiểm tra tại Sở VHTTDL [tỉnh/thành]."
- **Tuyên bố miễn trừ bắt buộc.**
