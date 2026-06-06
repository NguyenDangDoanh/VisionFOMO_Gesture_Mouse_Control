# Vision-FOMO Gesture Mouse Control

## 1. Thông tin đề tài

- Học phần: Mạng cảm biến
- Tên đề tài: Vision-FOMO Gesture Mouse Control
- Sinh viên thực hiện: Nguyễn Đăng Doanh
- MSSV: N23DCCI015
- Lớp: D23CQCI01-N
- Giảng viên hướng dẫn: Hồ Nhựt Minh

## 2. Mô tả đề tài

Đề tài xây dựng hệ thống điều khiển con trỏ ảo bằng cử chỉ bàn tay sử dụng mô hình Vision-FOMO trên nền tảng Edge Impulse.

Hệ thống sử dụng webcam trên trình duyệt để nhận diện trạng thái bàn tay. Mô hình AI nhận diện các lớp chính gồm:

- open_hand: bàn tay mở
- closed_hand: bàn tay khép
- no_hand: không có bàn tay

Từ kết quả nhận diện, chương trình xử lý vị trí tâm của bàn tay để điều khiển con trỏ ảo trong giao diện browser. Khi bàn tay mở, hệ thống theo dõi chuyển động để xác định thao tác kéo trái hoặc kéo phải. Khi bàn tay khép ổn định trong một khoảng thời gian ngắn, hệ thống xem đó là thao tác click.

## 3. Chức năng chính

- Nhận diện bàn tay theo thời gian thực bằng webcam.
- Phân loại trạng thái open_hand, closed_hand và no_hand.
- Điều khiển con trỏ ảo trong trình duyệt.
- Nhận biết thao tác kéo trái và kéo phải dựa trên chuyển động của bàn tay.
- Nhận biết thao tác click bằng cử chỉ khép tay.
- Hiển thị vùng LEFT, RIGHT và CLICK AREA để minh họa thao tác điều khiển.
- Chạy trực tiếp trên browser bằng WebAssembly export từ Edge Impulse.

## 4. Công nghệ sử dụng

- Edge Impulse
- FOMO Object Detection
- WebAssembly
- HTML, CSS, JavaScript
- Browser Webcam API
- Python HTTP Server

## 5. Cấu trúc thư mục

```text
VisionFOMO_Gesture_Mouse_Control/
│
├── README.md
│
├── web_demo/
│   ├── index.html
│   ├── index_old.html
│   ├── server.py
│   ├── edge-impulse-standalone.js
│   ├── edge-impulse-standalone.wasm
│   ├── run-impulse.js
│   └── README.md
│
├── screenshots/
│   ├── 01_edge_impulse_project/
│   ├── 02_data_acquisition/
│   ├── 03_labeling/
│   ├── 04_training/
│   ├── 05_confusion_matrix/
│   ├── 06_webassembly_export/
│   └── 07_realtime_browser_test/
│
└── report_assets/
    ├── figures/
    └── tables/