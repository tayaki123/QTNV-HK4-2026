# CHƯƠNG 3: PHƯƠNG PHÁP THỰC HIỆN DỰA TRÊN BẰNG CHỨNG
## Quy trình: Xử lý đơn hàng trực tuyến tại FAHASA

---

## 3.1. Mô tả quy trình chi tiết

Quy trình xử lý đơn hàng trực tuyến của FAHASA tập trung vào việc tối ưu hóa thời gian xử lý và giảm thiểu sai sót.

*   **Bước 1: Tiếp nhận và xác thực đơn hàng**
    *   **Mục tiêu:** Đảm bảo đơn hàng hợp lệ, đầy đủ thông tin giao nhận và hàng hóa sẵn sàng trong kho.
    *   **Bộ phận/Vai trò:** Hệ thống quản lý đơn hàng.
    *   **Hành động cụ thể:** Hệ thống tự động đồng bộ đơn hàng từ Website/Ứng dụng FAHASA, tiến hành đối chiếu với tồn kho thực tế trên hệ thống kho.
    *   **Điều kiện rẽ nhánh:**
        *   *Nếu hết hàng hoặc hàng lỗi:* Hệ thống chuyển trạng thái sang "Cần xử lý", đẩy yêu cầu về cho nhân viên Chăm sóc khách hàng gọi điện báo khách đổi sách khác hoặc hủy hoàn tiền.
        *   *Nếu đủ hàng:* Hệ thống chuyển trạng thái sang "Sẵn sàng lấy hàng" và tự động đẩy lệnh xuống kho.

*   **Bước 2: Lấy hàng**
    *   **Mục tiêu:** Nhặt đúng sách, đủ số lượng trong thời gian di chuyển ngắn nhất.
    *   **Bộ phận/Vai trò:** Nhân viên kho, Hệ thống quản lý kho.
    *   **Hành động cụ thể:** Hệ thống sử dụng thuật toán gộp đơn và vẽ lộ trình lấy hàng ngắn nhất. Nhân viên kho cầm thiết bị thông minh, đi theo chỉ dẫn, đến vị trí kệ quét mã vạch kệ và mã vạch sách để xác nhận lấy đúng hàng.
    *   **Điều kiện rẽ nhánh:**
        *   *Nếu phát hiện sách rách bìa/cong góc:* Nhân viên báo cáo lỗi qua thiết bị cầm tay, đưa sách ra rổ hàng lỗi. Hệ thống tự động tạo lệnh lấy bù cuốn khác.

*   **Bước 3: Đóng gói và dán nhãn**
    *   **Mục tiêu:** Bảo vệ an toàn cho sách trong quá trình vận chuyển và dán đúng tem vận đơn.
    *   **Bộ phận/Vai trò:** Nhân viên đóng gói.
    *   **Hành động cụ thể:** Nhân viên quét mã vạch sản phẩm tại bàn thao tác. Hệ thống màn hình sẽ hiển thị xác nhận đủ hàng, tự động in tem vận đơn. Nhân viên bọc 2 lớp xốp hơi, chèn xốp cố định trong hộp carton theo quy trình chuẩn, dán băng keo niêm phong và dán tem vận đơn.

*   **Bước 4: Bàn giao đối tác vận chuyển**
    *   **Mục tiêu:** Bàn giao chính xác số lượng kiện hàng, đảm bảo cam kết về thời gian xuất kho.
    *   **Bộ phận/Vai trò:** Điều phối viên kho, Tài xế đối tác (Giao Hàng Tiết Kiệm, Viettel Post, J&T).
    *   **Hành động cụ thể:** Gom các đơn hàng đã đóng gói theo từng hãng vận chuyển. Quét mã vạch tổng xuất kho. Tài xế đồng kiểm đếm số lượng, quét mã nhận hàng và hai bên ký biên bản bàn giao.

*   **Bước 5: Cập nhật trạng thái và đối soát**
    *   **Mục tiêu:** Cung cấp thông tin minh bạch cho khách hàng và quản lý dòng tiền.
    *   **Bộ phận/Vai trò:** Hệ thống quản lý đơn hàng, Kế toán đối soát.
    *   **Hành động cụ thể:** Hệ thống kết nối tự động với hãng vận chuyển để cập nhật trạng thái thời gian thực: *Đang giao, Giao thành công, Chuyển hoàn*. Kế toán định kỳ tải tệp dữ liệu để đối soát tiền thu hộ và phí vận chuyển.

