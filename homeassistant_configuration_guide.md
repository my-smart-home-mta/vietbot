Vietbot hỗ trợ Home Assistant để điều khiển nhà thông minh bằng giọng nói Việt với hai tham số là Base URL & Long Lived Token

### STEP1. Lấy Base URL và Long Lived token

1.1. Base URL Internal

Có dạng: http://X.X.X.X:8123 với X.X.X.X là địa chỉ Private

1.2. Base URL External

Có dạng: http://abc.def:8123 (Có thể không có 8123) hoặc không với abc.def là Domain

1.3. Truy cập vào Web UI của Home Assistant để lấy Long Lived Token 

### STEP3.  Chỉnh sửa trong File config.yaml

3.1. Nhập các giá trị tại 1.1 và 1.2 vào file config

3.2. Sửa dòng 
```sh
use_hass: 1
```
### STEP4.  Chỉnh sửa trong File config.yaml

4.1. Chạy lại bot theo hướng dẫn tại https://github.com/phanmemkhoinghiep/vietbot/blob/main/running_guide.md
