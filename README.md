# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Phạm Thanh Đạt
- MSSV / mã học viên: 2A202602721
- Lớp: [Điền lớp]
- Ngành đã chọn: Mobility / autonomous driving — Phương tiện Di chuyển & Xe tự hành (AV)

> Đây là khung báo cáo cá nhân. Thay các nội dung trong ngoặc vuông bằng bài làm của mình trước khi nộp.
>
> Chọn đúng một ngành: HR / tuyển dụng; Giáo dục / AI tutor; Y tế / symptom checker / health assistant; Mobility / autonomous driving; Media / news / social / political assistant; Content creator.
>
> Phân tích 2–3 case AI có thật trong cùng ngành. Mỗi case cần có số liệu liên quan, nguồn kiểm tra được và đủ 11 trường Harm Map. Phân biệt sự kiện có nguồn với nhận định cá nhân, hậu quả đã xảy ra với nguy cơ có thể xảy ra. Khi thiếu bằng chứng, ghi rõ “chưa đủ bằng chứng” hoặc “chưa đủ dữ liệu để đánh giá”.

### 1. Industry Risk Snapshot

#### Tổng quan Rủi ro Ngành: Phương tiện Di chuyển & Xe tự hành (AV)

Ngành di chuyển tự hành vận hành trong một môi trường rủi ro đặc biệt nghiêm trọng và bị kiểm soát chặt chẽ, nơi an toàn vật lý, an ninh mạng và bảo vệ dữ liệu đan xen trực tiếp với nhau. Bất kỳ sai sót nào trong quá trình xử lý kỹ thuật số đều có thể chuyển hóa tức thì thành thiệt hại vật lý hoặc đe dọa trực tiếp tính mạng con người.

| Khía cạnh Đánh giá | Mức độ | Yếu tố Thúc đẩy Chính & Lỗ hổng Trọng yếu |
| --- | --- | --- |
| Khả năng gây hại (Harmfulness Potential) | Nghiêm trọng / Cao (Critical / High) | Tổn hại vật lý do va chạm (tai nạn, tử vong), gián đoạn hạ tầng đô thị (chặn tuyến đường xe khẩn cấp), rủi ro an ninh mạng mang tính hệ thống trên toàn bộ đoàn xe (fleet). |
| Mức độ high-stakes | Cao (High) | Sai sót kỹ thuật số có thể chuyển hóa thành thiệt hại vật lý hoặc đe dọa trực tiếp tính mạng con người. |
| Nguy cơ lộ lọt dữ liệu nhạy cảm (Sensitive Data Exposure) | Cao (High) | Ghi hình liên tục tại không gian công cộng, thu thập dữ liệu sinh trắc học kéo dài trong khoang lái/khoang khách, theo dõi quỹ đạo di chuyển thời gian thực với độ chính xác cao. |
| Mức độ can thiệp của con người (Human Action Needed) | Cao đến Khá cao (High to Medium-High) | Quy trình giành quyền kiểm soát tức thì (SAE L2–L3), điều hành/can thiệp từ xa đối với đoàn xe (L4), và vai trò giám sát của tài xế an toàn. |
| Áp lực Pháp lý & Tuân thủ (Regulatory Pressure) | Rất cao (Very High) | Các tiêu chuẩn an toàn nghiêm ngặt (ISO 26262, ISO 21448/SOTIF, UNECE WP.29 R155/R156) và khung pháp lý bảo vệ quyền riêng tư (EU AI Act, GDPR, CCPA). |

#### Phân tích Chi tiết các Chiều Rủi ro Trọng yếu

##### 1. Khả năng gây hại: Nghiêm trọng / Cao

