# Mini guideline — bài làm cá nhân

> Điền nội dung này trước khi bắt đầu gán nhãn. Giữ lại các quyết định sau khi self-QC.

## Định nghĩa lớp

| Lớp | Định nghĩa của bạn | Ví dụ/điểm phân biệt |
| --- | --- | --- |
| `car` 	|	Xe nhỏ, chở ít người 			|	Xe ô tô, trên thân 2 bên có 2 hoặc 3 cửa sổ	|
| `truck` 	| 	Xe chở hang hóa 			|	Xe tải có thùng chở hang đằng sau hoặc container	|
| `bus` 	|	Xe to, dài, chở được nhiều người	|	Xe có nhiều cửa sổ bên hông, thân lớn	|
| `van` 	|	Xe có khoang kín, có thể chở người hoặc hang hóa	|	Xe van, có khoang đằng sau, hình hộp hơn xe hơi, kính đằng sau to	|

## Quy tắc chung

- Box bám sát vật thể nghĩa là: Bbox bao quanh toàn bộ phần nhìn thấy được của vật thể.
- Vật thể bị che khuất: Vẽ box theo phần có thể nhìn thấy được của vật thể, không tự suy đoán hoặc ước lượng.
- Vật thể bị cắt bởi rìa ảnh: Kéo box đền rìa ảnh tại vị trí vật bị cắt.
- Vật thể rất nhỏ/mơ hồ: Nếu đủ thông tin gán nhãn thì gán, không thì đánh dấu để escalation

## Ghi lại quyết định cho ít nhất ba ca mơ hồ

| Ảnh | Tình huống | Quyết định cuối | Lý do theo schema |
| --- | --- | --- | --- |
| `drive_044` | Xe di chuyển nhanh, bị nhòe | Đống khung cả phần nhòe | Vẫn đủ thông tin để biết đó là phương tiện gì |
| `drive_003` | Có nhiều xe nhỏ ở xa, nói đuôi nhau, chắc chắn có xe nhưng không biết bao nhiêu xe| Không gán nhãn vì không đủ thông tin để phân loại xe | |
| `drive_005` | Có nhiều xe nhỏ ở xa, khó phân loại, không biết có bao nhiêu xe | Không gán nhãn, không đủ thông tin phân loại xe | |
