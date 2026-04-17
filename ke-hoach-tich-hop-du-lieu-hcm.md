# Kế Hoạch Tích Hợp Dữ Liệu Quy Hoạch TP.HCM

**Ngày:** 2026-04-17
**Trạng thái:** Đề xuất — Phase 2.5
**Mục tiêu:** Tích hợp dữ liệu từ cổng Sở QHKT TP.HCM vào các kỹ năng (skills) của dự án architect-skill-vietnam, nâng cao độ chính xác cho phân tích quy hoạch khu vực TP.HCM.

---

## 1. Tổng Quan Nguồn Dữ Liệu

Sở Quy hoạch – Kiến trúc TP.HCM cung cấp **ba nguồn dữ liệu chính**, tất cả phục vụ miễn phí:

### 1.1. Cổng Bản Đồ Quy Hoạch (Static)
- **URL:** `https://qhkt.hochiminhcity.gov.vn/ban-do-quy-hoach.html`
- **Nội dung:** Mỗi quận/huyện có 2 mục:
  - **QĐ phê duyệt quy hoạch** — PDF tải trực tiếp (VD: `/Uploads/Document/Maps/QHC_Quan7_5760_QD_UBND_12_11_2012_1.pdf`)
  - **Bản Đồ** — Hình ảnh bản đồ quy hoạch 1/5000 (modal popup, ảnh tĩnh)
- **Định dạng:** PDF + hình ảnh JPEG/PNG
- **Độ phủ:** 21 quận/huyện + TP Thủ Đức (toàn TP.HCM)
- **Hạn chế:** Tĩnh, không tra cứu theo địa chỉ, cần đọc thủ công

### 1.2. Hệ Thống GIS Tra Cứu Quy Hoạch (Interactive)
- **URL:** `https://gisxaydung.tphcm.gov.vn/quy-hoach-xd-pk/`
- **API Backend:** `https://api-gisxaydung.tphcm.gov.vn/`
- **Nội dung:** Bản đồ GIS tương tác với dữ liệu quy hoạch phân khu
- **Tra cứu theo:**
  - Số tờ / Số thửa (parcel sheet + lot number) + Quận + Phường
  - Tọa độ VN-2000 (polygon, hỗ trợ upload Excel)
- **Dữ liệu trả về cho mỗi thửa đất:**

| Trường | Ý nghĩa | Tương đương skill |
|---|---|---|
| Mã mục đích sử dụng đất | Land use code (DGT, KDC, SKC, CTC, DAQ, DKH...) | Chức năng đất |
| Diện tích (m²) | Zone area within parcel | Diện tích quy hoạch |
| Hệ số sử dụng đất | FAR | HSSDĐ |
| Tầng cao xây dựng (tầng) | Max floors | Tầng cao |
| Mật độ xây dựng TB (%) | Average BCR | MDXD |
| Ký hiệu lô đất | Lot designation in zoning plan | Ký hiệu |
| Quy mô dân số | Population scale for the zone | — |
| Quyết định phê duyệt | Approval decision number + date | QĐ tham chiếu |

- **Lớp dữ liệu (Layers):**
  - Quy hoạch xây dựng (Construction zoning — color overlay)
  - Nền OpenStreetMap / Đường phố / Vệ tinh
- **Tính năng bổ sung:** Xuất PDF, chỉ đường, phản ảnh

### 1.3. API Endpoints Đã Xác Định

```
# 1. Parcel query by district + ward + bbox
GET api-gisxaydung.tphcm.gov.vn/rest/thua-dat
  ?fields=soTo,soThua,shape
  &limit=100
  &fGeo=geojson
  &bbox={"spatialReference":{"wkid":4326},"xmax":...,"xmin":...,"ymax":...,"ymin":...}
  &outSR={"wkid":4326}
  &filter[0]=maPhuongXa||$eq||{ward_code}
  &filter[1]=maQuanHuyen||$eq||{district_code}

# 2. Administrative boundary query
POST api-gisxaydung.tphcm.gov.vn/rest/ranh-gioi-hanh-chinh-cu/query
  ?fields=maPhuongXa,maQuanHuyen

# 3. ArcGIS Map export (tile images)
GET api-gisxaydung.tphcm.gov.vn/arcgis/rest/services/HanhChinhMoi/MapServer/export
  ?bbox=...&size=...&dpi=96&format=png32&transparent=true
  &bboxSR=3857&imageSR=3857&f=json
```

