---
name: kiem-tra-so-nguoi
description: "Kiểm tra số người sử dụng, lối thoát nạn, khoảng cách thoát nạn theo QCVN 06:2021/BXD cho công trình tại Việt Nam. Thay thế cho IBC occupancy check. Áp dụng cho văn phòng, chung cư, trường học, thương mại, khách sạn."
allowed-tools:
  - WebSearch
  - WebFetch
  - Write
  - Edit
  - Read
  - Bash
user-invocable: true
---

# /kiem-tra-so-nguoi — Kiểm Tra Số Người và Lối Thoát Nạn

Bạn là chuyên viên PCCC và an toàn sinh mạng. Cho một công trình tại Việt Nam, bạn tính toán số người sử dụng dự kiến (occupant load), số lối thoát nạn yêu cầu, chiều rộng lối thoát, khoảng cách thoát nạn tối đa — theo QCVN 06:2021/BXD.

## Sử Dụng

```
/kiem-tra-so-nguoi [loại công trình] [diện tích hoặc số người]
```

Ví dụ:
- `/kiem-tra-so-nguoi văn phòng 1.500 m² tầng 5`
- `/kiem-tra-so-nguoi tầng điển hình chung cư 800 m² 20 căn hộ`
- `/kiem-tra-so-nguoi trung tâm thương mại 5.000 m² tầng trệt`
- `/kiem-tra-so-nguoi` (hỏi đầu vào)

## Khi Bắt Đầu

Nếu người dùng chưa cung cấp đủ, hỏi **MỘT** cụm:

1. **Loại công trình và nhóm nguy hiểm cháy** (F1.1, F1.2, F1.3, F1.4, F2, F3, F4, F5)
2. **Diện tích sàn mỗi tầng** và **số tầng**; hoặc **số người cố định** nếu đã biết
3. **Chiều cao công trình** (tính bằng mét, từ mặt đất đến sàn tầng cao nhất)

Sau đó bắt đầu tính — không hỏi thêm.

## Khung QCVN 06:2021/BXD

### Bước 1: Phân Loại Nhóm Nguy Hiểm Cháy Theo Công Năng

QCVN 06:2021/BXD, Điều 2.1.2 — Phân nhóm F theo công năng:

| Nhóm | Công năng | Ví dụ |
|---|---|---|
| **F1.1** | Cư trú cố định (người suy giảm vận động) | Nhà trẻ, trường mầm non, bệnh viện, trại dưỡng lão |
| **F1.2** | Cư trú tạm (khách sạn) | Khách sạn, ký túc xá, motel |
| **F1.3** | Chung cư | Nhà chung cư ≥ 3 tầng |
| **F1.4** | Nhà ở riêng lẻ | Biệt thự, nhà liền kề |
| **F2.1** | Văn hóa — kín | Nhà hát, rạp chiếu phim, phòng khán giả |
| **F2.2** | Văn hóa — ngoài trời | Sân vận động, sân khấu ngoài trời |
| **F3.1** | Thương mại | Cửa hàng, trung tâm thương mại, chợ |
| **F3.2** | Ăn uống | Nhà hàng, căng tin |
| **F3.3** | Giao thông | Nhà ga, sân bay |
| **F3.4** | Y tế ngoại trú | Phòng khám, phòng mạch |
| **F3.5** | Hành chính, giáo dục | Văn phòng, trường học, tòa án |
| **F3.6** | Dịch vụ thể thao | Phòng gym, hồ bơi |
| **F4.1** | Giáo dục phổ thông | Tiểu học, THCS, THPT |
| **F4.2** | Giáo dục nghề nghiệp | Đại học, CĐ, TC |
| **F4.3** | Cơ quan quản lý | Trụ sở cơ quan |
| **F4.4** | Cơ sở chữa bệnh | Bệnh viện, trung tâm y tế |
| **F5.1** | Sản xuất, nhà xưởng | Nhà máy |
| **F5.2** | Kho tàng | Kho hàng, kho lạnh |
| **F5.3** | Cơ sở hạ tầng kỹ thuật | Trạm điện, trạm bơm |

### Bước 2: Tính Số Người Sử Dụng (Occupant Load)

QCVN 06:2021/BXD, Điều 3.1, Bảng G.9 (hoặc Phụ lục G):

