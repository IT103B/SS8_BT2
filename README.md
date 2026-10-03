# Bài 2 - Cập nhật và hiển thị hàng đợi xe

## Phân tích lỗi

- `hangDoiXeCho.pop()` lấy xe cuối hàng (`51C-45678`) thay vì xe đến sớm nhất. Dùng `shift()` để lấy và loại xe đầu hàng.
- Xe mới được thêm bằng `push()` vào cuối hàng, đúng thứ tự tiếp nhận.
- Điều kiện `i <= hangDoiXeCho.length` chạy thừa một lượt. Ở lượt cuối, phần tử là `undefined`, tạo ra dòng `"Xe undefined"`. Dùng `i < hangDoiXeCho.length` để chỉ in các phần tử có thật.

## Test cases

| Trường hợp kiểm thử | Dữ liệu đầu vào | Kết quả sai thực tế | Kết quả đúng mong đợi |
|---|---|---|---|
| Hàng đợi nhiều xe, tiếp nhận xe mới và in danh sách | `['30A-98765', '29B-12345', '51C-45678']`; xe mới `'43D-88888'` | `pop()` đưa `51C-45678` vào sạc; sau khi thêm xe, bảng in thêm một dòng `undefined` | `shift()` đưa `30A-98765` vào sạc; bảng in lần lượt `29B-12345`, `51C-45678`, `43D-88888`, không có dòng thừa |
| Hàng đợi chỉ có một xe | `['30A-98765']`; xe mới `'43D-88888'` | Lấy nhầm xe cuối bằng `pop()`; vòng lặp `<=` in thêm `undefined` | Xe `30A-98765` vào sạc; danh sách chờ còn `43D-88888`, chỉ in một dòng |
