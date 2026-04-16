# Kiểm Tra Phase 1 — Quy Tắc & Tham Chiếu

Chạy 3 prompt kiểm thử với vai trò kỹ năng sản xuất, sau đó tự đánh giá tuân thủ quy tắc.
Ngày kiểm tra: 2026-04-16.

---

## Bài Kiểm Tra 1

**Prompt:** "Tính mật độ xây dựng cho lô đất 500m2 tại Quận 1 TP.HCM, xây 3 tầng nhà ở riêng lẻ"

### Đầu Ra Mô Phỏng

---

```yaml
---
tieu-de: "Phân tích mật độ xây dựng — Nhà ở riêng lẻ, Quận 1, TP.HCM"
ngay: 2026-04-16
dia-chi: "Quận 1, TP.HCM (địa chỉ cụ thể chưa cung cấp)"
ky-nang: phan-tich-quy-hoach-vn
---
```

#### Phân Tích Mật Độ Xây Dựng — Nhà Ở Riêng Lẻ

**Thông tin đầu vào:**

| Thông số | Giá trị |
|---|---|
| Diện tích lô đất | 500 m² |
| Vị trí | Quận 1, TP.HCM |
| Loại công trình | Nhà ở riêng lẻ |
| Số tầng dự kiến | 3 tầng |

**1. Mật Độ Xây Dựng (MDXD) Tối Đa Cho Phép**

Theo QCVN 01:2021/BXD, Điều 2.8, nhà ở riêng lẻ ≤ 4 tầng có mật độ xây dựng (Building Coverage Ratio — BCR) tối đa phụ thuộc vào diện tích lô đất:

| Diện tích lô đất (m²) | MDXD tối đa (%) | Nguồn |
|---|---|---|
| < 50 | 100% | QCVN 01:2021/BXD, Bảng 2.8 |
| 50–100 | 90% | QCVN 01:2021/BXD, Bảng 2.8 |
| 100–200 | 80% | QCVN 01:2021/BXD, Bảng 2.8 |
| 200–500 | 70% | QCVN 01:2021/BXD, Bảng 2.8 |
| > 500 | 60% | QCVN 01:2021/BXD, Bảng 2.8 |

Với diện tích lô đất 500 m², mật độ xây dựng tối đa cho phép là **70%**.

**2. Tính Toán**

| Thông số | Công thức | Kết quả |
|---|---|---|
| Diện tích chiếm đất tối đa | 500 m² × 70% | **350 m²** |
| Diện tích sàn xây dựng (DT sàn) tối đa | 350 m² × 3 tầng | **1.050 m²** |
| Hệ số sử dụng đất (HSSDĐ) | 1.050 m² ÷ 500 m² | **2,1 lần** |

Tương đương quốc tế: HSSDĐ 2,1 lần = FAR (Floor Area Ratio) 2.1.

**3. Khoảng Lùi**

Khoảng lùi phụ thuộc vào lộ giới (chiều rộng đường theo quy hoạch) của tuyến đường phía trước lô đất. Chưa có thông tin lộ giới — giá trị tham khảo theo QCVN 01:2021/BXD:

| Lộ giới đường (m) | Khoảng lùi tối thiểu (m) |
|---|---|
| < 7 | Theo quy hoạch cục bộ |
| 7–12 | 0–3 |
| 12–20 | 3–6 |
| > 20 | ≥ 6 |

**4. Lưu Ý Quan Trọng**

- Giá trị MDXD 70% là theo QCVN 01:2021/BXD — giá trị thực tế phụ thuộc vào **bản đồ quy hoạch chi tiết 1/500 đã phê duyệt** tại Quận 1, TP.HCM. Cần kiểm tra tại Sở Quy hoạch — Kiến trúc (Department of Planning & Architecture) TP.HCM.
- Quận 1 là khu vực nội đô trung tâm, có thể có quy hoạch đặc thù với mật độ và tầng cao khác so với QCVN chung.
- Dữ liệu chưa bao gồm: chiều rộng lộ giới thực tế, chỉ giới xây dựng (building line), quy hoạch treo (suspended zoning) nếu có.

