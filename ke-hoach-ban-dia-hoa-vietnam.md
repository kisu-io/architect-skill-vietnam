# Kế Hoạch Bản Địa Hóa "Skills for Architects" cho Thị Trường Việt Nam

**Dự án:** Chuyển đổi toàn bộ bộ kỹ năng kiến trúc AlpacaLabs sang bối cảnh Việt Nam
**Phạm vi:** Toàn quốc — áp dụng được cho mọi tỉnh thành
**Ngôn ngữ đầu ra:** Tiếng Việt
**Đối tượng:** Kiến trúc sư, nhà phát triển bất động sản, tư vấn quốc tế

---

## 1. Tổng Quan Dự Án Gốc

Repository `AlpacaLabsLLC/skills-for-architects` là bộ công cụ AI gồm **9 plugin (36 kỹ năng)**, **7 agent**, và **7 quy tắc** dành cho ngành kiến trúc — xây dựng — bất động sản. Hiện tại tập trung vào thị trường **New York City** và **Uruguay**.

Cấu trúc gốc:

| Thành phần | Số lượng | Mô tả |
|---|---|---|
| Plugins | 9 | Theo vòng đời dự án: thẩm định → quy hoạch → quy hoạch phân khu → chương trình → đặc tả → bền vững → vật liệu → trình bày |
| Agents | 7 | Chuyên gia tự động: quy hoạch, phân khu, nội thất, bền vững, vật liệu, thương hiệu |
| Rules | 7 | Đơn vị đo, trích dẫn quy chuẩn, thuật ngữ AEC, định dạng đầu ra |
| Hooks | 3 | Tự động hóa theo sự kiện |

---

## 2. Khung Pháp Lý Việt Nam Cần Tích Hợp

### 2.1. Hệ Thống Tiêu Chuẩn

| Loại | Viết tắt | Vai trò | Ví dụ |
|---|---|---|---|
| Quy chuẩn kỹ thuật quốc gia | **QCVN** | Bắt buộc — yêu cầu tối thiểu về an toàn | QCVN 06:2021/BXD (PCCC) |
| Tiêu chuẩn quốc gia | **TCVN** | Tự nguyện — phương pháp kỹ thuật đạt QCVN | TCVN 2737:1995 (tải trọng) |

### 2.2. Các QCVN Trọng Yếu

| Mã | Nội dung |
|---|---|
| QCVN 01:2021/BXD | Quy hoạch xây dựng |
| QCVN 03:2012/BXD | Phân loại, phân cấp công trình |
| QCVN 04:2021/BXD | Nhà chung cư |
| QCVN 06:2021/BXD | An toàn cháy cho nhà và công trình |
| QCVN 09:2017/BXD | Tiết kiệm năng lượng trong công trình |
| TCVN 2737:1995 | Tải trọng và tác động (tương đương ASCE 7) |

### 2.3. Luật Liên Quan

| Luật | Vai trò |
|---|---|
| Luật Đất đai 31/2024/QH15 | Sở hữu, quyền sử dụng đất, chuyển nhượng |
| Luật Xây dựng 50/2014/QH13 | Quy trình xây dựng, giấy phép, nghiệm thu |
| Luật Quy hoạch 21/2017/QH14 | Quy hoạch vùng, đô thị, nông thôn |
| Luật Nhà ở 65/2014/QH13 | Phát triển nhà ở, sở hữu nhà |
| Luật Kinh doanh BĐS 66/2014/QH13 | Kinh doanh bất động sản |

### 2.4. Giấy Phép Xây Dựng

Cấp bởi **Sở Xây dựng** (cấp tỉnh) hoặc **UBND quận/huyện** (công trình nhỏ). Bộ Xây dựng quản lý ở cấp trung ương. Công trình ≤7 tầng thuộc dự án đã phê duyệt quy hoạch được miễn giấy phép.

---

## 3. Kế Hoạch Chuyển Đổi Từng Plugin

### Plugin 00: Thẩm Định (Due Diligence) → `00-tham-dinh`

**Gốc:** 7 kỹ năng tra cứu NYC (DOB, HPD, ACRIS, BSA, Landmarks)
**Chuyển đổi:** Thay thế hoàn toàn bằng nguồn dữ liệu Việt Nam

