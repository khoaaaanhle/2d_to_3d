# Depth-based Defect Detection from 2D Images

## Giới thiệu
Dự án này sử dụng **camera 2D** để thu thập hình ảnh sản phẩm, sau đó áp dụng **thuật toán ước lượng độ sâu (Depth Estimation)** nhằm tái tạo thông tin **3D (chiều sâu)** từ ảnh 2D.  
Từ dữ liệu độ sâu, hệ thống tiến hành **so sánh – phân tích – phát hiện khuyết tật** dựa trên sự khác biệt giữa các vùng quan tâm (ROI).

---

## Dữ liệu đầu vào

### Ảnh gốc (sản phẩm bình thường)
![20251211_024107_433_front_CAM1](https://github.com/user-attachments/assets/7ccc940c-0817-44ab-aba6-02b62273a0aa)

### Ảnh sản phẩm bị vỡ / khuyết tật (có thay đổi chiều sâu)
![20251211_024107_433_result_CAM1](https://github.com/user-attachments/assets/06e563b1-c321-4e79-aa7f-f5c5bf676f46)

Hai ảnh được sử dụng để:
- Ước lượng bản đồ độ sâu (depth map)
- Chia vùng ROI thành các ô lưới (grid)
- So sánh giá trị độ sâu giữa ảnh gốc và ảnh lỗi

---

## Quy trình xử lý

1. Đọc ảnh RGB từ camera
2. Dự đoán **Depth Map** từ ảnh 2D
3. Chia từng ROI thành các ô lưới (grid-based depth)
4. Tính hiệu độ sâu giữa:

5. Xác định các ô có **giá trị âm (diff < 0)** – biểu thị vùng khuyết tật
6. Đánh dấu và hiển thị trực quan trên ảnh gốc

---

## Kết quả đầu ra

Sau khi hoàn thành các thuật toán, hệ thống sinh ra các kết quả trong thư mục:

raw_depth_output/



Bao gồm:
- Ảnh depth thô (raw depth)
- Các file trung gian phục vụ phân tích

### Kết quả cuối cùng – Nhận dạng khuyết tật
<img width="540" height="960" alt="result_diff_negative_cells" src="https://github.com/user-attachments/assets/af395801-2924-4348-a100-3e3786e290bc" />

Ảnh kết quả:
- Hiển thị vùng ROI
- Các ô lưới có độ sâu bất thường được **đánh dấu màu đỏ**
- Giá trị chênh lệch độ sâu được ghi trực tiếp trên ảnh

---

## Ứng dụng
- Phát hiện vỡ, lõm, khuyết tật bề mặt
- Kiểm tra chất lượng sản phẩm công nghiệp
- Hỗ trợ hệ thống thị giác máy (Machine Vision) dựa trên chiều sâu

---

## Ghi chú
- Hệ thống **không cần camera 3D** chuyên dụng
- Có thể mở rộng cho nhiều ROI, nhiều ảnh, hoặc xuất dữ liệu CSV phục vụ phân tích thống kê

---

