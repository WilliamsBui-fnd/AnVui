# An Vui — Demo cộng đồng tuổi vàng

Một sản phẩm của nhóm **Zentech**: *Đơn giản là sức mạnh.* Zen (tối giản) + Tech (công nghệ), hướng đến sản phẩm công nghệ đơn giản nhưng hiệu quả. Logo nhóm (PNG nền trong suốt, dùng cho slide) nằm trong `brand/`.

Bản demo UI tương tác phục vụ thuyết trình dự án khởi nghiệp. Tên và nhận diện An Vui là phương án đề xuất, có thể đổi.

## Mở ngay

**Bản trực tuyến (GitHub Pages):** https://williamsbui-fnd.github.io/AnVui/ · bản ứng dụng điện thoại: https://williamsbui-fnd.github.io/AnVui/?app=1

Mỗi lần push lên nhánh `main`, workflow `.github/workflows/pages.yml` chạy kiểm tra (`npm run check`, `npm test`) rồi tự triển khai thư mục `dist/`.


Mở `dist/index.html` bằng Chrome, Edge hoặc Safari. Toàn bộ hình, mã và font đã có trong thư mục, không cần tải thư viện ngoài. Nhấn “Đặt lại demo” trước buổi trình bày.

Để thử đầy đủ chế độ ứng dụng web và service worker, chạy từ thư mục dự án:

```sh
python3 -m http.server 4173 --directory dist
```

Mở http://localhost:4173. Thêm `?app=1` để chỉ hiển thị khung điện thoại. Dừng server bằng Ctrl+C.

## Dùng trên iPhone (ứng dụng web)

1. Đưa thư mục `dist/` lên một hosting có HTTPS (Netlify, Vercel, GitHub Pages…). Đặt trong thư mục con cũng được vì manifest dùng đường dẫn tương đối.
2. Trên iPhone, mở link bằng Safari → nút Chia sẻ → **Thêm vào MH chính** → Thêm. Trang chủ cũng hiện banner hướng dẫn trên iPhone, có nút “Để sau”.
3. Mở An Vui từ màn hình chính: app chạy toàn màn hình, không có khung điện thoại giả, có chừa chỗ cho tai thỏ và thanh Home. Mở `?app=1` trong Safari trên điện thoại cũng cho giao diện tương tự.

Nút/vuốt Quay lại của trình duyệt đưa về màn hình trước. Trong Tài khoản có “Ẩn ghi chú demo” (thay các ghi chú nhỏ bằng một dải “Bản thử nghiệm”) và “Đặt lại bản demo”. Bấm logo chỉ về trang nhà; đặt lại demo luôn hỏi xác nhận.

Bản được triển khai qua Sites mặc định riêng tư cho chủ sở hữu; có thể cần đăng nhập đúng tài khoản khi mở. Bản HTML cục bộ là phương án dự phòng cho buổi thuyết trình.

## Chiến dịch và hỗ trợ trực tiếp

Tab “Chiến dịch” kể câu chuyện “Để ba mẹ không ngại hỏi”. Mở `?view=campaign`, `?view=business` hoặc `?view=launch` để vào thẳng trang tương ứng. Bộ ảnh, bài đăng, kịch bản phim và kế hoạch thử có trong `campaign/CHIEN_DICH_DE_BA_ME_KHONG_NGAI_HOI.md`.

Chức năng “Có người chỉ tận tay” cho chọn việc, khu vực, người hướng dẫn mẫu và điểm hẹn. Vị trí được xin quyền chủ động; GPS không lưu vào localStorage hay gửi máy chủ. Google Maps chỉ mở khi người dùng bấm liên kết. Sơ đồ/khoảng cách không phải kết quả tìm người thực tế. Yêu cầu chỉ lưu trên máy: đổi sang người trẻ để nhận mẫu, đổi về cô bác để xác nhận hoàn tất. Giá 99.000đ/45 phút và phí 20% là giả định, chưa bán dịch vụ.

## Giao diện (design system v2)