| Kỹ năng mới | Tương đương gốc | Nguồn dữ liệu |
|---|---|---|
| `tra-cuu-giay-phep-xd` | nyc-dob-permits | Sở Xây dựng tỉnh/thành, cổng dịch vụ công |
| `tra-cuu-vi-pham-xd` | nyc-dob-violations | Thanh tra xây dựng, báo cáo vi phạm trật tự xây dựng |
| `tra-cuu-dat-dai` | nyc-acris | Sổ đỏ / Giấy CNQSDĐ, Sở TNMT, VNPT iLand |
| `tra-cuu-quy-hoach` | nyc-bsa | Bản đồ quy hoạch 1/500, 1/2000 từ Sở QHKT |
| `tra-cuu-di-tich` | nyc-landmarks | Danh mục di tích quốc gia (Bộ VHTTDL), di tích cấp tỉnh |
| `tra-cuu-pccc` | (mới) | Quy định PCCC theo QCVN 06:2021/BXD, Cục CS PCCC |
| `bao-cao-tong-hop` | nyc-property-report | Tổng hợp tất cả các tra cứu trên |

**Thách thức chính:** Việt Nam chưa có hệ thống dữ liệu mở tập trung. Cần kết hợp web scraping từ cổng dịch vụ công + dữ liệu GIS mở (OpenStreetMap Vietnam, HCMGIS) + hướng dẫn người dùng cung cấp dữ liệu thủ công khi API không có.

### Plugin 01: Quy Hoạch Mặt Bằng (Site Planning) → `01-quy-hoach-mat-bang`

**Gốc:** 4 kỹ năng (môi trường, giao thông, dân số, lịch sử)
**Chuyển đổi:** Bản địa hóa nguồn dữ liệu

| Kỹ năng | Thay đổi chính |
|---|---|
| `phan-tich-moi-truong` | Khí hậu nhiệt đới gió mùa, phân vùng ASHRAE thay bằng phân vùng khí hậu VN (7 vùng), lũ lụt (Mekong Delta đặc thù), động đất (vùng Tây Bắc), đất yếu (ĐBSCL) |
| `phan-tich-giao-thong` | Metro HCMC/Hanoi, xe buýt BRT, xe máy là phương tiện chính, chỉ số Walk Score thay bằng đánh giá riêng |
| `phan-tich-dan-so` | Tổng cục Thống kê (GSO), dữ liệu dân số theo quận/huyện, thu nhập bình quân, tốc độ đô thị hóa |
| `phan-tich-lich-su` | Phố cổ, khu bảo tồn, di sản UNESCO (Hội An, Huế), kiến trúc thuộc địa Pháp, kiến trúc Đông Dương |

**Nguồn dữ liệu ưu tiên:**
- Tổng cục Khí tượng Thủy văn (VNMHA)
- Geofabrik OpenStreetMap Vietnam
- Tổng cục Thống kê (gso.gov.vn)
- HCMGIS OpenData (cho TP.HCM)

### Plugin 02: Phân Khu (Zoning Analysis) → `02-phan-khu`

**Gốc:** NYC zoning + Uruguay zoning + 3D envelope
**Chuyển đổi:** Hệ thống quy hoạch Việt Nam hoàn toàn khác NYC

| Kỹ năng | Mô tả |
|---|---|
| `phan-tich-quy-hoach-vn` | Tra cứu quy hoạch 1/500, 1/2000: mật độ xây dựng, tầng cao, hệ số sử dụng đất, khoảng lùi. Áp dụng QCVN 01:2021/BXD |
| `phan-tich-dat-dai` | Phân loại đất (đất ở, đất thương mại, đất nông nghiệp, đất hỗn hợp), quyền sử dụng đất, thời hạn sử dụng (50 năm / vĩnh viễn) |
| `mo-hinh-khoi-tich-3d` | Tạo mô hình 3D khối tích xây dựng cho phép (Three.js) dựa trên mật độ, tầng cao, khoảng lùi |

