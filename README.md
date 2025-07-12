# 🚦 Đề tài: Nhận diện biển báo bằng YOLO và ứng dụng Android

## 🎓 Trường ĐH Công Nghiệp TP.HCM – Khoa Công Nghệ Thông Tin  
**Lớp:** DHKHMT17B  
**GV Hướng Dẫn:** Võ Quang Hoàng Khang  
**Năm học:** 2025

## 👨‍👩‍👦 Thành viên nhóm 5

| Họ tên            | MSSV      |
|-------------------|-----------|
| Chau Tiểu Long    | 21094341  |
| Nguyễn Nhật Tùng  | 21096911  |

---

## 🧠 Mục tiêu đề tài

Xây dựng mô hình **nhận diện biển báo giao thông theo thời gian thực** bằng YOLOv5, YOLOv8 và YOLO11, sau đó **triển khai mô hình vào ứng dụng Android** sử dụng TensorFlow Lite (TFLite).

- Input: Video từ camera điện thoại gắn trên xe máy
- Output: Bounding box + tên biển báo hiển thị trực tiếp

---

## 🗃️ Xây dựng dữ liệu

- Thu thập dữ liệu bằng điện thoại gắn xe máy, trích xuất ảnh từ video
- Dữ liệu được label bằng Roboflow
- Tổng cộng **7536 ảnh**, **51 lớp nhãn**, sau khi làm sạch

### ✨ Các bước xử lý:
- Xóa ảnh mờ / khuất
- Tăng sáng và tương phản cho ảnh tối
- Chuyển đổi định dạng ảnh thống nhất (JPG/PNG)

---

## 🤖 Mô hình YOLO sử dụng

| Mô hình  | Precision | Recall | mAP@50 |
|----------|-----------|--------|--------|
| YOLOv5   | 0.934     | 0.913  | 0.951  |
| YOLOv8   | 0.934     | 0.914  | 0.953  |
| YOLO11   | **0.937** | **0.923** | **0.956** |

👉 **YOLO11** cho kết quả tốt nhất, YOLOv5 nhẹ và phù hợp mobile, YOLOv8 tối ưu mở rộng.

---

## 🛠️ Huấn luyện mô hình

- Sử dụng Kaggle và máy cá nhân (RTX 3050, CUDA 12.4)
- Framework: Ultralytics (YOLOv5/8/11)
- Cấu hình:
  - Epoch: 30
  - Image size: 640x640
  - Batch: 8

---

## 📲 Ứng dụng vào Android

- Chuyển mô hình `.pt` sang `.tflite`  
- Tích hợp với Android Studio sử dụng **CameraX** và **TFLite Interpreter**

### ⚙️ Tham số model:
- **Input**: `[1, 640, 640, 3]` (RGB)
- **Output**: `[1, 25200, 63]` (anchor boxes + classes)

### 📱 Giao diện:
- Vẽ bounding box + tên biển báo bằng `OverlayView`
- Tối ưu tốc độ và độ chính xác với Non-Max Suppression và CONF_THRESH

---

## 📈 Đánh giá mô hình

- Độ đo: **mAP@50**, **Precision**, **Recall**
- YOLO11 có kết quả cao nhất
- Mô hình chạy thời gian thực tốt trên điện thoại Android

---

## 🔗 Tài liệu tham khảo

- Cục CSGT – Bộ Công An (2019)
- Ultralytics YOLOv5, v8, YOLO11 Documentation
- https://docs.ultralytics.com/
- https://github.com/AarohiSingla/Object-Detection-Android-App

---

## 📎 Tham khảo file đầy đủ

👉 File báo cáo chi tiết: `BaoCao.docx` _(có thể tải tại thư mục `/`)_
