# Bài tập 2 - Đặc trưng góc và phân vùng ảnh

Môn Xử lý ảnh & Thị giác máy tính (121036).

**Hoàn thành nội bộ: thứ Tư, 18/11/2026. Hạn nộp: thứ Sáu, 20/11/2026.**

## Mở đúng bài

Mở thư mục repo này bằng VS Code, sau đó mở notebook trong `bai_tap_2/`. Bài tập 2 được làm riêng; notebook và ảnh của bài trước ở ngoài thư mục này được giữ nguyên.

```text
bai_tap_2/
├── bt2_nhom.ipynb             # Hiệp gộp các phần đã duyệt để nộp
├── lam_viec/
│   ├── bt2_gam.ipynb          # Harris cơ bản, repeatability, rà số đo
│   ├── bt2_nam.ipynb          # Harris-Laplace
│   ├── bt2_len.ipynb          # ANMS và Top-N
│   ├── bt2_sen.ipynb          # Region Growing, seed_sensitivity
│   └── bt2_hiep.ipynb         # SRG, ảnh tiến trình, gộp bài
├── anh/                      # Ảnh đầu vào dùng chung và nộp kèm
├── ket_qua/                  # Ảnh/biểu đồ xuất thử, không theo dõi bằng Git
├── tai_lieu/
│   ├── Computer_Vision_45.pdf
│   ├── phan_cong_bai_tap_2_ban_sua.pdf
│   └── phan_cong_bai_tap_2_ban_sua.xlsx
└── requirements.txt
```

## Môi trường

Dùng môi trường Python của nhóm nếu đã có đủ thư viện. Nếu cần tạo môi trường mới, chạy tại thư mục gốc repo:

```bash
python3 -m venv bai_tap_2/.venv
source bai_tap_2/.venv/bin/activate
python -m pip install -r bai_tap_2/requirements.txt
```

Trong VS Code, chọn **Select Kernel** của notebook và chọn môi trường vừa cài. Có thể mở bằng JupyterLab:

```bash
python -m jupyter lab bai_tap_2/
```

Cell chuẩn bị của từng notebook xác định thư mục Bài tập 2 từ thư mục chạy hiện tại, để dùng được khi kernel mở ở gốc repo, `bai_tap_2/` hoặc `bai_tap_2/lam_viec/`. Dùng `ANH_DIR / "ten_anh.png"` để đọc ảnh và `KET_QUA_DIR / "ten_ket_qua.png"` để lưu kết quả.

## Quy trình của nhóm

1. Pull thay đổi mới từ `main`, chuyển sang nhánh của mình theo bảng phân công.
2. Chỉ làm trong `lam_viec/bt2_<ten>.ipynb` và thêm ảnh cần dùng vào `anh/`.
3. Khi cần hàm người khác, lấy bản đã được duyệt và ghi rõ nguồn. Notebook cá nhân phải tự chạy được; không thực thi toàn bộ notebook của người khác để lấy biến.
4. Tự kiểm tra, lưu output, mở Pull Request về `main` và cập nhật trạng thái trong bảng phân công.
5. Chỉ Hiệp gộp nội dung đã duyệt vào `bt2_nhom.ipynb`, chỉ giữ một bản định nghĩa mỗi hàm dùng chung.

Nhánh thành viên theo bảng phân công đã sửa: `bt2-gam`, `bt2-nam`, `bt2-len`, `bt2-sen`, `bt2-hiep`. Đây là quy ước tên; các nhánh đó chưa được tạo bởi bộ khung này.

## Nội dung từng người

| Thành viên | Hàm phụ trách | Kiểm chứng chính |
| --- | --- | --- |
| Hồng Gấm | `gaussian_blur`, `structure_tensor`, `harris_response`, `nms_2d`, `harris_classic`, `repeatability` | A1, A2, A4: bàn cờ, xoay 30 độ, đối chiếu OpenCV |
| Huỳnh Nam | `scale_pyramid`, `log_normalized`, `harris_laplace` | A3: ảnh phóng to 3 lần |
| Tấn Lên | `anms`, `top_n`; dùng hoặc bổ sung `grid_occupancy` theo đề | A5: Top-N và ANMS cùng ứng viên, cùng N |
| Hồng Sen | `region_growing_classic`, `seed_sensitivity` | B1-B4: nhãn đầy đủ, số vùng, đảo seeds, stack/queue/SRG |
| Tấn Hiệp | `srg`, `srg_step_frames` | B5: ảnh phẳng; lazy/frozen, phá hòa và ảnh tiến trình |

Mã A1-A5, B1-B5 trong cột kiểm chứng là số thứ tự ở mục 3.7 và 4.5 của đề, không phải tên hai biến thể A1/A2.

## Các mốc bàn giao

| Mốc | Kết quả cần có |
| --- | --- |
| 11/11 | Gấm bàn giao 5 hàm Harris; Hiệp bàn giao giao diện SRG cho Sen |
| 12-13/11 | Hoàn thành các hàm, đúng giao diện đã thống nhất |
| 14/11 | Đủ 5 kiểm chứng A và 5 kiểm chứng B, có output |
| 16/11 | Đủ 3 cặp thí nghiệm và số đo, quét tham số, giải thích |
| 17-18/11 | Duyệt chéo, gộp, chạy lại và đóng gói hoàn chỉnh |

Chi tiết sản phẩm, người duyệt và tài liệu cần đọc nằm trong `tai_lieu/phan_cong_bai_tap_2_ban_sua.xlsx`.

## Phạm vi bộ khung và quy định của đề

Bộ khung do Codex tạo theo yêu cầu của nhóm: thư mục, bố cục notebook, cell chuẩn bị môi trường và mẫu khai báo prompt. Các cell cài đặt thuật toán được để trống. Chưa có thuật toán, thí nghiệm đã chạy hoặc kết quả để báo cáo.

Theo mục 2.1 của đề, phần **Cài đặt - KHÔNG dùng AI** do từng thành viên tự viết, bao gồm việc sửa lỗi. Để trống các cell đó cho tới khi tự thực hiện. Chỉ những cell thí nghiệm thực tế dùng AI mới cần điền prompt nguyên văn trong cell markdown ngay phía trên; không ghi một prompt chung thay cho nhiều yêu cầu khác nhau. Ý tưởng thí nghiệm và kết luận do thành viên quyết định.

`scipy.ndimage.gaussian_filter` được phép cho bước làm mờ. Các hàm dựng sẵn phát hiện góc/phân vùng chỉ dùng trong cell đối chiếu theo quy định của đề. Không dùng chúng để thay thuật toán phải tự cài đặt.

## Trước khi nộp

- Gộp đủ 15 hàm, 10 kiểm chứng và 3 cặp so sánh vào một notebook.
- Chạy **Restart & Run All**, sửa lỗi, lưu notebook cùng output.
- Dùng đường dẫn tương đối và nộp kèm thư mục `anh/` có đủ ảnh được notebook sử dụng.
- Nếu notebook đọc thêm tệp từ `ket_qua/`, chuyển tệp cần thiết vào thư mục nộp và kiểm tra lại đường dẫn.
- Xác nhận tên notebook trên LMS: đề Bài tập 2 ghi tên mẫu `bt1_<Nhom>.ipynb`. `bt2_nhom.ipynb` hiện là tên làm việc của nhóm.