---

## 3.2. Sơ đồ tổ chức & Phân nhiệm

Để vận hành quy trình trơn tru, FAHASA bố trí sơ đồ nhân sự tại Trung tâm xử lý đơn hàng như sau:

| Chức danh | Trách nhiệm cụ thể trong quy trình |
| :--- | :--- |
| **Giám đốc vận hành** | Quản trị toàn bộ cam kết thời gian xử lý đơn. Phê duyệt các cải tiến hệ thống và dự toán chi phí vật tư đóng gói. |
| **Quản lý kho** | Giám sát trực tiếp năng suất lấy hàng và đóng gói. Phân bổ nhân sự linh hoạt giữa các khâu khi có tắc nghẽn. |
| **Điều phối viên** | Theo dõi tiến độ đơn hàng trên hệ thống. Trực tiếp làm việc với tài xế các hãng vận chuyển để tổ chức khu vực bàn giao nhanh chóng. |
| **Nhân viên lấy hàng** | Đảm bảo tuân thủ lộ trình lấy hàng trên máy quét. Nhặt đúng mã sách, báo cáo kịp thời nếu phát hiện hàng hư hỏng trên kệ. |
| **Nhân viên đóng gói** | Tuân thủ tuyệt đối quy trình đóng gói. Đảm bảo 100% không dán nhầm mã vận đơn (đơn của người này dán cho người kia). |
| **Kế toán đối soát** | Xử lý công nợ tiền thu hộ với đối tác vận chuyển. Theo dõi và thu hồi chi phí bồi thường khi hãng vận chuyển làm mất/hỏng hàng. |
| **Nhân viên chăm sóc khách hàng** | Xử lý các ngoại lệ: đơn hàng bị khách hủy đột xuất, đơn vị vận chuyển lấy hàng trễ, giải quyết khiếu nại của khách. |

---

## 3.3. Bảng kế hoạch làm việc

Kế hoạch làm việc được thiết kế để đảm bảo kho hoạt động liên tục, đáp ứng yêu cầu giao hàng nhanh:

### 3.3.1. Kế hoạch theo ngày

| Ca làm việc | Khung giờ | Nhiệm vụ trọng tâm |
| :--- | :---: | :--- |
| **Ca sáng** | 06h00 – 14h00 | Ưu tiên xử lý toàn bộ đơn hàng khách đặt từ tối hôm trước. Bàn giao đợt 1 cho đối tác vận chuyển lúc 10h00, đợt 2 lúc 13h30. |
| **Ca chiều** | 14h00 – 22h00 | Xử lý các đơn hàng phát sinh trong giờ hành chính. Bàn giao đợt 3 lúc 16h00. Từ 18h00 trở đi tập trung gom đơn để bàn giao chuyến chót lúc 21h00. |
| **Ca đêm / Chốt ngày** | 22h00 – 06h00 | Tạm ngưng lấy hàng. Đội ngũ kho dọn dẹp vệ sinh, sắp xếp lại kệ. Hệ thống chạy tiến trình đồng bộ tồn kho, chuẩn bị dữ liệu lộ trình lấy hàng cho ca sáng hôm sau. |

### 3.3.2. Kế hoạch theo tuần

| Ngày | Nhiệm vụ trọng tâm |
| :--- | :--- |
| **Thứ Hai – Thứ Sáu** | Hoạt động theo quy trình chuẩn. Đánh giá báo cáo năng suất hàng ngày trong cuộc họp ngắn 15 phút vào 6h00 sáng. |
| **Thứ Bảy** | Tăng cường đội ngũ đóng gói để xử lý lượng đơn cuối tuần tăng vọt. Thực hiện kiểm kê luân phiên tại các kệ có tỷ lệ lấy hàng sai cao. |
| **Chủ Nhật** | Bố trí nhân sự ở mức 60% (do các hãng vận chuyển giảm tần suất lấy hàng). Tiến hành bảo trì thiết bị mạng, máy in nhiệt, sạc và kiểm tra thiết bị cầm tay. |

### 3.3.3. Kế hoạch theo tháng

