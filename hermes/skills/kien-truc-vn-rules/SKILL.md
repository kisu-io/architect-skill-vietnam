---
name: kien-truc-vn-rules
description: "Quy ước đầu ra áp dụng cho mọi kỹ năng kiến trúc Việt Nam — đơn vị đo, trích dẫn QCVN/TCVN, tuyên bố miễn trừ, định dạng CSI, thuật ngữ chuyên ngành, định dạng bảng/tiêu đề, minh bạch nguồn. Tự động tải trong mọi phiên làm việc."
version: 1.0.0
user-invocable: false
metadata:
  openclaw:
    always: true
    emoji: "📏"
    skillKey: kien-truc-vn-rules
---

# Quy Ước Đầu Ra — Kỹ Năng Kiến Trúc Việt Nam

Quy ước này áp dụng cho **mọi đầu ra** của các kỹ năng kiến trúc Việt Nam (thẩm định, quy hoạch mặt bằng, phân khu, v.v.). Kỹ năng này được cấu hình `metadata.openclaw.always: true` nên nội dung dưới đây được tải vào mọi phiên làm việc.

Tham chiếu tài liệu tra cứu: `{baseDir}/reference/` chứa QCVN tổng hợp, thuật ngữ song ngữ, nguồn dữ liệu, mã quy hoạch HCM.

---

## 1. Đơn Vị Đo Lường

### Hệ đo lường
- Mặc định **hệ mét (SI)**. Ghi kèm đơn vị imperial trong ngoặc khi phục vụ đối tác quốc tế: `120 m² (1,292 SF)`.
- Không trộn hệ đo lường trong cùng một bảng, phép tính, hoặc đoạn văn.

### Diện tích — luôn ghi rõ loại
- **DT sàn** — Diện tích sàn xây dựng (đến mép ngoài tường bao, ~GSF)
- **DT sử dụng** — Diện tích bố trí chức năng được (~USF)
- **DT thuê** — DT sử dụng + phần chung phân bổ (~RSF)
- **DT thông thủy** — Diện tích đo trong lòng tường (~NSF)
- **DT tim tường** — Đo đến tim tường (phổ biến cho chung cư VN)
- Ghi hệ số tổn hao khi quy đổi: "hệ số tổn hao sàn 18%".
- Viết tắt sau lần đầu: "Diện tích sàn xây dựng (DT sàn)" → "DT sàn".

### Kích thước
- Định dạng `D × R × C`, dấu nhân có khoảng trắng: `12,0 m × 10,0 m`.
- ≥1 m: mét, một chữ số thập phân (`3,7 m`). <1 m: milimét (`450 mm`).
- Bản vẽ kỹ thuật: milimét không đơn vị (`2400 × 1200`).

### Số và tiền
- Dấu chấm phân cách hàng nghìn: `1.250 m²`. Dấu phẩy thập phân: `12,5 m`.
- Tiền: mặc định **VND**. `1.500.000 VND` hoặc `1,5 triệu VND`. Kèm USD khi có yếu tố quốc tế.

### Đơn vị chuyên ngành
- Diện tích đất: m² / ha (1 ha = 10.000 m²)
- Mật độ xây dựng (MDXD): %
- Hệ số sử dụng đất (HSSDĐ): lần (~FAR)
- Tầng cao: tầng. Chiều cao công trình: m (từ cos ±0.000 đến đỉnh mái).
- Khoảng lùi, lộ giới: m. Tải trọng: kN/m² (TCVN 2737:1995). Bê tông: MPa (B25 = 25 MPa).

---

## 2. Trích Dẫn Quy Chuẩn

### Định dạng bắt buộc
- Luôn ghi năm ban hành: `QCVN 06:2021/BXD, Điều 3.2.1` — **không** ghi `QCVN 06/BXD`.
- Cấu trúc: `[Mã]:[Năm]/[Cơ quan], Điều [X], Khoản [Y]`.
- Bảng: `QCVN 06:2021/BXD, Bảng 4`. Phụ lục: `Phụ lục A, Mục A.3`.
- Luật: `Luật Xây dựng 50/2014/QH13, Điều 89, Khoản 1`.
- Nghị định: `Nghị định 15/2021/NĐ-CP, Điều 42`.
- Thông tư: `Thông tư 15/2016/TT-BXD, Điều 7`.

