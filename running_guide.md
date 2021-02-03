
### STEP1. Chạy Manual

1.1. Truy nhập vào thư mục Bot
Sử dụng lệnh sau

```sh
cd vietbot
```
1.2. Chạy boot bằng lệnh 

```sh
python3 main_process.py
```

### STEP2.  Chạy tự động khi khởi động Pi

Sử dụng lần lượt các lệnh sau

```sh
cd ~
mkdir .config
mkdir .config/systemd
mkdir .config/systemd/user
nano .config/systemd/user/bot.service

```
Tại cửa sổ nano, gõ các dòng sau

```sh
[Unit]
Description=Bot
After=syslog.target network.target
[Service]
Type=simple
WorkingDirectory=/home/pi/vietbot
ExecStart=/bin/bash -lc '. bot.sh'
RestartSec=1
Restart=on-failure
StandardOutput=syslog
StandardError=syslog
SyslogIdentifier=vietbot
[Install]
WantedBy=multi-user.target
```
Bấm Ctrl + X, Y, Enter

Sau đó gõ tiếp các lệnh sau
```sh
systemctl --user enable bot
systemctl --user enable bot
systemctl --user start bot
```
Khởi động lại Pi và bot sẽ tự động chạy