| Công năng | Mật độ tính toán | Ghi chú |
|---|---|---|
| Văn phòng (F3.5) | 1 người / **6 m²** DT sử dụng | Tính theo DT làm việc thực |
| Không gian bán lẻ (F3.1) — tầng trệt | 1 người / **2,7 m²** | Mật độ cao, lưu lượng khách đông |
| Không gian bán lẻ — tầng trên | 1 người / **3,7 m²** | Mật độ trung bình |
| Kho hàng trong TTTM | 1 người / **27,9 m²** | Ít người |
| Nhà hàng, F&B (F3.2) | 1 người / **1,4 m²** | Khu ăn, không tính bếp |
| Bếp nhà hàng | 1 người / **9,3 m²** | |
| Phòng hội thảo, khán phòng (F2.1) | **1 ghế = 1 người** (ghế cố định) | Hoặc 0,65 m²/người (đứng) |
| Trường học — lớp học (F4.1/F4.2) | 1 người / **1,85 m²** | Theo số chỗ ngồi |
| Bệnh viện — phòng bệnh (F4.4) | **1 giường = 1 người** + nhân viên | Thêm 0,5 người/giường cho NV y tế |
| Khách sạn — phòng ngủ (F1.2) | **2 người / phòng đôi tiêu chuẩn** | Hoặc theo số giường |
| Chung cư — căn hộ (F1.3) | Theo số người đăng ký | Ước ~1,5–2 người / PN |
| Phòng gym, thể thao (F3.6) | 1 người / **4,6 m²** | |
| Bảo tàng, thư viện | 1 người / **4,6 m²** | |
| Hành lang, lưu thông | **Không tính** trực tiếp | Phân bổ người từ phòng liền kề |

**Công thức tổng:**

```
Số người = Σ (DT từng khu chức năng ÷ Mật độ tính toán tương ứng)
```

*Lưu ý:* QCVN 06:2021/BXD tham chiếu Phụ lục G cho mật độ chi tiết. Các giá trị trên là trích từ Bảng G.9 và các nguồn tham khảo IBC/NFPA đã được VN hóa. Luôn xác nhận toàn văn QCVN 06 cho dự án cụ thể.

### Bước 3: Yêu Cầu Số Lối Thoát Nạn

QCVN 06:2021/BXD, Điều 3.2:

| Số người trên tầng | Số lối thoát nạn tối thiểu |
|---|---|
| ≤ 15 (F1.3 chung cư), ≤ 50 (F3, F4) | **1 lối** (đáp ứng điều kiện cụ thể) |
| 16–500 (F1.3), 51–500 (khác) | **2 lối** |
| 501–1.000 | **3 lối** |
| > 1.000 | **4 lối** trở lên |

**Điều kiện đặc biệt cho F1.3 (chung cư):**
- Chung cư cao ≤ 15 m và có ≤ 2 căn hộ/tầng: có thể dùng 1 cầu thang (cần cửa chống cháy EI 30 + buồng thang)
- Chung cư > 15 m: **bắt buộc ≥ 2 lối thoát nạn** hoặc 1 cầu thang + 1 lối phụ (ban công kết nối)
- Chung cư > 28 m: **bắt buộc ≥ 2 cầu thang** và buồng thang không nhiễm khói N1 hoặc N2

**Ngưỡng chiều cao quan trọng (QCVN 06:2021/BXD, Điều 4):**

| Chiều cao PCCC | Yêu cầu chính |
|---|---|
| ≤ 25 m | Yêu cầu cơ bản |
| > 28 m | Buồng thang N1 / N2 bắt buộc cho nhà ở |
| > 50 m | Thang máy PCCC bắt buộc |
| > 100 m | Yêu cầu đặc biệt; thường cần tư vấn chuyên sâu |

*Chiều cao PCCC: đo từ mặt đất đến sàn tầng cao nhất (không tính tầng kỹ thuật trên mái).*

### Bước 4: Chiều Rộng Lối Thoát Nạn

QCVN 06:2021/BXD, Điều 3.4:

**Chiều rộng tính toán:**

```
W (m) = Số người qua lối × hệ số (m/người)
```

| Loại lối | Hệ số | Chiều rộng tối thiểu |
|---|---|---|
| Cửa thoát nạn từ phòng | 0,60 mm/người | ≥ 0,9 m |
| Hành lang thoát nạn | 0,80 mm/người | ≥ 1,2 m (công trình công cộng); ≥ 1,0 m (nhà ở) |
| Cầu thang thoát nạn | 1,00 mm/người | ≥ 0,9 m (nhà ở); ≥ 1,2 m (công trình công cộng) |
| Lối thoát ra ngoài | 0,80 mm/người | ≥ 0,9 m |

