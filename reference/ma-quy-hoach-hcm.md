# Mã Tra Cứu Quy Hoạch TP.HCM

Tệp tham chiếu nhanh cho hệ thống GIS tra cứu quy hoạch TP.HCM (`gisxaydung.tphcm.gov.vn`).

---

## 1. Mã Quận/Huyện (maQuanHuyen)

Dùng trong API tra cứu GIS và dropdown trên cổng tra cứu.

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

**Lưu ý:** Quận 2, 9, Thủ Đức cũ đã sáp nhập thành **TP Thủ Đức** (mã 769) từ 01/01/2021. Trên cổng GIS chỉ còn mã 769.

---

## 2. Mã Phường/Xã (maPhuongXa) — Ví Dụ Quận 7

| Phường | Mã |
|---|---|
| Tân Thuận Đông | 27466 |
| Tân Thuận Tây | 27469 |
| Tân Kiểng | 27472 |
| Tân Hưng | 27475 |
| Bình Thuận | 27478 |
| Tân Quy | 27481 |
| Phú Thuận | 27484 |
| Tân Phú | 27487 |
| Tân Phong | 27490 |
| Phú Mỹ | 27493 |

> Mã phường/xã các quận khác: chọn quận trên GIS → dropdown phường sẽ hiển thị mã tương ứng.

---

## 3. Mã Mục Đích Sử Dụng Đất

Ký hiệu trên bản đồ quy hoạch phân khu TP.HCM.

| Mã | Tên Tiếng Việt | English | Màu sắc (ước lượng) |
|---|---|---|---|
| **KDC** | Đất khu dân cư | Residential | Vàng nhạt / cam |
| **SKC** | Đất cơ sở sản xuất kinh doanh | Commercial / Industrial | Tím / hồng |
| **CTC** | Đất công trình công cộng | Public Facilities | Xanh đậm |
| **DGT** | Đất giao thông | Transportation / Roads | Trắng / xám |
| **DGD** | Đất giáo dục | Education | Xanh lá nhạt |
| **DAN** | Đất an ninh quốc phòng | Defense / Security | Xám đậm |
| **SON** | Đất sông, kênh mương, hồ, thủy lợi | Waterways / Irrigation | Xanh dương |
| **DAQ** | Đất dự án quy hoạch | Planned Project Land | Tùy loại |
| **DKH** | Đất khác | Other | Tùy loại |
| **CX** | Cây xanh / công viên | Green Space / Parks | Xanh lá |

### Phân Loại Chi Tiết Đất Dân Cư

Trên GIS, đất dân cư được chia nhỏ hơn:

| Phân loại | Ý nghĩa |
|---|---|
| Đất ở xây dựng mới | Khu dân cư mới theo quy hoạch |
| Đất ở hiện hữu | Khu dân cư hiện hữu, cải tạo chỉnh trang |
| Đất ở hiện hữu chỉnh trang | Khu dân cư cần cải tạo theo quy hoạch |

---

## 4. Dữ Liệu Trả Về Khi Tra Cứu Thửa Đất

Khi tra cứu thành công (số tờ + số thửa), hệ thống trả về:

### Thông tin thửa đất:
| Trường | Ý nghĩa | Ví dụ |
|---|---|---|
| Phường/Xã | Tên phường (Quận) | Phường Tân Phong, Quận 7 |
| Diện tích | Tổng diện tích thửa đất (m²) | 1.828,5 m² |
| Số hiệu tờ bản đồ | Số tờ bản đồ địa chính | 26 |
| Số thứ tự thửa | Số thửa | 47 |

### Thông tin quy hoạch (có thể nhiều zone trên 1 thửa):
| Trường | Ý nghĩa | Ví dụ |
|---|---|---|
| QĐ phê duyệt | Số quyết định + ngày | 6692/QĐ-UBND ngày 28/12/2012 |
| Tên đồ án | Tên quy hoạch | KĐT Nam TP.HCM tỷ lệ 1/5000 |
| Mục đích sử dụng đất | Loại đất (mã + tên) | Đất ở xây dựng mới |
| Diện tích (m²) | Phần diện tích trong zone | 1.507,96 m² |
| Hệ số sử dụng đất | FAR | (có thể trống ở 1/5000) |
| Tầng cao xây dựng (tầng) | Tầng cao tối đa | (có thể trống ở 1/5000) |
| Mật độ xây dựng TB (%) | BCR trung bình | (có thể trống ở 1/5000) |
| Ký hiệu lô đất | Mã lô trong đồ án | 2 |
| Quy mô dân số | Dân số thiết kế cho khu vực | 10.000 |

