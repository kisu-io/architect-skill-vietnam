---
name: bao-cao-tong-hop
description: "Báo cáo thẩm định tổng hợp — chạy tất cả kỹ năng thẩm định (GPXD, vi phạm, đất đai, quy hoạch, di tích, PCCC) và tổng hợp thành một báo cáo duy nhất."
allowed-tools:
  - WebSearch
  - WebFetch
  - Write
  - Edit
  - Read
  - Bash
user-invocable: true
---

# /bao-cao-tong-hop — Báo Cáo Thẩm Định Tổng Hợp

Chạy toàn bộ quy trình thẩm định cho một công trình hoặc lô đất, tổng hợp kết quả thành một báo cáo duy nhất. Tương đương skill `nyc-property-report` trong bản gốc.

## Sử Dụng

```
/bao-cao-tong-hop [địa chỉ + mô tả công trình dự kiến]
```

Ví dụ:
- `/bao-cao-tong-hop 88 Nguyễn Huệ, Q1, TP.HCM — dự kiến tòa nhà VP 20 tầng`
- `/bao-cao-tong-hop Lô A5, KĐT Ecopark, Hưng Yên — biệt thự 3 tầng`

## Khi Bắt Đầu

Hỏi: **địa chỉ + loại công trình dự kiến + quy mô (tầng, diện tích)**.

Hỏi thêm: "Bạn có tài liệu nào sẵn có không? (Bản đồ QH 1/500, sổ đỏ, hồ sơ GPXD hiện tại)" — để biết dữ liệu nào cần tra cứu, dữ liệu nào đã có.

Sau đó bắt đầu — không hỏi thêm.

## Quy Trình

Chạy 6 module thẩm định song song (hoặc tuần tự nếu cần):

1. **`/tra-cuu-quy-hoach`** → Tình trạng quy hoạch, quy hoạch treo, điều chỉnh
2. **`/tra-cuu-dat-dai`** → Giá đất, pháp lý đất đai
3. **`/tra-cuu-giay-phep-xd`** → Quy trình cấp GPXD, hồ sơ yêu cầu
4. **`/tra-cuu-vi-pham-xd`** → Vi phạm xây dựng hiện hữu
5. **`/tra-cuu-di-tich`** → Di tích, di sản, khu bảo tồn
6. **`/tra-cuu-pccc`** → Yêu cầu PCCC cho công trình dự kiến

Sau khi có kết quả từ tất cả module, **tổng hợp** — không chỉ ghép nối.

## Tổng Hợp

Viết phần tổng hợp bao gồm:

### Đánh Giá Nhanh (Executive Summary)

Bảng traffic-light cho từng hạng mục:

| Hạng mục | Tình trạng | Ghi chú |
|---|---|---|
| Quy hoạch | 🟢 / 🟡 / 🔴 | [1 dòng] |
| Pháp lý đất đai | 🟢 / 🟡 / 🔴 | [1 dòng] |
| Giấy phép XD | 🟢 / 🟡 / 🔴 | [1 dòng] |
| Vi phạm XD | 🟢 / 🟡 / 🔴 | [1 dòng] |
| Di tích / Di sản | 🟢 / 🟡 / 🔴 | [1 dòng] |
| PCCC | 🟢 / 🟡 / 🔴 | [1 dòng] |

Quy ước: 🟢 = Thuận lợi / Không phát hiện vấn đề, 🟡 = Cần kiểm tra thêm / Có điều kiện, 🔴 = Rủi ro cao / Phát hiện vấn đề

### Cơ Hội & Rủi Ro

- **Cơ hội:** Điểm thuận lợi cho dự án (quy hoạch phù hợp, hạ tầng tốt, không vi phạm)
- **Rủi ro:** Vấn đề cần giải quyết trước khi tiến hành (quy hoạch treo, vi phạm, di tích)
- **Khuyến nghị:** 3–5 hành động tiếp theo cụ thể

### Kết Nối Chéo

Phân tích mối liên hệ giữa các hạng mục:
- Di tích + Quy hoạch: khu bảo tồn ảnh hưởng đến tầng cao cho phép
- PCCC + Quy mô: chiều cao > 28 m kích hoạt yêu cầu PCCC đặc biệt
- Đất đai + Quy hoạch: đất nông nghiệp trong vùng quy hoạch đô thị = cần chuyển mục đích

## Định Dạng Đầu Ra

Ghi vào: `./bao-cao-tham-dinh-[dia-chi-slug].md`

```markdown
---
tieu-de: "Báo cáo thẩm định tổng hợp — [Địa chỉ]"
ngay: [YYYY-MM-DD]
dia-chi: "[Địa chỉ đầy đủ]"
ky-nang: bao-cao-tong-hop
---

# Báo Cáo Thẩm Định Tổng Hợp — [Địa Chỉ]

> **Ngày:** [YYYY-MM-DD] | **Công trình dự kiến:** [Mô tả]

## Đánh Giá Nhanh
[Bảng traffic-light]

## Cơ Hội & Rủi Ro
[Phân tích tổng hợp]

## Khuyến Nghị
[3–5 hành động cụ thể]

---

## 1. Tình Trạng Quy Hoạch
[Kết quả từ /tra-cuu-quy-hoach]

## 2. Pháp Lý Đất Đai
[Kết quả từ /tra-cuu-dat-dai]

## 3. Giấy Phép Xây Dựng
[Kết quả từ /tra-cuu-giay-phep-xd]

## 4. Vi Phạm Xây Dựng
[Kết quả từ /tra-cuu-vi-pham-xd]

## 5. Di Tích & Di Sản
[Kết quả từ /tra-cuu-di-tich]

## 6. Yêu Cầu PCCC
[Kết quả từ /tra-cuu-pccc]

---

## Nguồn Tổng Hợp
[Tất cả nguồn từ 6 module]

## Khoảng Trống & Lưu Ý
[Tổng hợp dữ liệu thiếu từ tất cả module]
```

## Quy Tắc

- **Tổng hợp, không ghép nối.** Phần đầu phải là phân tích tổng hợp, không phải bản sao 6 báo cáo.
- **Traffic-light trung thực.** 🔴 chỉ khi thực sự phát hiện vấn đề, 🟡 khi thiếu dữ liệu.
- **Tuyên bố miễn trừ bắt buộc — ĐẶT Ở ĐẦU VÀ CUỐI** (vì đây là tài liệu có thể gửi cho khách hàng).
