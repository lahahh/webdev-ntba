# Phân tích bố cục trang chủ VNU-IS và ánh xạ Bootstrap 5

- **Trang được khảo sát:** https://www.is.vnu.edu.vn/
- **Ngày ghi nhận:** 06/10/2026
- **Mục tiêu:** mô tả bố cục theo thứ tự từ ngoài vào trong, sau đó đề xuất hệ thống lưới, component và utility Bootstrap 5 để dựng nhanh.

> Đây là bản phân tích nội dung và cấu trúc hiển thị, không phải xác nhận website gốc đang dùng Bootstrap. Banner, tin tức, menu con và popup có thể thay đổi theo dữ liệu/chiến dịch. Các menu cấp hai cần mở trực tiếp trên trang để kiểm kê chi tiết.

## 1. Tóm tắt cấu trúc

Theo thứ tự hiển thị trên trang chủ:

1. Nút nổi tư vấn tuyển sinh.
2. Header: nhận diện trường, liên kết tiện ích/ngôn ngữ, menu chính.
3. Banner carousel ba slide.
4. Sáu lối tắt nổi bật.
5. Khối tin tức, thông báo, Humans of VNU-IS và tuyển sinh.
6. Sự kiện và ảnh/video.
7. Các chương trình đào tạo theo ba tab.
8. Dải số liệu của trường.
9. Dải logo đối tác.
10. Footer: địa chỉ, bản đồ, thông tin, sơ đồ website, mạng xã hội, bản quyền.
11. Các modal/form chiến dịch tuyển sinh xuất hiện theo điều kiện; không phải tất cả đều là nội dung cố định của trang.

## 2. Phân tích từ ngoài vào trong

### 2.1. Nút tư vấn tuyển sinh nổi

Nút “Đăng ký tư vấn tuyển sinh” nổi ở cạnh dưới/phải trong lúc cuộn, mở lối vào biểu mẫu tư vấn.

**Bootstrap gợi ý:** `btn`, `position-fixed`, `bottom-0`, `end-0`, `m-3`; thêm CSS riêng cho màu thương hiệu, bo góc, bóng và trạng thái hover/focus.

### 2.2. Header

#### Hàng thương hiệu và tiện ích

- Logo Trường Quốc tế và Đại học Quốc gia Hà Nội.
- Liên kết hệ thống: VNU, E-GOV, E-Office, LMS, Tài nguyên số, Liên hệ.
- Chọn ngôn ngữ Việt, Anh, Pháp.
- Lối tắt: cổng việc làm, cổng sinh viên, tra cứu văn bằng; có biểu tượng tìm kiếm.

**Bootstrap gợi ý:** `.container` + `.row` + `.col`; dùng `.d-flex`, `.justify-content-between`, `.align-items-center`, `.gap-*`, `.flex-wrap`. Trên màn hình nhỏ có thể ẩn/thu gọn các liên kết ít dùng bằng responsive display utilities hoặc gom vào menu.

#### Menu chính

Các mục cấp cao quan sát được: Trang chủ, Giới thiệu chung, Đào tạo, Khoa học công nghệ, Hợp tác phát triển, Đời sống sinh viên, Tuyển sinh. Một số mục có mũi tên xổ xuống. Nội dung menu con chưa được kiểm kê vì cần mở từng menu trên website.

**Bootstrap gợi ý:** `navbar navbar-expand-xl`; `navbar-toggler`; `collapse navbar-collapse`; `navbar-nav`; `nav-item`; `dropdown`, `dropdown-toggle`, `dropdown-menu`. Dùng `navbar-brand` cho logo. Chọn breakpoint theo chiều rộng thực tế để tránh menu tràn.

### 2.3. Banner chính

Carousel banner desktop gồm 3 slide, có chỉ báo slide và nút trước/sau.

**Bootstrap gợi ý:** `carousel slide`, `carousel-inner`, `carousel-item`, `carousel-indicators`, `carousel-control-prev`, `carousel-control-next`. Ảnh dùng `img-fluid`/`w-100`; cần CSS riêng cho chiều cao ổn định, `object-fit: cover` và điểm crop theo từng breakpoint.