### Phân biệt QCVN / TCVN / Luật
| Loại | Tính chất | Ghi chú |
|---|---|---|
| **QCVN** | Bắt buộc — quy chuẩn kỹ thuật quốc gia | Phải tuân thủ |
| **TCVN** | Tự nguyện — tiêu chuẩn quốc gia | Phương pháp đạt QCVN |
| **Luật / NĐ / TT** | Văn bản pháp luật | Khung pháp lý cao nhất |

Không bao giờ ghi chung "tiêu chuẩn" mà không phân loại. Tham khảo bảng QCVN/TCVN thường gặp tại `{baseDir}/reference/qcvn-tong-hop.md`.

### Thẩm quyền địa phương
- Quy hoạch được phê duyệt cấp tỉnh/thành: Sở Xây dựng / Sở QHKT.
- Giấy phép XD do UBND quận/huyện hoặc Sở XD cấp tùy quy mô.
- Luôn ghi chú: "Kiểm tra quy hoạch chi tiết 1/500 đã phê duyệt tại địa phương".
- Không khẳng định "đạt quy chuẩn" — ghi "phù hợp với QCVN [X]:2021/BXD, Điều [Y] theo đánh giá sơ bộ".

---

## 3. Tuyên Bố Miễn Trừ

Mọi đầu ra có phân tích quy chuẩn, giả định kết cấu, diễn giải quy hoạch, hoặc tính toán an toàn sinh mạng **phải kết thúc bằng**:

> **Tuyên bố miễn trừ:** Đây là phân tích do AI hỗ trợ tạo ra, phục vụ mục đích nghiên cứu sơ bộ. Mọi kết quả cần được xác minh bởi kiến trúc sư / kỹ sư có chứng chỉ hành nghề trước khi sử dụng cho thiết kế, xin phép xây dựng, hoặc nộp hồ sơ pháp lý.

### Quy tắc ngôn ngữ
- Không nói "đạt quy chuẩn" → "theo đánh giá sơ bộ, phù hợp với [mã quy chuẩn, điều khoản]".
- Không nói "tuân thủ QCVN" → "dựa trên [QCVN X, Điều Y], có vẻ đáp ứng yêu cầu".
- Không nói "không có vi phạm" → "không phát hiện vi phạm trong phạm vi dữ liệu được rà soát".
- Không trình bày AI như thay thế cho bản vẽ có dấu, tính toán ký tên, hoặc thẩm duyệt chuyên môn.
- Không đưa tư vấn pháp lý về quyền sử dụng đất, tranh chấp, chuyển nhượng.

### Khi nào đính kèm
- Phân tích quy hoạch và khối tích xây dựng.
- Tính toán MDXD, HSSDĐ.
- Kiểm tra tuân thủ QCVN (PCCC, năng lượng, tiếp cận).
- Giả định kết cấu hoặc MEP.
- Đánh giá rủi ro môi trường, phân tích pháp lý đất đai.

Bỏ qua cho: nghiên cứu sản phẩm, slide trình bày, bảng màu, chuyển đổi dữ liệu (CSV/Excel).

### Chứng chỉ hành nghề VN
- Kiến trúc sư hành nghề phải có **Chứng chỉ hành nghề hoạt động xây dựng** theo Nghị định 15/2021/NĐ-CP.
- Chủ nhiệm đồ án: hạng I hoặc II tùy quy mô. Bản vẽ thiết kế phải do người có chứng chỉ phù hợp ký và đóng dấu.

---

## 4. Định Dạng CSI

### MasterFormat 2018
- Mã 6 chữ số có khoảng trắng: `09 29 00 — Tấm thạch cao (Gypsum Board)`.
- Không viết `092900`, `09-29-00`, `09.29.00`.
- Luôn kèm tên phần sau em dash. Ghi song ngữ Việt-Anh khi cần.

### Phân khu chính
`01` Yêu cầu chung · `03` Bê tông · `04` Xây gạch · `05` Kim loại · `06` Gỗ/nhựa/composite · `07` Cách nhiệt & chống thấm · `08` Cửa/lỗ mở · `09` Hoàn thiện · `10` Hạng mục đặc biệt · `21` Chữa cháy · `22` Cấp thoát nước · `23` HVAC · `26` Điện · `31` Nền móng · `32` Cảnh quan · `33` Hạ tầng kỹ thuật.

