B1: Git clone link repo git hub -> cd face-recognition
B2:
Tạo thư mục Dataset trong face-recognition, trong đó tạo tiếp thư mục FaceData và dưới FaceData là tạo tiếp 2 thư mục raw và processed.
Tạo thư mục Models trong face-recognition để chờ sẵn tẹo lưu model sau.
B3:
Bây giờ các bạn sưu tầm ảnh của 2 người trở lên, mỗi người 10 tấm hình rõ mặt (tạm chấp nhận yêu cầu hiện tại của bài này là at least 2 người nhé, mình sẽ tìm hiểu thêm sau). Mình ví dụ 2 người tên là NguyenVanA và LeThiB nhé. Các bạn tạo 02 thư mục NguyenVanA và LeThiB trong thư mục raw và copy ảnh của 2 người vào riêng 2 thư mục đó, ảnh của ai vào thư mục của người đó nhé.
VD:
|-FaceData
   |---processed
   |-----bao
   |-----thinh
   |---raw
   |-----bao
   |-----thinh
   
B4: Cài đặt các thư viện cần thiết

B5:Tiền xử lý dữ liệu để cắt khuôn mặt từ ảnh gốc

python src/align_dataset_mtcnn.py  Dataset/FaceData/raw Dataset/FaceData/processed --image_size 160 --margin 32  --random_order --gpu_memory_fraction 0.25

B6: Tải dữ liệu pretrain của Facenet về máy:

Link: https://drive.google.com/file/d/1EXPBSXwTaqrSC0OhUdXNmKSh9qJUQ55-/view

B7: Tiến hành train model để nhận diện khuôn mặt

python src/classifier.py TRAIN Dataset/FaceData/processed Models/20180402-114759.pb Models/facemodel.pkl --batch_size 1000

B8: Kiểm thử với webcam:

python src/face_rec_cam.py 

B9: Nhấn phím 'Q' để thoát chương trình