### 1.4. Mã Quận/Huyện (District Codes)

| Quận/Huyện | Mã | Quận/Huyện | Mã |
|---|---|---|---|
| Quận 1 | 760 | Quận Bình Tân | 777 |
| Quận 3 | 770 | Quận Bình Thạnh | 765 |
| Quận 4 | 773 | Quận Tân Bình | 766 |
| Quận 5 | 774 | Quận Tân Phú | 767 |
| Quận 6 | 775 | Quận Gò Vấp | 764 |
| Quận 7 | 778 | Quận Phú Nhuận | 768 |
| Quận 8 | 776 | TP Thủ Đức | 769 |
| Quận 10 | 771 | Huyện Bình Chánh | 785 |
| Quận 11 | 772 | Huyện Cần Giờ | 787 |
| Quận 12 | 761 | Huyện Củ Chi | 783 |
| | | Huyện Hóc Môn | 784 |
| | | Huyện Nhà Bè | 786 |

### 1.5. Mã Mục Đích Sử Dụng Đất (Land Use Codes)

| Mã | Tên | English |
|---|---|---|
| DGT | Đất giao thông | Transportation |
| SON | Đất sông, kênh mương, hồ thủy lợi | Waterways/Irrigation |
| DGD | Đất giáo dục | Education |
| DAN | Đất an ninh quốc phòng | Defense/Security |
| KDC | Đất khu dân cư | Residential |
| SKC | Đất cơ sở sản xuất kinh doanh | Commercial/Industrial |
| CTC | Đất công trình công cộng | Public Facilities |
| DAQ | Đất dự án quy hoạch | Planned Project |
| DKH | Đất khác | Other |

---

## 2. Kế Hoạch Tích Hợp

### Phase A: Cập Nhật URL & Hướng Dẫn Người Dùng (Ngay — đã hoàn thành)

**Đã thực hiện:**
- [x] Cập nhật `quyhoach.tphcm.gov.vn` → `qhkt.hochiminhcity.gov.vn` trong:
  - `plugins/02-phan-khu/skills/phan-tich-quy-hoach-vn/SKILL.md`
  - `plugins/00-tham-dinh/skills/tra-cuu-quy-hoach/SKILL.md`
  - `reference/nguon-du-lieu.md`

### Phase B: Tích Hợp GIS Lookup Vào Skills (Ưu tiên cao)

**Mục tiêu:** Khi người dùng cung cấp địa chỉ TP.HCM, skill tự động truy cập GIS portal để lấy thông số quy hoạch thay vì chỉ dựa vào QCVN chung.

**Cách tiếp cận: Hướng dẫn truy cập GIS (không dùng API trực tiếp)**

Lý do không gọi API trực tiếp:
1. API yêu cầu **số tờ + số thửa** (từ sổ đỏ) — người dùng thường chỉ có địa chỉ
2. API có thể thay đổi mà không thông báo (không có tài liệu API công khai)
3. Dữ liệu trả về cần diễn giải trong ngữ cảnh quyết định phê duyệt
4. Một số trường thường trống ở cấp 1/5000 — cần tra cứu bổ sung

**Thay đổi cho `phan-tich-quy-hoach-vn/SKILL.md`:**

```markdown
### Bước 1b: Tra Cứu GIS TP.HCM (Chỉ Cho Địa Chỉ TP.HCM)

Nếu địa chỉ thuộc TP.HCM:

1. **Hướng dẫn người dùng tra cứu tại:**
   `https://gisxaydung.tphcm.gov.vn/quy-hoach-xd-pk/`

2. **Thông tin cần từ GIS:**
   - Mã mục đích sử dụng đất (KDC, SKC, CTC, v.v.)
   - Tầng cao xây dựng (tầng)
   - Mật độ xây dựng TB (%)
   - Hệ số sử dụng đất
   - Quyết định phê duyệt (số QĐ + ngày)

3. **Nếu người dùng có số tờ/thửa (từ sổ đỏ):**
   → Tra cứu trực tiếp: chọn Quận → Phường → nhập số tờ/thửa → Tìm kiếm