### Cấu trúc ba phần
Phần 1 Tổng quát (tham chiếu QCVN/TCVN + quốc tế, shop drawings, QA) · Phần 2 Sản phẩm (nhà sản xuất VN + quốc tế, vật liệu) · Phần 3 Thi công (chuẩn bị, lắp đặt, vệ sinh).

### Tham chiếu TCVN tương ứng (rút gọn)
- 03 Bê tông → TCVN 5574:2018, TCVN 4453:1995
- 05 Thép → TCVN 5575:2012
- 07 Chống thấm → TCVN 9065:2012, TCVN 5718:1993
- 21 PCCC → QCVN 06:2021/BXD, TCVN 5738:2021
- 23 ĐHKK → QCVN 09:2017/BXD
- 26 Điện → QCVN 12:2014/BXD, TCVN 9206:2012

Luôn tham chiếu phần bằng mã đầy đủ: "Xem Phần 07 92 00 — Keo chèn khe". Không dùng tham chiếu mơ hồ.

---

## 5. Thuật Ngữ Chuyên Ngành

### Thuật ngữ ưu tiên (dùng cái bên trái, tránh cái bên phải)
- chương trình không gian (không: danh sách phòng)
- liền kề / tiếp giáp (không: gần, ở cạnh)
- giao thông / lưu thông (không: hành lang, lối đi)
- thoát nạn / lối thoát hiểm (không: lối ra)
- vỏ bao che (không: hoàn thiện bên ngoài)
- đồ gỗ lắp đặt (không: tủ kệ đóng sẵn)
- cơ điện (M&E) (không: điện nước)
- mật độ xây dựng / hệ số sử dụng đất / khoảng lùi / chỉ giới xây dựng / chỉ giới đường đỏ / cos ±0.000

### Quy tắc viết tắt
- Giải thích lần đầu, sau đó viết tắt: "Diện tích sàn xây dựng (DT sàn)" → "DT sàn".
- Không giả định người đọc hiểu viết tắt (kể cả PCCC).
- Viết tắt tiếng Anh phổ biến giữ nguyên nếu thông dụng tại VN: HVAC, MEP, BIM, CAD, FF&E.

### Tên vật liệu
- Tên tiêu chuẩn ngành: "tấm thạch cao" không "la phông thạch cao".
- Ghi song ngữ khi phù hợp: "gạch không nung (gạch bê tông nhẹ / AAC)".
- Viết thường tên chung, viết hoa tên thương hiệu khi dùng.

### Quy tắc số trong văn
- Một đến chín: chữ. Từ 10: chữ số. Trong bảng/kích thước/kỹ thuật: luôn dùng chữ số.
- `4 m²`, `6 md`, `3 tầng`. "tầng 1" (không "tầng một").

Bảng thuật ngữ song ngữ đầy đủ: `{baseDir}/reference/thuat-ngu-song-ngu.md`.

---

## 6. Định Dạng Đầu Ra

### Bảng
- Dùng bảng cho mọi dữ liệu so sánh (sản phẩm, kịch bản, yêu cầu quy chuẩn, diện tích).
- Đơn vị trong tiêu đề cột, không lặp trong ô: `Diện tích (m²)` → giá trị `1.250`.
- Căn phải cột số, trái cột chữ. Có hàng tổng kết khi phù hợp.
- Bảng diện tích phải ghi rõ loại (DT sàn, DT sử dụng, DT thông thủy).

### Tiêu đề
- Phân cấp rõ, mô tả: "Yêu cầu thoát nạn — Tầng 2" (không "Mục 3").
- Đánh số tiêu đề chỉ với đặc tả kỹ thuật hoặc báo cáo có tham chiếu chéo.

### Trích nguồn
- Dân số: "Nguồn: Tổng cục Thống kê, Niên giám Thống kê 2023"
- Quy hoạch: "Nguồn: Sở QHKT [tỉnh/thành], Bản đồ QH 1/2000 phê duyệt [năm]"
- Khí hậu: "Nguồn: Tổng cục KTTV, Số liệu khí hậu 1991–2020"
- Đất đai: "Nguồn: Sở TNMT [tỉnh/thành]"
- GIS: "Nguồn: OpenStreetMap Vietnam, truy cập [ngày]"
- Đặt nguồn ở cuối mỗi phần hoặc chú thích — không xen giữa từng câu.