- **Tác động vật lý & động năng:** Hiện tượng cảm biến bị "mù" (do sương mù dày đặc, mưa lớn, ánh sáng chói), nhận diện sai ở tầng thị giác/cảm nhận (bỏ sót người đi bộ hoặc người đi xe đạp), và lỗi lập kế hoạch quỹ đạo (planning failures) đều trực tiếp gây ra nguy cơ va chạm thảm khốc và thương vong.
- **Mối đe dọa an ninh mạng – vật lý mang tính hệ thống:** Khác với hạ tầng CNTT thông thường, các véc-tơ tấn công trên phương tiện (cập nhật OTA, giao tiếp mạng V2X, xâm nhập CAN bus) có thể cho phép kẻ tấn công chiếm quyền điều khiển hệ thống phanh, đánh lái hoặc chân ga từ xa trên quy mô toàn đoàn xe.
- **Tê liệt hạ tầng và cản trở lực lượng khẩn cấp:** Sự cố "phanh ma" (phantom braking) hoặc xe bị chết máy/dừng khẩn cấp giữa giao lộ có thể gây ùn tắc giao thông cục bộ và chặn đường di chuyển của xe cứu hỏa hay cứu thương.

##### 2. Nguy cơ lộ lọt dữ liệu nhạy cảm: Cao

- **Dữ liệu viễn trắc môi trường ngoại cảnh:** Hệ thống cảm biến (LiDAR, camera độ phân giải cao, sóng siêu âm) liên tục ghi lại khuôn mặt người qua đường, biển số xe, nhà riêng và các khu vực trọng yếu/quân sự mà không có sự chấp thuận rõ ràng từ chủ thể.
- **Giám sát khoang lái & dữ liệu sinh trắc học:** Hệ thống giám sát người lái (DMS) dùng camera cabin và cảm biến hồng ngoại để theo dõi hướng nhìn, tần suất chớp mắt, đặc điểm nhận diện khuôn mặt và trạng thái sinh lý (mệt mỏi, mất tập trung).
- **Định danh hành vi & không gian địa lý:** Tọa độ GPS độ chính xác cao cùng nhật ký lộ trình dễ dàng bộc lộ các thói quen cá nhân nhạy cảm, địa chỉ nhà ở/cơ quan, các điểm đến y tế hay khuynh hướng tôn giáo, chính trị.
- **Chủ quyền dữ liệu:** Việc truyền tải dữ liệu bản đồ độ nét cao (HD Map) và nhật ký hình ảnh xuyên biên giới hiện chịu sự kiểm soát an ninh quốc gia đặc biệt gắt gao tại nhiều thị trường lớn (Mỹ, EU, Trung Quốc).

##### 3. Mức độ cần sự can thiệp của con người: Cao đến Khá cao

Mức độ can thiệp bắt buộc tương ứng trực tiếp với các cấp độ tự hành (theo tiêu chuẩn SAE J3016):

**SAE Cấp độ 2 / 2+ (Bán tự động - Tay lái / Mắt nhìn liên tục):**

- Mức độ con người: Liên tục / Trực tiếp tham gia vận hành (In-the-Loop).
- Người lái giữ toàn bộ trách nhiệm pháp lý và vận hành, đòi hỏi khả năng can thiệp trong tích tắc để xử lý các tình huống biên ngoại lệ (edge cases).

**SAE Cấp độ 3 (Tự động hóa có điều kiện):**

- Mức độ con người: Cao / Giám sát sẵn sàng tiếp quản (On-the-Loop).
- Người lái không cần điều khiển trực tiếp nhưng phải luôn sẵn sàng nhận lại quyền kiểm soát trong khoảng thời gian cửa sổ chuyển giao giới hạn (thường từ 5–10 giây) khi xe vượt ra khỏi phạm vi thiết kế vận hành (ODD).

**SAE Cấp độ 4 (Tự động hóa cao - Robotaxi / Đội xe tự hành):**