**Khác biệt quan trọng với NYC:**
- VN dùng "mật độ xây dựng" (%) thay vì FAR (Floor Area Ratio) — cần kỹ năng chuyển đổi qua lại
- Tầng cao tối đa quy định trực tiếp (không tính qua FAR × diện tích)
- Khoảng lùi tùy thuộc lộ giới đường (≥6m, ≥12m, ≥20m...)
- Đất nông nghiệp không được chuyển đổi tự do — cần quy trình chuyển mục đích sử dụng

### Plugin 03: Chương Trình Không Gian (Programming) → `03-chuong-trinh`

**Gốc:** Workplace program + IBC occupancy
**Chuyển đổi:** Thay IBC bằng QCVN

| Kỹ năng | Thay đổi |
|---|---|
| `chuong-trinh-khong-gian` | Giữ logic, thay đơn vị sang m² (GSF→DT sàn, USF→DT sử dụng, RSF→DT thuê). Chuẩn thiết kế văn phòng VN (8-12 m²/người) |
| `kiem-tra-so-nguoi` | Thay IBC bằng QCVN 06:2021/BXD cho mật độ người, lối thoát hiểm, khoảng cách thoát nạn |

### Plugin 04: Đặc Tả Kỹ Thuật (Specifications) → `04-dac-ta`

**Gốc:** CSI MasterFormat outline specs
**Chuyển đổi:** Hỗ trợ cả MasterFormat và tiêu chuẩn VN

| Kỹ năng | Mô tả |
|---|---|
| `dac-ta-ky-thuat` | CSI MasterFormat 2018 (giữ lại cho dự án quốc tế) + bổ sung quy cách VN (TCVN, QCVN tham chiếu). Ghi chú vật liệu phổ biến tại VN |

### Plugin 05: Bền Vững (Sustainability) → `05-ben-vung`

**Gốc:** EPD parsing, carbon research, LEED thresholds
**Chuyển đổi:** Thêm LOTUS + EDGE

| Kỹ năng | Mô tả |
|---|---|
| `phan-tich-epd` | Giữ nguyên khả năng đọc EPD, bổ sung đối chiếu với ngưỡng LOTUS |
| `danh-gia-lotus` | Hệ thống chấm điểm LOTUS của VGBC: năng lượng, nước, vật liệu, sức khỏe, cộng đồng. 4 mức: Chứng nhận, Bạc, Vàng, Kim cương |
| `danh-gia-edge` | IFC EDGE: yêu cầu tiết kiệm 20% năng lượng/nước/vật liệu so với baseline |
| `tiet-kiem-nang-luong` | Đánh giá theo QCVN 09:2017/BXD, OTTV (Overall Thermal Transfer Value) cho vỏ bao che |

### Plugin 06: Nghiên Cứu Vật Liệu (Materials Research) → `06-vat-lieu`

**Gốc:** 12 kỹ năng (tìm kiếm, trích xuất spec, xử lý ảnh)
**Chuyển đổi:** Bản địa hóa nguồn cung

| Kỹ năng | Thay đổi |
|---|---|
| `tim-kiem-vat-lieu` | Tìm kiếm nhà cung cấp VN (Viglacera, Prime Group, Hòa Phát, Đồng Tâm, An Cường...) bên cạnh quốc tế |
| `trich-xuat-thong-so` | Giữ nguyên logic, hỗ trợ catalogue tiếng Việt |
| `so-sanh-san-pham` | Thêm cột giá VND, nhà phân phối tại VN, thời gian giao hàng nội địa |
| `xu-ly-du-lieu-noi-that` | Giữ nguyên (CSV/SIF format phổ quát) |

### Plugin 07: Trình Bày (Presentations) → `07-trinh-bay`

**Gốc:** Slide deck, color palette, image resize
**Chuyển đổi:** Bản địa hóa nhẹ

| Kỹ năng | Thay đổi |
|---|---|
| `tao-slide` | Template tiếng Việt, font hỗ trợ tiếng Việt (Roboto, Noto Sans Vietnamese, SVN-Poppins) |
| `bang-mau` | Giữ nguyên |
| `xu-ly-hinh-anh` | Giữ nguyên |

### Plugin 08: Điều Phối (Dispatcher) → `08-dieu-phoi`

