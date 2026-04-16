---
name: phan-tich-moi-truong
description: "Phân tích khí hậu và môi trường cho lô đất tại Việt Nam — nhiệt độ, mưa, gió, hướng nắng, ngập lụt, động đất, địa chất."
allowed-tools:
  - WebSearch
  - WebFetch
  - Write
  - Read
  - Bash
user-invocable: true
---

# /phan-tich-moi-truong — Phân Tích Khí Hậu & Môi Trường

Phân tích điều kiện khí hậu và môi trường tự nhiên cho một lô đất cụ thể, phục vụ thiết kế kiến trúc và quy hoạch mặt bằng. Tương đương skill `environmental-analysis` trong bản gốc.

## Sử Dụng

```
/phan-tich-moi-truong [địa chỉ]
```

Ví dụ:
- `/phan-tich-moi-truong 88 Nguyễn Huệ, Quận 1, TP.HCM`
- `/phan-tich-moi-truong Lô A5, KĐT Ecopark, Hưng Yên`

## Khi Bắt Đầu

Hỏi **địa chỉ + tỉnh/thành phố**. Sau đó bắt đầu nghiên cứu — không hỏi thêm.

## Quy Trình

### 1. Xác Định Vùng Khí Hậu

Việt Nam chia 6 vùng khí hậu xây dựng theo QCVN 02:2022/BXD:

| Vùng | Khu vực đại diện | Đặc điểm chính |
|---|---|---|
| Bắc (B1) | Hà Nội, Hải Phòng, Đồng bằng Bắc Bộ | Nóng ẩm mùa hè, lạnh mùa đông |
| Bắc (B2) | Lào Cai, Sơn La, Vùng núi phía Bắc | Lạnh hơn, sương mù |
| Trung (T1) | Nghệ An, Huế, Ven biển Bắc Trung Bộ | Gió Lào, bão, lũ |
| Trung (T2) | Đà Nẵng, Quy Nhơn, Nam Trung Bộ | Ít lạnh, mưa lệch pha |
| Nam (N1) | TP.HCM, Cần Thơ, Đồng bằng sông Cửu Long | Nóng ẩm quanh năm, 2 mùa rõ |
| Tây Nguyên (N2) | Đà Lạt, Buôn Ma Thuột | Mát, biên độ nhiệt lớn |

### 2. Dữ Liệu Nhiệt Độ & Độ Ẩm

Web search: `"nhiệt độ trung bình" + "[tỉnh/thành]"` và `"khí hậu" + "[khu vực]"`

Trích xuất:
- Nhiệt độ trung bình năm (°C)
- Nhiệt độ cao nhất trung bình tháng nóng nhất (°C)
- Nhiệt độ thấp nhất trung bình tháng lạnh nhất (°C)
- Độ ẩm trung bình năm (%)
- Biên độ nhiệt ngày đêm (°C)

Nguồn: Tổng cục Khí tượng Thủy văn (nchmf.gov.vn), Niên giám thống kê (GSO).

### 3. Lượng Mưa & Mùa Mưa

- Lượng mưa trung bình năm (mm)
- Phân bố mưa theo tháng (mùa mưa vs mùa khô)
- Số ngày mưa trung bình/năm
- Cường độ mưa lớn nhất (mm/giờ) — quan trọng cho thiết kế thoát nước

### 4. Gió

Web search: `"hướng gió chủ đạo" + "[tỉnh/thành]"` và `"tốc độ gió" + "[khu vực]"`

- Hướng gió chủ đạo theo mùa (mùa hè / mùa đông)
- Tốc độ gió trung bình (m/s)
- Vùng gió theo QCVN 02:2022/BXD — áp lực gió thiết kế (daN/m²)
- Bão: vùng bờ biển, tần suất, cấp gió thiết kế

Hướng gió phổ biến:
- Bắc Bộ: Đông Nam (hè), Đông Bắc (đông)
- Trung Bộ: Đông Nam, Tây Nam (gió Lào)
- Nam Bộ: Tây Nam (mùa mưa), Đông Bắc (mùa khô)

### 5. Hướng Nắng & Bức Xạ

