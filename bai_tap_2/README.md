# Bài tập 2

Hoàn thành nội bộ: **18/11/2026**. Hạn nộp: **20/11/2026**.

## Làm ở đâu?

- `bt2_nhom.ipynb`: Hiệp gộp các phần đã duyệt thành một notebook nộp bài.
- `lam_viec/bt2_gam.ipynb`: Harris cơ bản, repeatability, rà số đo.
- `lam_viec/bt2_nam.ipynb`: Harris-Laplace.
- `lam_viec/bt2_len.ipynb`: ANMS và Top-N.
- `lam_viec/bt2_sen.ipynb`: Region Growing, seed_sensitivity.
- `lam_viec/bt2_hiep.ipynb`: SRG và ảnh tiến trình.
- Ảnh dùng chung nằm ở **`images/` tại gốc repo**, cùng chỗ với bài trước.

Cell chuẩn bị đã có `IMAGES_DIR`. Ví dụ đường dẫn ảnh: `IMAGES_DIR / "ten_anh.png"`. Ảnh và biểu đồ kết quả hiển thị trực tiếp trong output notebook; không cần thư mục kết quả riêng.

## Môi trường và cách làm

Trong VS Code, mở notebook của mình và chọn kernel Python có đủ thư viện. Nếu môi trường hiện tại còn thiếu, chạy tại gốc repo:

```bash
python -m pip install -r bai_tap_2/requirements.txt
```

Mỗi người làm trên nhánh của mình, lưu output, mở Pull Request; chỉ Hiệp gộp vào notebook chung. Nhánh theo bảng phân công: `bt2-gam`, `bt2-nam`, `bt2-len`, `bt2-sen`, `bt2-hiep`.

Gấm bàn giao Harris ngày 11/11; Hiệp bàn giao giao diện SRG cho Sen ngày 11/11. Hoàn thành kiểm chứng ngày 14/11, thí nghiệm ngày 16/11, duyệt và gộp bài ngày 17-18/11.

## Quy định và bản nộp

Bộ khung do Codex tạo chỉ có bố cục và cell chuẩn bị. Các ô cài đặt thuật toán để trống cho thành viên tự viết theo đề. Cell thí nghiệm thực tế có dùng AI phải ghi prompt nguyên văn trong cell markdown ngay phía trên.

Khi làm trong repo, nhóm dùng chung `images/`. **Khi đóng gói nộp**, mục 2.3 của đề yêu cầu một notebook có output và thư mục `anh/` nộp cùng. Khi đó chỉ chép những ảnh Bài tập 2 thực sự dùng từ `images/` sang `anh/`, sửa đường dẫn của bản nộp rồi chạy lại. Không cần chép toàn bộ ảnh bài cũ.

Trước khi nộp: đủ 15 hàm, 10 kiểm chứng, 3 cặp thí nghiệm; chạy **Restart & Run All**, lưu output và xác nhận tên file trên LMS (đề Bài tập 2 ghi mẫu `bt1_<Nhom>.ipynb`).
