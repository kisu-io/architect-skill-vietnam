# Hướng Dẫn Nguồn Dữ Liệu Việt Nam

Tệp này hướng dẫn cách truy cập dữ liệu cho các kỹ năng kiến trúc — xây dựng — bất động sản tại Việt Nam.

---

## 1. Dữ Liệu Mở & Bán Mở (Tự Động Truy Cập Được)

### 1.1. Dữ Liệu Không Gian (GIS)

| Nguồn | URL | Dữ liệu | Định dạng |
|---|---|---|---|
| OpenStreetMap Vietnam | [download.geofabrik.de/asia/vietnam](https://download.geofabrik.de/asia/vietnam.html) | Ranh giới hành chính, đường sá, tòa nhà, POI | .osm.pbf, .shp |
| HCMGIS OpenData | [opendata.hcmgis.vn](https://opendata.hcmgis.vn) | Dữ liệu GIS TP.HCM: ranh quận, đường, sông ngòi | GeoJSON, CSV |
| Open Development Mekong | [opendevelopmentmekong.net](https://opendevelopmentmekong.net/vi/vietnam/) | Ranh giới tỉnh/huyện, hạ tầng, môi trường | .shp, .kml |
| GADM | [gadm.org/country/VNM](https://gadm.org/download_country.html) | Ranh giới hành chính cấp 1–3 (tỉnh, huyện, xã) | .shp, .gpkg |

### 1.2. Dữ Liệu Dân Số & Kinh Tế

| Nguồn | URL | Dữ liệu | Cập nhật |
|---|---|---|---|
| Tổng cục Thống kê (GSO) | [gso.gov.vn](https://www.gso.gov.vn) | Dân số, thu nhập, lao động, xây dựng, BĐS theo tỉnh | Hàng năm, quý |
| World Bank — Vietnam | [data.worldbank.org/country/VN](https://data.worldbank.org/country/vietnam) | GDP, đô thị hóa, hạ tầng | Hàng năm |
| UNDP Vietnam | [undp.org/vietnam](https://www.undp.org/vietnam) | Phát triển con người, biến đổi khí hậu | Theo báo cáo |

### 1.3. Dữ Liệu Khí Hậu & Môi Trường

| Nguồn | URL | Dữ liệu | Ghi chú |
|---|---|---|---|
| Tổng cục KTTV (VNMHA) | [nchmf.gov.vn](https://nchmf.gov.vn) | Dự báo thời tiết, cảnh báo bão, lũ | Cập nhật liên tục |
| NOAA Climate Data | [ncdc.noaa.gov](https://www.ncdc.noaa.gov/) | Trạm quan trắc VN, nhiệt độ, lượng mưa lịch sử | Dữ liệu lịch sử |
| Global Wind Atlas | [globalwindatlas.info](https://globalwindatlas.info/) | Tốc độ gió, mật độ năng lượng gió | Bản đồ tương tác |
| FEMA Global Flood | Không trực tiếp cho VN | Vùng ngập lụt | Dùng dữ liệu VNMHA + WorldPop |
| USGS Earthquake Hazards | [earthquake.usgs.gov](https://earthquake.usgs.gov/) | Bản đồ nguy hiểm động đất | Toàn cầu, bao gồm VN |

### 1.4. Dữ Liệu Pháp Lý & Quy Chuẩn

| Nguồn | URL | Dữ liệu |
|---|---|---|
| Bộ Xây dựng | [moc.gov.vn](https://moc.gov.vn) | QCVN, TCVN, thông tư, nghị định liên quan XD |
| Thư viện Pháp luật | [thuvienphapluat.vn](https://thuvienphapluat.vn) | Toàn bộ văn bản pháp luật, tra cứu theo số hiệu |
| Cổng TTĐT Chính phủ | [vanban.chinhphu.vn](https://vanban.chinhphu.vn) | Luật, nghị định, quyết định Thủ tướng |
| LawNet (EN) | [lawnet.vn/en](https://lawnet.vn/en) | Bản dịch tiếng Anh một số văn bản |

### 1.5. Dữ Liệu Bền Vững

| Nguồn | URL | Dữ liệu |
|---|---|---|
| VGBC (Hội đồng Công trình Xanh VN) | [vgbc.vn](https://vgbc.vn/en/) | Hệ thống LOTUS, danh sách dự án xanh, tài liệu hướng dẫn |
| EDGE (IFC) | [edgebuildings.com](https://www.edgebuildings.com/) | Công cụ tính EDGE, dự án đã chứng nhận |
| EPD International | [environdec.com](https://www.environdec.com/) | Environmental Product Declarations toàn cầu |

---

## 2. Dữ Liệu Hạn Chế (Cần Hỗ Trợ Người Dùng)

### 2.1. Bản Đồ Quy Hoạch

**Tình trạng:** Bản đồ quy hoạch 1/500, 1/2000 được phê duyệt tại cấp tỉnh/thành. Không có API quốc gia. Một số tỉnh/thành công bố online, đa số cần tra cứu trực tiếp.

**Cách truy cập:**
- TP.HCM: [quyhoach.tphcm.gov.vn](http://quyhoach.tphcm.gov.vn) — tra cứu thửa đất online (hạn chế)
- Hà Nội: Sở QHKT Hà Nội [hanoi.gov.vn](https://hanoi.gov.vn) — công bố quy hoạch phân khu
- Đà Nẵng: [quyhoach.danang.gov.vn](https://quyhoach.danang.gov.vn) — bản đồ quy hoạch online
- Các tỉnh khác: Tra cứu tại Sở QHKT hoặc Phòng QLĐT quận/huyện

**Giải pháp trong kỹ năng:**
1. Hỏi người dùng tỉnh/thành → kiểm tra có cổng tra cứu online không
2. Nếu không có: yêu cầu người dùng upload ảnh/PDF bản đồ quy hoạch
3. Đọc thông số từ ảnh/PDF bằng AI: mật độ, tầng cao, khoảng lùi, chức năng đất
4. Ghi rõ: "Thông số đọc từ bản đồ quy hoạch do người dùng cung cấp — cần xác minh tại Sở QHKT"

### 2.2. Giấy Chứng Nhận Quyền Sử Dụng Đất (Sổ Đỏ / Sổ Hồng)

**Tình trạng:** Thông tin cá nhân, không công khai trực tuyến.

**Giải pháp:**
- Yêu cầu người dùng cung cấp các thông số cần thiết: diện tích, mục đích sử dụng đất, thời hạn, vị trí, số thửa/tờ bản đồ
- Không bao giờ lưu trữ số GCNQSDĐ hoặc thông tin chủ sở hữu

### 2.3. Giá Đất

**Tình trạng:** Có hai loại giá:
- **Khung giá đất** (UBND tỉnh ban hành, 5 năm/lần): công khai, tra cứu được
- **Giá thị trường**: không có cơ sở dữ liệu chính thức, biến động theo thời gian

**Giải pháp:**
- Tra cứu khung giá đất tại website UBND tỉnh hoặc Sở TNMT
- Tham chiếu giá thị trường từ batdongsan.com.vn, cafeland.vn (cảnh báo: giá rao, không phải giá giao dịch thực)
- Luôn ghi rõ: "Giá tham khảo, cần thẩm định giá độc lập cho mục đích đầu tư"

### 2.4. Hồ Sơ Giấy Phép Xây Dựng

**Tình trạng:** Đang số hóa dần. Một số tỉnh/thành cho phép tra cứu qua Cổng dịch vụ công.

**Cách truy cập:**
- [dichvucong.gov.vn](https://dichvucong.gov.vn) — Cổng dịch vụ công quốc gia
- Cổng dịch vụ công cấp tỉnh (mỗi tỉnh riêng)
- Mức độ thông tin công khai khác nhau giữa các tỉnh

---

## 3. Ma Trận Nguồn Dữ Liệu Theo Kỹ Năng

| Kỹ năng | Nguồn tự động | Nguồn cần người dùng |
|---|---|---|
| Phân tích quy hoạch | OSM, QCVN 01 (tích hợp) | Bản đồ QH 1/500, GCNQSDĐ |
| Phân tích môi trường | NOAA, VNMHA, USGS, Global Wind Atlas | Khảo sát địa chất (nếu có) |
| Phân tích dân số | GSO, World Bank | — |
| Phân tích giao thông | OSM, Google Maps API | — |
| Tra cứu đất đai | Khung giá đất (web UBND) | Sổ đỏ, hồ sơ pháp lý |
| Tra cứu PCCC | QCVN 06 (tích hợp) | Hồ sơ thẩm duyệt PCCC |
| Đánh giá LOTUS/EDGE | VGBC, EDGE tool | Thiết kế chi tiết |
| Nghiên cứu vật liệu | Web search, EPD database | Catalogue nhà cung cấp |

---

## 4. Quy Tắc Trích Dẫn Nguồn

1. Luôn ghi **URL + ngày truy cập** cho dữ liệu online
2. Ghi **tên cơ quan + năm** cho dữ liệu offline: "Sở QHKT TP.HCM, Quy hoạch phân khu tỷ lệ 1/2000, phê duyệt 2020"
3. Phân biệt rõ **dữ liệu tự động** vs **dữ liệu người dùng cung cấp**
4. Đánh dấu **dữ liệu có thể lỗi thời**: "Bản đồ quy hoạch phê duyệt 2018, kiểm tra điều chỉnh mới nhất tại Sở QHKT"