- Số giờ nắng trung bình/năm
- Góc cao mặt trời tại vĩ độ khu vực (solstice mùa hè / mùa đông)
- Hướng bất lợi (Tây, Tây Nam — bức xạ mạnh buổi chiều)
- Tham chiếu QCVN 09:2017/BXD — giá trị OTTV (Overall Thermal Transfer Value) mục tiêu

Gợi ý thiết kế:
- Hướng tối ưu cho mặt đứng chính: Nam hoặc Đông Nam
- Hạn chế mặt kính lớn hướng Tây

### 6. Ngập Lụt & Thủy Văn

Web search: `"ngập lụt" + "[khu vực]"` hoặc `"bản đồ ngập" + "[tỉnh/thành]"`

- Lịch sử ngập lụt khu vực (báo chí, báo cáo)
- Cao trình nền so với mực nước biển (nếu có)
- Khu vực trũng, ven sông, ven biển: cảnh báo rủi ro
- Tham chiếu bản đồ ngập của TP (TP.HCM có bản đồ ngập công bố)

### 7. Động Đất & Địa Chất

Việt Nam thuộc vùng động đất yếu đến trung bình. Theo TCVN 9386:2012 (Eurocode 8 adapted):

| Vùng | Gia tốc nền a_g (g) | Khu vực |
|---|---|---|
| I | 0,0445 | Phần lớn miền Nam |
| II | 0,0668 | Trung du, ven biển Trung Bộ |
| III | 0,0892 | Tây Bắc, Bắc Trung Bộ |
| IV | 0,1117 | Điện Biên, Lai Châu |

Web search: `"phân vùng động đất" + "[tỉnh/thành]"` — xác định vùng và gia tốc nền.

Địa chất:
- Đồng bằng sông Cửu Long: đất yếu, cần gia cố nền
- Ven biển miền Trung: cát, cần chống xói mòn
- Vùng núi: đá, sạt lở

### 8. Hệ Quả Thiết Kế

Tổng hợp các yếu tố thành khuyến nghị thiết kế:
- **Hướng nhà:** tối ưu theo gió và nắng
- **Mái:** độ dốc theo lượng mưa, chống bão vùng ven biển
- **Kết cấu:** phân vùng gió, phân vùng động đất
- **Nền móng:** loại đất, ngập lụt, mực nước ngầm
- **Vỏ công trình:** OTTV theo QCVN 09:2017/BXD
- **Thoát nước:** theo cường độ mưa thiết kế

## Định Dạng Đầu Ra

```markdown
---
tieu-de: "Phân tích môi trường — [Địa chỉ]"
ngay: [YYYY-MM-DD]
dia-chi: "[Địa chỉ đầy đủ]"
ky-nang: phan-tich-moi-truong
---

# Phân Tích Khí Hậu & Môi Trường — [Địa Chỉ]

## Tổng Quan

| Thông số | Giá trị |
|---|---|
| Vùng khí hậu (QCVN 02) | [Vùng] |
| Nhiệt độ TB năm | [°C] |
| Lượng mưa TB năm | [mm] |
| Gió chủ đạo | [Hướng theo mùa] |
| Phân vùng gió (QCVN 02) | [Vùng + áp lực] |
| Phân vùng động đất (TCVN 9386) | [Vùng + a_g] |

## Nhiệt Độ & Độ Ẩm
[Bảng chi tiết theo tháng hoặc mùa]

## Lượng Mưa
[Phân bố mùa, cường độ thiết kế]

## Chế Độ Gió
[Hướng gió theo mùa, tốc độ, vùng bão]

## Hướng Nắng & Bức Xạ
[Giờ nắng, góc cao mặt trời, hướng bất lợi]

## Ngập Lụt & Thủy Văn
[Lịch sử ngập, rủi ro]

## Động Đất & Địa Chất
[Phân vùng, loại đất]

## Khuyến Nghị Thiết Kế
[Tổng hợp hệ quả cho kiến trúc]

## Nguồn
## Khoảng Trống & Lưu Ý
```

## Quy Tắc

- **Trích QCVN / TCVN có điều khoản cụ thể.**
- **Đơn vị SI** (°C, mm, m/s, daN/m², g). Theo `don-vi-do-luong.md`.
- **Gợi ý thiết kế phải dẫn từ dữ liệu**, không nêu chung chung.
- **Tuyên bố miễn trừ bắt buộc.**