### 2.4. Sáu lối tắt

Các mục quan sát được:

1. LAB.
2. Tổ chức đoàn thể.
3. Tuyển dụng.
4. Học giả quốc tế.
5. Thư viện.
6. Kiểm định chất lượng.

Mỗi mục có hình/icon và tên dẫn đến trang liên quan.

**Bootstrap gợi ý:** `row row-cols-2 row-cols-md-3 row-cols-xl-6 g-3`; mỗi mục là một `col`. Có thể dùng `card h-100` nếu thiết kế có khung nền; không bắt buộc dùng card nếu chỉ là icon và nhãn.

### 2.5. Tin tức và các khối thông tin phụ

Đây là vùng nội dung nhiều cột. Cách triển khai nhanh: hàng Bootstrap 12 cột, vùng tin chính chiếm 8 cột và sidebar chiếm 4 cột ở desktop; trên mobile xếp thành một cột.

#### Tin tức

- Tiêu đề chuyên mục và liên kết “Tin tức”.
- Bài nổi bật: ảnh, nhãn danh mục, ngày giờ, tiêu đề, tóm tắt.
- Danh sách tin mới: ảnh nhỏ, tiêu đề và ngày giờ.
- Ví dụ tin trong lần khảo sát: “Cụ Huỳnh Thúc Kháng: Một đời phụng sự Tổ quốc, một tấm gương cho hôm nay”; “Nhóm nghiên cứu ‘Chuyển đổi bền vững’ được công nhận là Nhóm nghiên cứu mạnh cấp ĐHQGHN”; tin phỏng vấn kỹ sư, trải nghiệm tại FPT, Istart Camp và hoạt động ĐHQGHN.

**Bootstrap gợi ý:** `.row g-4`; vùng chính `col-lg-8`, sidebar `col-lg-4`. Trong vùng tin có thể chia bài nổi bật và danh sách bằng một `.row` lồng nhau. Dùng `card border-0` cho bài lớn, `list-group list-group-flush` hoặc các hàng `.d-flex` cho tin nhỏ; ảnh dùng `img-fluid` và tỉ lệ khung nhất quán.

#### Thông báo

Danh sách thông báo có tiêu đề, ngày đăng và liên kết bài. Ví dụ được ghi nhận: học bổng Nguyễn Trường Tộ năm 2026; học bổng POSCO 2026–2027; trao đổi sinh viên kỳ Xuân năm 2027 tại Đại học Kansai.

**Bootstrap gợi ý:** `list-group list-group-flush`; mỗi mục có thể là `list-group-item`, tiêu đề liên kết và ngày dạng `small text-body-secondary`.

#### Humans of VNU-IS

Một bài nổi bật với ảnh, nhãn “HUMANS OF VNU-IS”, tiêu đề, ngày, đoạn giới thiệu và liên kết xem chuyên mục. Bài ghi nhận trong lần khảo sát: “Nguyễn Thu Trang và hành trình đến với ngôi trường của các Tổng thống Pháp”.

**Bootstrap gợi ý:** `card`, `card-img-top`, `card-body`; dùng `stretched-link` khi phù hợp và bảo đảm các nút/liên kết con vẫn thao tác được.

#### Tuyển sinh 2026

Khối có nhãn năm, tiêu đề thông tin tuyển sinh và các liên kết tuyển sinh đại học chính quy, sau đại học.

**Bootstrap gợi ý:** khối nội dung tùy chỉnh hoặc `card`; liên kết hành động dùng `btn btn-link`/`btn btn-outline-*`. Không trộn widget này với popup modal: widget nằm trong luồng trang, modal là lớp phủ tạm thời.

### 2.6. Sự kiện và ảnh/video

#### Sự kiện

Danh sách khoảng sáu mục, mỗi dòng có tháng, ngày và tiêu đề. Ví dụ: hội nghị viên chức/người lao động và tổng kết năm học; lễ trao giải Đại sứ Văn hóa đọc; IStart Camp; vòng bán kết ISTARTUP; VISL Talk về AI/IT trong y sinh; lễ khai giảng.

