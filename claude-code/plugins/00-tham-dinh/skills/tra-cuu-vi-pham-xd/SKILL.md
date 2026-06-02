---
name: tra-cuu-vi-pham-xd
description: "Tra cứu vi phạm trật tự xây dựng — xây dựng không phép, sai phép, lấn chiếm, vi phạm quy hoạch tại Việt Nam."
allowed-tools:
  - WebSearch
  - WebFetch
  - Write
  - Read
user-invocable: true
---

# /tra-cuu-vi-pham-xd — Tra Cứu Vi Phạm Xây Dựng

Tra cứu thông tin vi phạm trật tự xây dựng cho một công trình hoặc khu vực, bao gồm xây dựng không phép, sai phép, lấn chiếm, và vi phạm quy hoạch.

## Sử Dụng

```
/tra-cuu-vi-pham-xd [địa chỉ]
```

## Khi Bắt Đầu

Hỏi **địa chỉ cụ thể** hoặc **khu vực** cần tra cứu. Sau đó nghiên cứu.

## Quy Trình

### 1. Web Search

Tìm kiếm thông tin vi phạm từ các nguồn chính thống:
- `"vi phạm xây dựng" + "[địa chỉ]" + "[quận]"`
- `"xử phạt xây dựng" + "[địa chỉ]"`
- Website Thanh tra Sở Xây dựng tỉnh/thành
- Báo chí chính thống (Tuổi Trẻ, Thanh Niên, VnExpress — mục đô thị/pháp luật)

### 2. Phân Loại Vi Phạm

| Loại vi phạm | Mô tả | Chế tài tham khảo |
|---|---|---|
| Xây dựng không phép | Xây mới không có GPXD | NĐ 16/2022/NĐ-CP, Điều 15–16 |
| Xây dựng sai phép | Sai thiết kế, vượt tầng, vượt MDXD | NĐ 16/2022/NĐ-CP, Điều 15–16 |
| Lấn chiếm | Xây trên đất công, lấn chỉ giới | NĐ 16/2022/NĐ-CP |
| Vi phạm PCCC | Thiếu hệ thống PCCC, chặn lối thoát | Luật PCCC 40/2024/QH15 |
| Vi phạm quy hoạch | Sử dụng sai mục đích đất | Luật Đất đai 2024 |

### 3. Đầu Ra

```markdown
---
tieu-de: "Tra cứu vi phạm xây dựng — [Địa chỉ]"
ngay: [YYYY-MM-DD]
ky-nang: tra-cuu-vi-pham-xd
---

# Tra Cứu Vi Phạm Xây Dựng — [Địa Chỉ]

## Kết Quả
| # | Loại vi phạm | Mô tả | Nguồn | Ngày |
|---|---|---|---|---|

## Chế Tài Tham Khảo
[Mức phạt theo NĐ 16/2022/NĐ-CP]

## Nguồn
## Khoảng Trống & Lưu Ý
- Dữ liệu vi phạm VN không có cơ sở dữ liệu mở — kết quả dựa trên web search
```

## Quy Tắc

- **Ghi rõ nguồn cho từng vi phạm.** URL bài báo hoặc văn bản xử phạt.
- **Nếu không tìm thấy:** "Không tìm thấy thông tin vi phạm trong phạm vi tra cứu trực tuyến. Khuyến nghị kiểm tra tại Thanh tra Sở Xây dựng [tỉnh/thành]."
- **Tuyên bố miễn trừ bắt buộc.**