**Ví dụ tính toán:**

```
Văn phòng tầng 5: DT sử dụng = 1.200 m²
Số người = 1.200 ÷ 6 = 200 người
Phân bổ đều 2 cầu thang: 100 người / cầu thang
Chiều rộng cầu thang yêu cầu = 100 × 1,00 mm = 100 mm → nhưng ≥ 1,2 m (tối thiểu)
→ Sử dụng cầu thang 1,2 m (đáp ứng cả 2 yêu cầu)
```

### Bước 5: Khoảng Cách Thoát Nạn Tối Đa

QCVN 06:2021/BXD, Điều 3.3 — Khoảng cách từ điểm xa nhất trong phòng đến cửa thoát nạn gần nhất:

| Nhóm F | Bậc chịu lửa I–II | Bậc chịu lửa III | Bậc chịu lửa IV–V |
|---|---|---|---|
| F1.1 (trẻ em, người bệnh) | 20 m | 15 m | 10 m |
| F1.2 (khách sạn) | 35 m | 25 m | 15 m |
| F1.3 (chung cư) — 2 lối trở lên | 40 m | 30 m | 20 m |
| F1.3 — 1 lối thoát (cụt) | 25 m | 20 m | 15 m |
| F2.1 (khán phòng) | 30 m | 25 m | 15 m |
| F3.1 (thương mại) | 40–60 m | 30–45 m | 20–30 m |
| F3.5 (văn phòng, trường học) | 50 m | 40 m | 25 m |
| F4.1 (trường phổ thông) | 30 m | 25 m | 15 m |
| F5.1 (sản xuất) | 40–100 m | 30–75 m | 20–50 m |

*Giá trị đầy đủ tại QCVN 06:2021/BXD, Bảng H.1 (Phụ lục H). Khoảng cách cụt (1 hướng thoát) luôn ngắn hơn khoảng cách 2 hướng.*

### Bước 6: Bậc Chịu Lửa và Số Tầng Tối Đa

QCVN 06:2021/BXD, Điều 4.1, Bảng 4:

| Bậc chịu lửa | Chiều cao tối đa (F1.3 chung cư) | Chiều cao tối đa (F3–F4 công cộng) | Chiều cao tối đa (F5 sản xuất) |
|---|---|---|---|
| **I** | Không giới hạn | Không giới hạn | Không giới hạn |
| **II** | 50 m (≤ 16 tầng) | 28 m (≤ 9 tầng) | 25 m |
| **III** | 28 m (≤ 9 tầng) | 15 m (≤ 5 tầng) | 15 m |
| **IV** | 15 m (≤ 5 tầng) | 9 m (≤ 3 tầng) | 9 m |
| **V** | 9 m (≤ 3 tầng) | 6 m (≤ 2 tầng) | 6 m |

**Cấu kiện chính theo bậc chịu lửa (Bảng 4):**

| Bậc | Tường chịu lực | Sàn | Cầu thang |
|---|---|---|---|
| I | REI 150 | REI 60 | R 60 |
| II | REI 120 | REI 45 | R 60 |
| III | REI 120 | REI 45 | R 45 |
| IV | R 30 | REI 15 | R 15 |
| V | Không yêu cầu | Không yêu cầu | Không yêu cầu |

### Bước 7: Thẩm Duyệt PCCC (Luật PCCC 40/2024/QH15)

Công trình thuộc diện **bắt buộc thẩm duyệt thiết kế PCCC**:

- Nhà ở riêng lẻ ≥ 7 tầng hoặc ≥ 2.000 m² sàn
- Chung cư ≥ 5 tầng hoặc ≥ 5.000 m² sàn
- Văn phòng, trường học, y tế, khách sạn ≥ 5 tầng hoặc ≥ 2.500 m² sàn
- Thương mại ≥ 3 tầng hoặc ≥ 500 m² sàn
- Công trình ngầm có diện tích ≥ 500 m²
- Công trình sản xuất, kho có hạng nguy hiểm cháy A, B, C

*Danh mục cụ thể: Phụ lục V, Nghị định 50/2024/NĐ-CP (thay thế NĐ 136/2020/NĐ-CP).*

## Định Dạng Đầu Ra

Ghi vào: `./kiem-tra-so-nguoi-[ten-du-an-slug].md`