4. **Nếu chỉ có địa chỉ:**
   → Hướng dẫn zoom vào khu vực trên bản đồ → click vào thửa đất
   → Hoặc: sử dụng tọa độ từ Google Maps (chuyển sang VN-2000)

5. **Ghi chú dữ liệu:**
   - Dữ liệu GIS là "tính chất tham khảo" (ghi trên portal)
   - Quy hoạch 1/5000 có thể thiếu MDXD, HSSDĐ, tầng cao cụ thể
   - Cần bản đồ 1/500 hoặc 1/2000 cho thông số chính xác
   - Luôn ghi rõ số QĐ phê duyệt trong báo cáo
```

**Thay đổi cho `tra-cuu-quy-hoach/SKILL.md`:**

```markdown
### Bổ sung: Kiểm Tra GIS TP.HCM

Nếu địa chỉ thuộc TP.HCM, bổ sung vào phần tra cứu:

1. Mở `gisxaydung.tphcm.gov.vn/quy-hoach-xd-pk/`
2. Tra cứu theo số tờ/thửa hoặc trên bản đồ
3. Ghi nhận:
   - Mã chức năng đất (VD: KDC = dân cư, SKC = sản xuất kinh doanh)
   - QĐ phê duyệt (VD: 6692/QĐ-UBND ngày 28/12/2012)
   - Tên đồ án quy hoạch
4. Đối chiếu với thông tin quy hoạch treo (nếu có)
```

### Phase C: Bảng Tra Cứu QĐ Phê Duyệt Theo Quận (Ưu tiên trung bình)

Xây dựng bảng tham chiếu trong `reference/` liệt kê QĐ phê duyệt quy hoạch chung từng quận, để skill có thể tham chiếu nhanh mà không cần truy cập web mỗi lần.

**File mới: `reference/qd-quy-hoach-hcm.md`**

Cấu trúc đề xuất:

```markdown
# Quyết Định Phê Duyệt Quy Hoạch — TP.HCM

## Quy Hoạch Chung 1/5000

| Quận | Số QĐ | Ngày | Tên Đồ Án | PDF |
|---|---|---|---|---|
| Quận 7 | 5760/QĐ-UBND | 12/11/2012 | QHC Quận 7 | [Link PDF] |
| Quận 7 | 6692/QĐ-UBND | 28/12/2012 | KĐT Nam TP.HCM 1/5000 | [Link PDF] |
| ... | ... | ... | ... | ... |

## Ghi Chú
- Dữ liệu thu thập từ: qhkt.hochiminhcity.gov.vn/ban-do-quy-hoach.html
- PDF URL pattern: /Uploads/Document/Maps/QHC_{Quận}_{SốQĐ}_QD_UBND_{Ngày}.pdf
- Cần cập nhật khi có QĐ điều chỉnh mới
```

**Cách thu thập:** Dùng WebFetch để tải trang `ban-do-quy-hoach.html`, trích xuất tất cả link PDF và tên QĐ từ HTML → lập bảng.

### Phase D: MCP Connector Cho GIS API (Ưu tiên thấp — Phase 3+)

Nếu API ổn định và project mở rộng, có thể xây dựng MCP connector để:
1. Tự động tra cứu thửa đất bằng số tờ/thửa
2. Trả về dữ liệu quy hoạch có cấu trúc (JSON)
3. Hiển thị ranh thửa trên bản đồ

**Kiến trúc MCP đề xuất:**

```
mcp-gis-hcm/
├── server.py          (FastMCP server)
├── tools/
│   ├── tra_cuu_thua_dat.py    → GET /rest/thua-dat
│   ├── tra_cuu_quy_hoach.py   → Query zoning overlay
│   └── xuat_ban_do.py         → Export map image
└── config.py          (API base URL, district codes)
```

**Tools:**
- `tra-cuu-thua-dat(quan, phuong, so_to, so_thua)` → Parcel geometry + attributes
- `tra-cuu-quy-hoach(quan, phuong, so_to, so_thua)` → Zoning parameters
- `xuat-ban-do(bbox, scale)` → Map image export

**Rủi ro:**
- API không có tài liệu chính thức → có thể thay đổi bất ngờ
- Cần xác minh điều khoản sử dụng (terms of service)
- Token JWT có thời hạn ngắn (~15 phút theo observed expiry)

---

## 3. Cập Nhật `reference/nguon-du-lieu.md`

Bổ sung mục TP.HCM chi tiết hơn:

```markdown
### TP.HCM — Nguồn Dữ Liệu Quy Hoạch