**Quan trọng:**
- Một thửa đất có thể nằm trên **nhiều zone** quy hoạch (VD: một phần là DGT, một phần là KDC)
- Trường HSSDĐ, tầng cao, MDXD **thường trống** ở bản đồ 1/5000 — chỉ có ở 1/2000 hoặc 1/500
- Dữ liệu ghi "tính chất tham khảo" — cần xác minh tại Sở QHKT cho mục đích pháp lý

---

## 5. QĐ Phê Duyệt Quy Hoạch Chung Theo Quận

PDF có thể tải từ `qhkt.hochiminhcity.gov.vn/ban-do-quy-hoach.html`.

### Quy Hoạch Chung 1/5000

| Quận/Huyện | Số QĐ | Năm | URL filename |
|---|---|---|---|
| TP.HCM (tổng thể) | 24/QĐ-TTg | — | quyet-dinh-24-qd-ttg-thu-tuong-chinh-phu.pdf |
| Quận 1 | 6790/QĐ-UBND | 1998 | QHC_Quan1_6790_QD_UBND_1998.pdf |
| Quận 2 (nay TP Thủ Đức) | 6707/QĐ-UBND | 29/12/2012 | QHC_Quan2_6707_QD_UBND_29_12_2012_2.pdf |
| Quận 3 | 244/QĐ-UBND | 13/01/2012 | QHC_Quan3_244_QD_UBND_13_01_2012_1.pdf |
| Quận 4 | 5191/QĐ-UBND | 29/11/2008 | QHC_Quan4_5191QD_UBND_29_11_2008_1.pdf |
| Quận 5 | 6786/QĐ-UBND | 1998 | QHC_Quan5_6786_QD_UBND_1998.pdf |
| Quận 6 | 5106/QĐ-UBND | 04/10/2012 | QHC_Quan6_5106_QD_UBND_04_10_2012_1.pdf |
| Quận 7 | 5760/QĐ-UBND | 12/11/2012 | QHC_Quan7_5760_QD_UBND_12_11_2012_1.pdf |
| Quận 8 | 5651/QĐ-UBND | 13/12/2010 | QHC_Quan8_5651_QD_UBND_13_12_2010_1.pdf |
| Quận 9 (nay TP Thủ Đức) | 5758/QĐ-UBND | 12/11/2012 | QHC_Quan9_5758_QD_UBND_12_11_2012_1.pdf |
| Quận 10 | 6011/QĐ-UBND | 26/11/2012 | QHC_Quan10_6011_QD_UBND_26_11_2012_1.pdf |
| Quận 11 | 6179/QĐ-UBND | 04/12/2012 | QHC_Quan11_6179_QD_UBND_4_12_2012_1.pdf |
| Quận 12 | 6706/QĐ-UBND | 29/12/2012 | QHC_Quan12_6706_QD_UBND_29_12_2012_1.pdf |
| Quận Bình Tân | 6012/QĐ-UBND | 26/11/2012 | QHC_BinhTan_6012_QD_UBND_26_11_2012_1.pdf |
| Quận Bình Thạnh | 6014/QĐ-UBND | 26/11/2012 | QHC_BinhThanh_6014_QD_UBND_26_11_2012_1.pdf |
| Quận Gò Vấp | 6705/QĐ-UBND | 28/12/2012 | QHC_GoVap_6705_QD_UBND_28_12_2012_1.pdf |
| Quận Phú Nhuận | 5761/QĐ-UBND | 12/11/2012 | QHC_PhuNhuan_5761_QD_UBND_12_11_2012_1.pdf |
| Quận Tân Bình | 3348/QĐ-UBND | 04/08/2008 | QHC_TanBinh_3348_QD_UBND_04_08_2008_1.pdf |
| Quận Tân Phú | 1980/QĐ-UBND | 05/05/2008 | QHC_TanPhu_1980_QD_UBND_05_05_2008_1.pdf |
| Quận Thủ Đức (nay TP Thủ Đức) | 5759/QĐ-UBND | 12/11/2012 | QHC_ThuDuc_5759_QD_UBND_12_11_2012_1.pdf |
| Huyện Bình Chánh | 6013/QĐ-UBND | 26/11/2012 | QHC_BinhChanh_6013_QD_UBND_26_11_2012_1.pdf |
| Huyện Cần Giờ | 4766/QĐ-UBND | 15/09/2012 | QHC_CanGio_4766_QD_UBND_15_9_2012_1.pdf |
| Huyện Củ Chi | 2645/QĐ-UBND | 23/05/2012 | QHC_CuChi_2645_QD_UBND_23_5_2012_1.pdf |
| Huyện Hóc Môn | 3680/QĐ-UBND | 21/08/2010 | QHC_HocMon_3680_QD_UBND_21_8_2010_1.pdf |
| Huyện Nhà Bè | 6015/QĐ-UBND | 26/11/2012 | QHC_NhaBe_6015_QD_UBND_26_11_2012_1.pdf |

