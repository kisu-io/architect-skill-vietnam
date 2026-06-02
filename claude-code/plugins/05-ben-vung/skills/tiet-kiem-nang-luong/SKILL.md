---
name: tiet-kiem-nang-luong
description: Tính toán hiệu quả năng lượng vỏ công trình theo QCVN 09:2017/BXD — OTTV, RTTV, WWR, SHGC, chiếu sáng, ĐHKK — và lập báo cáo tuân thủ cho hồ sơ xin cấp phép xây dựng.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
user-invocable: true
---

# Tiết Kiệm Năng Lượng (QCVN 09:2017/BXD)

**QCVN 09:2017/BXD** — *Quy chuẩn kỹ thuật quốc gia về Các công trình xây dựng sử dụng năng lượng hiệu quả* — là quy chuẩn **bắt buộc** áp dụng cho tất cả các công trình mới hoặc cải tạo lớn có diện tích sàn từ **2.500 m²** trở lên (văn phòng, thương mại, chung cư, khách sạn, bệnh viện, trường học). Đây là căn cứ pháp lý để cơ quan quản lý kiểm tra trong quá trình cấp phép xây dựng và nghiệm thu.

## Khi Dùng Kỹ Năng Này

Dùng khi:
- Lập Báo cáo Tuân thủ QCVN 09 (Energy Compliance Report) cho hồ sơ xin cấp phép
- Tính OTTV/RTTV để so sánh với ngưỡng quy chuẩn
- Tối ưu thiết kế vỏ công trình (tường, mái, cửa)
- Tính điểm EDGE (năng lượng) hoặc LOTUS (E-1)

## Phạm Vi Áp Dụng QCVN 09:2017/BXD

Áp dụng bắt buộc cho công trình có **tổng diện tích sàn ≥ 2.500 m²**:

- Văn phòng
- Khách sạn
- Bệnh viện
- Trường học
- Công trình thương mại (siêu thị, TTTM)
- Chung cư (chỉ áp dụng phần khu vực chung)

**Không áp dụng** cho:
- Nhà ở riêng lẻ
- Công trình công nghiệp sản xuất
- Công trình có yêu cầu vi khí hậu đặc biệt (kho lạnh, phòng sạch)
- Công trình < 2.500 m² sàn

## Yêu Cầu Kỹ Thuật Chính

### 1. OTTV — Chỉ Số Truyền Nhiệt Tổng Qua Tường (Overall Thermal Transfer Value)

Đơn vị: **W/m²**

**Ngưỡng bắt buộc**: OTTV ≤ **60 W/m²** (tất cả các vùng khí hậu)

**Công thức**:

```
OTTV = (Aw · Uw · TDeq + Af · Uf · ΔT + Af · SC · SF) / Ao
```

Trong đó:
- `Aw` = diện tích tường đặc (m²)
- `Af` = diện tích cửa sổ/vách kính (m²)
- `Ao` = tổng diện tích vỏ bên ngoài (Aw + Af) (m²)
- `Uw` = hệ số truyền nhiệt tường (W/m²K)
- `Uf` = hệ số truyền nhiệt kính (W/m²K)
- `TDeq` = chênh lệch nhiệt độ tương đương (K) — xem Bảng 2.1 QCVN 09
- `ΔT` = chênh nhiệt độ trong-ngoài = 9 K (chuẩn)
- `SC` = hệ số che nắng tổng hợp (Shading Coefficient)
- `SF` = hệ số bức xạ mặt trời (W/m²) — xem Bảng 2.2 theo hướng

**TDeq theo hướng và loại tường** (QCVN 09 Bảng 2.1):

| Loại tường (m²K/W) | Bắc | Đông | Nam | Tây |
|---|---|---|---|---|
| Nhẹ (< 0,1) | 12 | 22 | 15 | 24 |
| Trung bình (0,1–0,25) | 10 | 18 | 13 | 20 |
| Nặng (> 0,25) | 8 | 15 | 10 | 17 |

**SF theo hướng** (W/m²):

| Hướng | Bắc | Đông | Nam | Tây | Đông Bắc | Đông Nam | Tây Nam | Tây Bắc |
|---|---|---|---|---|---|---|---|---|
| SF | 85 | 200 | 105 | 220 | 160 | 170 | 200 | 200 |

### 2. RTTV — Chỉ Số Truyền Nhiệt Tổng Qua Mái (Roof Thermal Transfer Value)

Đơn vị: **W/m²**

**Ngưỡng bắt buộc**: RTTV ≤ **25 W/m²**

**Công thức**:

```
RTTV = (Ar · Ur · TDeqR + Ask · Usk · ΔT + Ask · SC · SFR) / Aro
```

Tương tự OTTV nhưng cho mái, với:
- `TDeqR` = 15–24 K tùy loại mái
- `SFR` = 485 W/m² (mặt trời trực tiếp mái phẳng)

### 3. WWR — Tỷ Lệ Cửa Sổ/Tường (Window-to-Wall Ratio)

