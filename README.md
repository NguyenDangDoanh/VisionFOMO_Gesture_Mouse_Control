# Vision-FOMO Gesture Mouse Control

## 1. Thông tin đề tài

* Học phần: Mạng cảm biến
* Tên đề tài: Vision-FOMO Gesture Mouse Control
* Sinh viên thực hiện: Nguyễn Đăng Doanh
* MSSV: N23DCCI015
* Lớp: D23CQCI01-N
* Giảng viên hướng dẫn: Hồ Nhựt Minh
* Repository: https://github.com/NguyenDangDoanh/VisionFOMO_Gesture_Mouse_Control

## 2. Mô tả đề tài

Đề tài xây dựng hệ thống điều khiển con trỏ ảo bằng cử chỉ bàn tay sử dụng mô hình Vision-FOMO trên nền tảng Edge Impulse.

Hệ thống sử dụng webcam trên trình duyệt để nhận diện trạng thái bàn tay theo thời gian thực. Mô hình AI được huấn luyện để nhận diện các lớp chính gồm:

* `open_hand`: bàn tay mở
* `closed_hand`: bàn tay khép
* `no_hand`: không có bàn tay hoặc không phát hiện được bàn tay

Sau khi nhận diện, chương trình xử lý vị trí tâm của bàn tay để điều khiển con trỏ ảo trong giao diện browser. Khi phát hiện `open_hand`, hệ thống theo dõi sự thay đổi vị trí tâm bàn tay qua nhiều khung hình để xác định thao tác kéo trái hoặc kéo phải. Khi phát hiện `closed_hand` ổn định trong một khoảng thời gian ngắn, hệ thống xem đó là thao tác click.

## 3. Mục tiêu đề tài

* Tìm hiểu quy trình xây dựng mô hình nhận diện bàn tay bằng Edge Impulse.
* Thu thập và gán nhãn dữ liệu ảnh cho các trạng thái bàn tay.
* Huấn luyện mô hình FOMO để nhận diện bàn tay theo thời gian thực.
* Export mô hình sang WebAssembly để chạy trực tiếp trên trình duyệt.
* Xây dựng giao diện demo điều khiển con trỏ ảo bằng webcam.
* Kiểm tra khả năng nhận diện các thao tác kéo trái, kéo phải và click.

## 4. Chức năng chính

* Nhận diện bàn tay theo thời gian thực bằng webcam.
* Phân loại trạng thái `open_hand`, `closed_hand` và `no_hand`.
* Hiển thị bounding box, nhãn nhận diện và độ tin cậy của mô hình.
* Điều khiển con trỏ ảo trong giao diện trình duyệt.
* Nhận biết thao tác kéo trái và kéo phải dựa trên chuyển động của bàn tay.
* Nhận biết thao tác click bằng cử chỉ khép tay.
* Hiển thị vùng LEFT, RIGHT và CLICK AREA để minh họa thao tác điều khiển.
* Chạy trực tiếp trên browser bằng mô hình WebAssembly export từ Edge Impulse.

## 5. Công nghệ sử dụng

* Edge Impulse
* FOMO Object Detection
* WebAssembly
* HTML, CSS, JavaScript
* Browser Webcam API
* Python HTTP Server
* Git/GitHub

## 6. Cấu trúc thư mục

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
└── screenshots/
    ├── 01_edge_impulse_project.png
    ├── 02_data_acquisition.png
    ├── 03_labeling.png
    ├── 04_training_confusion_matrix.png
    ├── 05_model_testing_success.png
    ├── 06_webassembly_export.png
    └── 07_realtime_browser_test.png