**URL gốc:** `https://qhkt.hochiminhcity.gov.vn/Uploads/Document/Maps/{filename}`

### Quy Hoạch Phân Khu Đặc Biệt

| Khu | Số QĐ | Năm | URL filename |
|---|---|---|---|
| Khu Nam TP.HCM | 6692/QĐ-UBND | 2012 | QHPK_KhuNam_2012_6692_QD_1.pdf |
| Tây Bắc — Khu I (một phần) | 845/QĐ-UBND | 2013 | QHPK_TayBac_2013_845_QD_1.pdf |
| Tây Bắc — Khu II + III | 5045/QĐ-UBND | 2013 | QHPK_TayBac_2013_5045_QD_2.pdf |
| Tây Bắc — Khu V (một phần) | 5333/QĐ-UBND | 2013 | QHPK_TayBac_2013_5333_QD_1.pdf |
| Tây Bắc — Khu VI (một phần) | 5338/QĐ-UBND | 2013 | QHPK_TayBac_2013_5338_QD_1.pdf |
| Tây Bắc — Khu VIII | 5340/QĐ-UBND | 2013 | QHPK_TayBac_2013_5340_QD_1.pdf |
| Tây Bắc — Khu IV + IX | 5384/QĐ-UBND | 2013 | QHPK_TayBac_2013_5384_QD_1.pdf |
| Khu CNC — Giai đoạn 1 | 1028/QĐ-UBND | 2007 | QHPK_CNC_2007_1028_QD_1.pdf |
| Khu CNC — Giai đoạn 2 | 5625/QĐ-UBND | 2009 | QHPK_CNC_2009_5625_QD_1.pdf |
| Nông nghiệp CNC (Củ Chi) | 2189/QĐ-UBND | 2005 | QHPK_CuChi_2005_2189_QD_1.pdf |

---

## 6. Cách Sử Dụng Trong Skill

### Khi người dùng cung cấp địa chỉ TP.HCM:

```
1. Xác định quận/huyện → tra mã quận (bảng 1)
2. Tra QĐ phê duyệt QHC tương ứng (bảng 5)
3. Hướng dẫn tra GIS: gisxaydung.tphcm.gov.vn/quy-hoach-xd-pk/
   → Chọn quận → chọn phường → nhập số tờ/thửa (từ sổ đỏ)
4. Nếu không có số tờ/thửa: zoom vào khu vực trên bản đồ GIS
5. Ghi nhận: mã đất, tầng cao, MDXD, HSSDĐ, QĐ phê duyệt
6. Đối chiếu QCVN 01:2021/BXD khi GIS không có giá trị cụ thể
```

### Khi GIS trả về trường trống:

Nhiều trường (MDXD, HSSDĐ, tầng cao) trống ở bản đồ 1/5000. Khi đó:
1. Ghi "Chưa xác định trong QH 1/5000 — cần tra QH 1/2000 hoặc 1/500"
2. Cung cấp **giá trị tham chiếu QCVN** làm fallback
3. Khuyến cáo tra cứu bổ sung tại Sở QHKT hoặc Phòng QLĐT quận

---

*Nguồn: Sở Quy hoạch – Kiến trúc TP.HCM, truy cập 17/04/2026*
*GIS: gisxaydung.tphcm.gov.vn | Portal: qhkt.hochiminhcity.gov.vn*