**Cổng chính:** [qhkt.hochiminhcity.gov.vn](https://qhkt.hochiminhcity.gov.vn)

| Nguồn | URL | Nội Dung | Cách Dùng |
|---|---|---|---|
| Bản đồ QH | /ban-do-quy-hoach.html | PDF QĐ + bản đồ 1/5000 theo quận | Tải PDF, đọc QĐ |
| GIS tra cứu | gisxaydung.tphcm.gov.vn/quy-hoach-xd-pk/ | Tra cứu theo thửa đất hoặc tọa độ | Nhập số tờ/thửa → xem chức năng đất, MDXD, tầng cao |
| QH phân khu 1/2000 | /quy-hoach-phan-khu-1-2000.html | Quy hoạch chi tiết hơn | Chưa khảo sát |
| Dữ liệu biệt thự | (trong nav) | Lớp dữ liệu biệt thự | Chưa khảo sát |
| Dịch vụ công | (trong nav) | Nộp hồ sơ online | Không liên quan trực tiếp |

**Lưu ý:** Dữ liệu GIS ghi "tính chất tham khảo" — cần xác minh tại Sở QHKT cho mục đích pháp lý.
```

---

## 4. Thứ Tự Ưu Tiên

| # | Công việc | Effort | Impact | Ưu tiên |
|---|---|---|---|---|
| A | Cập nhật URL (đã xong) | ✅ Done | Cao | — |
| B1 | Thêm hướng dẫn GIS vào `phan-tich-quy-hoach-vn` | 1 giờ | Cao | **Tiếp theo** |
| B2 | Thêm hướng dẫn GIS vào `tra-cuu-quy-hoach` | 30 phút | Cao | **Tiếp theo** |
| B3 | Cập nhật `nguon-du-lieu.md` với chi tiết GIS | 30 phút | Trung bình | **Tiếp theo** |
| C | Bảng QĐ phê duyệt theo quận | 2-3 giờ | Trung bình | Phase 2.5 |
| D | MCP Connector cho GIS API | 1-2 ngày | Cao (nếu ổn định) | Phase 3+ |

---

## 5. Rủi Ro & Giải Pháp

| Rủi ro | Mức độ | Giải pháp |
|---|---|---|
| API thay đổi không báo trước | Cao | Skill dùng hướng dẫn thủ công, không phụ thuộc API |
| Dữ liệu 1/5000 thiếu MDXD/tầng cao | Trung bình | Ghi rõ cần tra 1/500 hoặc 1/2000, fallback QCVN |
| Portal không ổn định | Trung bình | Skill có fallback: yêu cầu upload bản đồ QH |
| Chỉ phủ TP.HCM | Thấp | Các tỉnh khác vẫn dùng quy trình hiện tại |
| Dữ liệu "tham khảo" không chính xác | Trung bình | Tuyên bố miễn trừ + khuyến cáo xác minh tại Sở |

---

## 6. Các Cổng Tỉnh/Thành Khác Cần Khảo Sát

Mô hình tương tự có thể áp dụng cho:

| Tỉnh/Thành | URL hiện biết | Trạng thái |
|---|---|---|
| Hà Nội | quyhoach.hanoi.vn | Chưa khảo sát |
| Đà Nẵng | quyhoach.danang.gov.vn | Chưa khảo sát |
| Bình Dương | (GIS HCM có mã huyện Bình Dương) | Phát hiện trong GIS |
| Bà Rịa - Vũng Tàu | (GIS HCM có mã TP Bà Rịa) | Phát hiện trong GIS |

**Ghi chú:** GIS TP.HCM bất ngờ bao gồm cả một số huyện thuộc Bình Dương (Bàu Bàng, Bến Cát, Dầu Tiếng, Dĩ An, Tân Uyên, Bắc Tân Uyên, Thủ Dầu Một, Thuận An, Phú Giáo) và TP Bà Rịa — có thể là do vùng đô thị TP.HCM mở rộng.