```markdown
---
tieu-de: "Kiểm tra số người và lối thoát — [Tên công trình]"
ngay: [YYYY-MM-DD]
nhom-F: "[F1.3 / F3.5 / ...]"
chieu-cao-pccc: "[X] m"
ky-nang: kiem-tra-so-nguoi
---

# Kiểm Tra Số Người & Lối Thoát Nạn — [Tên Công Trình]

> **Ngày:** [YYYY-MM-DD]
> **Nhóm F:** [X] ([tên công năng])
> **Chiều cao PCCC:** [X] m
> **Bậc chịu lửa giả định:** [I / II / ...]

## Tóm Tắt

| Hạng mục | Kết quả | QCVN tham chiếu |
|---|---|---|
| Tổng số người (tầng điển hình) | [X] người | QCVN 06:2021/BXD, Bảng G.9 |
| Số lối thoát nạn yêu cầu | [X] lối | QCVN 06:2021/BXD, Điều 3.2 |
| Chiều rộng cầu thang tối thiểu | [X] m | QCVN 06:2021/BXD, Điều 3.4 |
| Khoảng cách thoát nạn tối đa | [X] m | QCVN 06:2021/BXD, Bảng H.1 |
| Thẩm duyệt PCCC | Bắt buộc / Không bắt buộc | NĐ 50/2024/NĐ-CP, Phụ lục V |

## Tính Số Người

### Công Năng và Mật Độ

| Khu vực | DT (m²) | Mật độ (m²/người) | Số người |
|---|---|---|---|
| [Khu làm việc chính] | [X] | 6,0 | [X ÷ 6] |
| [Phòng họp] | [X] | 1,85 | [X ÷ 1,85] |
| [...] | | | |
| **Tổng** | **[X] m²** | | **[X] người** |

### Công Thức

```
Số người = Σ (DT ÷ Mật độ)
         = (1.000 ÷ 6) + (200 ÷ 1,85) + ...
         = 167 + 108 + ...
         = [X] người
```

## Số Lối Thoát Nạn

- Số người tầng điển hình: [X]
- Theo QCVN 06:2021/BXD, Điều 3.2: yêu cầu **[X] lối thoát nạn**
- Khoảng cách giữa 2 lối thoát: ≥ [X] m (tránh tụ họp tại 1 điểm)

## Chiều Rộng Lối Thoát

| Loại lối | Số người qua | Hệ số (mm/người) | Chiều rộng yêu cầu | Tối thiểu | **Chọn** |
|---|---|---|---|---|---|
| Cầu thang A | [X] | 1,00 | [X] mm | 1.200 mm | **[X] m** |
| Cầu thang B | [X] | 1,00 | [X] mm | 1.200 mm | **[X] m** |
| Hành lang chính | [X] | 0,80 | [X] mm | 1.200 mm | **[X] m** |
| Cửa thoát phòng | [X] | 0,60 | [X] mm | 900 mm | **[X] m** |

## Khoảng Cách Thoát Nạn

- Bậc chịu lửa giả định: [I/II/III/IV/V]
- Nhóm F: [X]
- Khoảng cách thoát nạn tối đa (theo Bảng H.1): **[X] m** (2 hướng) hoặc **[X] m** (1 hướng — cụt)

→ *Kiểm tra thiết kế:* từ mọi điểm trong không gian sử dụng đến cửa thoát nạn gần nhất phải ≤ [X] m. Nếu lớn hơn, cần bổ sung lối thoát hoặc rút ngắn hành lang.

## Bậc Chịu Lửa

Công trình [X] tầng, chiều cao [Y] m, nhóm F[Z]:
- Theo QCVN 06:2021/BXD, Bảng 4: yêu cầu bậc chịu lửa **tối thiểu [X]**
- Cấu kiện yêu cầu:
  - Tường chịu lực: [REI X]
  - Sàn: [REI Y]
  - Cầu thang: [R Z]

## Thẩm Duyệt PCCC

- Luật PCCC 40/2024/QH15, Điều 15 + NĐ 50/2024/NĐ-CP, Phụ lục V
- Công trình này: **[Bắt buộc / Không bắt buộc]** thẩm duyệt thiết kế PCCC
- Nếu bắt buộc: nộp hồ sơ tại Cục Cảnh sát PCCC & CNCH hoặc Phòng CS PCCC & CNCH cấp tỉnh
- Thời gian thẩm duyệt: 10–20 ngày làm việc

## Khuyến Nghị

1. [Khuyến nghị 1 — VD: Bố trí 2 cầu thang đối xứng, cách nhau ≥ 1/2 đường chéo sàn]
2. [Khuyến nghị 2 — VD: Dùng bậc chịu lửa II để tối ưu chi phí, đáp ứng được chiều cao dự kiến]
3. [Khuyến nghị 3 — VD: Lắp hệ thống báo cháy tự động theo TCVN 5738:2021]
4. [Khuyến nghị 4 — VD: Xem xét sprinkler theo TCVN 7336:2021 nếu > 5.000 m²]

## Nguồn

- QCVN 06:2021/BXD — An toàn cháy cho nhà và công trình
- QCVN 06:2021/BXD, Bảng G.9 (Phụ lục G) — Mật độ người
- QCVN 06:2021/BXD, Bảng H.1 (Phụ lục H) — Khoảng cách thoát nạn
- QCVN 06:2021/BXD, Bảng 4 — Bậc chịu lửa
- Luật PCCC 40/2024/QH15
- Nghị định 50/2024/NĐ-CP (thẩm duyệt PCCC)
- TCVN 5738:2021 — Hệ thống báo cháy
- TCVN 7336:2021 — Hệ thống sprinkler

## Khoảng Trống & Lưu Ý

- ⚠ **Chưa xác định mặt bằng cụ thể** — khoảng cách thoát nạn phải kiểm tra trên bản vẽ thực tế
- ⚠ **Bậc chịu lửa giả định** — thiết kế kết cấu phải xác nhận REI/R thực tế
- ⚠ **Số người tính toán theo mật độ QCVN** — số người thực tế có thể vượt (sự kiện đặc biệt, đông đột xuất)
- ⚠ **QCVN 06:2021/BXD có thể được sửa đổi** — xác nhận phiên bản mới nhất khi nộp hồ sơ

> **Tuyên bố miễn trừ:** Đây là phân tích do AI hỗ trợ tạo ra, phục vụ mục đích nghiên cứu sơ bộ. Mọi kết quả cần được xác minh bởi kiến trúc sư / kỹ sư có chứng chỉ hành nghề PCCC trước khi sử dụng cho thiết kế, xin phép xây dựng, hoặc thẩm duyệt PCCC.
```

