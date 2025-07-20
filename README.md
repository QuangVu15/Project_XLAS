# Hướng dẫn chạy Notebook

Notebook này thực hiện một số xử lý liên quan đến ảnh và mô hình học sâu. Để chạy được notebook, bạn cần cài đặt các thư viện cần thiết và sử dụng Jupyter Notebook hoặc Google Colab.

## Cài đặt thư viện

Chạy đoạn lệnh sau để cài đặt các thư viện cần thiết:

```bash
pip install numpy opencv-python matplotlib tensorflow
```

```hoặc trực tiếp từ Jupyter Notebook 
!pip install opencv-python numpy matplotlib tensorflow
```

## Hướng dẫn chạy

1. Mở Jupyter Notebook hoặc Google Colab.
2. Tải notebook `.ipynb` lên.
3. Chạy tuần tự từng cell để thực hiện xử lý.

## Thư viện sử dụng

- `numpy`: xử lý mảng số liệu
- `opencv-python`: đọc và xử lý ảnh
- `matplotlib`: hiển thị ảnh
- `tensorflow`: sử dụng cho mô hình học sâu nếu có


## Nhận diện khuôn mặt bằng phương pháp Haar_Cascade_Recognition

🧠 Chức năng chính
- Chương trình cho phép nhận diện khuôn mặt bằng thuật toán Haar Cascade trong thư viện OpenCV với 3 chế độ:

1. 🎥 Nhận diện từ Webcam
- Mở webcam máy tính.
- Tự động quét liên tục các khung hình.
- Vẽ khung quanh khuôn mặt và hiển thị văn bản “Face detected”.
- Lưu các khung hình có khuôn mặt vào thư mục resuilt_haar_cascade/.
- Ghi log phát hiện vào file log.txt.
- Nhấn e hoặc Esc để thoát.

2. 🖼️ Nhận diện từ Ảnh
- Nhập đường dẫn tới ảnh.
- Phát hiện và vẽ khung quanh các khuôn mặt trong ảnh.
- Hiển thị kết quả.
- Lưu ảnh đã nhận diện vào thư mục result/.

3. 📹 Nhận diện từ Video
- Nhập đường dẫn tới file video.
- Quét từng khung hình để nhận diện khuôn mặt.
- Vẽ khung mặt và hiển thị.
- Tự động lưu các khung có chứa khuôn mặt vào thư mục result/.

📂 Cấu trúc thư mục đầu ra
| Thư mục                 | Mô tả                                                    |
| ----------------------- | -------------------------------------------------------- |
| `result/`               | Lưu ảnh đầu ra từ ảnh và video                           |
| `resuilt_haar_cascade/` | Lưu ảnh từ webcam có chứa khuôn mặt                      |
| `log.txt`               | Ghi log thời gian và số khuôn mặt đã phát hiện từ webcam |


✅ Ghi chú
- Sử dụng mô hình haarcascade_frontalface_default.xml có sẵn trong OpenCV để nhận diện khuôn mặt.
- Dừng quét webcam bằng phím e hoặc Esc.

## Nhận diện khuôn mặt bằng phương pháp Deepface_Recognition
🧠 Chức năng chính của chương trình
- Chương trình sử dụng DeepFace để phân tích giới tính, độ tuổi, và cảm xúc từ ảnh, video hoặc webcam.

1. 🖼️ Phân tích từ Ảnh
- Nhập đường dẫn đến ảnh.
- Phân tích các khuôn mặt và hiển thị:
- Tuổi (age)
- Giới tính (gender)
- Cảm xúc (emotion)
- Vẽ khung và thông tin lên khuôn mặt.
- Lưu ảnh kết quả vào thư mục result_deepface/.

2. 📹 Phân tích từ Video
- Nhập đường dẫn đến video.
- Đọc từng frame của video, thực hiện phân tích khuôn mặt.
- Ghi từng frame kết quả vào thư mục result_deepface/.
- Nhấn q để dừng nếu có giao diện hiển thị (GUI).

3. 🎥 Phân tích từ Webcam
- Mở webcam để phát hiện khuôn mặt theo thời gian thực.
- Với mỗi khuôn mặt được phát hiện:
- Phân tích tuổi, giới tính và cảm xúc.
- Hiển thị và vẽ kết quả trực tiếp lên khung hình.
- Tự động lưu ảnh chứa khuôn mặt vào thư mục result_deepface/.
- Nhấn e hoặc Esc để kết thúc.

📂 Cấu trúc thư mục đầu ra
| Thư mục            | Mô tả                                     |
| ------------------ | ----------------------------------------- |
| `result_deepface/` | Lưu ảnh phân tích từ ảnh, video và webcam |


🧩 Ghi chú kỹ thuật
- Sử dụng enforce_detection=False để tránh lỗi nếu không phát hiện được khuôn mặt.
- Có xử lý tự động kiểm tra môi trường hiển thị (GUI) để tránh lỗi trên Linux server không có màn hình.
- Sử dụng thư viện DeepFace để phân tích ba đặc điểm chính:
        - Age: độ tuổi ước lượng
        - Gender: giới tính
        - Emotion: cảm xúc chủ đạo

## So sánh phương pháp Deepface_Recognition và Haar_Cascade_Recognition
🧠 Chức năng chính của chương trình
Chương trình cho phép so sánh trực quan hai phương pháp phát hiện và phân tích khuôn mặt:
 - Haar Cascade: dùng để phát hiện vị trí khuôn mặt.
 - DeepFace: phát hiện và phân tích khuôn mặt (tuổi, giới tính, cảm xúc).
Các khung hình đầu ra sẽ ghép song song:
 - Bên trái: kết quả từ Haar Cascade (màu xanh lá, nhãn “Haar”).
 - Bên phải: kết quả từ DeepFace (màu xanh dương, hiển thị thông tin phân tích).

⚙️ Các chế độ hoạt động
1. 🖼️ So sánh từ ảnh
- Nhập đường dẫn ảnh.
- Chương trình xử lý và hiển thị kết quả nhận diện từ cả 2 phương pháp.
- Ảnh đầu ra được lưu vào thư mục result_compare/.

2. 📹 So sánh từ video
- Nhập đường dẫn đến video.
- Mỗi khung hình được xử lý với cả Haar và DeepFace.
- Từng khung ảnh kết quả được lưu vào thư mục result_compare/.

3. 🎥 So sánh từ webcam
- Sử dụng webcam để so sánh thời gian thực.
- Tự động lưu từng khung hình có kết quả so sánh vào result_compare/.
- Nhấn e hoặc ESC để thoát chế độ webcam.

📂 Thư mục đầu ra
| Thư mục           | Nội dung                                   |
| ----------------- | ------------------------------------------ |
| `result_compare/` | Lưu ảnh đầu ra đã ghép từ Haar và DeepFace |


🧩 Ghi chú kỹ thuật
- Sử dụng cv2.hconcat() để ghép ảnh Haar và DeepFace.
- Hàm is_gui_available() giúp chương trình chạy được trên các môi trường không có giao diện hiển thị (Linux headless).
- DeepFace sử dụng enforce_detection=False để tránh lỗi nếu không phát hiện được khuôn mặt.