WWR không có giới hạn cứng, nhưng **nếu WWR > 40%** thì phải chứng minh OTTV vẫn đạt bằng kính Low-E, SHGC thấp.

### 4. U-value Tối Đa Cho Từng Bộ Phận

| Bộ phận | U tối đa (W/m²K) |
|---|---|
| Tường ngoài | 1,80 |
| Mái bằng | 1,00 |
| Mái dốc | 1,50 |
| Cửa sổ kính đơn | 5,80 |
| Cửa sổ kính hộp (2 lớp) | 3,30 |
| Cửa sổ Low-E | 2,50 |

### 5. SHGC — Hệ Số Hấp Thụ Nhiệt Mặt Trời Kính

| Loại kính | SHGC khuyến nghị cho VN |
|---|---|
| Kính trong thường | 0,85 (quá cao, không nên dùng) |
| Kính phản quang | 0,35–0,50 |
| Kính Low-E nhiệt đới | 0,25–0,35 |
| Kính hộp Low-E + khí Argon | 0,20–0,28 |

**Khuyến nghị thực hành tốt**: SHGC ≤ **0,35** cho hướng Tây/Đông, ≤ **0,50** cho hướng Bắc/Nam.

### 6. Chiếu Sáng

| Khu vực | LPD tối đa (W/m²) |
|---|---|
| Văn phòng | 11 |
| Sảnh | 13 |
| Phòng họp | 13 |
| Hành lang | 5 |
| Cầu thang | 5 |
| Nhà kho | 6 |
| Phòng khám | 13 |
| Lớp học | 11 |

LPD = Lighting Power Density = Tổng công suất chiếu sáng / Diện tích chiếu sáng.

### 7. Điều Hòa Không Khí

**Hiệu suất tối thiểu** (theo QCVN 09 Phụ lục 3):

| Loại | Chỉ số | Tối thiểu |
|---|---|---|
| ĐH gia dụng Inverter | CSPF | 4,0 |
| ĐH thương mại VRF/VRV | IPLV | 4,5 |
| Chiller giải nhiệt nước (Water-cooled) | COP / IPLV | 5,5 / 6,5 |
| Chiller giải nhiệt gió (Air-cooled) | COP / IPLV | 2,9 / 3,5 |

## Quy Trình Tính Toán OTTV Điển Hình

### Bước 1: Phân tách mặt đứng theo hướng

Chia mặt ngoài theo 4 hướng chính (Bắc/Đông/Nam/Tây), tính diện tích từng mặt.

### Bước 2: Xác định tường đặc và kính

- Tường đặc: `Aw_i`, tra `Uw`, `TDeq_i`
- Kính: `Af_i`, tra `Uf`, `SC` (tra catalogue kính)

### Bước 3: Tính OTTV từng mặt

```
OTTVi = (Awi · Uw · TDeqi + Afi · Uf · ΔT + Afi · SC · SFi) / (Awi + Afi)
```

### Bước 4: Tính OTTV tổng

```
OTTV_tong = Σ(OTTVi · Aoi) / Σ Aoi
```

### Bước 5: So sánh với 60 W/m²

- OTTV ≤ 60 → Đạt
- OTTV > 60 → Phải điều chỉnh (tăng cách nhiệt, giảm WWR, dùng kính tốt hơn)

## Ví Dụ Tính Toán Nhanh

**Dữ liệu**:
- Tòa nhà văn phòng hình chữ nhật, 4 mặt đứng
- Kích thước mỗi tầng: 40 m × 25 m, cao 3,6 m, 10 tầng
- WWR = 40% (vách kính)
- Tường: gạch AAC 200 mm + vữa, Uw = 0,85 W/m²K (nặng)
- Kính: Low-E hộp, Uf = 2,5 W/m²K, SC = 0,30

**Tính toán mặt Tây** (ví dụ):
- Diện tích mặt: 40 × 3,6 × 10 = 1.440 m²
- Kính: 1.440 × 0,4 = 576 m²
- Tường: 1.440 × 0,6 = 864 m²
- Dẫn nhiệt tường: 864 × 0,85 × 17 = 12.487 W
- Dẫn nhiệt kính: 576 × 2,5 × 9 = 12.960 W
- Bức xạ qua kính: 576 × 0,30 × 220 = 38.016 W
- Tổng: 63.463 W
- OTTV mặt Tây: 63.463 / 1.440 = **44,1 W/m²** → Đạt

**Kết luận**: Với kính Low-E SC=0,30, mặt Tây WWR 40% vẫn đạt QCVN 09.

## Cấu Trúc Báo Cáo Tuân Thủ QCVN 09

