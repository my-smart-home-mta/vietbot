
### STEP1. Cài đặt hệ điều hành Raspbian

1.1. Download Raspberry Pi OS
Tối ưu cho phần cứng Pi Zero Wireless nên Vietbot chỉ cần bản Raspberry OS Lite, kích thước 438MB, tại địa chỉ:
https://downloads.raspberrypi.org/raspios_lite_armhf/images/raspios_lite_armhf-2021-01-12/2021-01-11-raspios-buster-armhf-lite.zip

1.2. Flash vào thẻ nhớ
Sử dụng tool của Raspberry hoặc Etcher

1.3. Config để vào được SSH qua WiFi

1.3.1. Cắm lại thẻ nhớ vào máy

1.3.2. Tạo file có tên là wpa-supplicant trong thư mục boot của thẻ nhớ với các tham số tên SSID và mật khẩu tương ứng
```sh
network={
    ssid="testing"
    psk="testingPassword"
}
```

1.3.3. Tạo file rỗng có tên là SSH trong thư mục boot 

1.4. Cài đặt các thư viện chung cho Vietbot và các hỗ trợ cho gói Python trên OS

1.4.1. Cắm thẻ nhớ vào Pi Zero Wireless, chờ Pi boot up xong, xác định IP của Pi

1.4.2. Sử dụng putty truy cập ssh vào địa chỉ IP của Pi với username là pi, password là raspberry

1.4.3. Chạy lần lượt các lệnh sau
```sh
sudo apt-get update -y
```
sau đó 
```sh
sudo apt-get upgrade-y
```
sau đó
```sh
sudo apt-get install libportaudio2 libatlas-base-dev libsdl2-mixer-2.0-0 libpq-dev libpq-dev libssl-dev openssl libffi-dev zlib1g-dev  libportmidi-dev libswscale-dev libavformat-dev libavcodec-dev libfreetype6-dev libasound2-dev -y

```
sau đó
```sh
sudo apt-get install libncurses5-dev libncursesw5-dev libreadline6-dev libdb5.3-dev libgdbm-dev libsqlite3-dev libssl-dev libbz2-dev libexpat1-dev liblzma-dev zlib1g-dev libffi-dev wget  -y

```
sau đó
```sh
sudo apt-get install libportaudio-dev libsdl1.2-dev libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-ttf2.0-dev libsmpeg-dev libportmidi-dev libswscale-dev libavformat-dev libavcodec-dev libfreetype6-dev -y
```
sau đó
```sh
sudo apt-get install python3-setuptools python3-psutil python3-bottle python3-requests python3-dev python3-pyaudio python3-numpy python3-pip python3-wheel python3-dev-y
```
sau đó
```sh
sudo apt-get install python3-pygame
```
sau đó
```sh
sudo apt-get install sudo apt-get install vlc
```
