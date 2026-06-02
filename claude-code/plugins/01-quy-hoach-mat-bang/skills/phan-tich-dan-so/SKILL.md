---
name: phan-tich-dan-so
description: "Phân tích dân số và thị trường bất động sản cho khu vực tại Việt Nam — dân số, thu nhập, độ tuổi, nhà ở, việc làm."
allowed-tools:
  - WebSearch
  - WebFetch
  - Write
  - Read
  - Bash
user-invocable: true
---

# /phan-tich-dan-so — Phân Tích Dân Số & Thị Trường

Phân tích dữ liệu dân số, kinh tế, và thị trường bất động sản cho một khu vực, phục vụ đánh giá khả thi và lập hồ sơ dự án. Tương đương skill `demographics-analysis` trong bản gốc.

## Sử Dụng

```
/phan-tich-dan-so [địa chỉ hoặc khu vực]
```

Ví dụ:
- `/phan-tich-dan-so Quận 7, TP.HCM`
- `/phan-tich-dan-so TP. Thủ Đức, TP.HCM`
- `/phan-tich-dan-so Huyện Gia Lâm, Hà Nội`

## Khi Bắt Đầu

Hỏi **khu vực (quận/huyện + tỉnh/thành)** và **loại dự án dự kiến** (nhà ở / thương mại / văn phòng / hỗn hợp). Sau đó bắt đầu.

## Quy Trình

### 1. Dân Số & Mật Độ

Nguồn chính: Tổng cục Thống kê (gso.gov.vn), Cục Thống kê tỉnh/thành, Niên giám thống kê.

Web search: `"dân số" + "[quận/huyện]" + "[tỉnh/thành]" + "[năm gần nhất]"`

Trích xuất:
- Dân số (người)
- Diện tích tự nhiên (km²)
- Mật độ dân số (người/km²)
- Tốc độ tăng dân số (% / năm)
- Dân số đô thị vs nông thôn (%)
- So sánh với trung bình tỉnh/thành

Mốc tham chiếu: Tổng điều tra dân số 2019 + cập nhật hàng năm.

### 2. Cơ Cấu Tuổi & Hộ Gia Đình

Web search: `"cơ cấu dân số" + "[khu vực]"` hoặc `"dân số theo độ tuổi" + "[tỉnh/thành]"`

- Phân bố theo nhóm tuổi: 0–14, 15–24, 25–44, 45–64, 65+
- Quy mô hộ gia đình trung bình (người/hộ)
- Số hộ gia đình
- Tỷ lệ nhập cư / di cư (đặc biệt quan trọng tại TP.HCM, Bình Dương, Đồng Nai)

### 3. Thu Nhập & Kinh Tế

Web search: `"thu nhập bình quân" + "[tỉnh/thành]"` hoặc `"GRDP" + "[tỉnh/thành]"`

- GRDP bình quân đầu người (triệu VND / năm)
- Thu nhập bình quân hộ gia đình (triệu VND / tháng)
- Cơ cấu kinh tế: nông nghiệp / công nghiệp / dịch vụ (%)
- Tỷ lệ thất nghiệp (%)
- Khu công nghiệp (KCN) lớn lân cận — nguồn cầu nhà ở

Nguồn: GSO, Sở KH&ĐT tỉnh/thành, Báo cáo KT-XH hàng năm.

### 4. Thị Trường Nhà Ở

Web search: `"giá nhà" + "[khu vực]"` hoặc `"thị trường bất động sản" + "[quận/huyện]" + [năm]`

#### a) Giá bán
- Căn hộ chung cư (triệu VND/m²): phân khúc bình dân / trung cấp / cao cấp
- Nhà phố / biệt thự (triệu VND/m² đất)
- Đất nền (triệu VND/m²)
- Xu hướng giá 1–3 năm gần nhất

#### b) Giá thuê
- Căn hộ thuê (triệu VND / tháng theo diện tích)
- Mặt bằng thương mại (USD/m²/tháng — thường báo giá bằng USD)
- Văn phòng cho thuê (USD/m²/tháng, phân hạng A/B/C)

#### c) Nguồn cung
- Dự án đang triển khai lân cận
- Tồn kho / tỷ lệ hấp thụ
- Tỷ lệ lấp đầy (văn phòng, thương mại)

Nguồn: CBRE, Savills, JLL, Knight Frank (báo cáo quý), batdongsan.com.vn, cafeland.vn.

### 5. Tiện Ích & Dịch Vụ Lân Cận

Khảo sát bán kính 1–2 km:
- Trường học: mầm non, tiểu học, THCS, THPT, đại học
- Bệnh viện / phòng khám
- Siêu thị / trung tâm thương mại
- Công viên / không gian xanh
- Cơ quan hành chính (UBND quận/phường)

### 6. Đánh Giá Tổng Hợp

Bảng SWOT cho vị trí:

| | Tích cực | Tiêu cực |
|---|---|---|
| **Nội tại** | Điểm mạnh | Điểm yếu |
| **Bên ngoài** | Cơ hội | Thách thức |

Kết luận:
- Phân khúc phù hợp nhất cho dự án
- Mức giá tham chiếu
- Đối tượng khách hàng mục tiêu

## Định Dạng Đầu Ra

```markdown
---
tieu-de: "Phân tích dân số & thị trường — [Khu vực]"
ngay: [YYYY-MM-DD]
khu-vuc: "[Quận/Huyện, Tỉnh/Thành]"
ky-nang: phan-tich-dan-so
---

# Phân Tích Dân Số & Thị Trường — [Khu Vực]

## Tổng Quan

| Thông số | Giá trị | Nguồn |
|---|---|---|
| Dân số | [người] | |
| Mật độ | [người/km²] | |
| GRDP bình quân | [triệu VND/người/năm] | |
| Giá căn hộ TB | [triệu VND/m²] | |

## Dân Số & Mật Độ
[Chi tiết + so sánh]

## Cơ Cấu Tuổi & Hộ Gia Đình
[Phân bố + nhập cư]

## Thu Nhập & Kinh Tế
[GRDP, cơ cấu, KCN]

## Thị Trường Nhà Ở
[Giá bán, giá thuê, nguồn cung]

## Tiện Ích Lân Cận
[Trường, bệnh viện, thương mại]

## Đánh Giá SWOT
[Bảng SWOT + kết luận]

## Nguồn
## Khoảng Trống & Lưu Ý
```

## Quy Tắc

- **Đơn vị tiền tệ:** VND là mặc định. USD chỉ dùng cho mặt bằng thương mại / văn phòng (thông lệ thị trường). Theo `don-vi-do-luong.md`.
- **Dữ liệu dân số VN cập nhật chậm** — luôn ghi năm dữ liệu. Tổng điều tra 2019 là nguồn gốc chính, cập nhật hàng năm từ GSO.
- **Giá BĐS biến động mạnh** — ghi thời điểm thu thập, ghi rõ là tham khảo.
- **Tuyên bố miễn trừ bắt buộc.**