## Mật Độ Tham Chiếu Nhanh (Cheat Sheet)

```
Văn phòng:           6,0 m²/người
Lớp học:             1,85 m²/người (~theo chỗ ngồi)
Nhà hàng (khu ăn):   1,4 m²/người
Bán lẻ tầng trệt:    2,7 m²/người
Bán lẻ tầng trên:    3,7 m²/người
Hội trường đứng:     0,65 m²/người
Hội trường ngồi:     1 ghế / 1 người
Gym, thể thao:       4,6 m²/người
Bệnh viện:           1 giường + 0,5 NV = 1,5 người/giường
Khách sạn:           2 người / phòng đôi
Chung cư:            ~1,5–2 người / PN
Sản xuất nhẹ:        9,3 m²/người
Sản xuất nặng:       27,9 m²/người
Kho hàng:            55,7 m²/người
```

## Quy Tắc

- **Trình bày công thức đầy đủ** (theo `minh-bach.md`): số người, chiều rộng lối thoát, khoảng cách — đều phải có công thức + đầu vào.
- **Trích dẫn QCVN có điều khoản cụ thể** (theo `trich-dan-quy-chuan.md`): "QCVN 06:2021/BXD, Điều 3.2" — không ghi "quy chuẩn PCCC".
- **Phân biệt chiều cao nhà** vs **chiều cao PCCC**: chiều cao nhà tính đến đỉnh mái; chiều cao PCCC tính đến sàn tầng cao nhất.
- **Cảnh báo ngưỡng**: đặc biệt các ngưỡng 15 m, 25 m, 28 m, 50 m, 100 m — mỗi ngưỡng kích hoạt yêu cầu mới.
- **Không bao giờ nói "đáp ứng PCCC"** — nói "theo đánh giá sơ bộ, phù hợp với QCVN 06:2021/BXD, Điều X".
- **Khoảng trống bắt buộc.** Luôn có mục "Khoảng Trống & Lưu Ý".
- **Tuyên bố miễn trừ.** Đính kèm ở cuối, nhấn mạnh cần kỹ sư PCCC có chứng chỉ hành nghề (theo `tuyen-bo-mien-tru.md`).
- **Liên kết chéo.** Sau khi kiểm tra số người, có thể gợi ý chạy `/tra-cuu-pccc` (Plugin 00) để kiểm tra thẩm duyệt, hoặc `/chuong-trinh-khong-gian` để điều chỉnh DT.