| Kỳ | Thời gian | Nhiệm vụ trọng tâm |
| :--- | :---: | :--- |
| **Kỳ đầu tháng** | Ngày 1 – 5 | Dự báo sản lượng cho các chương trình khuyến mãi lớn. Dự trù và đặt mua vật tư (thùng carton các kích cỡ, băng keo, xốp hơi). |
| **Giữa tháng** | Ngày 15 – 16 | Quản lý kho họp với các đối tác vận chuyển để đánh giá chất lượng dịch vụ: tỷ lệ giao thành công, tỷ lệ rách hỏng. |
| **Cuối tháng đối soát** | Ngày 25 – 30 | Kế toán chốt đối soát tiền thu hộ, xuất hóa đơn phí dịch vụ. Bộ phận chăm sóc khách hàng tổng hợp báo cáo khiếu nại tháng. |

---

## 3.4. Thuật ngữ & Hệ thống

| Thuật ngữ | Giải nghĩa chuyên ngành nghiệp vụ |
| :--- | :--- |
| **Hệ thống quản lý đơn hàng** | Nơi tiếp nhận, lưu trữ và điều phối trạng thái mọi đơn hàng trực tuyến của FAHASA. |
| **Hệ thống quản lý kho** | Điều khiển vị trí kệ hàng, tối ưu lộ trình nhặt hàng và quản lý mức tồn kho thời gian thực. |
| **Quy trình chuẩn** | Quy trình thao tác chuẩn. Mọi nhân viên đóng gói phải làm theo từng bước quy định để đảm bảo đồng đều chất lượng. |
| **Thiết bị cầm tay** | Thiết bị thông minh có tích hợp máy quét mã vạch laser chuyên dụng để quét sách và kệ hàng. |
| **Bảng kê** | Bảng kê khai danh sách tổng hợp mã vận đơn các kiện hàng, dùng để ký xác nhận khi bàn giao cho tài xế. |
| **Tiền thu hộ** | Số tiền thu hộ khách hàng bằng tiền mặt khi giao hàng thành công. |
| **Cam kết dịch vụ** | Cam kết mức độ dịch vụ. Ví dụ: Cam kết 100% đơn hàng phải được đóng gói trong vòng 4 giờ. |
| **Tem vận đơn** | Tem dán trên gói hàng chứa thông tin người nhận và mã vạch để theo dõi hành trình giao hàng. |

---

## 3.5. Biểu mẫu nghiệp vụ

### Biểu mẫu 1: Biên bản bàn giao bưu gửi

**CÔNG TY CP PHÁT HÀNH SÁCH FAHASA**
**BIÊN BẢN BÀN GIAO HÀNG HÓA CHO ĐỐI TÁC VẬN CHUYỂN**
Mã biên bản: BG-20260824-001 | Ngày bàn giao: .../.../20... | Ca: [Sáng / Chiều]

*   **Bên giao (Kho FAHASA):** .................................... - Nhân viên Điều phối: .................................
*   **Bên nhận (Đối tác):** [ ] Giao Hàng Tiết Kiệm  [ ] SPX  [ ] Viettel Post - Tên tài xế: ..........................
*   **Biển số xe:** ................................. - SĐT Tài xế: .......................................

| STT | Mã kiện tổng (Túi/Bao) | Số lượng đơn hàng bên trong | Tình trạng ngoại quan | Ghi chú |
| :---: | :--- | :---: | :--- | :--- |
| 1 | BAO-GHTK-001 | 45 | [x] Nguyên tem niêm phong | Hàng dễ vỡ |
| 2 | BAO-GHTK-002 | 50 | [x] Nguyên tem niêm phong | |
| 3 | Khai thác rời | 12 (Đơn hàng lớn/quá khổ) | [x] Hộp nguyên vẹn | |
| **Tổng:** | **3 đầu mục** | **107 Đơn hàng** | | |

*Cam kết: Bên nhận đã đồng kiểm đếm đủ số lượng kiện hàng và xác nhận tình trạng niêm phong nguyên vẹn trước khi rời kho.*

*   **Chữ ký bên giao:** ______________________
*   **Chữ ký bên nhận:** ______________________

---

### Biểu mẫu 2: Biên bản đối soát thu hộ & Phí vận chuyển

