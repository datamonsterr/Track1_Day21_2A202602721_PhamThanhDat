# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Phạm Thanh Đạt
- MSSV / mã học viên: 2A202602721
- Lớp: H201
- Ngành đã chọn: Mobility / autonomous driving — Phương tiện Di chuyển & Xe tự hành (AV)

> Bài cá nhân phân tích hai case trong ngành Mobility / autonomous driving: an toàn vật lý của xe thử nghiệm Uber ATG và quyền riêng tư trong chuỗi dữ liệu AI của Tesla. Nhãn rủi ro là đánh giá định tính phục vụ bài tập, không phải phân loại pháp lý.
>
> Phân biệt kết luận điều tra, tường thuật báo chí, cáo buộc trong đơn kiện và nhận định cá nhân. “Chưa đủ dữ liệu để đánh giá” là kết luận có giải thích về giới hạn bằng chứng, không phải một trường bị bỏ trống.

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
| High-risk moment | Trong 5,6 giây trước va chạm, người đi bộ dắt xe đạp cắt ngang quỹ đạo xe. ADS chỉ xác định tình huống khẩn cấp ở mốc −1,2 giây, rồi trì hoãn phanh 1 giây trong khi người vận hành mất tập trung. |
| Stakeholder bị ảnh hưởng | Người đi bộ là nạn nhân trực tiếp; gia đình, người vận hành, Uber ATG, người tham gia giao thông và cơ quan quản lý là các bên liên quan. Thiệt hại gián tiếp chưa được định lượng. |
| Failure mode | **Escalation failure**, theo quy chiếu của tôi: dự phòng dựa vào người vận hành không xử lý nguy cơ kịp thời; **Over-reliance** tương ứng với automation complacency được NTSB phân tích. Cơ chế kỹ thuật là phân loại vật thể và dự đoán quỹ đạo sai; không gọi đây là hallucination. |
| Layer bắt đầu lỗi | Lỗi đầu chuỗi nằm ở perception/tracking/prediction, quy chiếu chức năng vào **Model**; **Safety** không chặn hậu quả vì trì hoãn phanh và FCW/AEB của Volvo không hoạt động. Chưa đủ bằng chứng để xác định lỗi do riêng trọng số, dữ liệu huấn luyện hay quy tắc phần mềm; không gán Grounding khi thiếu căn cứ. |
| Harm xảy ra là gì? | **Đã xảy ra:** một người đi bộ tử vong do va chạm; người vận hành không bị thương. |
| Harm lens | Injury — tổn hại thể chất dẫn đến tử vong. |
| Severity | **Critical** — nhận định của tôi vì hậu quả là mất tính mạng. |
| Scale | **1 người tử vong trong vụ Tempe**. Cấu hình tương tự có thể tạo nguy cơ trên các xe khác, nhưng chưa có số nạn nhân của cùng lỗi để ngoại suy ra toàn đội xe. |
| Probability | **Chưa đủ dữ liệu để đánh giá xác suất tái diễn**: thiếu số lần gặp tình huống tương đương và dữ liệu phơi nhiễm. Việc tai nạn đã xảy ra không có nghĩa xác suất là 100% hoặc High. |
| Frequency | **1 vụ được phân tích**, không phải kết luận toàn đội xe chỉ từng gặp lỗi một lần. Báo cáo không cho tần suất lặp lại cùng chuỗi lỗi; 37 sự cố đội xe thuộc nhiều loại nên không dùng làm tỷ lệ lỗi này. |
| Vì sao? | NTSB tr. 1–2, 5, 13–17, 19–22, 57–59 xác nhận hậu quả và chuỗi mất dự phòng. **Critical** dựa trên tử vong thực tế; Scale, Probability và Frequency được đánh giá riêng, không suy ra từ Severity. [Lập luận và biện pháp kiểm soát](cases/01-uber-tempe-2018/analysis.md#8-đánh-giá-harm-map-và-điểm-can-thiệp). |

### 3. Case study 2 — Yeh v. Tesla, Inc.: quyền riêng tư dữ liệu camera (2023)

#### Brief Case

- Tổ chức / sản phẩm AI: Tesla; dữ liệu camera và quy trình gán nhãn phục vụ phát triển công nghệ hỗ trợ lái Autopilot. Nguyên đơn là **Henry Yeh**; tên hồ sơ là **Yeh v. Tesla, Inc., 3:23-cv-01704**.
- Thời gian, địa điểm / bối cảnh: Reuters điều tra hành vi được cựu nhân viên mô tả trong **2019–2022**; đơn kiện nộp **07/04/2023** tại Tòa án Liên bang Khu vực Bắc California, Mỹ. Văn phòng San Mateo được nhắc đến trong phóng sự.
- AI được dùng để làm gì: Camera cung cấp ảnh/video để con người gán nhãn vật thể phục vụ phát triển hệ thống hỗ trợ lái. Rủi ro nằm trong chuỗi dữ liệu AI và việc con người sử dụng dữ liệu, không phải một lỗi quyết định lái xe được chứng minh trong vụ kiện.
- Vấn đề hoặc sự kiện đáng chú ý: Theo Reuters, một số nhân viên chia sẻ ảnh/video khách hàng trong chat nội bộ ngoài mục đích công việc, có nội dung đời tư và vị trí ghi hình. Yeh kiện về các hành vi bị cáo buộc. Lệnh **12/10/2023** yêu cầu trọng tài và tạm dừng vụ án; không phải phán quyết xác nhận Tesla vi phạm quyền riêng tư.
- Số liệu có nguồn: Reuters dẫn **9 cựu nhân viên** về chia sẻ ảnh/video; **7 cựu nhân viên** cho biết công cụ hiển thị vị trí ghi hình, trong bối cảnh **2019–2022**. Đây là số người cung cấp lời kể, **không phải số nạn nhân hoặc tỷ lệ rò rỉ**. Reuters không thu được các file đã chia sẻ và không xác định được mức độ phổ biến.
- Nguồn: [Reuters — Steve Stecklow, Waylon Cunningham, Hyunjoo Jin — 06/04/2023](https://www.investing.com/news/stock-market-news/special-report--tesla-workers-shared-sensitive-images-recorded-by-customer-cars-3050469); [đơn kiện, Document 1 — 07/04/2023, ¶¶ 12–19](cases/02-tesla-privacy-yeh-2023/sources/complaint-2023-04-07.pdf#page=4); [lệnh tòa, Document 52 — 12/10/2023, tr. 1–3, 14–15](cases/02-tesla-privacy-yeh-2023/sources/court-order-2023-10-12.pdf); VnExpress/Mỹ Anh: [bài điều tra, 08/04/2023](https://vnexpress.net/nhan-vien-tesla-chia-se-hinh-anh-nhay-cam-cua-khach-hang-4590667.html) và [bài về vụ kiện, 11/04/2023](https://vnexpress.net/tesla-bi-kien-vi-xam-pham-doi-tu-4591528.html). [Danh mục nguồn và nhật ký thu thập](cases/02-tesla-privacy-yeh-2023/sources/README.md).
- Phân biệt bằng chứng và nhận định: Việc nộp đơn và lệnh trọng tài có hồ sơ tòa; hành vi chia sẻ là tường thuật Reuters và cáo buộc, chưa được lệnh này xét xử về nội dung. Không xác nhận ảnh của riêng gia đình Yeh đã bị chia sẻ, dữ liệu đã công khai ngoài Tesla hoặc mọi khách hàng đều là nạn nhân. Nhãn Harm Map dưới đây là nhận định của tôi.

#### Harm Map Worksheet

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Nhân viên truy cập ảnh/video để gán nhãn rồi chuyển nội dung riêng tư sang chat giải trí ngoài mục đích được phép; vị trí hoặc chi tiết trong hình có thể làm lộ danh tính. |
| Stakeholder bị ảnh hưởng | Chủ xe, thành viên gia đình, trẻ em, hành khách và người được ghi hình; nhân viên xử lý dữ liệu, Tesla và bộ phận bảo vệ dữ liệu là các bên liên quan. |
| Failure mode | **Privacy leak + Misuse**, theo quy chiếu của tôi: dữ liệu dùng sai mục đích và chia sẻ ngoài nhu cầu công việc. Chưa có bằng chứng về jailbreak, hacker bên ngoài hoặc mô hình AI tự làm lộ dữ liệu. |
| Layer bắt đầu lỗi | **Safety**, theo chức năng kiểm soát truy cập/sử dụng dữ liệu trong toàn hệ thống AI; kiến trúc kiểm soát cụ thể chưa đủ bằng chứng. UX/đồng ý chia sẻ là yếu tố cần xem xét; không kết luận lỗi bắt đầu từ Model hay Grounding. |
| Harm xảy ra là gì? | **Được Reuters tường thuật, chưa được lệnh tòa xác nhận về nội dung:** người được ghi hình mất kiểm soát dữ liệu riêng tư khi nội dung bị chia sẻ để tiêu khiển. Lộ địa chỉ, phát tán ra ngoài và thiệt hại của riêng gia đình Yeh vẫn là nguy cơ/cáo buộc chưa xác minh. |
| Harm lens | **Privacy loss**; **dignity loss** đối với nội dung nhạy cảm bị chế giễu, theo đánh giá của tôi. Không coi tai nạn xuất hiện trong video là hậu quả do việc chia sẻ dữ liệu gây ra. |
| Severity | **High**, đánh giá định tính dựa trên nội dung riêng tư, trẻ em và khả năng suy ra nơi ở; mức thiệt hại của từng người chưa xác định. Không chọn Critical chỉ vì video có cảnh tai nạn. |
| Scale | Tường thuật cho thấy chia sẻ nội bộ giữa một số nhân viên/nhóm; **chưa có số nạn nhân hoặc số file xác minh**. 9 và 7 là số nguồn lời kể, không phải quy mô người bị hại; nhóm khởi kiện được đề xuất không đồng nghĩa tất cả chủ xe đã chịu hại. |
| Probability | **Chưa đủ dữ liệu để đánh giá xác suất**: không có mẫu số file được truy cập/chia sẻ hay số khách hàng có dữ liệu trong hệ thống. Không tính 7/9 thành tỷ lệ lộ vị trí hoặc rò rỉ. |
| Frequency | Nhiều lần chia sẻ được cựu nhân viên mô tả trong 2019–2022; **không có số lần hoặc tần suất/ngày**. Không khẳng định hành vi tiếp diễn ở thời điểm hiện tại. |
| Vì sao? | Reuters ghi lời kể và giới hạn điều tra; đơn kiện là cáo buộc; lệnh tòa chỉ giải quyết trọng tài. Privacy/dignity có thể bị tổn hại dù chia sẻ chỉ diễn ra nội bộ, nhưng thiếu căn cứ định lượng. [Phân tích sâu và đối chiếu nguồn](cases/02-tesla-privacy-yeh-2023/analysis.md). |

### 4. Đối chiếu yêu cầu bài cá nhân

| Yêu cầu | Nội dung đã có |
| --- | --- |
| Chọn một ngành | Mobility / autonomous driving; cả hai case thuộc ngành này, ở hai giai đoạn vận hành và phát triển dữ liệu AI. |
| Industry Risk Snapshot | Harm chính, high-stakes, dữ liệu nhạy cảm và human review đều có đánh giá, lý do; bổ sung áp lực tuân thủ. |
| Hai Brief Case có số liệu và nguồn | Mỗi case có đủ 7 trường; số liệu kèm phạm vi và nguồn, không dùng số nhân chứng làm số nạn nhân. |
| Harm Map cho từng case | Mỗi case có đủ 11 trường; Severity, Scale, Probability và Frequency được đánh giá riêng, có giới hạn bằng chứng. |
| Hồ sơ đối chiếu | [Case 1](cases/01-uber-tempe-2018/analysis.md) có PDF NTSB; [Case 2](cases/02-tesla-privacy-yeh-2023/analysis.md) có hồ sơ tòa, thư Thượng viện, nguồn Reuters/VnExpress và nhật ký thu thập. |