**Bootstrap gợi ý:** `list-group` hoặc từng hàng `.d-flex`; ngày/tháng đặt trong một khối có chiều rộng ổn định (`flex-shrink-0`).

#### Ảnh và video

Có tiêu đề “Ảnh và video”, video YouTube nhúng và dải ảnh/video sự kiện có tiêu đề liên kết.

**Bootstrap gợi ý:** vùng media dùng `.ratio.ratio-16x9` cho iframe; gallery dùng `row row-cols-2 row-cols-md-3 g-2`, ảnh `img-fluid`. Nếu cần carousel nhiều thẻ cùng lúc, Bootstrap Carousel mặc định cần thêm logic cho nhiều item hoặc dùng thư viện slider riêng.

**Bố cục đề xuất:** `.row g-4`, sự kiện `col-lg-5`, media `col-lg-7`.

### 2.7. Các chương trình đào tạo

Có ba tab:

- Cử nhân - Kỹ sư (17).
- Thạc sỹ (8).
- Tiến sỹ (2).

Tab chứa các mục chương trình dạng ảnh + tên và điều khiển trước/sau. 17 tên Cử nhân/Kỹ sư được nhận diện:

1. Truyền thông số.
2. Kinh doanh số.
3. Công nghệ thông tin ứng dụng.
4. Kinh doanh quốc tế.
5. Kế toán, Phân tích và Kiểm toán.
6. Hệ thống thông tin quản lí.
7. Tin học và Kĩ thuật máy tính.
8. Phân tích dữ liệu kinh doanh.
9. Tự động hóa và Tin học.
10. Ngôn ngữ Anh.
11. Khoa học quản lí.
12. Kế toán và Tài chính.
13. Quản trị Khách sạn, Thể thao và Du lịch.
14. Marketing.
15. Cử nhân ngành Quản lý (song bằng).
16. Công nghệ tài chính và Kinh doanh số.
17. Kỹ thuật hệ thống công nghiệp và Logistics.

**Bootstrap gợi ý:** `nav nav-tabs` hoặc `nav nav-pills` kết hợp `tab-content` và `tab-pane`; mỗi pane dùng `row row-cols-1 row-cols-sm-2 row-cols-lg-4 g-3`. Item dùng `card h-100`, ảnh `card-img-top`, tên trong `card-body`. Với 17 chương trình nên phân trang/trượt, không cố dàn tất cả thành một hàng.

### 2.8. Dải số liệu

Sáu chỉ số quan sát được:

- 24 chương trình đào tạo.
- Hơn 7.000 sinh viên, học viên.
- Hơn 400 giảng viên, chuyên gia, nhà khoa học.
- 40 đối tác trong và ngoài nước.
- 30 quốc tịch.
- 93% tỉ lệ việc làm trong 12 tháng sau tốt nghiệp.

**Bootstrap gợi ý:** `row row-cols-2 row-cols-md-3 row-cols-xl-6 g-3`; mỗi ô có icon, số liệu, nhãn; dùng `.text-center` và utility typography. Màu nền, đường chia, icon và kích thước chữ cần CSS thương hiệu.

### 2.9. Logo đối tác

Dải logo liên kết tới các trường/đối tác trong và ngoài nước. Ví dụ trong dữ liệu trang: Macquarie, Aix-Marseille, Canberra, Keuka, Missouri, Western Sydney, UniSA, UNB, Nantes, Arizona, University of East London, MPEI, LHU, IPAG, ECU, Heriot-Watt, Curtin, Deakin và Russkiy Mir.

**Bootstrap gợi ý:** lưới `row row-cols-3 row-cols-md-5 row-cols-xl-7 g-3` hoặc carousel. Đặt chiều cao khung logo nhất quán và dùng `object-fit: contain` để không méo logo.

### 2.10. Footer