**CÔNG TY CP PHÁT HÀNH SÁCH FAHASA**
**BIÊN BẢN ĐỐI SOÁT VẬN CHUYỂN ĐỊNH KỲ**
Kỳ đối soát: Từ ngày 01/08/20... đến 15/08/20... | Đối tác: GIAO HÀNG TIẾT KIỆM

**A. THỐNG KÊ SẢN LƯỢNG**

1. Tổng số đơn hàng phát sinh: 15.420 đơn
2. Đơn hàng giao thành công: 14.800 đơn (Tỷ lệ: 96%)
3. Đơn hàng chuyển hoàn: 620 đơn
4. Đơn hàng thất lạc/Hư hỏng: 05 đơn (Cần bồi thường)

**B. CHI TIẾT TÀI CHÍNH (VNĐ)**

| Hạng mục | Số tiền phát sinh | Diễn giải |
| :--- | ---: | :--- |
| Tổng tiền thu hộ (1) | 3.450.000.000 | Tiền thực tế tài xế thu của khách |
| Tổng cước vận chuyển (2) | 370.000.000 | Cước tính theo bảng giá hợp đồng |
| Phí chuyển hoàn (3) | 3.100.000 | Cước phí hàng quay đầu về kho FAHASA |
| Phí bồi thường mất hàng (4) | 1.250.000 | Theo giá trị khai báo của đơn hàng |
| **SỐ TIỀN THỰC NHẬN** | **3.078.150.000** | **Công thức: (1) - (2) - (3) + (4)** |

*   **Kế toán FAHASA (Ký & Đóng dấu):** ______________________
*   **Kế toán Đối tác (Ký & Đóng dấu):** ______________________

---

### Biểu mẫu 3: Phiếu ghi nhận sự cố vận hành kho

**PHIẾU GHI NHẬN SỰ CỐ / NGOẠI LỆ VẬN HÀNH**
Ngày ghi nhận: .../.../20... | Thời gian xảy ra: __:__ | Mức độ ảnh hưởng: [ ] Thấp  [x] Cao  [ ] Nghiêm trọng

**1. THÔNG TIN SỰ CỐ:**
*   Phân loại: [ ] Lỗi hệ thống  [ ] Hỏng thiết bị  [x] Lỗi đối tác vận chuyển  [ ] Khác...
*   Mô tả chi tiết: Vào ca 16h00, xe tải của bên đối tác SPX đến trễ 2 tiếng so với cam kết. Dẫn đến tồn đọng 1.200 đơn hàng trên khu vực bàn giao, gây ùn tắc không có chỗ chứa hàng cho ca đóng gói tiếp theo.

**2. HÀNH ĐỘNG XỬ LÝ TỨC THỜI:**
*   Điều phối viên đã liên hệ đường dây nóng của SPX để thúc giục xe tải.
*   Quản lý kho chỉ đạo tạm dừng khu vực đóng gói 30 phút, dồn 1.200 đơn hàng SPX sang khu vực lưu trữ dự phòng để giải phóng mặt bằng bàn giao cho xe của Viettel Post vào lấy hàng lúc 17h00.

**3. ĐỀ XUẤT PHÒNG NGỪA:**
*   Gửi thư điện tử cảnh báo cho Giám đốc Bưu cục SPX khu vực. Nếu tái phạm trên 3 lần/tháng, đề xuất tự động cấu hình hệ thống giảm 50% sản lượng phân bổ cho SPX vào khung giờ chiều.

*   **Người lập phiếu:** ______________________
*   **Duyệt bởi Quản lý kho:** ______________________

---

## 3.6. Bảng câu hỏi phỏng vấn thu thập dữ liệu

### 3.6.1. Câu hỏi định tính (10 câu)

#### 3.6.1.1. Câu hỏi có cấu trúc (05 câu)
*Dạng trắc nghiệm nhiều lựa chọn và thang đo đánh giá Likert 1–5*