### Tệp đầu ra
- Tên tệp mô tả: `quan-2-phan-tich-quy-hoach.md` không `output.md`.
- Markdown (`.md`) cho báo cáo; HTML cho đầu ra tương tác (3D, slide, dashboard).
- YAML front matter cho báo cáo:

```yaml
---
tieu-de: "Phân tích quy hoạch — 123 Nguyễn Huệ, Quận 1, TP.HCM"
ngay: 2026-04-16
dia-chi: "123 Nguyễn Huệ, Phường Bến Nghé, Quận 1, TP.HCM"
ky-nang: phan-tich-quy-hoach-vn
---
```

### Ngôn ngữ
- Mặc định **tiếng Việt** cho mọi đầu ra.
- Thuật ngữ kỹ thuật quốc tế trong ngoặc lần đầu: "mật độ xây dựng (Building Coverage Ratio)".
- Mã quy chuẩn giữ ký hiệu gốc: QCVN, TCVN, ASTM, ISO.
- Địa chỉ theo thứ tự VN: [Số nhà] [Tên đường], [Phường/Xã], [Quận/Huyện], [Tỉnh/Thành phố].

---

## 7. Minh Bạch

Người dùng không bao giờ phải tin một con số mà không truy được nguồn gốc.

### Trình bày quá trình
- **Không đưa số dẫn xuất mà không có đầu vào.** Tính HSSDĐ → trình bày DT lô đất + tổng DT sàn. Tính MDXD → trình bày DT chiếm đất + DT lô.
- **Không đưa khuyến nghị mà không có lý do.** Nếu đề xuất 20% phòng họp, giải thích cơ sở (mô hình hybrid, số nhân sự, phong cách làm việc).
- **Không tóm tắt mà bỏ chi tiết.** Tóm tắt đầu được; dữ liệu hỗ trợ phải cùng nằm trong đầu ra.

### Dẫn nguồn
- **Mọi dữ liệu bên ngoài phải có liên kết.** URL có thể nhấn. "Nguồn: Tổng cục Thống kê" chưa đủ → "Nguồn: [Tổng cục Thống kê — Dân số và Lao động 2023](https://www.gso.gov.vn/en/population/)".
- Khi không có liên kết: trích đủ chi tiết để tìm được (cơ quan, tên tài liệu, năm, điều/mục).
- Với dữ liệu tích hợp sẵn: ghi rõ tệp và phiên bản/năm.

### Trích dẫn quy chuẩn
- Kèm liên kết công khai khi có:
  - QCVN/TCVN: [Bộ Xây dựng — Văn bản QPPL](https://moc.gov.vn/vn/Pages/VanBanQuyPhamPhapLuat.aspx)
  - Luật/NĐ: [Thư viện pháp luật](https://thuvienphapluat.vn/), [Cổng TTĐT Chính phủ](https://vanban.chinhphu.vn/)
- Không bao giờ trích quy chuẩn thiếu năm ban hành.

### Nguồn gốc dữ liệu
- Ghi thời điểm truy xuất. Phân biệt dữ liệu truy vấn trực tiếp và dữ liệu tích hợp sẵn.
- Cảnh báo khi dữ liệu có thể lỗi thời (bản đồ trước điều chỉnh, dân số kỳ cũ, khung giá cũ).
- Dữ liệu người dùng cung cấp thủ công: ghi rõ "Dữ liệu do người dùng cung cấp, chưa xác minh độc lập."

### Tiêu chuẩn
Người dùng phải có thể: (1) xác minh mọi con số qua nguồn đã trích; (2) tái tạo phép tính bằng đầu vào + công thức; (3) cập nhật kết quả khi giả định thay đổi.

---

## Tài Liệu Tham Chiếu

- `{baseDir}/reference/qcvn-tong-hop.md` — bảng tra QCVN/TCVN chính
- `{baseDir}/reference/thuat-ngu-song-ngu.md` — 234 thuật ngữ song ngữ, 12 phân loại
- `{baseDir}/reference/nguon-du-lieu.md` — nguồn dữ liệu Việt Nam + cách xử lý giới hạn
- `{baseDir}/reference/ma-quy-hoach-hcm.md` — bảng tra mã quy hoạch TP.HCM (quận/phường/chức năng)
