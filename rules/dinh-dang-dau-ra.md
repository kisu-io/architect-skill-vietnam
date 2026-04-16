# Định Dạng Đầu Ra

Các quy ước này quy định cách cấu trúc và trình bày đầu ra của kỹ năng.

## Bảng

- Sử dụng bảng cho **mọi dữ liệu so sánh**: so sánh sản phẩm, phân tích kịch bản, yêu cầu quy chuẩn, bảng kê diện tích
- Ghi đơn vị trong tiêu đề cột, không lặp trong mỗi ô: `Diện tích (m²)` với giá trị `1.250` — không ghi `1.250 m²` trong từng hàng
- Căn phải cột số; căn trái cột chữ
- Luôn có hàng tổng hoặc tổng kết khi phù hợp
- Bảng diện tích phải ghi rõ loại diện tích (DT sàn, DT sử dụng, DT thông thủy)

## Tiêu Đề

- Cấu trúc đầu ra với tiêu đề phân cấp rõ ràng, phù hợp với quy cách tài liệu chuyên nghiệp
- Dùng tiêu đề mô tả, không chung chung: "Yêu cầu thoát nạn — Tầng 2" không phải "Mục 3"
- Đánh số tiêu đề chỉ khi đầu ra là đặc tả kỹ thuật hoặc báo cáo có tham chiếu chéo

## Trích Dẫn Nguồn

- Trích nguồn cho mọi dữ liệu từ cơ sở dữ liệu hoặc API bên ngoài:
  - Dữ liệu dân số: "Nguồn: Tổng cục Thống kê, Niên giám Thống kê 2023"
  - Dữ liệu quy hoạch: "Nguồn: Sở QHKT [tỉnh/thành], Bản đồ quy hoạch 1/2000 phê duyệt [năm]"
  - Dữ liệu khí hậu: "Nguồn: Tổng cục KTTV, Số liệu khí hậu 1991–2020"
  - Dữ liệu đất đai: "Nguồn: Sở TNMT [tỉnh/thành], [loại dữ liệu]"
  - Dữ liệu GIS: "Nguồn: OpenStreetMap Vietnam, truy cập [ngày]" hoặc "Nguồn: HCMGIS OpenData"
- Đặt nguồn ở cuối mỗi phần hoặc dạng chú thích — không xen giữa từng câu

## Tệp Đầu Ra

- Khi kỹ năng ghi tệp, dùng tên tệp mô tả: `quan-2-phan-tich-quy-hoach.md` không phải `output.md`
- Mặc định dùng markdown (`.md`) cho báo cáo văn bản
- Dùng HTML chỉ cho đầu ra tương tác hoặc trực quan (mô hình 3D, slide, dashboard)
- Đặt khối YAML front matter trong báo cáo markdown:

```yaml
---
tieu-de: "Phân tích quy hoạch — 123 Nguyễn Huệ, Quận 1, TP.HCM"
ngay: 2026-04-16
dia-chi: "123 Nguyễn Huệ, Phường Bến Nghé, Quận 1, TP.HCM"
ky-nang: phan-tich-quy-hoach-vn
---
```

## Danh Sách

- Dùng gạch đầu dòng cho mục không thứ tự (vật liệu, đặc điểm, nhận xét)
- Dùng danh sách đánh số chỉ cho bước tuần tự hoặc xếp hạng
- Giữ các mục song song về ngữ pháp: tất cả bắt đầu bằng động từ, hoặc tất cả bắt đầu bằng danh từ

## Ngôn Ngữ

- **Mặc định: tiếng Việt** cho mọi đầu ra
- Thuật ngữ kỹ thuật quốc tế ghi kèm trong ngoặc khi lần đầu xuất hiện: "mật độ xây dựng (Building Coverage Ratio)"
- Mã quy chuẩn giữ nguyên ký hiệu gốc: QCVN, TCVN, ASTM, ISO
- Tên riêng địa danh: dùng tên chính thức tiếng Việt có dấu đầy đủ
- Địa chỉ: theo thứ tự Việt Nam: [Số nhà] [Tên đường], [Phường/Xã], [Quận/Huyện], [Tỉnh/Thành phố]
