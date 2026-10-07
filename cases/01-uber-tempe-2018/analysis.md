# Case 1 — Uber ATG: va chạm chết người tại Tempe, Arizona (2018)

[Báo cáo tóm tắt](../../README.md) · [PDF nguồn](har1903.pdf) · [Danh mục case](../README.md)

## 1. Nguồn và cách đọc số trang

Nguồn chính là báo cáo điều tra của **National Transportation Safety Board (NTSB)**: *Collision Between Vehicle Controlled by Developmental Automated Driving System and Pedestrian, Tempe, Arizona, March 18, 2018*, **NTSB/HAR-19/03**, hồ sơ **HWY18MH010**. Báo cáo được thông qua ngày **19/11/2019**; bản đính kèm ghi tái phát hành ngày **26/06/2020** để sửa tiêu đề trên trang thông tin xuất bản.

- [Bản PDF chính thức của NTSB](https://www.ntsb.gov/investigations/AccidentReports/Reports/HAR1903.pdf).
- [Bản PDF lưu nguyên vẹn trong repo](har1903.pdf), gồm 78 trang.

Các số trang trong bài là **số in ở chân trang báo cáo**. Từ trang nội dung 1, số trang trên trình đọc PDF bằng số trang báo cáo cộng 12. Ví dụ: trang báo cáo 16 là trang PDF 28; trang báo cáo 59 là trang PDF 71. Các liên kết dưới đây dùng số trang PDF.

Sự kiện và số liệu được diễn giải từ báo cáo. Nhãn Harm Map, cách quy chiếu layer và đề xuất bổ sung là nhận định của tôi.

## 2. Brief Case

**Hệ thống và mục đích.** Uber Advanced Technologies Group (ATG) lắp hệ thống lái tự động đang phát triển (ADS) lên một chiếc Volvo XC90 đời 2017. Hệ thống sử dụng cảm biến để nhận biết vật thể, dự đoán quỹ đạo và điều khiển xe trên các tuyến đã lập bản đồ; đây là xe thử nghiệm có người vận hành, không phải dịch vụ robotaxi thương mại không có tài xế. [Nguồn: tr. 1, 8–12](har1903.pdf#page=13).

**Bối cảnh.** Lúc 21:58 ngày 18/03/2018, giờ địa phương Mountain Standard Time, tại N. Mill Avenue, Tempe, Arizona, xe đang chạy bằng ADS khi một phụ nữ 49 tuổi dắt xe đạp qua đường ngoài vạch sang đường. Mặt đường khô và có đèn đường. Xe có một người vận hành ở ghế lái. [Nguồn: tr. 1; Executive Summary, tr. v](har1903.pdf#page=8).

**Sự kiện.** ADS phát hiện vật thể nhưng không nhận dạng đúng là người đi bộ hoặc dự đoán đúng đường đi. Khi nhận ra tình huống khẩn cấp, hệ thống dựa vào người vận hành tiếp quản; người này đang mất tập trung vì điện thoại. Xe đâm người đi bộ ở tốc độ 39 mph. Nạn nhân tử vong tại hiện trường; người vận hành không bị thương. [Nguồn: tr. 1–2, 5, 16–17](har1903.pdf#page=17).

**Kết luận điều tra.** NTSB xác định nguyên nhân có khả năng nhất là người vận hành không theo dõi môi trường lái và ADS vì bị điện thoại làm mất tập trung. Những yếu tố góp phần gồm đánh giá rủi ro và giám sát của ATG không đầy đủ, thiếu biện pháp chống automation complacency, hành vi sang đường của người đi bộ bị suy giảm khả năng nhận thức/phán đoán, và giám sát thử nghiệm của Arizona không đầy đủ. Báo cáo xem đây là chuỗi yếu tố kỹ thuật, con người và tổ chức; không kết luận chỉ riêng AI gây tai nạn. [Nguồn: mục 3.2, tr. 59](har1903.pdf#page=71).

## 3. Số liệu và diễn biến đã được xác nhận

Mốc thời gian dưới đây tính tương đối với lúc va chạm: giá trị âm là trước va chạm, giá trị dương là sau va chạm.

| Mốc / số liệu | Nội dung được nguồn xác nhận | Nguồn |
| --- | --- | --- |
| −5,6 giây | Radar phát hiện người đi bộ nhưng phân loại thành xe; tốc độ xe thử nghiệm 44,3 mph. | Bảng dữ liệu ADS, tr. 15 ([PDF 27](har1903.pdf#page=27)). |
| −5,2 đến −1,5 giây | Nhãn vật thể thay đổi giữa xe, vật thể khác và xe đạp. Khi đổi nhãn, hệ thống không sử dụng lịch sử vị trí trước đó để dự đoán quỹ đạo. | Tr. 13, 15–17 ([PDF 25](har1903.pdf#page=25)). |
| −1,2 giây | Hệ thống nhận ra vật thể nằm trên đường xe đi và xác định tình huống khẩn cấp; bắt đầu action suppression. | Bảng dữ liệu ADS, tr. 16 ([PDF 28](har1903.pdf#page=28)). |
| Khoảng trì hoãn 1 giây | ADS tạm ngăn phanh để kiểm tra nguy cơ/tìm đường khác hoặc chờ người vận hành tiếp quản; không cảnh báo khi bắt đầu khoảng này. | Tr. 13–14 ([PDF 25](har1903.pdf#page=25)). |
| −0,2 giây | Hết action suppression; hệ thống phát cảnh báo âm thanh và khởi tạo kế hoạch giảm tốc từ từ. Báo cáo ghi chưa rõ việc thực thi kế hoạch đã bắt đầu trước khi người vận hành tiếp quản hay chưa. | Tr. 16–17, chú thích e của bảng ([PDF 28](har1903.pdf#page=28)). |
| −0,02 giây | Người vận hành bắt đầu đánh lái, ngắt ADS; tốc độ ghi nhận 39,0 mph, tương ứng tốc độ lúc va chạm nêu trong phần tường thuật. | Tr. 2, 16 ([PDF 14](har1903.pdf#page=14)). |
| +0,7 giây | Người vận hành bắt đầu phanh sau va chạm. | Bảng dữ liệu ADS, tr. 16 ([PDF 28](har1903.pdf#page=28)). |
| 1 người tử vong | Người đi bộ chết tại hiện trường do nhiều chấn thương do lực va đập; người vận hành không bị thương. | Mục 1.3, tr. 5 ([PDF 17](har1903.pdf#page=17)). |

Khoảng **5,6 giây** là thời gian kể từ khi ADS phát hiện vật thể, không phải thời gian xe đã nhận dạng đúng một người đi bộ. Khoảng **1,2 giây** lấy từ báo cáo cuối cùng. Không thay bằng số liệu của báo cáo sơ bộ.

## 4. Chuỗi lỗi và cách quy chiếu sang worksheet

**Moment → Mode → Layer → Harm → Severity:** người đi bộ cắt ngang đường xe → phân loại/dự đoán sai, phương án chuyển trách nhiệm xử lý cho người vận hành thất bại → perception/prediction và dự phòng an toàn → va chạm gây tử vong → Critical.

| Khía cạnh | Bằng chứng và nhận định |
| --- | --- |
| Nhận biết và dự đoán | ADS không phân loại nạn nhân thành người đi bộ. Việc đổi nhãn làm mất lịch sử vị trí dùng cho dự đoán; chức năng dự đoán chưa xử lý đầy đủ việc sang đường ngoài vạch. Tôi quy chiếu lỗi này vào **Model** theo chức năng perception/prediction, không khẳng định lỗi chỉ nằm trong trọng số một mô hình học máy. NTSB không công bố đủ chi tiết để tách nguyên nhân do dữ liệu huấn luyện, trọng số hay quy tắc phần mềm. [Tr. 13, 16–17, 39](har1903.pdf#page=51). |
| Dự phòng phanh | Thiết kế trì hoãn phanh 1 giây; nếu không thể tránh va chạm trong giới hạn phanh của ADS, hệ thống không dùng phanh tối đa chỉ để giảm thiệt hại. FCW/AEB nguyên bản của Volvo bị vô hiệu hóa khi ADS hoạt động. Tôi quy chiếu vào **Safety**. [Tr. 13–14, 22, 40–41](har1903.pdf#page=52). |
| Chuyển giao cho con người | Không có cảnh báo lúc bắt đầu trì hoãn; cảnh báo âm thanh đến sát thời điểm va chạm. **Escalation failure** là nhãn tôi dùng cho việc phương án dự phòng dựa vào người vận hành không xử lý được nguy cơ kịp thời. [Tr. 13–17](har1903.pdf#page=25). |
| Giám sát của con người | NTSB liên hệ mất tập trung kéo dài với automation complacency; ATG không có biện pháp hiệu quả để kiểm soát sự suy giảm giám sát. Tôi quy chiếu vào **Over-reliance**. Đây không phải bằng chứng về hallucination hay sycophancy. [Tr. 43–45, 57–58](har1903.pdf#page=56). |
| UX và Grounding | Thời điểm cảnh báo có liên quan đến giao diện, nhưng không đủ cơ sở để coi giao diện là nơi bắt đầu lỗi. Báo cáo không mô tả lỗi system message hoặc truy xuất nguồn theo nghĩa Grounding của một trợ lý ngôn ngữ; không gán nhãn này chỉ để đủ mục. |

## 5. Harm Map Worksheet — phân tích chi tiết

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | Một người đi bộ dắt xe đạp đi vào quỹ đạo xe thử nghiệm trên đường công cộng. Đến 1,2 giây trước va chạm, ADS mới xác định tình huống khẩn cấp, trong khi người vận hành chưa phát hiện nguy cơ. |
| Stakeholder bị ảnh hưởng | Người đi bộ là nạn nhân trực tiếp. Gia đình nạn nhân, người vận hành, Uber ATG, người tham gia giao thông và cơ quan quản lý là các bên liên quan. Báo cáo không định lượng thiệt hại cho từng nhóm gián tiếp. |
| Failure mode | **Escalation failure** và **Over-reliance**, theo quy chiếu của tôi; lỗi phân loại vật thể/dự đoán quỹ đạo là cơ chế kỹ thuật cụ thể. Không gọi lỗi nhận dạng này là hallucination của LLM. |
| Layer bắt đầu lỗi | **Model**, theo chức năng perception/prediction; **Safety** không chặn được hậu quả khi tầng này sai. Các quyết định thiết kế và giám sát tổ chức góp phần làm mất dự phòng. Chưa đủ bằng chứng để xác định nguyên nhân trong trọng số hay dữ liệu huấn luyện. |
| Harm xảy ra là gì? | **Đã xảy ra:** người đi bộ tử vong do xe va chạm; người vận hành không bị thương. Tổn thất tâm lý, tài chính hay danh tiếng có thể là tác động gián tiếp, nhưng không được định lượng hoặc kết luận thêm ở đây. |
| Harm lens | **Injury:** tổn hại thể chất dẫn đến tử vong. Không có căn cứ trong case để kết luận đã xảy ra privacy loss. |
| Severity | **Critical**, nhận định của tôi dựa trên một ca tử vong thực tế, không phải thiệt hại giả định. |
| Scale | Một nạn nhân tử vong trong vụ Tempe. Các lỗi thiết kế có thể ảnh hưởng những xe dùng cấu hình tương tự, nhưng đây là nguy cơ chưa có số nạn nhân được xác nhận trong báo cáo. |
| Probability | **Chưa đủ dữ liệu để đánh giá xác suất tái diễn.** Không có mẫu số số lần gặp tình huống tương đương hoặc quãng đường phơi nhiễm phù hợp. Không suy ra một tỷ lệ phần trăm từ một vụ tai nạn. |
| Frequency | **Một vụ được phân tích; chưa đủ dữ liệu để xác định tần suất cùng chuỗi lỗi.** Các số liệu sự cố đội xe không chứng minh lỗi này lặp lại với cùng cơ chế. |
| Vì sao? | Tr. 1–2, 5, 13–17, 22 và 57–59 xác nhận hậu quả, diễn biến, thiếu dự phòng và nguyên nhân góp phần. Hậu quả chết người đủ căn cứ cho Critical, nhưng không đủ để kết luận Probability/Frequency cao. |

## 6. Biện pháp khắc phục và human review

**Thay đổi sau tai nạn được NTSB ghi nhận, tại thời điểm báo cáo:**

- Cho phép FCW/AEB của Volvo hoạt động cùng ADS sau khi xử lý vấn đề tích hợp; loại bỏ action suppression và cho phép phanh khẩn cấp để giảm mức độ va chạm. [Tr. 30](har1903.pdf#page=42).
- Duy trì lịch sử vị trí khi vật thể đổi nhãn và bổ sung dự đoán người đi bộ sang đường ngoài vạch. [Tr. 30](har1903.pdf#page=42).
- Khi thử nghiệm trở lại tháng 12/2018, dùng hai người vận hành; bổ sung đào tạo và giám sát sự chú ý theo thời gian thực, với cảnh báo tại xe và báo cáo cho người giám sát. [Tr. 31, 45](har1903.pdf#page=43).
- Tổ chức bộ phận an toàn độc lập hơn với đội phát triển/thử nghiệm và bắt đầu xây dựng safety management system. Đây là quá trình triển khai được ghi nhận, không phải bằng chứng hệ thống đã hoàn toàn an toàn. [Tr. 32, 58](har1903.pdf#page=44).

**Đề xuất của tôi:** người phụ trách an toàn cần duyệt các tình huống kiểm thử trước khi thử trên đường công cộng, bao gồm người dắt xe đạp, sang đường ngoài vạch và vật thể đổi nhãn. Human review cần hiện diện ở cả bước phê duyệt thử nghiệm, giám sát chuyến chạy và xem xét sự cố. Người giám sát trên xe cần được hỗ trợ bằng dự phòng kỹ thuật và cơ chế theo dõi sự chú ý; việc chỉ bố trí một người sẵn sàng tiếp quản không tự bảo đảm an toàn.

## 7. Giới hạn bằng chứng

- **Không lấy số sự cố đội xe làm tần suất lỗi này.** ATG ghi nhận 37 vụ va chạm/sự cố khi chạy tự động từ tháng 09/2016 đến tháng 03/2018, không bao gồm vụ Tempe; 33 vụ là xe khác đâm xe thử nghiệm, hai vụ xe thử nghiệm va chạm, hai vụ phá hoại. Những sự kiện khác loại này không tạo thành mẫu số xác suất hay số lần tái diễn lỗi Tempe. [Tr. 19–20](har1903.pdf#page=31).
- **Không biến mô phỏng thành kết quả thực tế.** Mô phỏng của Volvo dự đoán tránh được va chạm trong 17/20 biến thể chuyển động của người đi bộ; ba biến thể còn lại có tốc độ va chạm dưới 10 mph. Mô phỏng giả định cảm biến hoạt động lý tưởng, người đi bộ di chuyển tuyến tính với tốc độ không đổi. Đây không phải 20 vụ thử nghiệm thực tế và không phải xác suất tránh tai nạn của toàn hệ thống. [Tr. 21–22](har1903.pdf#page=33).
- **Không suy diễn kiến trúc AI.** Báo cáo mô tả hành vi perception, tracking, prediction và braking, nhưng không đủ để kết luận về tập huấn luyện hoặc mô hình cụ thể. Không gán nhãn bias, hallucination hay privacy leak khi không có bằng chứng tương ứng.
- **Không xem kết luận điều tra là phán quyết trách nhiệm pháp lý.** NTSB mô tả báo cáo là điều tra tìm hiểu sự kiện để cải thiện an toàn, không nhằm xác định quyền hoặc trách nhiệm pháp lý của cá nhân/tổ chức. [Trang thông tin xuất bản, PDF 3](har1903.pdf#page=3).
- **Không ngoại suy sang mọi AV hoặc hệ thống hiện tại.** Những kết luận trên áp dụng cho vụ tai nạn và hệ thống thử nghiệm được báo cáo; không tự động đại diện cho tất cả xe tự hành hoặc phiên bản phần mềm sau này.

## 8. Đánh giá Harm Map và điểm can thiệp

### Vì sao các trường không có cùng mức đánh giá?

**Severity là Critical** vì nguồn xác nhận một người đã tử vong. **Scale trực tiếp là một nạn nhân** trong vụ được điều tra, không phải mọi chủ xe thử nghiệm. **Probability và Frequency chưa đủ dữ liệu** vì báo cáo không cung cấp số lần phơi nhiễm với cùng tình huống hoặc số lần lặp lại chính xác cùng chuỗi lỗi. Ghi giới hạn bằng chứng là một kết quả đánh giá, không phải bỏ trống trường.

NTSB phân tích một chuỗi mất dự phòng: phát hiện vật thể nhưng không hiểu đúng đường đi; thiết kế xử lý khẩn cấp không ưu tiên giảm hậu quả khi không tránh được va chạm; lớp FCW/AEB gốc không hoạt động; người vận hành mất tập trung; tổ chức không quản lý hữu hiệu các rủi ro này. Vì vậy, việc cải thiện độ chính xác nhận dạng đơn lẻ chưa đủ để giải quyết toàn bộ Harm Map. [Tr. 39–45, 57–59](har1903.pdf#page=51).

### Ai cần kiểm tra, tại thời điểm nào?

Bảng dưới đây là **đề xuất của tôi** dựa trên các vấn đề NTSB nêu, không phải khẳng định mọi biện pháp đã được triển khai.

| Điểm can thiệp | Người chịu trách nhiệm kiểm tra | Điều cần kiểm tra và bằng chứng để chấp nhận |
| --- | --- | --- |
| Trước thử nghiệm trên đường công cộng | Nhóm an toàn độc lập và người phê duyệt thử nghiệm | Kịch bản người dắt xe đạp sang đường ngoài vạch; lịch sử tracking còn được sử dụng sau đổi nhãn; giới hạn hệ thống và phương án dự phòng được kiểm thử, ghi lại. |
| Khi tích hợp ADS với xe | Kỹ sư hệ thống và người kiểm định an toàn | Xung đột radar/lệnh phanh được xử lý; mất một chức năng không đồng thời làm mất mọi lớp giảm thiểu va chạm. Không coi việc vô hiệu hóa AEB là giải pháp đầy đủ khi chưa có dự phòng tương đương. |
| Khi xe gặp tình huống khẩn cấp | ADS thực thi dự phòng kỹ thuật; người vận hành đã được đào tạo giám sát và can thiệp | Cảnh báo phải có thời gian để phản ứng; phương tiện vẫn cần giảm mức độ va chạm khi không thể tránh hoàn toàn. Không dựa vào một giả định rằng người vận hành luôn tập trung. |
| Trong chuyến thử nghiệm | Người vận hành chính, người giám sát bổ sung và quản lý ca | Theo dõi sự chú ý, kiểm soát dùng điện thoại và phân công rõ việc quan sát/ghi chú. Human review cần cơ chế giám sát hữu hiệu, không chỉ tên một người trong quy trình. |
| Sau sự cố hoặc near-miss | Nhóm điều tra/an toàn và người phê duyệt chạy lại | Đối chiếu log, video và các thời điểm cảnh báo/phanh; tái hiện trong mô phỏng hoặc sân thử; kiểm tra hồi quy và điều kiện chạy lại trước khi tiếp tục thử công cộng. |

**Đánh đổi cần quản lý:** tránh phanh nhầm có thể là mục tiêu hợp lý, nhưng trì hoãn phanh và không giảm thiệt hại khi va chạm không tránh được làm giảm dự phòng trong vụ này. Cần kiểm thử cả false positive lẫn false negative và hậu quả của mỗi loại; không tối ưu cảm giác vận hành êm bằng cách bỏ qua tổn hại có thể giảm được. Đây là nhận định của tôi từ thiết kế action suppression và kết luận của NTSB. [Tr. 13–14, 40–41](har1903.pdf#page=52).