| Kỹ năng | Thay đổi |
|---|---|
| `dieu-phoi` | Cập nhật router cho tên kỹ năng tiếng Việt |
| `tro-giup` | Menu trợ giúp tiếng Việt, liệt kê tất cả slash commands |

---

## 4. Chuyển Đổi 7 Agent

| Agent gốc | Agent mới | Thay đổi chính |
|---|---|---|
| site-planner | `chuyen-gia-quy-hoach` | Nguồn dữ liệu VN, khí hậu nhiệt đới, vùng ngập lụt ĐBSCL |
| nyc-zoning-expert | `chuyen-gia-phan-khu-vn` | Thay NYC Zoning Resolution bằng QCVN 01, Luật Đất đai, bản đồ quy hoạch |
| workplace-strategist | `chuyen-gia-khong-gian` | Tiêu chuẩn diện tích VN (m²), QCVN 04 cho chung cư |
| product-researcher | `nghien-cuu-vat-lieu` | Nhà cung cấp VN, giá VND, catalogue tiếng Việt |
| ffe-designer | `thiet-ke-noi-that` | Nhà cung cấp nội thất VN, đơn vị VND |
| sustainability-specialist | `chuyen-gia-ben-vung` | LOTUS/EDGE thay LEED, QCVN 09 năng lượng |
| brand-manager | `quan-ly-thuong-hieu` | Font tiếng Việt, template VN |

---

## 5. Chuyển Đổi 7 Rules

| Rule gốc | Rule mới | Thay đổi |
|---|---|---|
| units-and-measurements | `don-vi-do-luong` | **Mét (m)** là đơn vị chính. m², m³. Ghi kèm imperial trong ngoặc cho dự án quốc tế. Diện tích: DT sàn, DT sử dụng, DT thuê, DT thông thủy |
| code-citations | `trich-dan-quy-chuan` | Trích dẫn QCVN/TCVN theo format: `QCVN XX:YYYY/BXD, Điều Z, Khoản W`. Ghi rõ năm ban hành và sửa đổi |
| professional-disclaimer | `tuyen-bo-mien-tru` | Bản tiếng Việt: "Tài liệu này do AI hỗ trợ tạo ra, không thay thế tư vấn chuyên môn của kiến trúc sư/kỹ sư có chứng chỉ hành nghề" |
| csi-formatting | `dinh-dang-csi` | Giữ MasterFormat cho dự án quốc tế, bổ sung tham chiếu TCVN tương ứng |
| terminology | `thuat-ngu` | Bảng thuật ngữ song ngữ Việt-Anh. VD: Giấy phép xây dựng = Building Permit, Mật độ xây dựng = Building Coverage Ratio |
| output-formatting | `dinh-dang-dau-ra` | Tiếng Việt, dấu phẩy phân cách thập phân (1.000,5 m² hoặc 1,000.5 m² tùy bối cảnh), tiền tệ VND |
| transparency | `minh-bach` | Giữ nguyên tinh thần: trích nguồn, ghi rõ dữ liệu thiếu, đánh dấu thông tin cần xác minh thực địa |

---

## 6. Nguồn Dữ Liệu Việt Nam

### 6.1. Dữ Liệu Mở / Bán Mở

| Nguồn | URL / Cách truy cập | Dữ liệu |
|---|---|---|
| Geofabrik OSM Vietnam | download.geofabrik.de/asia/vietnam | Ranh giới hành chính, hạ tầng, đường sá |
| HCMGIS OpenData | opendata.hcmgis.vn | Dữ liệu GIS TP.HCM |
| Tổng cục Thống kê | gso.gov.vn | Dân số, kinh tế, lao động theo tỉnh |
| Cổng TTĐT Bộ Xây dựng | moc.gov.vn | Văn bản QCVN, TCVN, thông tư |
| Cổng dịch vụ công quốc gia | dichvucong.gov.vn | Tra cứu giấy phép, thủ tục hành chính |
| VGBC | vgbc.vn | Tài liệu LOTUS, dự án xanh đã chứng nhận |

### 6.2. Dữ Liệu Cần Thu Thập Thủ Công

