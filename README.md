# Lab 21 — Phân tích rủi ro AI qua case study thực tế

- Họ và tên: Đỗ Trọng Bình
- Mã học viên: 2A202602855
- Lớp: H201
- Ngành đã chọn: **Mobility / autonomous driving — AI trong di chuyển, xe tự hành**

### 1. Industry Risk Snapshot

**Phạm vi:** hệ thống AI nhận biết môi trường, dự đoán chuyển động và hỗ trợ hoặc điều khiển xe trên đường bộ. Hai case dưới đây gồm một hệ thống lái tự động thử nghiệm có người giám sát và một hệ thống hỗ trợ lái cấp 2. Các mức Thấp / Trung bình / Cao là nhận định định tính của tôi cho bài tập, không phải phân loại pháp lý.

| Nội dung | Đánh giá của tôi và lý do |
| --- | --- |
| Những tác hại chính có thể xảy ra | Nhận diện sai người đi bộ, dự đoán sai quỹ đạo hoặc điều khiển sai có thể gây va chạm, thương tích, tử vong và thiệt hại tài sản cho người đi đường, tài xế và hành khách. Người giám sát quá tin vào AI có thể bỏ lỡ thời điểm can thiệp. Việc lưu hoặc chia sẻ dữ liệu hành trình có thể xâm phạm riêng tư; đây là nguy cơ ở mức ngành, không phải hậu quả đã được xác nhận trong hai case. |
| Mức độ high-stakes | **Cao.** Quyết định lái, tăng tốc hoặc phanh tác động trực tiếp tới tính mạng, kể cả người không sử dụng dịch vụ. Thời gian xử lý có thể chỉ tính bằng giây; hậu quả va chạm nặng khó khắc phục. Hai sự kiện được NTSB điều tra dưới đây minh họa mức độ nghiêm trọng, nhưng không đủ để suy ra xác suất tai nạn của toàn ngành. |
| Dữ liệu nhạy cảm có thể được sử dụng | Tùy hệ thống: vị trí GPS, lịch sử hành trình, địa chỉ đón/trả, video đường phố ghi khuôn mặt hoặc biển số, video trong cabin và dữ liệu theo dõi sự chú ý của tài xế. Các dữ liệu này có thể nhận diện cá nhân hoặc suy ra thói quen đi lại. Không đưa dữ liệu cá nhân thật vào báo cáo. |
| Nhu cầu human review | **Cao.** Trước triển khai hoặc cập nhật, kỹ sư và nhóm an toàn cần kiểm tra các tình huống nguy hiểm, giới hạn vận hành và cơ chế giảm thiểu. Với xe thử nghiệm có người giám sát và hỗ trợ lái cấp 2, người vận hành phải theo dõi liên tục và sẵn sàng can thiệp. Sau sự cố, nhóm an toàn cần xem log trước khi cho tiếp tục vận hành. Không thể chỉ dựa vào phản ứng của con người khi nguy hiểm xuất hiện quá nhanh; cần cơ chế an toàn tự động. Với xe vận hành không có tài xế, phải thiết kế phương án dừng an toàn phù hợp. |

### 2. Case study 1 — Uber ATG: xe thử nghiệm đâm người đi bộ tại Tempe (2018)

#### Brief Case