- **Địa chỉ:** Trường Quốc tế, ĐHQGHN; cơ sở Xuân Thủy (Nhà E5 & G7, 144 Xuân Thủy, Cầu Giấy); Phan Tây Nhạc (số 1, phố Phan Tây Nhạc, Xuân Phương); Hòa Lạc (tòa HT1, Khu đô thị đại học); email `is@vnu.edu.vn`.
- **Bản đồ chỉ dẫn:** iframe bản đồ.
- **Thông tin:** ĐHQGHN, phòng chức năng, khoa trực thuộc, trung tâm/viện.
- **Sơ đồ website:** sơ đồ trang và liên hệ.
- **Cuối trang:** YouTube, Instagram, TikTok, Facebook và dòng bản quyền © 2022 thuộc về Trường Quốc tế - ĐHQGHN.

**Bootstrap gợi ý:** `.container` + `.row g-4`; địa chỉ `col-lg-4`, bản đồ `col-lg-4`, hai cột liên kết `col-md-6 col-lg-2`. Bản đồ đặt trong `.ratio.ratio-16x9`. Mạng xã hội dùng danh sách `.d-flex gap-3`; phần bản quyền có thể căn giữa hoặc hai đầu bằng flex.

### 2.11. Popup và biểu mẫu chiến dịch

Dữ liệu trích xuất ghi nhận các biểu mẫu tư vấn chương trình thạc sĩ/tiến sĩ, biểu mẫu tuyển sinh/xét tuyển, đăng ký trở thành ISER và tư vấn tuyển sinh. Trường có thể gồm họ tên, số điện thoại, email, ngành học/chương trình quan tâm, nền tảng tiếng Anh, kinh nghiệm hoặc thông tin xét tuyển. Popup thay đổi theo chiến dịch và không nhất thiết cùng xuất hiện.

**Bootstrap gợi ý:** `modal` nếu cần phủ nền và giữ người dùng trong luồng xác nhận; `offcanvas` nếu là panel trượt. Form dùng `form-label`, `form-control`, `form-select`, `form-check`, `row g-3`. Cần nút đóng, nhãn trường, trạng thái lỗi/thành công, quản lý focus và chính sách quyền riêng tư.

> Chuỗi “Our Spring Sale Has Started” trong dữ liệu crawl có vẻ là popup mẫu/không liên quan; không nên tái tạo nếu không xác minh đó là nội dung thật.

## 3. Bảng ánh xạ Bootstrap 5

| Khu vực | Grid/component/class đề xuất | Responsive |
|---|---|---|
| Header tiện ích | `container`, `row`, `d-flex`, `gap-*` | Thu gọn/ẩn link phụ trên mobile |
| Menu | `navbar navbar-expand-xl`, `collapse`, `dropdown` | Hamburger dưới breakpoint XL |
| Banner | `carousel slide`, `carousel-item`, controls/indicators | Ảnh riêng hoặc crop theo viewport |
| Sáu lối tắt | `row-cols-2 row-cols-md-3 row-cols-xl-6 g-3` | 2, 3 rồi 6 cột |
| Tin và sidebar | `row g-4`, `col-lg-8`, `col-lg-4` | Sidebar xếp dưới tin |
| Sự kiện/media | `row`, `col-lg-5`, `col-lg-7`, `ratio-16x9` | Xếp dọc trên mobile |
| Chương trình | `nav-tabs`, `tab-content`, `row-cols-*`, `card` | Tối đa 4 thẻ mỗi hàng ở desktop |
| Số liệu | `row-cols-2 row-cols-md-3 row-cols-xl-6` | 2/3/6 cột |
| Đối tác | `row-cols-3 row-cols-md-5 row-cols-xl-7` hoặc carousel | Có thể cuộn ngang |
| Footer | `row g-4`, `col-lg-4`, `col-md-6 col-lg-2` | Các cột xếp dọc |
| CTA/modal | `position-fixed`, `btn`, `modal`/`offcanvas` | CTA tránh che nội dung và safe area |

