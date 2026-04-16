---
name: phan-tich-lich-su
description: "Phân tích bối cảnh lịch sử, kiến trúc lân cận, và phát triển đô thị cho khu vực tại Việt Nam."
allowed-tools:
  - WebSearch
  - WebFetch
  - Write
  - Read
  - Bash
user-invocable: true
---

# /phan-tich-lich-su — Phân Tích Bối Cảnh & Lịch Sử Khu Vực

Phân tích bối cảnh lịch sử, đặc trưng kiến trúc lân cận, xu hướng phát triển đô thị, và hoạt động thương mại cho một khu vực cụ thể. Tương đương skill `history` trong bản gốc.

## Sử Dụng

```
/phan-tich-lich-su [địa chỉ hoặc khu vực]
```

Ví dụ:
- `/phan-tich-lich-su Quận 1, TP.HCM`
- `/phan-tich-lich-su Khu phố cổ Hà Nội`
- `/phan-tich-lich-su Phú Mỹ Hưng, Quận 7, TP.HCM`

## Khi Bắt Đầu

Hỏi **địa chỉ hoặc khu vực + tỉnh/thành phố**. Sau đó bắt đầu — không hỏi thêm.

## Quy Trình

### 1. Lịch Sử Phát Triển Khu Vực

Web search: `"lịch sử" + "[khu vực]"` hoặc `"quá trình phát triển" + "[quận/phường]"`

Xác định:
- Thời kỳ hình thành: tiền thuộc địa / Pháp thuộc (1858–1945) / 1945–1975 / sau 1975 / sau Đổi Mới (1986+) / 2000+
- Chức năng lịch sử: thương cảng / hành chính / quân sự / nông nghiệp / công nghiệp
- Các mốc phát triển quan trọng (thành lập KĐT, mở rộng đô thị, hợp nhất hành chính)
- Biến đổi chức năng qua thời gian

### 2. Đặc Trưng Kiến Trúc Lân Cận

Web search: `"kiến trúc" + "[khu vực]"` hoặc quan sát qua Google Street View / ảnh vệ tinh.

- Phong cách chủ đạo:
  - Kiến trúc Pháp thuộc (biệt thự, nhà hàng, công sở — Q1/Q3 TP.HCM, Ba Đình Hà Nội)
  - Nhà ống truyền thống (phố cổ Hà Nội, Hội An)
  - Nhà phố tự xây (phổ biến nhất — mặt tiền hẹp, nhiều tầng)
  - Chung cư cũ (KTT — khu tập thể 1960–1980)
  - Khu đô thị mới (KĐT — Phú Mỹ Hưng, Ecopark, Vinhomes)
  - Công trình hiện đại (tòa nhà VP, thương mại sau 2000)

- Chiều cao phổ biến: [1–3 tầng / 4–7 tầng / cao tầng]
- Vật liệu chủ đạo: gạch + bê tông / kính / mái ngói
- Mật độ xây dựng quan sát: thấp / trung bình / cao / rất cao

### 3. Công Trình Đáng Chú Ý

Liệt kê công trình nổi bật trong bán kính 500 m – 1 km:
- Di tích / di sản (liên kết với `/tra-cuu-di-tich`)
- Công trình kiến trúc tiêu biểu (có giải thưởng, KTS nổi tiếng)
- Landmark (tòa nhà cao nhất, TTTM lớn, công viên)
- Dự án đang xây dựng / vừa hoàn thành

### 4. Hoạt Động Thương Mại

Web search: `"thương mại" + "[khu vực]"` hoặc `"kinh doanh" + "[đường / phường]"`

- Loại hình thương mại chủ đạo: bán lẻ / F&B / dịch vụ / sản xuất nhỏ
- Phố chuyên doanh (nếu có): phố đèn lồng, phố ẩm thực, phố thời trang
- Chợ truyền thống lân cận
- TTTM / siêu thị
- Mức giá thuê mặt bằng tham khảo (nếu có)

### 5. Xu Hướng Phát Triển

Web search: `"dự án" + "[khu vực]" + "quy hoạch"` hoặc `"phát triển đô thị" + "[quận]"`

- Dự án hạ tầng đang/sắp triển khai (metro, cầu, đường vành đai, cao tốc)
- Dự án BĐS lớn đang triển khai lân cận
- Kế hoạch chỉnh trang đô thị / di dời (KCN, bến cảng, nhà máy)
- Xu hướng giá đất 3–5 năm
- Dân số nhập cư / xu hướng đô thị hóa

### 6. Hệ Quả Cho Thiết Kế

Tổng hợp thành khuyến nghị:
- **Phong cách kiến trúc:** hòa nhập vs tương phản với bối cảnh
- **Chiều cao:** phù hợp với skyline lân cận (ngoài yêu cầu QH)
- **Mặt đứng:** vật liệu, tỷ lệ tương thích
- **Công năng:** phù hợp với nhu cầu thương mại khu vực
- **Bảo tồn:** nếu khu vực có giá trị kiến trúc / lịch sử

## Định Dạng Đầu Ra

```markdown
---
tieu-de: "Phân tích bối cảnh khu vực — [Khu vực]"
ngay: [YYYY-MM-DD]
khu-vuc: "[Quận/Phường, Tỉnh/Thành]"
ky-nang: phan-tich-lich-su
---

# Phân Tích Bối Cảnh & Lịch Sử — [Khu Vực]

## Tổng Quan

| Thông số | Mô tả |
|---|---|
| Thời kỳ hình thành | [Giai đoạn] |
| Đặc trưng kiến trúc | [Phong cách chủ đạo] |
| Chiều cao phổ biến | [Số tầng] |
| Hoạt động thương mại | [Loại hình chủ đạo] |

## Lịch Sử Phát Triển
[Mô tả theo timeline]

## Đặc Trưng Kiến Trúc Lân Cận
[Phong cách, vật liệu, mật độ]

## Công Trình Đáng Chú Ý
[Danh sách + mô tả ngắn]

## Hoạt Động Thương Mại
[Loại hình, phố chuyên doanh, chợ, TTTM]

## Xu Hướng Phát Triển
[Hạ tầng, BĐS, đô thị hóa]

## Khuyến Nghị Thiết Kế
[Tổng hợp hệ quả cho kiến trúc]

## Nguồn
## Khoảng Trống & Lưu Ý
```

## Quy Tắc

- **Bối cảnh Việt Nam đặc thù.** Không áp dụng phân loại kiến trúc phương Tây (Victorian, Art Deco...) trừ khi thực sự có mặt (kiến trúc Pháp thuộc).
- **Nhà ống / nhà phố tự xây** là hình thái đô thị phổ biến nhất — đặc trưng: mặt tiền 4–6 m, sâu 15–20 m, 3–5 tầng. Ghi nhận nếu đây là bối cảnh.
- **Cẩn trọng với dự án "quy hoạch".** Nhiều dự án được công bố nhưng chậm triển khai — ghi rõ trạng thái (đã khởi công / mới phê duyệt / chỉ đồn đoán).
- **Tuyên bố miễn trừ bắt buộc.**