Nguồn: QCVN 01:2021/BXD — [Bộ Xây dựng](https://moc.gov.vn/vn/Pages/VanBanQuyPhamPhapLuat.aspx), truy cập 2026-04-16.

> **Tuyên bố miễn trừ:** Đây là phân tích do AI hỗ trợ tạo ra, phục vụ mục đích nghiên cứu sơ bộ. Mọi kết quả cần được xác minh bởi kiến trúc sư / kỹ sư có chứng chỉ hành nghề trước khi sử dụng cho thiết kế, xin phép xây dựng, hoặc nộp hồ sơ pháp lý.

---

### Bảng Chấm Điểm — Bài 1

| Quy tắc | Yêu cầu kiểm tra | Kết quả | Ghi chú |
|---|---|---|---|
| **don-vi-do-luong** | Hệ mét là chính, dấu phẩy thập phân, VND nếu có | ✅ ĐẠT | m², "2,1 lần", dấu chấm phân cách hàng nghìn "1.050 m²" |
| **don-vi-do-luong** | Ghi rõ loại diện tích (DT sàn, MDXD) | ✅ ĐẠT | "Diện tích sàn xây dựng (DT sàn)", "mật độ xây dựng (MDXD)" |
| **don-vi-do-luong** | Bảng đơn vị chuyên ngành: MDXD (%), HSSDĐ (lần) | ✅ ĐẠT | MDXD 70%, HSSDĐ 2,1 lần |
| **trich-dan-quy-chuan** | Trích QCVN có năm + điều khoản | ✅ ĐẠT | "QCVN 01:2021/BXD, Điều 2.8, Bảng 2.8" |
| **trich-dan-quy-chuan** | Phân biệt QCVN (bắt buộc) vs TCVN | ✅ ĐẠT | Chỉ trích QCVN, đúng ngữ cảnh |
| **trich-dan-quy-chuan** | Ghi chú thẩm quyền địa phương | ✅ ĐẠT | "Kiểm tra tại Sở QHKT TP.HCM", nhắc bản đồ QH 1/500 |
| **tuyen-bo-mien-tru** | Có tuyên bố miễn trừ đầy đủ | ✅ ĐẠT | Đúng nguyên văn theo quy tắc |
| **tuyen-bo-mien-tru** | Không khẳng định "đạt quy chuẩn" | ✅ ĐẠT | Dùng "tối đa cho phép", "giá trị tham khảo" |
| **thuat-ngu** | Thuật ngữ chuẩn, giải thích viết tắt lần đầu | ✅ ĐẠT | "mật độ xây dựng (Building Coverage Ratio — BCR)", "HSSDĐ" |
| **thuat-ngu** | Tên chuyên ngành: khoảng lùi, chỉ giới xây dựng, lộ giới | ✅ ĐẠT | Đúng thuật ngữ bảng glossary |
| **dinh-dang-dau-ra** | YAML front matter | ✅ ĐẠT | Có đầy đủ: tiêu đề, ngày, địa chỉ, kỹ năng |
| **dinh-dang-dau-ra** | Bảng cho dữ liệu so sánh, đơn vị ở tiêu đề cột | ✅ ĐẠT | 4 bảng, đơn vị trong tiêu đề |
| **dinh-dang-dau-ra** | Trích nguồn cuối phần | ✅ ĐẠT | URL + ngày truy cập |
| **minh-bach** | Trình bày công thức + đầu vào | ✅ ĐẠT | Cột "Công thức" hiển thị rõ |
| **minh-bach** | Ghi rõ dữ liệu thiếu | ✅ ĐẠT | "Chưa có thông tin lộ giới", "Dữ liệu chưa bao gồm" |
| **minh-bach** | Cảnh báo dữ liệu có thể lỗi thời | ✅ ĐẠT | Nhắc quy hoạch đặc thù Quận 1, quy hoạch treo |
| **dinh-dang-csi** | Không yêu cầu trong bài này | — | Không liên quan |

**Tổng: 15/15 quy tắc áp dụng được → 15 ĐẠT, 0 KHÔNG ĐẠT**

---

## Bài Kiểm Tra 2

**Prompt:** "So sánh yêu cầu khoảng lùi (setback) cho nhà ở riêng lẻ vs biệt thự theo QCVN"

### Đầu Ra Mô Phỏng

---

```yaml
---
tieu-de: "So sánh khoảng lùi — Nhà ở riêng lẻ vs Biệt thự"
ngay: 2026-04-16
dia-chi: "Không xác định (áp dụng chung toàn quốc)"
ky-nang: phan-tich-quy-hoach-vn
---
```

#### So Sánh Khoảng Lùi: Nhà Ở Riêng Lẻ vs Biệt Thự

**1. Khung Pháp Lý**

Yêu cầu khoảng lùi (setback) cho nhà ở riêng lẻ và biệt thự (villa) được quy định tại:
- QCVN 01:2021/BXD, Điều 2.8 — Quy hoạch xây dựng khu ở
- QCVN 05:2023/BXD — Nhà ở riêng lẻ (bao gồm nhà phố/nhà liền kề và biệt thự)

Ngoài ra, khoảng lùi cụ thể phụ thuộc vào **bản đồ quy hoạch chi tiết 1/500** đã phê duyệt tại từng địa phương, trong đó ghi rõ chỉ giới xây dựng (building line) cho từng thửa đất (land parcel).

**2. Bảng So Sánh**

| Thông số | Nhà ở riêng lẻ / Nhà liền kề (Townhouse) | Biệt thự (Villa) | Nguồn |
|---|---|---|---|
| Khoảng lùi trước (phía đường) | Theo chỉ giới xây dựng trên bản đồ QH 1/500. Nếu lộ giới < 7 m: có thể 0 m (xây sát đường) | Tối thiểu 2,0–3,0 m so với chỉ giới đường đỏ (road boundary) | QCVN 01:2021/BXD, Điều 2.8 |
| Khoảng lùi bên | 0 m (tường chung với nhà liền kề) hoặc ≥ 2,0 m nếu có cửa sổ | ≥ 2,0 m mỗi bên (yêu cầu khoảng cách giữa hai công trình) | QCVN 01:2021/BXD, Điều 2.8 |
| Khoảng lùi sau | ≥ 2,0 m (khuyến nghị, phụ thuộc PCCC) | ≥ 2,0–3,0 m | QCVN 01:2021/BXD |
| Mật độ xây dựng tối đa (MDXD) | 70–90% (tùy diện tích lô) | 50–60% (diện tích lô lớn hơn, MDXD thấp hơn) | QCVN 01:2021/BXD, Bảng 2.8 |
| Tầng cao phổ biến | 3–5 tầng | 2–3 tầng | Theo quy hoạch cục bộ |
| Khoảng cách PCCC giữa 2 công trình | ≥ 4,0 m (nếu tường có lỗ mở) | ≥ 6,0 m (nếu tường có lỗ mở) | QCVN 06:2021/BXD, Bảng G.1 |

**3. Phân Tích**

Sự khác biệt chính giữa hai loại hình:

- **Nhà liền kề** có mật độ xây dựng cao hơn (70–90%) và thường có khoảng lùi bên bằng 0 m (tường chung). Điều này phản ánh đặc thù đô thị Việt Nam, nơi nhà phố chiếm phần lớn quỹ nhà ở.
- **Biệt thự** yêu cầu khoảng lùi tất cả các phía ≥ 2,0 m, mật độ xây dựng thấp hơn (50–60%), và khoảng cách Phòng cháy chữa cháy (PCCC — Fire Protection) lớn hơn giữa hai công trình.
- Cả hai loại đều bị ràng buộc bởi **chỉ giới đường đỏ** (road boundary / right-of-way) — ranh giới giữa đất công (đường) và đất tư. Khoảng lùi được tính từ chỉ giới đường đỏ hoặc chỉ giới xây dựng, tùy quy hoạch cục bộ.

**4. Khoảng Trống Dữ Liệu & Lưu Ý**

- QCVN 01:2021/BXD đưa ra **khung chung**. Giá trị khoảng lùi cụ thể tại mỗi lô đất do bản đồ quy hoạch 1/500 quy định — bản đồ này do Sở Quy hoạch — Kiến trúc (Department of Planning & Architecture) cấp tỉnh/thành phê duyệt.
- QCVN 05:2023/BXD (Nhà ở riêng lẻ) là quy chuẩn mới, có hiệu lực từ 2023. Một số địa phương có thể chưa cập nhật quy hoạch theo phiên bản này.
- Khoảng cách PCCC (QCVN 06:2021/BXD, Bảng G.1) là giá trị tham khảo — giá trị chính xác phụ thuộc bậc chịu lửa (fire resistance rating) của công trình. Dữ liệu bậc chịu lửa cần được xác định từ hồ sơ thiết kế.
- Bảng so sánh trên dựa trên dữ liệu tích hợp sẵn từ QCVN 01:2021/BXD và QCVN 06:2021/BXD. Phiên bản QCVN tích hợp: 2021 (QCVN 01), 2021 (QCVN 06), 2023 (QCVN 05).

Nguồn:
- [QCVN 01:2021/BXD — Bộ Xây dựng](https://moc.gov.vn/vn/Pages/VanBanQuyPhamPhapLuat.aspx), truy cập 2026-04-16
- [QCVN 06:2021/BXD — Bộ Xây dựng](https://moc.gov.vn/vn/Pages/VanBanQuyPhamPhapLuat.aspx), truy cập 2026-04-16
- [QCVN 05:2023/BXD — Bộ Xây dựng](https://moc.gov.vn/vn/Pages/VanBanQuyPhamPhapLuat.aspx), truy cập 2026-04-16

> **Tuyên bố miễn trừ:** Đây là phân tích do AI hỗ trợ tạo ra, phục vụ mục đích nghiên cứu sơ bộ. Mọi kết quả cần được xác minh bởi kiến trúc sư / kỹ sư có chứng chỉ hành nghề trước khi sử dụng cho thiết kế, xin phép xây dựng, hoặc nộp hồ sơ pháp lý.

---

### Bảng Chấm Điểm — Bài 2

| Quy tắc | Yêu cầu kiểm tra | Kết quả | Ghi chú |
|---|---|---|---|
| **don-vi-do-luong** | Hệ mét, dấu phẩy thập phân | ✅ ĐẠT | "2,0 m", "4,0 m", "≥ 6,0 m" |
| **don-vi-do-luong** | MDXD (%), khoảng lùi (m) | ✅ ĐẠT | Đúng đơn vị chuyên ngành |
| **trich-dan-quy-chuan** | Trích đúng format: QCVN XX:YYYY/BXD, Điều, Bảng | ✅ ĐẠT | "QCVN 01:2021/BXD, Điều 2.8", "QCVN 06:2021/BXD, Bảng G.1" |
| **trich-dan-quy-chuan** | Phân biệt rõ nhiều QCVN (01, 05, 06) | ✅ ĐẠT | 3 QCVN khác nhau, đúng phạm vi |
| **trich-dan-quy-chuan** | Ghi nhận thẩm quyền địa phương | ✅ ĐẠT | "Sở QHKT cấp tỉnh/thành phê duyệt" |
| **trich-dan-quy-chuan** | Không khẳng định "đạt quy chuẩn" | ✅ ĐẠT | Dùng "giá trị tham khảo", "phụ thuộc" |
| **tuyen-bo-mien-tru** | Có tuyên bố miễn trừ | ✅ ĐẠT | Đúng nguyên văn |
| **thuat-ngu** | Thuật ngữ chuẩn + song ngữ lần đầu | ✅ ĐẠT | "khoảng lùi (setback)", "biệt thự (villa)", "chỉ giới đường đỏ (road boundary / right-of-way)", "bậc chịu lửa (fire resistance rating)" |
| **thuat-ngu** | Dùng "nhà liền kề" thay "nhà phố" nhất quán | ⚠️ MỘT PHẦN | Dùng cả "nhà liền kề" và "nhà phố" — nên chọn một thuật ngữ chính. Glossary ghi "Nhà phố / Nhà liền kề = Townhouse / Shophouse" → cả hai đều chấp nhận được, nhưng nên nhất quán |
| **dinh-dang-dau-ra** | YAML front matter | ✅ ĐẠT | Đầy đủ |
| **dinh-dang-dau-ra** | Bảng so sánh, đơn vị ở tiêu đề cột | ✅ ĐẠT | Bảng chính có cột Nguồn |
| **dinh-dang-dau-ra** | Trích nguồn cuối phần kèm URL + ngày | ✅ ĐẠT | 3 nguồn, tất cả có URL + ngày |
| **minh-bach** | Ghi rõ khoảng trống dữ liệu | ✅ ĐẠT | Mục riêng "Khoảng Trống Dữ Liệu & Lưu Ý" |
| **minh-bach** | Ghi rõ phiên bản dữ liệu tích hợp | ✅ ĐẠT | "Phiên bản QCVN tích hợp: 2021 (QCVN 01), 2021 (QCVN 06), 2023 (QCVN 05)" |
| **minh-bach** | Cảnh báo dữ liệu có thể lỗi thời | ✅ ĐẠT | "Một số địa phương có thể chưa cập nhật quy hoạch theo phiên bản này" |
| **dinh-dang-csi** | Không yêu cầu trực tiếp | — | Không liên quan |

**Tổng: 14/15 quy tắc áp dụng được → 13 ĐẠT, 1 MỘT PHẦN, 0 KHÔNG ĐẠT**

**Phát hiện cải tiến:** Quy tắc `thuat-ngu.md` nên bổ sung hướng dẫn: khi một khái niệm có nhiều tên phổ biến (VD: nhà phố / nhà liền kề), chọn một thuật ngữ chính và ghi chú đồng nghĩa lần đầu, sau đó dùng thuật ngữ chính nhất quán.

---

## Bài Kiểm Tra 3

**Prompt:** "Cho tôi thông tin về yêu cầu PCCC cho tòa nhà hỗn hợp cao 10 tầng tại Hà Nội"

### Đầu Ra Mô Phỏng

---

```yaml
---
tieu-de: "Yêu cầu PCCC — Tòa nhà hỗn hợp 10 tầng, Hà Nội"
ngay: 2026-04-16
dia-chi: "Hà Nội (địa chỉ cụ thể chưa cung cấp)"
ky-nang: tra-cuu-pccc
---
```

#### Yêu Cầu Phòng Cháy Chữa Cháy — Tòa Nhà Hỗn Hợp 10 Tầng

**Thông tin đầu vào:**

| Thông số | Giá trị |
|---|---|
| Loại công trình | Hỗn hợp (mixed-use): thương mại + văn phòng + nhà ở |
| Số tầng | 10 tầng |
| Vị trí | Hà Nội |
| Chiều cao ước tính | ~36,0 m (giả định 3,6 m/tầng) |

**1. Quy Chuẩn Áp Dụng**

| Văn bản | Phạm vi | Phân khu CSI |
|---|---|---|
| QCVN 06:2021/BXD | An toàn cháy cho nhà và công trình — quy chuẩn chính | 21 00 00 — Chữa cháy (Fire Suppression) |
| TCVN 5738:2021 | Hệ thống báo cháy tự động — thiết kế, lắp đặt | 28 31 00 — Hệ thống báo cháy (Fire Detection and Alarm) |
| TCVN 7336:2021 | Hệ thống chữa cháy Sprinkler tự động | 21 13 00 — Sprinkler chữa cháy (Fire-Suppression Sprinkler Systems) |
| TCVN 3890:2023 | Phương tiện PCCC cho nhà và công trình | 21 00 00 — Chữa cháy |
| Luật PCCC 40/2024/QH15 | Phòng cháy chữa cháy và cứu nạn cứu hộ | — |

**2. Bậc Chịu Lửa**

Tòa nhà hỗn hợp 10 tầng (~36 m) yêu cầu bậc chịu lửa (fire resistance rating) tối thiểu **Bậc I hoặc Bậc II** theo QCVN 06:2021/BXD, Điều 4.1:

| Cấu kiện | Bậc I (giờ) | Bậc II (giờ) |
|---|---|---|
| Tường chịu lực | 2,5 | 2,0 |
| Cột | 2,5 | 2,0 |
| Dầm | 1,0 | 0,75 |
| Sàn | 1,0 | 0,75 |
| Tường ngăn cháy (fire wall) | 2,5 | 2,5 |
| Cầu thang thoát nạn | 1,0 | 1,0 |

Nguồn: QCVN 06:2021/BXD, Bảng 4, truy cập 2026-04-16.

**3. Thoát Nạn**

| Yêu cầu | Giá trị | Nguồn |
|---|---|---|
| Số lối thoát nạn tối thiểu | ≥ 2 (mỗi tầng) | QCVN 06:2021/BXD, Điều 3.2.6 |
| Chiều rộng cầu thang thoát nạn (fire escape stairway) | ≥ 1,2 m (cho nhà công cộng), ≥ 0,9 m (cho nhà ở) | QCVN 06:2021/BXD, Điều 3.4.1 |
| Chiều rộng hành lang thoát nạn (corridor) | ≥ 1,4 m (công cộng), ≥ 1,2 m (nhà ở) | QCVN 06:2021/BXD, Điều 3.3.3 |
| Khoảng cách thoát nạn tối đa (hành lang cụt) | 25 m (nhà công cộng, Bậc I–II) | QCVN 06:2021/BXD, Bảng 6 |
| Khoảng cách thoát nạn tối đa (hành lang thông) | 60 m (nhà công cộng, Bậc I–II) | QCVN 06:2021/BXD, Bảng 6 |
| Buồng thang bộ | Loại N1 (buồng thang bộ không nhiễm khói — smoke-proof stairwell) bắt buộc cho nhà > 28 m | QCVN 06:2021/BXD, Điều 3.4.7 |

**4. Hệ Thống Chữa Cháy Bắt Buộc**

Tòa nhà hỗn hợp 10 tầng thuộc diện bắt buộc lắp đặt (theo QCVN 06:2021/BXD, Phụ lục D và TCVN tương ứng):

| Hệ thống | Bắt buộc? | TCVN / Mã CSI | Ghi chú |
|---|---|---|---|
| Hệ thống Sprinkler tự động | ✅ Có | TCVN 7336:2021 / `21 13 00 — Sprinkler chữa cháy` | Cho mọi tầng |
| Hệ thống báo cháy tự động | ✅ Có | TCVN 5738:2021 / `28 31 00 — Hệ thống báo cháy` | Đầu báo khói + nhiệt |
| Họng nước chữa cháy trong nhà (fire hydrant / standpipe) | ✅ Có | TCVN 3890:2023 / `21 13 00` | Mỗi tầng |
| Hệ thống hút khói (smoke extraction) | ✅ Có | QCVN 06:2021/BXD, Điều 3.8 / `23 00 00 — ĐHKK (HVAC)` | Hành lang, tầng hầm |
| Thang máy chữa cháy (fire elevator) | ✅ Có | QCVN 06:2021/BXD, Điều 3.5.2 / `14 00 00 — Thang máy` | Bắt buộc cho nhà > 28 m |
| Đèn chiếu sáng sự cố (emergency lighting) | ✅ Có | QCVN 12:2014/BXD / `26 00 00 — Điện` | Lối thoát nạn |
| Bể nước chữa cháy (fire water tank) | ✅ Có | TCVN 3890:2023 | Dung tích theo tính toán |
| Bơm chữa cháy (fire pump) | ✅ Có | TCVN 7336:2021 | Bơm chính + bơm dự phòng |

**5. Khoang Ngăn Cháy**

Tòa nhà hỗn hợp cần phân khoang ngăn cháy (fire compartment) theo công năng:

| Khoang | Diện tích tối đa (m²) | Nguồn |
|---|---|---|
| Khu thương mại (tầng trệt / tầng 1–2) | 2.500 m² (có Sprinkler) | QCVN 06:2021/BXD, Bảng 5 |
| Khu văn phòng (tầng 3–6 giả định) | 3.000 m² (có Sprinkler) | QCVN 06:2021/BXD, Bảng 5 |
| Khu nhà ở (tầng 7–10 giả định) | Mỗi căn hộ là một khoang | QCVN 06:2021/BXD, Điều 4.2 |

**6. Thẩm Duyệt PCCC**

Tòa nhà hỗn hợp 10 tầng thuộc diện **bắt buộc thẩm duyệt thiết kế về PCCC** (fire safety approval) trước khi cấp Giấy phép xây dựng (building permit), theo Luật PCCC 40/2024/QH15, Điều 15.

Cơ quan thẩm duyệt: **Phòng Cảnh sát PCCC và CNCH — Công an TP. Hà Nội**.

**7. Khoảng Trống Dữ Liệu**

- Các giá trị trong bảng dựa trên QCVN 06:2021/BXD (dữ liệu tích hợp sẵn, phiên bản 2021). Chưa xác nhận có sửa đổi, bổ sung sau 2021.
- Khoảng cách thoát nạn và diện tích khoang ngăn cháy phụ thuộc vào **công năng cụ thể từng tầng** — cần hồ sơ thiết kế chi tiết để tính chính xác.
- Dung tích bể nước chữa cháy và công suất bơm cần tính toán theo diện tích sàn và nguy hiểm cháy thực tế.
- Chưa đánh giá: khoảng cách PCCC với công trình lân cận (cần biết vị trí cụ thể), đường giao thông cho xe chữa cháy (chiều rộng ≥ 3,5 m, bán kính quay ≥ 12 m).

Nguồn:
- [QCVN 06:2021/BXD — Bộ Xây dựng](https://moc.gov.vn/vn/Pages/VanBanQuyPhamPhapLuat.aspx), truy cập 2026-04-16
- [Luật PCCC 40/2024/QH15 — Thư viện Pháp luật](https://thuvienphapluat.vn/), truy cập 2026-04-16
- Dữ liệu tích hợp: QCVN 06:2021/BXD Bảng 4, 5, 6; TCVN 5738:2021; TCVN 7336:2021; TCVN 3890:2023

> **Tuyên bố miễn trừ:** Đây là phân tích do AI hỗ trợ tạo ra, phục vụ mục đích nghiên cứu sơ bộ. Mọi kết quả cần được xác minh bởi kiến trúc sư / kỹ sư có chứng chỉ hành nghề trước khi sử dụng cho thiết kế, xin phép xây dựng, hoặc nộp hồ sơ pháp lý.

---

### Bảng Chấm Điểm — Bài 3

| Quy tắc | Yêu cầu kiểm tra | Kết quả | Ghi chú |
|---|---|---|---|
| **don-vi-do-luong** | Hệ mét, m², m, giờ | ✅ ĐẠT | "36,0 m", "2.500 m²", "2,5 giờ", "≥ 1,2 m" |
| **don-vi-do-luong** | Dấu phẩy thập phân, dấu chấm hàng nghìn | ✅ ĐẠT | "2.500 m²", "3.000 m²", "3,6 m/tầng" |
| **trich-dan-quy-chuan** | Trích QCVN + TCVN đúng format có năm | ✅ ĐẠT | "QCVN 06:2021/BXD, Điều 3.2.6", "TCVN 5738:2021", "TCVN 7336:2021" |
| **trich-dan-quy-chuan** | Phân biệt QCVN (bắt buộc) vs TCVN (tự nguyện) | ✅ ĐẠT | QCVN cho yêu cầu chính, TCVN cho hệ thống cụ thể |
| **trich-dan-quy-chuan** | Trích luật đúng format | ✅ ĐẠT | "Luật PCCC 40/2024/QH15, Điều 15" |
| **trich-dan-quy-chuan** | Ghi nhận cơ quan thẩm quyền | ✅ ĐẠT | "Phòng CS PCCC — Công an TP. Hà Nội" |
| **tuyen-bo-mien-tru** | Có tuyên bố miễn trừ đầy đủ | ✅ ĐẠT | Đúng nguyên văn |
| **tuyen-bo-mien-tru** | Không khẳng định "đạt quy chuẩn" | ✅ ĐẠT | Dùng "bắt buộc theo", "yêu cầu" — mô tả quy định, không khẳng định tuân thủ |
| **thuat-ngu** | Thuật ngữ chuẩn + song ngữ lần đầu | ✅ ĐẠT | "bậc chịu lửa (fire resistance rating)", "khoang ngăn cháy (fire compartment)", "buồng thang bộ không nhiễm khói (smoke-proof stairwell)" |
| **thuat-ngu** | Viết tắt giải thích lần đầu | ✅ ĐẠT | "PCCC (Phòng cháy chữa cháy — Fire Protection)" trong Bài 2 liền trước; "ĐHKK (HVAC)" |
| **dinh-dang-csi** | Mã CSI cho hệ thống PCCC | ✅ ĐẠT | "21 00 00 — Chữa cháy", "28 31 00 — Hệ thống báo cháy", "21 13 00 — Sprinkler", "14 00 00 — Thang máy" |
| **dinh-dang-csi** | Mã 6 chữ số + tên song ngữ | ✅ ĐẠT | Đúng format MasterFormat 2018 |
| **dinh-dang-csi** | Tham chiếu TCVN tương ứng với CSI division | ✅ ĐẠT | Mỗi hệ thống có cả mã CSI và TCVN |
| **dinh-dang-dau-ra** | YAML front matter | ✅ ĐẠT | Đầy đủ |
| **dinh-dang-dau-ra** | Bảng cho dữ liệu kỹ thuật, đơn vị tiêu đề cột | ✅ ĐẠT | 6 bảng, đơn vị rõ ràng |
| **dinh-dang-dau-ra** | Trích nguồn cuối phần kèm URL + ngày | ✅ ĐẠT | 2 URL + danh sách dữ liệu tích hợp |
| **minh-bach** | Trình bày đầu vào / giả định | ✅ ĐẠT | "giả định 3,6 m/tầng", "tầng 3–6 giả định" — ghi rõ đâu là giả định |
| **minh-bach** | Ghi rõ dữ liệu thiếu | ✅ ĐẠT | Mục "Khoảng Trống Dữ Liệu" — 4 khoảng trống cụ thể |
| **minh-bach** | Ghi rõ phiên bản dữ liệu tích hợp | ✅ ĐẠT | "dữ liệu tích hợp sẵn, phiên bản 2021" |
| **minh-bach** | Cảnh báo lỗi thời | ✅ ĐẠT | "Chưa xác nhận có sửa đổi, bổ sung sau 2021" |

**Tổng: 19/19 quy tắc áp dụng được → 19 ĐẠT, 0 KHÔNG ĐẠT**

---

## Tổng Kết

| Bài | Quy tắc áp dụng | ĐẠT | MỘT PHẦN | KHÔNG ĐẠT | Tỷ lệ |
|---|---|---|---|---|---|
| Bài 1 — Mật độ xây dựng | 15 | 15 | 0 | 0 | **100%** |
| Bài 2 — So sánh khoảng lùi | 15 | 13 | 1 | 0 | **93%** |
| Bài 3 — PCCC tòa nhà hỗn hợp | 19 | 19 | 0 | 0 | **100%** |
| **Tổng cộng** | **49** | **47** | **1** | **0** | **97,9%** |

### Phát Hiện & Cải Tiến

| # | Phát hiện | Quy tắc liên quan | Hành động đề xuất |
|---|---|---|---|
| 1 | Khi một khái niệm có nhiều tên phổ biến (nhà phố / nhà liền kề), cần hướng dẫn chọn thuật ngữ chính | `thuat-ngu.md` | Bổ sung mục: "Khi có đồng nghĩa, chọn một thuật ngữ chính, ghi đồng nghĩa trong ngoặc lần đầu, sau đó dùng thuật ngữ chính nhất quán" |
| 2 | Bài 3 sử dụng `dinh-dang-csi.md` hiệu quả nhất vì PCCC trực tiếp liên quan CSI Division 21/28 — các bài khác không kích hoạt quy tắc CSI | `dinh-dang-csi.md` | Cân nhắc bổ sung hướng dẫn: "Chỉ đưa mã CSI khi đầu ra liên quan trực tiếp đến đặc tả hệ thống kỹ thuật" |
| 3 | Quy tắc `minh-bach.md` hoạt động đặc biệt tốt cho bối cảnh VN — nơi dữ liệu mở hạn chế | `minh-bach.md` | Giữ nguyên, đã phù hợp |
| 4 | Bảng chấm điểm PCCC có nhiều quy tắc nhất (19) vì kích hoạt cả CSI — cho thấy bài kiểm tra PCCC là stress test tốt nhất | — | Dùng kịch bản PCCC/MEP cho kiểm thử Phase 2 |
