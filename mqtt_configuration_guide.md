Vietbot hỗ trợ MQTT để điều khiển nhà thông minh bằng giọng nói Việt với các tham số là Tên thiết bị & Topic và Payload

### STEP1. Cài đặt MQTT Broker

Vietbot không yêu cầu config trên Broker, chỉ cần lấy và lưu lại các tham số sau

1.1. MQTT Address

Có dạng: X.X.X.X với X.X.X.X là địa chỉ Private hoặc Public

1.2. MQTT Port

Có dạng: XXXX với XXXX là Port (Mặc định là 8123)

Các tham số 1.1 và 1.2 sẽ được nhập vào config.yaml, xem mục: https://github.com/phanmemkhoinghiep/vietbot/blob/main/configuration_guide.md 

### STEP2. Cài đặt thiết bị kết nối với MQTT Broker

Vietbot không yêu cầu config trên thiết bị, chỉ cần lấy và lưu lại các tham số sau

2.1 Device Name

Đây là tên sẽ dùng cho thiết bị, có thể đặt nhiều hơn 1 tên cho thiết bị, ví dụ

- ĐÈN PHÒNG BẾP
- ĐÈN THỨ NHẤT
- ĐÈN PHÒNG BẾP THỨ NHẤT

Tên đèn sẽ được bổ sung trong file device.yaml ở mục device_name, người dùng có thể bổ sung thêm các câu khác có nghĩa tương đương để phong phú việc ra lệnh

2.1. MQTT Topic

Có dạng: /abc/def... hoặc abc/def/...

2.2. MQTT Payload

Có dạng: 'ON', 'OFF' với thiết bị đóng mở, với 1 số thiết bị loại khác sẽ có payload khác

Các tham số 2.1 và 2.2 sẽ được nhập vào config.yaml, xem mục: https://github.com/phanmemkhoinghiep/vietbot/blob/main/configuration_guide.md 

### STEP3. Các câu lệnh tương tác với thiết bị

Các câu lệnh tương tác đã có trong file request.yaml, người dùng có thể bổ sung thêm các câu khác có nghĩa tương đương để phong phú việc ra lệnh


### STEP4. Các câu lệnh phản hồi

Các câu lệnh phản hồi đã có trong file response.yaml ở mục response_mqtt_success và response_mqtt_failed, người dùng có thể bổ sung thêm các câu khác có nghĩa tương đương để phong phú việc ra lệnh


