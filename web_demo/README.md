# Web Demo - Vision-FOMO Gesture Mouse Control

Thư mục này chứa source code demo chạy mô hình Vision-FOMO Gesture Mouse Control trên trình duyệt bằng WebAssembly.

## 1. Các file chính

- `index.html`: giao diện demo chính, hiển thị webcam, bounding box, gesture status và con trỏ ảo.
- `server.py`: server local dùng để chạy demo trên trình duyệt.
- `run-impulse.js`: file hỗ trợ gọi mô hình Edge Impulse.
- `edge-impulse-standalone.js`: thư viện JavaScript export từ Edge Impulse.
- `edge-impulse-standalone.wasm`: mô hình WebAssembly export từ Edge Impulse.
- `index_old.html`: bản giao diện cũ được giữ lại để tham khảo/backup.

## 2. Cách chạy demo

Mở terminal tại thư mục `web_demo`, sau đó chạy:

```bash
python server.py