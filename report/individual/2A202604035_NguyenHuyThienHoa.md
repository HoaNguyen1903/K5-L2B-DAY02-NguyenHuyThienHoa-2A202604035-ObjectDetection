# Báo cáo cá nhân — Ngày 2 Object Detection

Đổi tên file theo `MSSV_HoTen.md`, ví dụ `20241234_NguyenVanAn.md`. Điền kết quả thật, xóa dòng hướng dẫn khi nộp. Xem [quy định nộp](../../SUBMISSION.md).

## 1. Thông tin học viên

- Họ tên:Nguyễn Huy Thiên Hòa
- MSSV:2A202604035
- Email:hoa76lqd@gmail.com
- Lớp:L2B
- Link repo bài làm:https://github.com/HoaNguyen1903/K5-L2B-DAY02-NguyenHuyThienHoa-2A202604035-ObjectDetection
- Link Colab đã chạy:https://colab.research.google.com/github/HoaNguyen1903/K5-L2B-DAY02-NguyenHuyThienHoa-2A202604035-ObjectDetection/blob/main/notebooks/day2_annotation_to_yolo.ipynb#scrollTo=3e0508d8

## 2. Schema và mini guideline

Dẫn tới [GUIDELINE_MINI.md](../../GUIDELINE_MINI.md). Tóm tắt ba ca mơ hồ đã quyết định, cách áp dụng schema và phần cần giảng viên làm rõ.

https://github.com/HoaNguyen1903/K5-L2B-DAY02-NguyenHuyThienHoa-2A202604035-ObjectDetection/blob/main/GUIDELINE_MINI.md

## 3. Annotation và self-QC

- Số file nhãn train:
- Kết quả checker và lỗi đã xử lý:
- Danh sách ít nhất 10 ảnh đã rà bằng mắt:
- Lỗi bỏ sót/box/class phát hiện khi rà và cách sửa:
- Commit khóa nhãn ban đầu:

## 4. Gold QC và rework

| Chỉ số | Trước sửa | Sau sửa nếu có |
|---|---:|---:|
| TP | 482 | 526 |
| FP | 764 | 174 |
| FN | 171 | 127 |
| Precision | 0.3868 | 0.7514 |
| Recall | 0.7381 | 0.8055 |
| F1 | 0.5076 | 0.7775 |
| mean_iou_of_matches | 08469 | 0.8468 |
| passed | false | false |

Dẫn tới `outputs/annotation_evaluation.json` trong repo. Nếu rework, ghi ảnh, lỗi đã kiểm, quyết định sửa/giữ và lý do. Không suy nguyên nhân chỉ từ FP/FN. Không có rework thì ghi rõ.

https://github.com/HoaNguyen1903/K5-L2B-DAY02-NguyenHuyThienHoa-2A202604035-ObjectDetection/blob/main/outputs/annotation_evaluation.json

Đã reworked : 001, 002, 003, 004, 005, 006, 007, 008, 009, 011, 012, 013, 014, 015, 016, 017, 018, 019, 020, 021, 024, 026, 027, 028, 029, 030, 031, 033, 038, 039, 040, 041, 042, 043, 044, 045, 046, 048, 049, 050. 
Lỗi : xe bị mờ do ở xa
Quyết định : bỏ khung những xe bị mờ do ở xa
Lý do : Lúc đầu được bảo xe nào nhìn thấy thì khoanh, dẫn đến gấp đôi số lượng khung so với gold, FP cũng cao theo.

## 5. Kết quả YOLO

- Runtime, GPU/CPU, phiên bản Ultralytics và Torch: T4 GPU, Ultralytics 8.4.208, Torch 2.14.1
- Các tham số thay đổi so với notebook nếu có và lý do:
- Đường dẫn best checkpoint trong phiên chạy: /content/Day2-Lab/outputs/yolo26_runs/vehicle_annotation/weights/best.pt

| Chỉ số trên 10 ảnh eval | Giá trị |
|---|---:|
| Precision | 0.2977136245150981 |
| Recall | 0.4147163120567376 |
| mAP50 | 0.34425922047650576 |
| mAP50–95 | 0.23358266322804927 |

Đặt cả 2 folder `assets/eval_predictions/` và `assets/yolo26_runs/` (giải nén từ `day2_colab_outputs.zip`) cạnh báo cáo và dẫn link tương đối. Không chỉ ghi số; chỉ ra ít nhất một ảnh và vật thể cụ thể.

Trả lời bốn câu hỏi cuối notebook:

1. Lớp nào recall thấp nhất? Ảnh nào minh họa?
- Lớp bus recall thấp nhất, drive_060.
2. Nếu mAP50 cao nhưng mAP50–95 thấp, cần kiểm điều gì trên box?
- mAP50 cao nhưng mAP50-95 thấp là đúng vật thể và lớp, nhưng box chưa sát. Kiểm tra lại xem box đã đúng guidelines và sát phần nhìn thấy được của vật thể chưa
3. Lỗi class nào có thể liên quan guideline? Dữ kiện nào hỗ trợ nhận xét? 
4. Vì sao không dùng 10 ảnh eval để train? Vai trò validation của chúng trong notebook là gì? 
- Ảnh eval là ảnh để test, nếu dùng để train thì model sẽ ghi nhớ và cho số liệu quá tốt trong khi thực tế không phải như vậy, giống như học đề tủ.
- Vai trò validation trong notebook là log tiến trình cho phép theo dõi, chọn best.pt và tổng kết đánh giá.

## 6. Khó khăn và cách xử lý

| Bước/thời điểm | Lỗi quan sát | Cách đã thử | Kết quả/còn thiếu |
|---|---|---|---|
| | | | |

## 7. Tự đánh giá theo rubric

Đối chiếu [RUBRIC.md](../../RUBRIC.md): phần nào đã có kết quả, phần nào còn thiếu hoặc chưa kiểm được. Không tự nhận hoàn thành bước chưa chạy.
- FN/FP chưa đạt, nếu gán đủ xe thuộc schema, kể cả xe che/cắt khung có thể nhận diện thì fail check, còn gán mà pass check thì không đủ xe

## 8. Công cụ AI và tài liệu tham khảo

Ghi công cụ đã dùng, dùng ở bước nào và phần đã tự kiểm tra; không dùng thì ghi rõ. Liệt kê nguồn ngoài repo được sử dụng. Không ghi mật khẩu/token hoặc đính kèm gold train.