| Dữ liệu | Lý do | Giải pháp |
|---|---|---|
| Bản đồ quy hoạch 1/500 | Không có API công khai | Prompt người dùng upload ảnh/PDF bản đồ → đọc bằng AI |
| Sổ đỏ / GCN QSDĐ | Thông tin cá nhân, không công khai | Prompt người dùng cung cấp thông số: diện tích, mục đích SDĐ, thời hạn |
| Giá đất | Khung giá đất UBND tỉnh (công khai) vs giá thị trường | Web search giá khung + cảnh báo chênh lệch giá thị trường |

---

## 7. Lộ Trình Triển Khai

### Giai đoạn 1 — Nền tảng (2-3 tuần)

- [ ] Fork repo, cấu trúc lại thư mục với tên tiếng Việt
- [ ] Viết 7 rules bản Việt Nam
- [ ] Tạo bảng thuật ngữ song ngữ (`thuat-ngu.md`) — ≥200 thuật ngữ AEC
- [ ] Nhúng toàn bộ QCVN/TCVN trọng yếu vào tệp tham chiếu

### Giai đoạn 2 — Plugin Ưu Tiên Cao (3-4 tuần)

- [ ] Plugin 02 `phan-khu`: mật độ xây dựng, tầng cao, khoảng lùi, mô hình 3D
- [ ] Plugin 00 `tham-dinh`: tra cứu đất đai, quy hoạch, PCCC, di tích
- [ ] Plugin 01 `quy-hoach-mat-bang`: khí hậu, giao thông, dân số, lịch sử
- [ ] Agent `chuyen-gia-phan-khu-vn` và `chuyen-gia-quy-hoach`

### Giai đoạn 3 — Plugin Chuyên Sâu (3-4 tuần)

- [ ] Plugin 03 `chuong-trinh`: diện tích theo QCVN, mật độ người
- [ ] Plugin 05 `ben-vung`: LOTUS, EDGE, QCVN 09 năng lượng
- [ ] Plugin 06 `vat-lieu`: nhà cung cấp VN, catalogue tiếng Việt
- [ ] Plugin 04 `dac-ta`: TCVN tham chiếu

### Giai đoạn 4 — Hoàn Thiện (2 tuần)

- [ ] Plugin 07 `trinh-bay`: font tiếng Việt, template
- [ ] Plugin 08 `dieu-phoi`: router + menu trợ giúp
- [ ] 5 agent còn lại
- [ ] Hooks: tự động kiểm tra QCVN khi tạo báo cáo
- [ ] Kiểm thử end-to-end với 3 kịch bản thực tế

---

## 8. Cấu Trúc Thư Mục Đề Xuất