```

## 7. Cách chạy demo

### Bước 1: Clone repository

```bash
git clone https://github.com/NguyenDangDoanh/VisionFOMO_Gesture_Mouse_Control.git
```

### Bước 2: Di chuyển vào thư mục web demo

```bash
cd VisionFOMO_Gesture_Mouse_Control/web_demo
```

### Bước 3: Chạy server local

```bash
python server.py
```

Nếu không chạy được bằng `server.py`, có thể dùng lệnh thay thế:

```bash
python -m http.server 8082
```

### Bước 4: Mở trình duyệt

Truy cập địa chỉ:

```text
http://localhost:8082
```

hoặc:

```text
http://localhost:8082/index.html
```

### Bước 5: Cấp quyền webcam

Khi trình duyệt hỏi quyền sử dụng camera, chọn **Allow** hoặc **Cho phép**.

### Bước 6: Kiểm tra cử chỉ

* Đưa bàn tay mở trước camera để kiểm tra trạng thái `open_hand`.
* Di chuyển tay sang trái hoặc phải để kiểm tra thao tác kéo trái/kéo phải.
* Khép tay để kiểm tra thao tác click.
* Đưa tay ra khỏi khung hình để kiểm tra trạng thái `no_hand`.

## 8. Quy trình thực hiện

1. Tạo project trên Edge Impulse với dạng bài toán Object Detection.
2. Thu thập dữ liệu ảnh bàn tay.
3. Gán nhãn dữ liệu với các lớp `open_hand`, `closed_hand` và `no_hand`.
4. Thiết kế impulse cho bài toán nhận diện ảnh.
5. Huấn luyện mô hình FOMO.
6. Kiểm tra kết quả huấn luyện bằng F1 Score và confusion matrix.
7. Export mô hình sang WebAssembly.
8. Xây dựng giao diện browser demo bằng HTML, CSS và JavaScript.
9. Tích hợp webcam, xử lý ảnh đầu vào và gọi mô hình AI để phân loại.
10. Xử lý logic điều khiển con trỏ ảo, kéo trái, kéo phải và click.

## 9. Ghi chú kỹ thuật

Demo hiện tại điều khiển con trỏ ảo trong browser, chưa điều khiển trực tiếp con trỏ chuột thật của hệ điều hành. Lý do là trình duyệt có giới hạn bảo mật, không cho website tự ý điều khiển chuột thật của máy tính.

Để giảm rung và giảm nhận diện sai, chương trình sử dụng một số kỹ thuật xử lý:

* Làm mượt tọa độ con trỏ.
* Sử dụng vùng chết để bỏ qua dao động nhỏ.
* Sử dụng ngưỡng confidence cho kết quả nhận diện.
* Giữ lại kết quả nhận diện gần nhất trong một khoảng thời gian ngắn.
* Dùng debounce/cooldown cho thao tác click.
* Tính hướng kéo trái/phải dựa trên chuyển động của tâm bàn tay qua nhiều frame.

## 10. Kết quả đạt được

* Mô hình đã nhận diện được trạng thái `open_hand` và `closed_hand`.
* Demo browser chạy được bằng webcam trên máy tính.
* Hệ thống hiển thị được nhãn, độ tin cậy và vị trí tâm bàn tay.
* Con trỏ ảo di chuyển theo vị trí bàn tay.
* Hệ thống nhận biết được thao tác kéo trái, kéo phải và click trong giao diện demo.
* Mô hình đã được export sang WebAssembly để chạy trực tiếp trên trình duyệt.

## 11. Hạn chế

* Độ chính xác phụ thuộc vào ánh sáng, background và chất lượng webcam.
* Mô hình có thể nhận nhầm khi nền phía sau có nhiều vật thể giống bàn tay.
* Chưa điều khiển trực tiếp con trỏ chuột của hệ điều hành.
* Dataset vẫn có thể mở rộng thêm để tăng độ ổn định.
* Một số thao tác có thể bị nhiễu nếu tay di chuyển quá nhanh hoặc ra khỏi vùng camera.

## 12. Hướng phát triển

* Bổ sung thêm dữ liệu với nhiều điều kiện ánh sáng và background khác nhau.
* Thêm nhiều cử chỉ điều khiển hơn.
* Tối ưu mô hình để giảm nhận nhầm.
* Phát triển phiên bản điều khiển chuột thật bằng Python hoặc ứng dụng desktop.
* Triển khai trên thiết bị edge hoặc hệ thống nhúng.
* Cải thiện giao diện demo để phù hợp hơn cho trình bày và kiểm thử.

## 13. Tài liệu tham khảo

- [1] Edge Impulse, “FOMO - Edge Impulse Documentation.” https://docs.edgeimpulse.com/studio/projects/learning-blocks/blocks/object-detection/fomo
- [2] Edge Impulse, “Run WebAssembly library (browser).” https://docs.edgeimpulse.com/hardware/deployments/run-webassembly-browser
- [3] MDN Web Docs, “MediaDevices: getUserMedia() method.” https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices/getUserMedia
- [4] WebAssembly, “WebAssembly.” https://webassembly.org/
- [5] MDN Web Docs, “WebAssembly.” https://developer.mozilla.org/en-US/docs/WebAssembly
- [6] Edge Impulse, “Object detection with centroids.” https://docs.edgeimpulse.com/tutorials/end-to-end/object-detection-centroids
- [7] S. Hymel et al., “Edge Impulse: An MLOps Platform for Tiny Machine Learning,” arXiv:2212.03332, 2022.