| STT | Nội dung câu hỏi | Lựa chọn trả lời | Đối tượng phỏng vấn |
| :---: | :--- | :--- | :--- |
| C1.1 | Theo anh/chị, mức độ phức tạp của quy trình xử lý đơn hàng trực tuyến hiện tại tại FAHASA là? *(Thang đo 1–5: 1 = Rất đơn giản, 5 = Rất phức tạp)* | ☐ 1 &emsp; ☐ 2 &emsp; ☐ 3 &emsp; ☐ 4 &emsp; ☐ 5 | Nhân viên vận hành |
| C1.2 | Khâu nào thường xuyên gây ra tình trạng tắc nghẽn nhất trong quy trình xử lý đơn hàng trực tuyến? | ☐ Tiếp nhận & xác thực đơn hàng<br>☐ Lấy hàng tại kệ<br>☐ Đóng gói & dán nhãn<br>☐ Bàn giao đối tác vận chuyển<br>☐ Cập nhật trạng thái & đối soát | Điều phối viên |
| C1.3 | Anh/chị đánh giá mức độ hỗ trợ của hệ thống quản lý kho trong việc tối ưu lộ trình lấy hàng ở mức nào? *(Thang đo 1–5: 1 = Hoàn toàn không hỗ trợ, 5 = Hỗ trợ rất tốt)* | ☐ 1 &emsp; ☐ 2 &emsp; ☐ 3 &emsp; ☐ 4 &emsp; ☐ 5 | Nhân viên vận hành |
| C1.4 | Nguyên nhân phổ biến nhất dẫn đến việc đơn hàng bị giao trễ so với cam kết là gì? | ☐ Nhân viên kho lấy nhầm/thiếu hàng<br>☐ Đối tác vận chuyển đến lấy hàng muộn<br>☐ Hệ thống kỹ thuật bị lỗi/mất kết nối<br>☐ Đơn hàng phát sinh quá lớn trong ngày<br>☐ Thiếu nhân sự trong ca làm việc | Trưởng bộ phận kho |
| C1.5 | Anh/chị đánh giá mức độ hài lòng về quy trình đóng gói hiện tại (đảm bảo hàng không bị hư hỏng khi giao tới khách)? *(Thang đo 1–5: 1 = Rất không hài lòng, 5 = Rất hài lòng)* | ☐ 1 &emsp; ☐ 2 &emsp; ☐ 3 &emsp; ☐ 4 &emsp; ☐ 5 | Khách hàng |

#### 3.6.1.2. Câu hỏi không có cấu trúc (05 câu)
*Dạng câu hỏi mở để tìm điểm nghẽn, lý do phát sinh lỗi và đề xuất cải tiến*

| STT | Nội dung câu hỏi mở | Đối tượng phỏng vấn |
| :---: | :--- | :--- |
| C1.6 | Trong ca làm việc của mình, anh/chị thường gặp phải những khó khăn hoặc vướng mắc nào lặp đi lặp lại nhiều nhất khi thực hiện lấy hàng tại kệ? Nguyên nhân theo anh/chị là do đâu? | Nhân viên vận hành |
| C1.7 | Khi xảy ra sự cố (hệ thống lỗi, đối tác vận chuyển đến trễ, thiếu vật tư đóng gói), quy trình xử lý tình huống ngoại lệ hiện tại có đủ rõ ràng và nhanh chóng để anh/chị tự xử lý không? Anh/chị thường phải làm gì? | Điều phối viên |
| C1.8 | Theo anh/chị, bước nào trong quy trình đang gây lãng phí thời gian và công sức nhiều nhất nhưng lại ít mang lại giá trị cho khách hàng? Vì sao? | Trưởng bộ phận kho |
| C1.9 | Khi nhận hàng từ kho FAHASA, anh/chị có nhận thấy những bất cập nào trong khâu bàn giao (chênh lệch số lượng, hàng không khớp bảng kê, thời gian chờ đợi lâu,...) không? Xin mô tả cụ thể. | Tài xế |
| C1.10 | Nếu được quyền thay đổi một điều trong quy trình nhận hàng, theo dõi đơn hoặc giải quyết khiếu nại giao hàng hiện tại của FAHASA, anh/chị muốn thay đổi điều gì nhất? Tại sao? | Khách hàng |

---

### 3.6.2. Câu hỏi định lượng (10 câu)

#### 3.6.2.1. Câu hỏi có cấu trúc (05 câu)
*Dạng trắc nghiệm với các khoảng thời gian, số lượng hoặc tỷ lệ % định sẵn*