```markdown
# Báo Cáo Tuân Thủ QCVN 09:2017/BXD
## [Tên Dự Án]

**Chủ đầu tư:** [...]
**Đơn vị tư vấn thiết kế:** [...]
**Ngày lập:** [DD/MM/YYYY]

## 1. Thông Tin Dự Án

- Loại công trình: Văn phòng / Khách sạn / ...
- Tổng diện tích sàn: [X] m²
- Số tầng: [Y]
- Vùng khí hậu: Miền Bắc / Trung / Nam
- Diện tích vỏ ngoài: [Z] m²

## 2. Thông Số Vỏ Công Trình

### 2.1 Tường Ngoài

| Lớp | Vật liệu | Dày (mm) | λ (W/mK) |
|---|---|---|---|
| 1 | Vữa trát ngoài | 15 | 0,93 |
| 2 | Gạch AAC | 200 | 0,16 |
| 3 | Vữa trát trong | 15 | 0,93 |
| | **Tổng Rt = 1,34 m²K/W, Uw = 0,74 W/m²K** | | |

### 2.2 Kính Cửa Sổ

- Loại: Kính hộp Low-E 6-12Ar-6 mm
- Uf = 2,5 W/m²K
- SHGC (SC) = 0,30

### 2.3 Mái

| Lớp | Vật liệu | Dày (mm) |
|---|---|---|
| 1 | Bê tông sàn | 150 |
| 2 | Cách nhiệt PIR | 50 |
| 3 | Lớp tạo dốc + chống thấm | 100 |
| | **Ur = 0,55 W/m²K** | |

## 3. Tính Toán OTTV

| Hướng | Aw (m²) | Af (m²) | Tổng (m²) | OTTV (W/m²) |
|---|---|---|---|---|
| Bắc | 864 | 576 | 1.440 | 32,5 |
| Đông | 540 | 360 | 900 | 48,8 |
| Nam | 864 | 576 | 1.440 | 38,2 |
| Tây | 540 | 360 | 900 | 52,1 |
| **Trung bình trọng số** | | | | **42,3** |

**Kết luận**: OTTV = 42,3 W/m² ≤ 60 W/m² → **Đạt QCVN 09**.

## 4. Tính Toán RTTV

- Diện tích mái: 1.000 m²
- RTTV = 14,5 W/m² ≤ 25 W/m² → **Đạt**

## 5. Chiếu Sáng

| Khu vực | Diện tích (m²) | LPD thiết kế (W/m²) | LPD max QCVN | Đạt? |
|---|---|---|---|---|
| Văn phòng | 6.000 | 8,5 | 11 | ✓ |
| Sảnh | 400 | 10 | 13 | ✓ |
| Hành lang | 800 | 4 | 5 | ✓ |

## 6. Điều Hòa Không Khí

- Hệ thống: VRF Daikin VRV X Series
- IPLV thiết kế: 6,1 ≥ 4,5 (yêu cầu) → **Đạt**

## 7. Kết Luận Tổng Thể

Công trình đạt tất cả yêu cầu bắt buộc của QCVN 09:2017/BXD.

## Phụ Lục

- P1. Bản vẽ mặt đứng có bóc tách diện tích tường/kính
- P2. Datasheet kính Low-E (tham chiếu tiêu chuẩn)
- P3. Datasheet VRF
- P4. Tính toán chi tiết OTTV từng mặt
```

## Liên Kết Với Các Kỹ Năng Khác

- **`danh-gia-edge`:** Dùng kết quả OTTV/LPD để nhập EDGE App
- **`danh-gia-lotus`:** Vượt QCVN 09 ≥ 10% để ghi điểm E-1 LOTUS
- **`phan-tich-epd`:** Tác động môi trường của cách nhiệt (PIR, XPS, len khoáng)
- **`dac-ta-ky-thuat`:** Viết spec kính Low-E, cách nhiệt theo thông số tính

## Quy Tắc Khi Tính Toán

- Dùng **TMY cho Hà Nội/Đà Nẵng/TP.HCM** (dữ liệu EnergyPlus.gov)
- Diện tích đo từ **trục tim cột đến trục tim cột**, không trừ dầm
- SHGC từ nhà sản xuất phải có **chứng nhận NFRC** hoặc tương đương (chấp nhận EN 410, JIS R3106, ISO 9050)
- Mô phỏng nâng cao (bắt buộc nếu WWR > 60%): dùng IESVE, EnergyPlus, DesignBuilder — **không dùng eQUEST** vì thiếu thư viện kính nhiệt đới
- Báo cáo phải có chữ ký của kỹ sư chuyên ngành điện + cơ khí
- Cơ quan thẩm định: **Sở Xây dựng** (hoặc Ban Quản lý Khu công nghiệp)

## Tham Chiếu Pháp Lý

- **QCVN 09:2017/BXD** — Công trình sử dụng năng lượng hiệu quả (bản cập nhật mới nhất)
- **Luật Sử dụng năng lượng tiết kiệm và hiệu quả 50/2010/QH12**
- **Nghị định 21/2011/NĐ-CP** — hướng dẫn thi hành Luật 50/2010
- **Thông tư 15/2017/TT-BXD** — hướng dẫn áp dụng QCVN 09
- **TCVN 5687:2010** — thông gió điều hòa (hỗ trợ)
- **TCVN 7830:2015** — hiệu suất năng lượng ĐHKK không ống gió