```
skills-for-architects-vietnam/
├── .claude-plugin/
│   └── manifest.json
├── agents/
│   ├── chuyen-gia-quy-hoach.md
│   ├── chuyen-gia-phan-khu-vn.md
│   ├── chuyen-gia-khong-gian.md
│   ├── nghien-cuu-vat-lieu.md
│   ├── thiet-ke-noi-that.md
│   ├── chuyen-gia-ben-vung.md
│   └── quan-ly-thuong-hieu.md
├── plugins/
│   ├── 00-tham-dinh/
│   │   └── skills/
│   │       ├── tra-cuu-giay-phep-xd/SKILL.md
│   │       ├── tra-cuu-vi-pham-xd/SKILL.md
│   │       ├── tra-cuu-dat-dai/SKILL.md
│   │       ├── tra-cuu-quy-hoach/SKILL.md
│   │       ├── tra-cuu-di-tich/SKILL.md
│   │       ├── tra-cuu-pccc/SKILL.md
│   │       └── bao-cao-tong-hop/SKILL.md
│   ├── 01-quy-hoach-mat-bang/
│   │   └── skills/
│   │       ├── phan-tich-moi-truong/SKILL.md
│   │       ├── phan-tich-giao-thong/SKILL.md
│   │       ├── phan-tich-dan-so/SKILL.md
│   │       └── phan-tich-lich-su/SKILL.md
│   ├── 02-phan-khu/
│   │   └── skills/
│   │       ├── phan-tich-quy-hoach-vn/SKILL.md
│   │       ├── phan-tich-dat-dai/SKILL.md
│   │       └── mo-hinh-khoi-tich-3d/SKILL.md
│   ├── 03-chuong-trinh/
│   │   └── skills/
│   │       ├── chuong-trinh-khong-gian/SKILL.md
│   │       └── kiem-tra-so-nguoi/SKILL.md
│   ├── 04-dac-ta/
│   │   └── skills/
│   │       └── dac-ta-ky-thuat/SKILL.md
│   ├── 05-ben-vung/
│   │   └── skills/
│   │       ├── phan-tich-epd/SKILL.md
│   │       ├── danh-gia-lotus/SKILL.md
│   │       ├── danh-gia-edge/SKILL.md
│   │       └── tiet-kiem-nang-luong/SKILL.md
│   ├── 06-vat-lieu/
│   │   └── skills/
│   │       ├── tim-kiem-vat-lieu/SKILL.md
│   │       ├── trich-xuat-thong-so/SKILL.md
│   │       ├── so-sanh-san-pham/SKILL.md
│   │       └── xu-ly-du-lieu-noi-that/SKILL.md
│   ├── 07-trinh-bay/
│   │   └── skills/
│   │       ├── tao-slide/SKILL.md
│   │       ├── bang-mau/SKILL.md
│   │       └── xu-ly-hinh-anh/SKILL.md
│   └── 08-dieu-phoi/
│       └── skills/
│           ├── dieu-phoi/SKILL.md
│           └── tro-giup/SKILL.md
├── rules/
│   ├── don-vi-do-luong.md
│   ├── trich-dan-quy-chuan.md
│   ├── tuyen-bo-mien-tru.md
│   ├── dinh-dang-csi.md
│   ├── thuat-ngu.md
│   ├── dinh-dang-dau-ra.md
│   └── minh-bach.md
├── hooks/
│   ├── kiem-tra-qcvn.sh
│   ├── kiem-tra-don-vi.sh
│   └── tao-disclaimer.sh
├── reference/
│   ├── qcvn-tong-hop.md          # Tổng hợp QCVN trọng yếu
│   ├── tcvn-tong-hop.md          # Tổng hợp TCVN quan trọng
│   ├── thuat-ngu-song-ngu.md     # Bảng thuật ngữ Việt-Anh ≥200 từ
│   ├── nha-cung-cap-vn.md        # Danh mục nhà cung cấp vật liệu VN
│   └── nguon-du-lieu.md          # Hướng dẫn truy cập dữ liệu
└── README.md
```

---

## 9. Rủi Ro và Giải Pháp

| Rủi ro | Mức độ | Giải pháp |
|---|---|---|
| Thiếu dữ liệu mở (API) | **Cao** | Thiết kế skill theo mô hình hybrid: tự động khi có dữ liệu + prompt người dùng upload khi không có |
| QCVN thay đổi thường xuyên | Trung bình | Ghi rõ ngày cập nhật trong mỗi tệp tham chiếu, đặt hook nhắc kiểm tra hàng quý |
| Font tiếng Việt trong output | Thấp | Sử dụng Google Fonts có hỗ trợ Vietnamese: Roboto, Noto Sans, Open Sans |
| Khác biệt quy hoạch giữa các tỉnh | Trung bình | Skill hỏi tỉnh/thành trước khi chạy, tải quy định cụ thể theo địa phương |
| Thuật ngữ pháp lý phức tạp | Trung bình | Bảng thuật ngữ song ngữ chi tiết, luôn ghi kèm tên tiếng Anh |

---

## 10. Kịch Bản Kiểm Thử

**Kịch bản 1 — Thẩm định lô đất TP.HCM:**
Chạy `/bao-cao-tong-hop` cho một địa chỉ Quận 2, kiểm tra: quy hoạch, mật độ, tầng cao, khoảng lùi, PCCC, di tích, pháp lý đất.

**Kịch bản 2 — Thiết kế văn phòng Hà Nội:**
`/chuong-trinh-khong-gian` cho 200 nhân viên → kiểm tra diện tích m², mật độ người theo QCVN 06, lối thoát hiểm.

**Kịch bản 3 — Đánh giá bền vững resort Đà Nẵng:**
`/danh-gia-lotus` + `/phan-tich-moi-truong` → kiểm tra điểm LOTUS, khí hậu miền Trung, vùng ngập, tiết kiệm năng lượng.
