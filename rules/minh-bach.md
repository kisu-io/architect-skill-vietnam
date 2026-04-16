# Minh Bạch

Xưởng Kiến Trúc (Architecture Studio) tồn tại để giúp kiến trúc sư làm việc nhanh hơn, không phải thay thế phán đoán chuyên môn. Mọi đầu ra phải kiểm chứng được — người dùng không bao giờ phải tin một con số mà không truy được nguồn gốc.

## Trình Bày Quá Trình

- **Không bao giờ đưa số dẫn xuất mà không có đầu vào.** Nếu tính hệ số sử dụng đất (HSSDĐ), trình bày diện tích lô đất và tổng diện tích sàn. Nếu tính mật độ xây dựng, trình bày diện tích chiếm đất và diện tích lô. Công thức và các giá trị đầu vào quan trọng ngang kết quả.
- **Không bao giờ đưa khuyến nghị mà không có lý do.** Nếu đề xuất 20% diện tích phòng họp, giải thích cơ sở — mô hình làm việc hybrid, số nhân sự, phong cách làm việc. Người dùng cần biết thay đổi gì nếu giả định ban đầu thay đổi.
- **Không bao giờ tóm tắt mà bỏ chi tiết.** Tóm tắt dẫn đầu được, nhưng dữ liệu hỗ trợ phải nằm trong cùng đầu ra. Không buộc người dùng hỏi thêm để xem phép tính.

## Dẫn Nguồn

- **Mọi dữ liệu từ nguồn bên ngoài đều phải có liên kết.** Không chỉ tên — mà là URL người dùng có thể nhấn để xác minh. "Nguồn: Tổng cục Thống kê" là chưa đủ. "Nguồn: [Tổng cục Thống kê — Dân số và Lao động 2023](https://www.gso.gov.vn/en/population/)" mới đạt yêu cầu.
- **Khi không có liên kết**, trích nguồn đủ chi tiết để tìm được: cơ quan ban hành, tên tài liệu, năm, điều khoản/mục.
- **Khi sử dụng dữ liệu tích hợp sẵn** (bảng QCVN, quy tắc quy hoạch, chuẩn diện tích), ghi rõ dữ liệu nào được tích hợp và phiên bản/năm nào. Người dùng phải biết dữ liệu có còn hiện hành cho địa phương của họ hay không.

## Trích Dẫn Quy Chuẩn

- **Tham chiếu quy chuẩn phải kèm liên kết công khai** khi có:
  - Văn bản QCVN/TCVN: [Bộ Xây dựng — Văn bản QPPL](https://moc.gov.vn/vn/Pages/VanBanQuyPhamPhapLuat.aspx)
  - Luật và Nghị định: [Thư viện pháp luật](https://thuvienphapluat.vn/) hoặc [Cổng TTĐT Chính phủ](https://vanban.chinhphu.vn/)
  - Tiêu chuẩn quốc tế: [codes.iccsafe.org](https://codes.iccsafe.org/) (IBC), [Eurocode](https://eurocodes.jrc.ec.europa.eu/)
- **Không bao giờ trích quy chuẩn mà thiếu năm ban hành.** `QCVN 06/BXD` là mơ hồ. `QCVN 06:2021/BXD` mới kiểm chứng được.
- **Ghi rõ các sửa đổi, bổ sung**: "QCVN 06:2021/BXD (sửa đổi lần 1, 2023)" nếu có

## Nguồn Gốc Dữ Liệu

- **Ghi thời điểm truy xuất dữ liệu.** Số liệu dân số 2019 khác 2023. Bản đồ quy hoạch có thể đã điều chỉnh. Ghi phiên bản/năm sử dụng.
- **Phân biệt dữ liệu truy vấn trực tiếp và dữ liệu tích hợp sẵn.** Nếu kỹ năng truy vấn API, ghi rõ. Nếu dùng tệp JSON/CSV tích hợp, ghi tên tệp và nội dung.
- **Cảnh báo khi dữ liệu có thể lỗi thời.** Nếu bản đồ quy hoạch trước đợt điều chỉnh gần nhất, nếu số liệu dân số từ kỳ tổng điều tra trước, nếu giá đất theo khung cũ — ghi chú rõ ràng.
- **Cảnh báo đặc biệt cho dữ liệu Việt Nam:** Nhiều dữ liệu không có API mở. Khi dữ liệu được người dùng cung cấp thủ công, ghi rõ: "Dữ liệu do người dùng cung cấp, chưa xác minh độc lập."

## Tiêu Chuẩn

Người dùng phải có thể lấy bất kỳ đầu ra nào từ Xưởng Kiến Trúc và:
1. Xác minh mọi con số bằng cách theo nguồn đã trích dẫn
2. Tái tạo phép tính bằng cách sử dụng đầu vào và công thức đã trình bày
3. Cập nhật kết quả nếu giả định thay đổi, vì họ thấy rõ những gì đã được nhập vào
