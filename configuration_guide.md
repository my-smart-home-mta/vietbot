
Vietbot hỗ trợ File cấu hình các tham số của bot tại file config.yaml

### STEP1. Cấu hình STT &TTS

1.1 Cấu hình STT

1.1.1. STT Engine

```sh
stt_engine: x
```
x có các giá trị sau: 0 (Ko sử dụng STT), 1 (Google STT Free (gTTS)), 2 (Google Cloud STT), 3 (VTCC STT), 4: (FPT STT)

1.1.2. STT Timeout

Điều chỉnh mục sau
```sh
stt_timeout: x
```
x đơn vị là ms

1.1.3. Google credentials

Điều chỉnh mục sau
```sh
google_application_credentials: file_name.json
```
file_name.json là file thu được từ bước cấu hình credential tạo Google tại: https://github.com/phanmemkhoinghiep/vietbot/blob/main/stt_and_tts_configuration_guide.md

1.1.4. VTCC AI WS

Điều chỉnh mục sau
```sh
stt_viettel_url: ws://abc.def
```
abc.def là địa chỉ WebSocket VTCC

1.2. Cấu hình TTS

1.2.1. TTS Engine

Điều chỉnh mục sau
```sh
tts_engine: x
```
x có các giá trị sau: 0 (Ko sử dụng STT), 1 (Google TTS Free (gTTS)), 2 (Google Cloud TTS), 3 (VTCC TTS), 4: (FPT TTS), 5: (Zalo TTS)

1.2.2. API của Google, Token của Viettel, API của FPT, Zalo của API

Điều chỉnh mục sau:

```sh
google_api: sfsljflsjfanwsn5Lu-LYqKSLJRLJGY
viettel_token: SysfdsfdsfadsjBFqq-jxLrWpxlyXxzdWỦKLDDRD
fpt_api: 7591A4mt9hBzp8kLJFLDLJRNLLDEORKDEELLR
zalo_api: 8sJJ39o7qhfSFDLJFLREOEOJGLLSLrrRILE
```
Các giá trị là giá trị đăng ký tại: https://github.com/phanmemkhoinghiep/vietbot/blob/main/stt_and_tts_configuration_guide.md

1.2.3. Tham số cho TTS Zalo
```sh
tts_zalo_voice_id: x
tts_zalo_speed: y
```
x có các giá trị sau: 1,2,3,4
y có các giá trị từ 0.1 tới 1.0

1.2.4. Giá trị âm lượng
```sh
volume: x
```
x có các giá trị từ 0.1 tới 1.0