| STT | Nội dung câu hỏi | Lựa chọn trả lời | Đối tượng phỏng vấn |
| :---: | :--- | :--- | :--- |
| C2.1 | Thông thường, thời gian từ khi một đơn hàng được xác nhận trên hệ thống đến khi nhân viên hoàn tất lấy hàng và chuyển qua khu đóng gói mất bao lâu? | ☐ Dưới 5 phút<br>☐ Từ 5 – 10 phút<br>☐ Từ 10 – 20 phút<br>☐ Từ 20 – 30 phút<br>☐ Trên 30 phút | Nhân viên vận hành |
| C2.2 | Trong một ca làm việc 8 tiếng, một nhân viên đóng gói tại FAHASA có thể hoàn tất bao nhiêu đơn hàng? | ☐ Dưới 50 đơn<br>☐ Từ 50 – 100 đơn<br>☐ Từ 100 – 150 đơn<br>☐ Từ 150 – 200 đơn<br>☐ Trên 200 đơn | Trưởng bộ phận kho |
| C2.3 | Tỷ lệ đơn hàng bị đối tác vận chuyển chuyển hoàn (giao không thành công) trong tháng gần nhất chiếm khoảng bao nhiêu? | ☐ Dưới 2%<br>☐ Từ 2% – 5%<br>☐ Từ 5% – 10%<br>☐ Từ 10% – 15%<br>☐ Trên 15% | Điều phối viên |
| C2.4 | Trung bình mỗi ngày, đối tác vận chuyển đến kho FAHASA lấy hàng mấy lần? | ☐ 1 lần/ngày<br>☐ 2 lần/ngày<br>☐ 3 lần/ngày<br>☐ 4 lần/ngày<br>☐ Hơn 4 lần/ngày | Điều phối viên |
| C2.5 | Sau khi đặt hàng thành công trên website/ứng dụng FAHASA, anh/chị thường nhận được hàng trong vòng bao lâu? | ☐ Trong ngày<br>☐ Ngày hôm sau<br>☐ Từ 2 – 3 ngày<br>☐ Từ 3 – 5 ngày<br>☐ Trên 5 ngày | Khách hàng |

#### 3.6.2.2. Câu hỏi không có cấu trúc (05 câu)
*Yêu cầu cung cấp trực tiếp số liệu thống kê cụ thể*

| STT | Nội dung câu hỏi yêu cầu số liệu | Đối tượng phỏng vấn |
| :---: | :--- | :--- |
| C2.6 | Anh/chị cho biết cụ thể: Trong tuần vừa qua, có bao nhiêu đơn hàng bị lấy nhầm sách hoặc thiếu số lượng tại khâu lấy hàng? Chi phí xử lý trung bình cho mỗi trường hợp sai lệch đó là bao nhiêu (bao gồm chi phí lấy lại hàng, in lại tem, đền bù khách)? | Trưởng bộ phận kho |
| C2.7 | Anh/chị cho biết cụ thể: Thời gian chờ đợi trung bình (tính bằng phút) từ khi hàng đã đóng gói xong đến khi tài xế đến lấy và xuất kho trong mỗi ca làm việc là bao nhiêu? Con số này có tăng vào các ngày cuối tuần không? | Điều phối viên |
| C2.8 | Anh/chị cho biết cụ thể: Trong tháng vừa qua, tổng chi phí phát sinh do đơn hàng bị hư hỏng trong quá trình vận chuyển (bao gồm chi phí bồi thường, đổi hàng mới, cước phí vận chuyển lần hai) là bao nhiêu? Số lượng đơn bị hư hỏng là bao nhiêu? | Trưởng bộ phận kho |
| C2.9 | Anh/chị cho biết cụ thể: Trong một tuần làm việc, anh/chị phải mang bao nhiêu chuyến hàng chuyển hoàn quay lại kho FAHASA? Lý do phổ biến nhất của việc giao thất bại là gì và thời gian chờ đợi tại địa chỉ giao trước khi quyết định chuyển hoàn trung bình là bao lâu? | Tài xế |
| C2.10 | Anh/chị cho biết cụ thể: Trong 3 lần đặt hàng gần nhất trên FAHASA, thời gian giao hàng thực tế so với ngày giao dự kiến chênh lệch bao nhiêu ngày? Anh/chị đã phải liên hệ bộ phận hỗ trợ bao nhiêu lần để hỏi về trạng thái đơn hàng? | Khách hàng |