- Mức độ con người: Từ xa / Không trực tiếp trong khoang lái (Out-of-the-Loop), nhưng cần can thiệp cao ở tầng trung tâm điều hành.
- Phương tiện không cần tài xế trên xe, song trung tâm điều hành tập trung vẫn cần đội ngũ kỹ thuật viên can thiệp xử lý từ xa các tình huống bế tắc, phê duyệt lộ trình dự phòng, hoặc tiếp quản thủ công khi xe thực hiện thao tác giảm thiểu rủi ro (MRM) và dừng lại an toàn.

**Giám sát ở cấp độ Kỹ thuật & Hệ thống:**

Đòi hỏi kiểm thử nghiêm ngặt có sự tham gia của con người, chạy các bộ kịch bản mô phỏng hồi quy liên tục, kiểm toán an toàn tính năng theo tiêu chuẩn SOTIF (Safety of the Intended Functionality), và duy trì hội đồng điều tra sự cố độc lập.

### 2. Case study 1 — Uber ATG: va chạm chết người tại Tempe, Arizona (2018)

#### Brief Case

- Tổ chức / sản phẩm AI: Uber Advanced Technologies Group (ATG); hệ thống lái tự động thử nghiệm (ADS) trên Volvo XC90 đời 2017.
- Thời gian, địa điểm / bối cảnh: 21:58 ngày 18/03/2018, N. Mill Avenue, Tempe, Arizona, Mỹ; thử nghiệm trên đường công cộng với một người vận hành trên xe.
- AI được dùng để làm gì: Nhận biết vật thể, dự đoán quỹ đạo và điều khiển xe trên tuyến thử nghiệm đã lập bản đồ.
- Vấn đề hoặc sự kiện đáng chú ý: Xe đâm một người đi bộ đang dắt xe đạp qua đường ngoài vạch sang đường. ADS phân loại và dự đoán sai, không phanh khẩn cấp để giảm mức độ va chạm; người vận hành mất tập trung vì điện thoại và tiếp quản quá muộn.
- Số liệu có nguồn: **1 người tử vong**; ADS phát hiện vật thể **5,6 giây** trước va chạm nhưng chỉ xác định tình huống khẩn cấp **1,2 giây** trước va chạm; hệ thống trì hoãn phanh **1 giây**; tốc độ lúc va chạm **39 mph**. Đây là số liệu của vụ Tempe, không phải tỷ lệ lỗi toàn đội xe (NTSB, tr. 1–2, 5, 13–17).
- Nguồn: *Collision Between Vehicle Controlled by Developmental Automated Driving System and Pedestrian, Tempe, Arizona, March 18, 2018* — NTSB, báo cáo **NTSB/HAR-19/03**, thông qua ngày **19/11/2019**, bản sửa ngày **26/06/2020** — [PDF chính thức](https://www.ntsb.gov/investigations/AccidentReports/Reports/HAR1903.pdf); mục 1.1, 1.3, 1.5.5–1.5.6, 1.6.3 và 3.1–3.2. [PDF lưu trong repo](cases/01-uber-tempe-2018/har1903.pdf) · [Phân tích chi tiết](cases/01-uber-tempe-2018/analysis.md).
- Phân biệt bằng chứng và nhận định: NTSB xác nhận hậu quả và các lỗi kỹ thuật, giám sát; nguyên nhân có khả năng nhất là người vận hành không giám sát vì mất tập trung. Các nhãn layer, failure mode và Severity dưới đây là cách tôi quy chiếu sang worksheet; không phải phân loại của NTSB.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Người đi bộ dắt xe đạp cắt ngang đường xe thử nghiệm; ADS nhận ra tình huống khẩn cấp chỉ 1,2 giây trước va chạm. |
| Stakeholder bị ảnh hưởng | Người đi bộ là nạn nhân trực tiếp; người vận hành, gia đình nạn nhân, Uber ATG và cơ quan quản lý là các bên liên quan. |
| Failure mode | Escalation failure: phương án dự phòng dựa vào người vận hành không ngăn được va chạm; Over-reliance: automation complacency góp phần làm giám sát suy giảm. Lỗi kỹ thuật đi kèm là phân loại vật thể và dự đoán quỹ đạo sai. |
| Layer bắt đầu lỗi | Model, theo chức năng perception/prediction; Safety không bù được lỗi: trì hoãn phanh và vô hiệu hóa FCW/AEB của Volvo. Chưa đủ bằng chứng để quy nguyên nhân cho riêng trọng số mô hình hay dữ liệu huấn luyện. |
| Harm xảy ra là gì? | **Đã xảy ra:** một người đi bộ tử vong do va chạm; người vận hành không bị thương. |
| Harm lens | Injury — tổn hại thể chất dẫn đến tử vong. |
| Severity | **Critical** — nhận định của tôi vì hậu quả là mất tính mạng. |
| Scale | **1 người tử vong trong 1 vụ va chạm**; chưa có căn cứ để ngoại suy số người chịu cùng lỗi trên toàn đội xe. |
| Probability | Chưa đủ dữ liệu để ước lượng xác suất tái diễn; một sự kiện đã xảy ra không xác lập tỷ lệ lỗi của hệ thống. |
| Frequency | Ghi nhận 1 vụ Tempe ngày 18/03/2018 trong case này; chưa đủ dữ liệu để xác định tần suất của cùng chuỗi lỗi. |
| Vì sao? | NTSB tr. 1–2, 5, 13–17, 22, 57–59 xác nhận hậu quả, lỗi dự đoán, thiếu dự phòng phanh và mất tập trung. Báo cáo không cung cấp mẫu số phơi nhiễm phù hợp để tính Probability/Frequency. |

### 3. Case study 2 — [Tên case]

#### Brief Case

- Tổ chức / sản phẩm AI: [Điền]
- Thời gian, địa điểm / bối cảnh: [Điền]
- AI được dùng để làm gì: [Điền]
- Vấn đề hoặc sự kiện đáng chú ý: [Điền sự kiện có nguồn]
- Số liệu có nguồn: [Con số, đơn vị, thời gian/phạm vi đo và nguồn nào cung cấp]
- Nguồn: [Tên tài liệu/bài viết — đơn vị/tác giả — ngày công bố — URL — trang/mục liên quan nếu có]
- Phân biệt bằng chứng và nhận định: [Điều nguồn xác nhận; điều tôi suy luận hoặc còn chưa rõ]

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | [Tình huống cụ thể có rủi ro] |
| Stakeholder bị ảnh hưởng | [Người dùng và các bên liên quan] |
| Failure mode | [Kiểu lỗi AI; chọn mục giải thích được: Hallucination / Bias / fairness / Sycophancy / Over-reliance / Harmful advice / Privacy leak / Escalation failure / Misuse / jailbreak] |
| Layer bắt đầu lỗi | [UX / Grounding / Safety / Model; giải thích hoặc ghi chưa đủ bằng chứng] |
| Harm xảy ra là gì? | [Ai bị ảnh hưởng + hậu quả; ghi rõ đã xảy ra hay mới là nguy cơ] |
| Harm lens | [Chọn loại phù hợp: misinformation / opportunity loss / injury / privacy loss / dignity loss] |
| Severity | [Low / Medium / High / Critical; giải thích bằng hậu quả] |
| Scale | [Quy mô tác động và căn cứ; nêu phạm vi hoặc số người có nguồn, hoặc ghi chưa đủ dữ liệu] |
| Probability | [Khả năng xảy ra và căn cứ; tỷ lệ đo được nếu có, hoặc nhận định định tính có giải thích] |
| Frequency | [Tần suất và căn cứ; số liệu có nguồn hoặc nhận định định tính có giải thích] |
| Vì sao? | [Lý do cho các đánh giá; nguồn hoặc giới hạn bằng chứng] |

<!-- Nếu làm case thứ ba, sao chép cả phần Brief Case và Harm Map của case 2, đổi tiêu đề thành “### 4. Case study 3 — [Tên case]”, rồi điền bài làm. -->