## 4. Sơ đồ ASCII layout desktop

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│ HEADER                                                                      │
│ ┌──────────────────────────────────────┬──────────────────────────────────┐ │
│ │ Logo VNU-IS + ĐHQGHN                 │ VNU | E-GOV | E-Office | LMS     │ │
│ │                                      │ Tài nguyên | Liên hệ | VI/EN/FR  │ │
│ ├──────────────────────────────────────┴──────────────────────────────────┤ │
│ │ Trang chủ | Giới thiệu | Đào tạo | KHCN | Hợp tác | Sinh viên | Tuyển sinh│ │
│ └─────────────────────────────────────────────────────────────────────────┘ │
├─────────────────────────────────────────────────────────────────────────────┤
│ CAROUSEL: banner tuyển sinh / hoạt động (3 slide, điều khiển trước-sau)    │
├─────────────────────────────────────────────────────────────────────────────┤
│ LỐI TẮT: LAB | Đoàn thể | Tuyển dụng | Học giả | Thư viện | Kiểm định      │
├─────────────────────────────────────────────────────────────────────────────┤
│ TIN TỨC + THÔNG TIN PHỤ                                                     │
│ ┌──────────────────────── 8/12 ─────────────────────┐ ┌─── 4/12 ─────────┐ │
│ │ Tin nổi bật + ảnh        │ Danh sách tin + ảnh nhỏ│ │ Thông báo        │ │
│ │ tiêu đề/ngày/tóm tắt     │ tiêu đề/ngày           │ │ Humans of VNU-IS │ │
│ │                                                │   │ Tuyển sinh 2026 │ │
│ └────────────────────────────────────────────────┘ └───────────────────┘ │
├─────────────────────────────────────────────────────────────────────────────┤
│ ┌──────────── 5/12 ────────────┐ ┌───────────── 7/12 ───────────────────┐ │
│ │ SỰ KIỆN: ngày/tháng + tiêu đề│ │ ẢNH VÀ VIDEO: YouTube + gallery    │ │
│ └───────────────────────────────┘ └──────────────────────────────────────┘ │
├─────────────────────────────────────────────────────────────────────────────┤
│ CHƯƠNG TRÌNH ĐÀO TẠO                                                       │
│ [Cử nhân - Kỹ sư (17)] [Thạc sỹ (8)] [Tiến sỹ (2)]                         │
│ [Chương trình] [Chương trình] [Chương trình] [Chương trình]  ← trượt →     │
├─────────────────────────────────────────────────────────────────────────────┤
│ THỐNG KÊ: 24 chương trình | 7.000+ SV | 400+ cán bộ | 40 đối tác | ...     │
├─────────────────────────────────────────────────────────────────────────────┤
│ LOGO ĐỐI TÁC: [logo] [logo] [logo] [logo] [logo] [logo] ...                │
├─────────────────────────────────────────────────────────────────────────────┤
│ FOOTER: Địa chỉ 4/12 | Bản đồ 4/12 | Thông tin 2/12 | Sơ đồ web 2/12       │
│ Mạng xã hội: YouTube | Instagram | TikTok | Facebook | Bản quyền           │
└─────────────────────────────────────────────────────────────────────────────┘
                                           [Nút tư vấn tuyển sinh cố định]
```

### Responsive đề xuất

- **Mobile:** header và menu thu gọn; lối tắt 2 cột; mọi vùng 8/4 và 5/7 xếp dọc; các thẻ chương trình và số liệu 1–2 cột; footer xếp theo thứ tự nội dung.
- **Tablet:** tăng lối tắt lên 3 cột; tin/sidebar có thể tiếp tục xếp dọc tùy độ rộng; số liệu 3 cột.
- **Desktop:** dùng `container-xxl`; tin/sidebar 8/4; sự kiện/media 5/7; số liệu tối đa 6 cột.
- Dùng breakpoint Bootstrap (`sm`, `md`, `lg`, `xl`, `xxl`) theo nội dung thực tế. Bootstrap giải quyết khung lưới và component cơ bản; font, màu, khoảng cách, crop ảnh, icon, trạng thái tương tác cần CSS/JS riêng để khớp nhận diện.
