---
name: tra-cuu-quy-hoach
description: "Tra cứu tình trạng quy hoạch — kiểm tra lô đất có nằm trong quy hoạch treo, dự án thu hồi, hoặc điều chỉnh quy hoạch không."
allowed-tools:
  - WebSearch
  - WebFetch
  - Write
  - Read
user-invocable: true
---

# /tra-cuu-quy-hoach — Tra Cứu Tình Trạng Quy Hoạch

Kiểm tra tình trạng quy hoạch của lô đất: quy hoạch treo (suspended zoning), dự án thu hồi đất, điều chỉnh quy hoạch gần đây, và tình trạng phê duyệt bản đồ quy hoạch 1/500.

## Sử Dụng

```
/tra-cuu-quy-hoach [địa chỉ]
```

## Khi Bắt Đầu

Hỏi **địa chỉ + tỉnh/thành phố**. Sau đó nghiên cứu.

## Quy Trình

### 1. Kiểm Tra Cổng Quy Hoạch Online

Truy cập cổng tra cứu quy hoạch của tỉnh/thành (nếu có):
- TP.HCM: `quyhoach.tphcm.gov.vn`
- Hà Nội: `quyhoach.hanoi.vn`
- Đà Nẵng: `quyhoach.danang.gov.vn`

### 2. Tra Cứu Quy Hoạch Treo

Web search: `"quy hoạch treo" + "[địa chỉ/khu vực]"` hoặc `"thu hồi đất" + "[khu vực]"`

Quy hoạch treo là khu vực đã có quyết định quy hoạch nhưng chưa triển khai, hạn chế quyền xây dựng và chuyển nhượng. Theo Luật Quy hoạch 2017, quy hoạch treo quá 3 năm phải được xem xét điều chỉnh hoặc hủy bỏ.

### 3. Tra Cứu Điều Chỉnh Gần Đây

Web search: `"điều chỉnh quy hoạch" + "[khu vực]" + "[tỉnh/thành]" + [năm gần nhất]`

Kiểm tra:
- Có quyết định điều chỉnh quy hoạch cục bộ nào ảnh hưởng đến khu vực không
- Thay đổi chức năng đất, mật độ, tầng cao
- Dự án mới được phê duyệt lân cận (có thể thay đổi hạ tầng)

### 4. Đầu Ra

```markdown
---
tieu-de: "Tra cứu tình trạng quy hoạch — [Địa chỉ]"
ngay: [YYYY-MM-DD]
ky-nang: tra-cuu-quy-hoach
---

# Tra Cứu Tình Trạng Quy Hoạch — [Địa Chỉ]

## Tình Trạng

| Hạng mục | Kết quả | Nguồn |
|---|---|---|
| Quy hoạch treo | [Có / Không / Chưa xác định] | |
| Thu hồi đất | [Có / Không / Chưa xác định] | |
| Điều chỉnh QH gần đây | [Có / Không] | |
| QH 1/500 phê duyệt | [Có / Chưa / Không rõ] | |

## Chi Tiết
[Mô tả tình trạng, quyết định liên quan]

## Nguồn
## Khoảng Trống & Lưu Ý
```

## Quy Tắc

- **Quy hoạch treo là rủi ro cao.** Nếu phát hiện, cảnh báo rõ ràng: ảnh hưởng đến quyền xây dựng, chuyển nhượng, giá trị.
- **Tuyên bố miễn trừ bắt buộc.**