- Toàn bộ `dist/style.css` dùng chung một bộ token khai báo ở `:root`: màu thương hiệu (xanh lá An Vui, cam đất làm điểm nhấn, xanh xám Zentech), màu chữ và nền, ba tông thông báo (cảnh báo/vàng, tích cực/xanh lá, thông tin/xanh dương), bo góc, đổ bóng.
- Icon: một bộ nét đều kiểu Lucide trong `ICONS` (`dist/app.js`), gọi qua `icon('tên')`. Logo An Vui (mầm hai lá) vẽ bằng SVG; icon ứng dụng trong `dist/assets/icon*.png|svg` dùng cùng hình.
- Logo Z của Zentech luôn ở góc màn hình: nút nổi góc dưới bên trái trên máy tính/tablet, góc trên bên trái trong ứng dụng điện thoại. Bấm vào để mở giới thiệu nhóm.
- Chữ trong app tối thiểu khoảng 14px ở cỡ chữ nhỏ nhất, nút bấm cao 52–56px. Không còn `style=""` viết trực tiếp trong mẫu HTML (trừ chiều rộng thanh tiến độ).

## Các luồng đã triển khai

- Cô bác: hướng dẫn mở đầu, ba cỡ chữ, đăng bài, đặt câu hỏi, tìm kiếm/lọc, xác nhận hữu ích, kết bạn và nhắn tin.
- Người trẻ: chỉ trả lời, nhắn tin và xem điểm đóng góp; không được đăng câu hỏi hay bài cộng đồng.
- Kiểm duyệt mẫu: trả lời → chờ duyệt → bấm duyệt mẫu → cô bác xác nhận → cộng 10 điểm đúng một lần.
- Mua sắm: lọc sản phẩm, xem chi tiết, kiểm tra đơn mẫu, đặt thử và tạo nội dung nhờ con cháu mua giúp.
- Gia đình: hướng dẫn cài ứng dụng web, chọn chữ, thử trải nghiệm cùng ba mẹ.
- Tài khoản: kết quả căn cước mẫu cho nhóm 60+ và 18–59; không có trường tải giấy tờ.
- Mô hình kinh doanh: ba nguồn thu và bảng tính giả định tương tác, tách GMV/doanh thu/chi phí.
- Kế hoạch ra mắt: thử nghiệm 4 tuần, mục tiêu kiểm chứng và kịch bản thuyết trình.

Dữ liệu được lưu bằng localStorage trên từng trình duyệt. Không có máy chủ đăng nhập, nhắn tin trực tiếp, AI đánh giá câu trả lời, xác thực căn cước, đơn hàng, thông báo đẩy hoặc thanh toán thật. Trạng thái “đã duyệt/đã xác thực” chỉ là mô phỏng. Không nhập dữ liệu thật.

Tính năng đọc văn bản và nhập giọng nói dùng khả năng sẵn có của trình duyệt; sự hỗ trợ tiếng Việt phụ thuộc thiết bị và quyền người dùng. Có thông báo và phương án gõ văn bản khi không hỗ trợ. Không tuyên bố đã đạt chứng nhận WCAG hoặc đã kiểm chứng với người cao tuổi.

## Kiểm tra

JavaScript đã kiểm tra cú pháp và 31 nhóm kiểm tra DOM với jsdom, bao gồm phân quyền, chuỗi hỏi đáp, kiểm duyệt mẫu, chống cộng điểm lặp, dữ liệu nhập không trở thành HTML, kết bạn, nhắn tin, đặt thử, giả lập căn cước và công thức doanh thu.

Trình duyệt kiểm thử không có sẵn trong môi trường thực hiện. Chưa xác nhận bố cục bằng screenshot hay thao tác trên thiết bị thật; cần mở trước trên máy dùng thuyết trình và thử cùng cô bác.

```sh
npm install
npm run check
npm test
```

Ứng dụng chạy không cần npm; jsdom chỉ dùng để kiểm tra. Yêu cầu Node tương thích phiên bản jsdom trong package.json.

## Hình ảnh và nguồn

- `dist/assets/community.webp`: ảnh minh họa do công cụ image_gen tích hợp tạo, không phải người dùng hay lời chứng thực thật. Prompt đầy đủ trong `ASSET_SOURCES.md`.
- Các ảnh sản phẩm và làm vườn: Unsplash, chỉ minh họa, không đại diện hàng hóa đang được bán.
- Font Be Vietnam Pro: Google Fonts, lưu cục bộ, giấy phép SIL Open Font License; xem `dist/assets/fonts/OFL.txt`.
- Cơ sở định hướng khả năng tiếp cận: https://www.w3.org/WAI/older-users/developing/
- Bối cảnh già hóa dân số: https://vietnam.unfpa.org/en/topics/ageing-0

Xem `CHUAN_BI_THUYET_TRINH.md` để có đề xuất sản phẩm, mô hình tiền, cách thu hút người dùng và câu trả lời cho các câu hỏi của giảng viên.
