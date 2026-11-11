# Báo cáo thực hành Day 3 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên [LMS](https://aithucchien.vinuni.edu.vn). Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](../../reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202603276
- Ngày / CVAT local: 11/11/2026 - CVAT local v2.74.1 (Docker)
- Công cụ đã dùng: Brush/Polygon trong CVAT

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh [LMS](https://aithucchien.vinuni.edu.vn) đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | cp5_occlusion.zip | 1 / 1 | 3 |
| cp3_thin | cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | cp4_curb.zip | 1 / 1 | 3 |
| cp6_coverage | cp6_coverage.zip | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: ảnh 000000181542.jpg, người đi bộ mặc áo dài
- Class và quy tắc tôi dùng để chọn biên: Class person, quy tắc vẽ là dung mask ở mép cơ thể có thể nhìn thấy được, không lấn sang nền, bóng hay các object khác
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: không dùng - gán class person vì thấy rõ dáng người, gán mask sát với mép quần áo nhìn thấy, không lấn sang object khác
- Nếu không dùng gợi ý: ghi “không dùng”; vẫn giải thích một quyết định gán nhãn của mình.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: easy_semantic, ảnh 81ae7cbb-6bc63a4a.jpg, các cây bên đường
- Lỗi thuộc loại: sai lớp / thiếu-thừa vật / gộp-tách / biên / phủ vùng / khác: biên
- Bằng chứng tôi nhìn thấy: khi zoom, mép vegetation lấn vào khe trời giữa các cành
- Quy tắc và hành động sửa: sky chỉ vùng trời thật; cây/cành nhìn thấy thuộc vegetation → brush nhỏ chỉnh lại mép, không tô đè sky/building
- Sau sửa đã Save và export lại chưa? có rồi

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): … / chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| easy_semantic – 7ee6d192-89e2408b.jpg, dải đồi khô màu nâu hai bên đường cao tốc | (1) Gán vegetation vì là đồi có cỏ/cây thưa; (2) bỏ trống vì trông khô, gần như đất trống | Class của task chỉ có road/sidewalk/building… bề mặt tự nhiên có thực vật thưa nên xếp vegetation | Xác nhận: đã gán vegetation cho đồi |
| medium_instance – 000000181542.jpg, người đang ngồi trên xe máy ở ngã tư | (1) Một đối tượng (người + xe dính nhau); (2) hai instance: person và motorcycle | person và motorcycle là hai class, hai vật đếm được riêng | Tách 2 mask: một person + một motorcycle |
| hard_panoptic – 000000460147.jpg, các xe con nằm trên thùng xe chở ô tô | (1) Đếm từng xe con là car instance; (2) chỉ đếm xe tải, coi xe trên thùng là hàng hóa | Panoptic đếm mọi thing nhìn thấy thuộc class; xe con vẫn nhìn thấy và đúng class car | Xác nhận: đếm từng car + truck riêng |
