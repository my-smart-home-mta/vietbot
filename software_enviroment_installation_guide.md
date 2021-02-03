
### STEP1. Cài đặt hệ điều hành Raspbian

1.1. Download Raspberry Pi OS
Tối ưu cho phần cứng Pi Zero Wireless nên Vietbot chỉ cần bản OS Buster Lite

Download đúng phiên bản sau tại địa chỉ:

https://downloads.raspberrypi.org/raspios_lite_armhf/images/raspios_lite_armhf-2020-08-24/2020-08-20-raspios-buster-armhf-lite.zip

1.2. Flash vào thẻ nhớ
Sử dụng tool của Raspberry hoặc Etcher

1.3. Config để vào được SSH qua WiFi

1.3.1. Cắm lại thẻ nhớ vào máy

1.3.2. Sử dụng Notepad ++ để tạo file có tên là wpa-supplicant trong thư mục boot của thẻ nhớ với  định dạng file EOL Conversion là Unix (LF), nội dung là các tham số tên SSID và mật khẩu tương ứng
Chú ý, tham số country có thể đổi sang us hoặc vn tùy theo cài đặt tại bộ phát WiFi
```sh
country=vn
update_config=1
ctrl_interface=/var/run/wpa_supplicant
network={
    ssid="testing"
    psk="testingPassword"
}
```
1.3.3. Tạo file rỗng có tên là SSH trong thư mục boot 

1.4. Truy cập ssh vào Pi Zero Wirless

1.4.1. Cắm thẻ nhớ vào Pi Zero Wireless, chờ Pi boot up xong, xác định IP của Pi từ Modem, Access Pint

1.4.2. Sử dụng putty truy cập ssh vào địa chỉ IP của Pi với username là pi, password là raspberry

### STEP2. Cài đặt các thư viện chung cho Vietbot và thư viện cho Python trên OS

2.1. Cài đặt các thư viện chung cho Vietbot

Chạy lần lượt các lệnh sau
```sh
sudo apt-get update -y
```
sau đó 
```sh
sudo apt-get upgrade -y
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
2.2. Cài đặt các thư viện cho Python

Chạy lần lượt các lệnh sau
```sh
sudo apt-get install python3-pip python3-setuptools python3-psutil python3-bottle python3-requests python3-dev python3-pyaudio python3-numpy python3-pip python3-wheel python3-dev python3-pygame -y
```
sau đó
```sh
sudo apt-get install vlc git -y
```
### STEP3. Cài đặt các gói Python

3.1. Nâng cấp PIP

Chạy lần lượt các lệnh sau
```sh
python3 -m pip install --upgrade pip

```
3.2. Cài đặt các gói Python cơ bản
```sh
python3 -m pip install wheel python-Levenshtein PyAudio pyusb pygame pyalsaaudio pyyaml pydub 

```
3.3. Cài đặt các gói Python liên quan tới các Skill
```sh
python3 -m pip install pixel-ring apa102 spidev ffmpeg termcolor fuzzywuzzy datefinder feedparser pafy youtube-dl forecastiopy mutagen playsound wget enums wikipedia pvporcupine python-vlc nltk underthesea pyglet paho-mqtt untangle  

```
3.4. Cài đặt các gói Python liên quan tới tổng hợp và xử lý âm thanh
```sh
python3 -m pip install google-cloud google-cloud-speech gTTS SpeechRecognition googletrans  

```
### STEP4. Config Mig, Speaker, LED

4.1. Cài đặt cho Modun ReSpeaker 2 Mic Hat hoặc ReSpeaker 4-Mic Array for Raspberry Pi (Nếu ko sử dụng thì bỏ qua)

4.1.1. Cắm Modun 2 Mic Hat hoặc ReSpeaker 4-Mic Array vào Pi Zero

Chạy lần lượt các lệnh sau
```sh
git clone https://github.com/respeaker/seeed-voicecard.git
```
sau đó
```sh
cd seeed-voicecard
```
sau đó
```sh
sudo ./install.sh
```
chờ cài đặt kết thúc

khởi động lại

```sh
sudo reboot

```

sau đó xóa file asound.conf

```sh
sudo cp /etc/asound.conf asound.conf.bak
sudo rm -rf /etc/asound.conf
```
gỡ bỏ pulseaudio bằng lệnh (Nếu không cài đặt pulseaudio trước đây thì bỏ qua bước này

```sh
sudo apt-get purge pulseaudio -y
```
Sau đó khởi động lại (Nếu không cài đặt pulseaudio trước đây thì bỏ qua bước này

```sh
sudo reboot
```

Sau khi khởi động lại vào alxamixer bằng lệnh

```sh
alsamixer
```
bấm F6 để chọn sound card seed, sau đó bấm F5, dùng phím lên trên bàn phím để kéo hết các giá trị lên Max, phím trái, phải để chọn các giá trị Stereo tại các mục tương ứng


4.2. Cài đặt cho Mic USB và Loa 

4.2.1. Thống kê ID của Mic USB và Loa (Chỉ dành cho 1/sử dụng Mic USB Soundcard USB hoặc 2/sử dụng phiên bản Pi có nhiều hơn 1 Sound card hoặc cả 1/ và 2/)

Chạy lệnh sau để biết ID của Mic USB
```sh
arecord -l
```
sau đó chạy lệnh sau để biết ID của Loa

```sh
aplay -l
```
Lưu lại thông tin về card_id và device_id ở mỗi kết quả lệnh

4.2.2. Khai báo cho cả Mic USB (Nếu ko sử dụng Mic USB thì bỏ qua phần này)

Chạy lệnh sau 
```sh
sudo nano /home/pi/.asoundrc
```
Cửa sổ nano hiện lên, paste dòng sau, thay thế <card_id> và <device_id> bằng kết quả đã lưu:

```sh
pcm.!default {
  type asym
  capture.pcm "mic"  
}
pcm.mic {
  type plug
  slave {
    pcm "hw:<card_id>,<device_id>"
  }
}
```
Bấm lần lượt Ctrl + X, sau đó Y rồi Enter

4.2.3. Khai báo cho loa (Nếu ko sử dụng phiên bản Pi có nhiều hơn 1 Sound card thì bỏ qua phần này)
Chạy lệnh sau 

```sh
sudo nano /home/pi/.asoundrc
```
Cửa sổ nano hiện lên, paste dòng sau, thay thế <card_id> và <device_id> bằng kết quả đã lưu:

```sh
pcm.!default {
  type asym
  playback.pcm "speaker"
}
pcm.speaker {
  type plug
  slave {
    pcm "hw:<card_id>,<device_id>"
  }
}
```
Bấm lần lượt Ctrl + X, sau đó Y rồi Enter

4.2.4. Copy file thiết lập cho mọi account (Nếu chỉ dùng Account Pi thì bỏ qua bước này)

Chạy lệnh sau
```sh
sudo cp /home/pi/.asoundrc /etc/asound.conf
```
4.2.5. Reboot lại Pi
Chạy lệnh sau
```sh
sudo reboot
```
4.3. Cài đặt điều khiển Led cho Modun ReSpeaker Mic Array v2.0 hoặc ReSpeaker USB Mic Array (Nếu không dùng thì bỏ qua)

4.3.1. Đưa Account đang dùng (Ví dụ pi) vào group root

Chạy lệnh sau
```sh
sudo usermod -aG root account_name
```
4.3.2. Reboot lại Pi
Chạy lệnh sau
```sh
sudo reboot
```
