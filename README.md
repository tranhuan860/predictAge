# predictAge
## Bộ dữ liệu: [UTKFace|Kaggle](https://www.kaggle.com/datasets/jangedoo/utkface-new)
- Bộ dữ liệu UTKFace là bộ dữ liệu khuôn mặt quy mô lớn với độ tuổi dài (từ 0 đến 116 tuổi). Bộ dữ liệu bao gồm hơn 20.000 hình ảnh khuôn mặt với chú thích về độ tuổi, giới tính và dân tộc. Các hình ảnh bao gồm sự thay đổi lớn về tư thế, nét mặt, độ sáng, độ che khuất, độ phân giải, v.v.. Kích thước các ảnh là 128x128 px.

<img src="https://img.upanh.tv/2024/06/08/imageab64c8c7ca5b3385.png">


## Cấu trúc mô hình

| Layer (type)                    | Output Shape           | Param #       |
|---------------------------------|------------------------|---------------|
| conv2d_3 (Conv2D)               | (None, 126, 126, 32)   |           896 |
| max_pooling2d_2 (MaxPooling2D)  | (None, 63, 63, 32)     |             0 |
| conv2d_4 (Conv2D)               | (None, 61, 61, 64)     |        18,496 |
| max_pooling2d_3 (MaxPooling2D)  | (None, 30, 30, 64)     |             0 |
| conv2d_5 (Conv2D)               | (None, 28, 28, 128)    |        73,856 |
| flatten_1 (Flatten)             | (None, 100352)         |             0 |
| dense_2 (Dense)                 | (None, 128)            |    12,845,184 |
| dropout_1 (Dropout)             | (None, 128)            |             0 |
| dense_3 (Dense)                 | (None, 1)              |           129 |

 ```
Total params: 12,938,561 (49.36 MB)
 Trainable params: 12,938,561 (49.36 MB)
 Non-trainable params: 0 (0.00 B)
```

- Cấu hình mô hình với optimizer Adam, hàm tổn thất MAE, metrics là MSE

- Huấn luyện mô hình với 25 epochs
<img src="https://img.upanh.tv/2024/06/08/imageda8bfd1a0ddde0f3.png">

- Độ chính xác chưa cao lắm do bộ thiếu dữ liệu huấn luyện nhưng về cơ bản đã đạt đủ yêu cầu ban đầu
- Loss = Chênh lệch giữa trung bình tuổi dự đoán và tuổi thật
  
<img src="https://img.upanh.tv/2024/06/08/image4d919b1c24bd7065.png">
- Nhận thấy từ 70 tuổi trở lên Loss cao do ít dữ liệu huấn luyện

## Các bước cài đặt:
### Bước 1:
- Clone repository này về máy
### Bước 2:
- Tải bộ dữ liệu để huấn luyện từ [UTKFace|Kaggle](https://www.kaggle.com/datasets/jangedoo/utkface-new) rồi giải nén vào folder "data". Huấn luyện mô hình bằng cách chạy file train.ipynb 
- Hoặc có thể tải mô hình đã được huẩn luyện từ [link Driver](https://drive.google.com/drive/folders/1NTPS5FcQejuK8OiXe1Zn1E2CeiHj0Eh5?usp=drive_link)
### Bước 3:
- Cài đặt các thư viện cần thiết
- Chạy file predict.ipynb
- Ấn phím q để thoát, p để dự đoán