- **Tổ chức / sản phẩm AI:** Uber Advanced Technologies Group (ATG); ADS thử nghiệm trên Volvo XC90 cải tiến, có người giám sát.
- **Thời gian, địa điểm / bối cảnh:** 21:58 ngày 18/03/2018, N. Mill Avenue, Tempe, Arizona, Hoa Kỳ; người đi bộ dắt xe đạp sang đường ngoài vạch qua đường. [U2]
- **AI được dùng để làm gì:** Nhận biết vật thể, dự đoán chuyển động và điều khiển xe theo tuyến thử nghiệm. [U1]
- **Vấn đề hoặc sự kiện đáng chú ý:** Xe đâm chết người đi bộ. ADS không phân loại đúng người này và không dự đoán đúng đường đi; thiết kế dựa vào người vận hành thay vì phanh khẩn cấp giảm nhẹ va chạm. NTSB xác định người vận hành mất tập trung vì điện thoại; đánh giá rủi ro, giám sát và văn hóa an toàn của Uber cũng góp phần. [U2]
- **Số liệu có nguồn:** Trong lần va chạm này, ADS phát hiện đối tượng trước **5,6 giây**; tới **1,2 giây** trước va chạm mới xác định tình huống khẩn cấp. Đây là mốc thời gian của một sự kiện, không phải tỷ lệ lỗi. [U1, mục 1.1 và 1.5.6.1]
- **Nguồn:**
  - **[U1]** *Collision Between Vehicle Controlled by Developmental Automated Driving System and Pedestrian, Tempe, Arizona, March 18, 2018* — NTSB, HAR-19/03; thông qua **19/11/2019**, sửa tên báo cáo **26/06/2020**. [Báo cáo PDF](https://www.ntsb.gov/investigations/AccidentReports/Reports/HAR1903.pdf), trang in **1, 16–17, 59** (trang PDF **13, 28–29, 71**).
  - **[U2]** [Hồ sơ điều tra HWY18MH010](https://www.ntsb.gov/investigations/Pages/HWY18MH010.aspx) — NTSB; trang không ghi ngày công bố, truy cập **07/10/2026**; mục *What Happened* và *What We Found*.
- **Phân biệt bằng chứng và nhận định:** Nguồn xác nhận tử vong và các hạn chế nêu trên. Tôi nhận định giám sát con người cần đi cùng cơ chế an toàn dự phòng. Chưa có căn cứ từ case này để ước tính rủi ro trên mỗi km của toàn bộ xe tự hành.

#### Harm Map Worksheet

**Cách đọc:** Sự kiện và số liệu dẫn [U1]/[U2] là bằng chứng từ NTSB. Failure mode, layer, harm lens và severity là cách tôi ánh xạ vào worksheet của lớp; NTSB không dùng hệ nhãn này. Với xe tự hành, tôi hiểu “escalation” là chuyển sang người vận hành can thiệp khi hệ thống không còn xử lý an toàn được.

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | **1,2 giây trước va chạm**, ADS xác định tình huống khẩn cấp nhưng bắt đầu khoảng trì hoãn hành động kéo dài **1 giây** để chờ người vận hành. Âm báo xuất hiện khoảng **0,2 giây trước va chạm**, cùng kế hoạch giảm tốc từ từ. Tôi chọn thời điểm cần can thiệp này để phân tích. [U1, mục 1.5.6.1, trang 16–17] |
| Stakeholder bị ảnh hưởng | Người đi bộ là người chịu hậu quả trực tiếp dù không sử dụng xe; người vận hành là người chịu trách nhiệm giám sát. Người thân nạn nhân, Uber ATG và đơn vị quản lý thử nghiệm là các bên liên quan; nguồn được dùng chưa định lượng tổn thất của từng bên. |
| Failure mode | **Escalation failure — chính:** Theo cách hiểu trên, cơ chế chờ người can thiệp và báo hiệu quá muộn không tạo được chuyển tiếp an toàn trong sự kiện này. **Over-reliance — liên quan:** NTSB nêu thiếu biện pháp chống sự chủ quan do tự động hóa, cùng việc người vận hành mất tập trung. Lỗi phân loại/dự đoán là hạn chế kỹ thuật có nguồn; tôi không gọi lỗi đó là hallucination. [U1, trang 16–17; U2, What We Found] |
| Layer bắt đầu lỗi | **Safety, đối với cơ chế chuyển sang người can thiệp đã chọn:** Thiết kế không thực hiện phanh khẩn cấp chỉ để giảm nhẹ va chạm và phụ thuộc người vận hành khi đã vượt giới hạn phanh của ADS. Đây là ánh xạ chức năng bảo vệ của tôi. **Chưa đủ bằng chứng** để xác định thành phần mô hình hoặc lỗi khởi phát đầu tiên của toàn chuỗi nhận biết–dự đoán–điều khiển. [U1, trang 17] |
| Harm xảy ra là gì? | **Đã xảy ra:** Người đi bộ bị tử vong khi xe thử nghiệm đâm vào trong lúc sang đường; người vận hành không bị thương. [U2, What Happened] **Nguy cơ tôi suy luận:** Tình huống tương tự có thể gây thương tích cho những người đi đường khác; đây không phải số nạn nhân bổ sung của vụ việc. |
| Harm lens | **Injury — tổn hại thể chất**, cụ thể là mất mạng. Chọn lens này vì hậu quả trực tiếp được xác nhận; không có bằng chứng trong case để ghi privacy loss hoặc dignity loss như hậu quả đã xảy ra. |
| Severity | **Critical — đánh giá của tôi**, do hậu quả tử vong, không thể khắc phục. Mức này mô tả độ nghiêm trọng, không thể hiện xác suất xảy ra cao. |
| Scale | Trong vụ Tempe được phân tích: **1 người tử vong**, **1 xe thử nghiệm** va chạm với người đi bộ; người vận hành không bị thương. [U2] Đây là phạm vi quan sát của một vụ việc; không suy rộng thành số người chịu ảnh hưởng trên toàn đội xe. Tác động gián tiếp tới người thân/tổ chức chưa được định lượng. |
| Probability | **Chưa đủ dữ liệu để đánh giá.** Một vụ đã xảy ra không cho biết xác suất tái diễn. Cần số lần gặp tình huống tương tự và số lần xảy ra lỗi/harm, gắn với cùng phiên bản ADS và điều kiện thử nghiệm; không tự gán phần trăm hoặc mức Low / Medium / High. |
| Frequency | **Chưa đủ dữ liệu để đánh giá tần suất của chuỗi lỗi cụ thể này.** Báo cáo mô tả một sự kiện, chưa cung cấp số lần lặp lại chuỗi “nhận diện sai → chờ can thiệp → va chạm” trên mỗi giờ hoặc km trong điều kiện tương đương. Không coi việc mất tập trung nhiều lần là nhiều tai nạn. |
| Vì sao? | Tôi chọn moment chuyển sang người can thiệp để thấy rõ mối liên hệ **Moment → Escalation failure → Safety → Injury → Critical**. Các mốc thời gian trong [U1, trang 16–17] hỗ trợ đánh giá cơ chế bảo vệ; tử vong trong [U2] là căn cứ cho severity và scale. Probability cần mẫu số tình huống; frequency cần số lần lặp theo thời gian/quãng đường nên cả hai chưa xác định. NTSB nêu nhiều yếu tố góp phần, vì vậy tôi không quy toàn bộ hậu quả cho riêng AI hoặc riêng người vận hành. |

### 3. Case study 2 — Tesla Autopilot: va chạm tại Mountain View (2018)

#### Brief Case

- **Tổ chức / sản phẩm AI:** Tesla Model X 2017; Autopilot gồm Autosteer và Traffic-Aware Cruise Control. Đây là **hỗ trợ lái cấp 2**, tài xế phải giám sát liên tục. [T1, trang vii]
- **Thời gian, địa điểm / bối cảnh:** 09:27 ngày 23/03/2018, nút giao US-101/SR-85, Mountain View, California, Hoa Kỳ. [T2]
- **AI được dùng để làm gì:** Hỗ trợ giữ làn, điều khiển tốc độ và khoảng cách với xe phía trước. [T2]
- **Vấn đề hoặc sự kiện đáng chú ý:** Autopilot lái xe vào vùng phân luồng không dành cho xe chạy rồi đâm bộ giảm chấn đã hỏng; tài xế tử vong. NTSB xác định giới hạn hệ thống, tài xế không phản ứng do mất tập trung có khả năng liên quan trò chơi điện thoại và quá tin vào Autopilot; giám sát tài xế kém hiệu quả góp phần. Bộ giảm chấn hỏng làm hậu quả nặng hơn. [T2]
- **Số liệu có nguồn:** Trong sự kiện này, Autosteer bắt đầu đánh lái trái **5,9 giây** trước va chạm; tốc độ khi đâm bộ giảm chấn là **70,8 mph**. Đây là dữ liệu của xe trong một vụ tai nạn, không phải thống kê toàn đội xe. [T1, mục 1.2 và 2.2.1]
- **Nguồn:**
  - **[T1]** *Collision Between a Sport Utility Vehicle Operating With Partial Driving Automation and a Crash Attenuator, Mountain View, California, March 23, 2018* — NTSB, HAR-20/01; thông qua **25/02/2020**. [Báo cáo PDF](https://www.ntsb.gov/investigations/AccidentReports/Reports/HAR2001.pdf), trang in **vii, 6, 31, 40–41, 58** (trang PDF **10, 26, 51, 60–61, 78**).
  - **[T2]** [Hồ sơ điều tra HWY18FH011](https://www.ntsb.gov/investigations/Pages/HWY18FH011.aspx) — NTSB; trang không ghi ngày công bố, truy cập **07/10/2026**; mục *What Happened* và *What We Found*.
- **Phân biệt bằng chứng và nhận định:** NTSB xác nhận hậu quả và các yếu tố trên; việc chơi game được nêu ở mức khả năng. Tôi nhận định cần kiểm soát giới hạn vận hành và sự chú ý của tài xế. Case không chứng minh mọi phiên bản Autopilot có cùng lỗi hoặc rủi ro cao hơn lái thủ công.

#### Harm Map Worksheet

**Cách đọc:** Sự kiện và số liệu dẫn [T1]/[T2] là bằng chứng từ NTSB. Các nhãn phân tích dưới đây là nhận định của tôi theo worksheet. Autopilot trong case này là hỗ trợ lái cấp 2, tài xế phải giám sát liên tục.

| Trường | Phân tích của tôi |
| --- | --- |
| High-risk moment | **5,9 giây trước va chạm**, Autosteer bắt đầu đánh lái trái vào vùng phân luồng không dành cho xe chạy; tài xế không thực hiện động tác tránh va chạm. Xe sau đó đâm bộ giảm chấn ở **70,8 mph**. Tôi chọn thời điểm xe rời đường đi an toàn nhưng người giám sát không can thiệp. [T1, mục 1.2 và 2.2.1, trang 6, 31] |
| Stakeholder bị ảnh hưởng | Tài xế Tesla và tài xế hai xe Mazda/Audi liên quan là những người trực tiếp trong vụ việc. Người thân, lực lượng cứu hộ, Tesla và đơn vị quản lý hạ tầng là các bên liên quan; không mặc định mọi bên đều đã bị thiệt hại thể chất hoặc có tổn thất được định lượng. |
| Failure mode | **Over-reliance — chính:** NTSB nêu tài xế quá tin vào Autopilot và không phản ứng, cùng tình trạng mất tập trung có khả năng liên quan trò chơi điện thoại. Tôi không khẳng định việc chơi game chắc chắn đã xảy ra. Lỗi hướng lái là hạn chế hệ thống được ghi nhận; không đủ căn cứ để gọi là hallucination hoặc bias. [T2, What We Found] |
| Layer bắt đầu lỗi | **Safety, đối với việc ngăn mất giám sát:** Cơ chế theo dõi sự tham gia của tài xế không hiệu quả, cho phép sự thiếu chú ý tiếp diễn. Đây là cách tôi ánh xạ bằng chứng sang lớp bảo vệ. **Chưa đủ bằng chứng** để xác định lỗi gốc của mô hình gây đánh lái, hoặc kết luận thiết kế UX cụ thể đã khiến tài xế hiểu sai. [T1, mục 2.2.4.5, trang 40–41; T2] |
| Harm xảy ra là gì? | **Đã xảy ra:** Tài xế Tesla bị tử vong khi xe đâm bộ giảm chấn; tài xế Mazda bị thương nhẹ trong các va chạm liên quan; tài xế Audi không bị thương. Bộ giảm chấn đã hỏng góp phần làm hậu quả nặng hơn. [T2] **Nguy cơ tôi suy luận:** Mất giám sát ở tình huống khác có thể gây thêm thương tích cho người đi đường; nguồn không xác nhận nạn nhân bổ sung trong case này. |
| Harm lens | **Injury — tổn hại thể chất**, gồm tử vong và thương tích đã xác nhận. Tôi không chọn misinformation chỉ vì tài xế quá tin hệ thống: case chưa chứng minh AI đã cung cấp một thông tin sai cụ thể cho tài xế. |
| Severity | **Critical — đánh giá của tôi** cho toàn sự kiện, dựa trên hậu quả tử vong. Người lái Mazda bị thương nhẹ không làm giảm mức nghiêm trọng của hậu quả nặng nhất; cũng không có nghĩa mọi người trong vụ việc chịu mức tổn hại Critical. |
| Scale | Trong vụ Mountain View: **3 xe** liên quan, **1 người tử vong**, **1 người bị thương nhẹ**; tài xế Audi không bị thương. [T2, What Happened] Đây là phạm vi của vụ tai nạn, không phải số người bị ảnh hưởng trên toàn bộ khách hàng Autopilot; tác động gián tiếp chưa được định lượng. |
| Probability | **Chưa đủ dữ liệu để đánh giá.** Muốn ước tính khả năng xảy ra chuỗi “đánh lái vào vùng phân luồng + tài xế không can thiệp”, cần tổng số tình huống tương đương và số lần lỗi/harm trên cùng phiên bản hệ thống. Một vụ tử vong không chứng minh xác suất cao hoặc xác suất bằng 100%. |
| Frequency | **Chưa đủ dữ liệu để đánh giá tần suất của chuỗi lỗi cụ thể này.** NTSB có xem xét các vụ Autopilot khác, nhưng không thể coi mọi vụ đều có cùng cơ chế lỗi; cần dữ liệu lặp lại theo giờ/km và điều kiện tương đương. [T2] Không suy ra mức High chỉ từ việc đã có tai nạn. |
| Vì sao? | Luồng tôi chọn là **Moment → Over-reliance → Safety → Injury → Critical**. [T1, trang 6, 31, 40–41] và [T2] hỗ trợ việc nhận diện tình huống, thiếu giám sát và hậu quả. Severity dựa vào tử vong; scale dựa vào số xe/người được ghi nhận. Probability và frequency thiếu dữ liệu phơi nhiễm và lặp lại nên để chưa xác định. Đường đi của xe, hành vi tài xế và bộ giảm chấn hỏng cùng góp phần; ánh xạ Safety không phải kết luận rằng toàn bộ nguyên nhân bắt đầu ở một lớp duy nhất. |
