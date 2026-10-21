# BÀI TẬP TỔNG HỢP: INTEGRATED SPRINT PLANNING & TRACKING PACK — CAMPUSFOOD

## 1. Giả định và nguyên tắc lập kế hoạch

Để xây dựng kế hoạch khả thi trong một Sprint 10 ngày, nhóm sử dụng các giả định sau:

- Sprint kéo dài 10 ngày làm việc.
- 1 Story Point (SP) phản ánh độ phức tạp, khối lượng tương đối, rủi ro và mức độ bất định; không quy đổi SP thành giờ làm việc.
- Developers gồm Lan, Minh, Ngọc và Phúc; cả nhóm cùng chịu trách nhiệm tạo Increment đạt Definition of Done (DoD).
- Luồng dùng thử tối thiểu gồm xem thực đơn còn món → tạo đơn và mã xác nhận → thanh toán QR an toàn → có trạng thái để nhận/giao đơn.
- Vì chưa có quy tắc điểm nhận ngoài trường và SLA cổng QR, nhóm không tự giả định các quy tắc nghiệp vụ còn thiếu là đã được xác nhận.
- PO quyết định thứ tự Product Backlog, nhưng không tự quyết định Story Point. Developers thống nhất ước lượng qua Planning Poker sau khi làm rõ yêu cầu.

# Phần 5.1 — Chuẩn hóa ước lượng

## 2. Đánh giá các PBI theo Planning Poker

Planning Poker dùng các mức Fibonacci tương đối: 1, 2, 3, 5, 8, 13. Khi phiếu cao và thấp chênh lệch lớn, nhóm cần thảo luận nguyên nhân rồi bỏ phiếu lại, không lấy trung bình cộng để ép ra kết quả.

| PBI                           | Phiếu hiện tại  | Đánh giá                         | Căn cứ và hành động                                                                                                                                                                                                             |
| ----------------------------- | --------------- | -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| CF03 — Chọn điểm nhận         | 3 / 5 / 5 / 8   | Cần refine trước khi chốt        | Chênh lệch giữa 3 và 8 có thể do cách hiểu khác nhau về điểm nhận trong/ngoài trường, xác thực địa điểm và xử lý địa chỉ không hợp lệ. Thiếu quy tắc ngoài trường nên cần làm rõ Acceptance Criteria trước khi ước lượng lại.   |
| CF04 — Nhận đơn/cập nhật giao | 5 / 8 / 8 / 13  | Cần thảo luận lại và có thể tách | Phiếu 5 và 13 cho thấy khác biệt về phạm vi. Cần làm rõ trạng thái đơn, ai được cập nhật, luồng nhận tại căn tin hay giao hàng, và phụ thuộc CF02, CF03. Có thể tách luồng nhận đơn và cập nhật trạng thái giao nếu đủ độc lập. |
| CF06 — Thanh toán QR          | 5 / 8 / 13 / 13 | Chưa nên chốt                    | Hai phiếu 13 phản ánh rủi ro tích hợp hoặc SLA chưa rõ; phiếu 5 có thể đang giả định cổng QR ổn định và đã có tích hợp sẵn. Cần xác nhận SLA, timeout, trạng thái giao dịch, xử lý callback trùng và cách đối soát.             |
| CF08 — Hoàn tiền khi quán hủy | 13 tạm chốt     | Thiếu dữ liệu để chốt chính thức | “13 tạm chốt” không phải ước lượng đáng tin cậy khi Acceptance Criteria còn thiếu. Cần xác định điều kiện hoàn tiền, thời điểm hoàn, lỗi hoàn tiền, trạng thái đơn và trách nhiệm đối soát trước khi bỏ phiếu lại.              |

### Kết luận về ước lượng

- CF03, CF04 và CF06 cần thảo luận lại, làm rõ bất đồng và bỏ phiếu lại.
- CF08 cần bổ sung Acceptance Criteria trước khi ước lượng chính thức.
- Không lấy trung bình phiếu để biến CF03 thành 5, CF04 thành 8 hay CF06 thành 8.
- PBI chưa đủ rõ có thể tiếp tục được làm rõ trong Product Backlog Refinement, nhưng không nên cam kết đưa vào Sprint khi chưa sẵn sàng.

### Hạng mục có thể dùng làm mốc tham chiếu

CF01 — Xem thực đơn/còn món có 3 SP đã chốt, phù hợp với mốc tham chiếu “xem thực đơn hôm nay = 3 SP”. Đây là mốc so sánh độ lớn tương đối cho nhóm khi ước lượng các PBI khác.

# Phần 5.2 — Sprint Goal và phạm vi Sprint

## 3. Sprint Goal

Sprint Goal: “Xây dựng luồng đặt món tối thiểu cho CampusFood, cho phép sinh viên xem món còn bán, tạo đơn hàng có mã xác nhận và tiến tới thanh toán QR trong môi trường thử nghiệm, với trạng thái đơn được kiểm tra rõ ràng.”

Mục tiêu này hướng đến giá trị dùng thử thực tế, không phải hoàn thành càng nhiều PBI càng tốt.

## 4. Quyết định phạm vi

Velocity ba Sprint gần nhất là 18, 21 và 15 SP, nhưng dữ liệu hiện tại cho thấy một số PBI quan trọng chưa sẵn sàng. Do đó, nhóm không nên chỉ cộng các SP để chọn phạm vi.

| PBI                           | SP hiện tại | Quyết định   | Lý do                                                                                     |
| ----------------------------- | ----------- | ------------ | ----------------------------------------------------------------------------------------- |
| CF01 — Xem thực đơn/còn món   | 3           | Chọn         | Đã sẵn sàng, ước lượng rõ, là điểm bắt đầu của luồng.                                     |
| CF02 — Tạo đơn/mã xác nhận    | 5           | Chọn         | Đã chốt SP và phụ thuộc trực tiếp CF01.                                                   |
| CF03 — Chọn điểm nhận         | Chưa chốt   | Chưa cam kết | Thiếu quy tắc ngoài trường và còn bất đồng ước lượng.                                     |
| CF04 — Nhận đơn/cập nhật giao | Chưa chốt   | Chưa cam kết | Phụ thuộc CF02 và CF03; phạm vi còn bất định.                                             |
| CF05 — Xem trạng thái giao    | 5           | Chưa chọn    | Phụ thuộc CF04 chưa sẵn sàng.                                                             |
| CF06 — Thanh toán QR          | Chưa chốt   | Chưa cam kết | Chưa rõ SLA và cách xử lý lỗi cổng QR. Đây là rủi ro lớn nhất đối với luồng dùng thử.     |
| CF07 — Biên nhận điện tử      | 3           | Chưa chọn    | Phụ thuộc CF06.                                                                           |
| CF08 — Hoàn tiền khi quán hủy | Chưa chốt   | Chưa chọn    | Thiếu Acceptance Criteria, 13 SP mới là tạm chốt.                                         |
| CF09 — Đánh giá người giao    | 3           | Không chọn   | Không trực tiếp cần thiết cho luồng đặt và thanh toán ban đầu; còn thiếu quy tắc sửa/xóa. |

Điểm cần minh bạch: CF01 + CF02 mới có 8 SP và chưa tạo được luồng đặt–thanh toán–nhận/giao hoàn chỉnh. Vì CF06 chưa sẵn sàng, nhóm cần làm rõ SLA và các trường hợp lỗi QR trước khi cam kết Sprint Goal dùng thử đầu-cuối.

Để giữ mục tiêu kinh doanh, trước khi chốt Sprint Planning, PO cần phối hợp với Developers làm rõ CF06 và CF03. Nếu hai PBI vẫn chưa đủ rõ, không được giả vờ rằng toàn bộ luồng đã sẵn sàng; phải thống nhất lại Sprint Goal khả thi hoặc công khai rủi ro chưa đạt được luồng dùng thử đầu-cuối. Không nên đưa CF04–CF07 vào chỉ để tăng tổng SP.

# Phần 5.3 — Task Breakdown và Capacity

## 5. Tính Capacity từng thành viên

Capacity được tính bằng thời gian làm việc dự kiến trừ thời gian gián đoạn đã biết. Đây là giờ làm việc khả dụng, không phải cách quy đổi Story Point sang giờ.

| Thành viên      | Thời gian dự kiến | Gián đoạn         | Capacity còn lại |
| --------------- | ----------------- | ----------------- | ---------------- |
| Lan — Frontend  | 10 × 6 = 60 giờ   | 6 giờ hỗ trợ      | 54 giờ           |
| Minh — Backend  | 8 × 6 = 48 giờ    | 0 giờ đã nêu      | 48 giờ           |
| Ngọc — QA/BA    | 10 × 5 = 50 giờ   | 5 giờ họp         | 45 giờ           |
| Phúc — Tích hợp | 9 × 6 = 54 giờ    | 8 giờ tích hợp cũ | 46 giờ           |
| Tổng đội        | 212 giờ           | 19 giờ            | 193 giờ          |

Giả định: số ngày của mỗi người đã phản ánh lịch làm việc dự kiến trong Sprint; thời gian gián đoạn được trừ thêm một lần.

### Nếu Minh nghỉ thêm 2 ngày

Minh hiện có 8 ngày làm việc, tương ứng 48 giờ. Nếu nghỉ thêm 2 ngày làm việc, thời gian của Minh còn 6 × 6 = 36 giờ.

| Chỉ số            | Ban đầu | Sau khi Minh nghỉ thêm |
| ----------------- | ------- | ---------------------- |
| Capacity Minh     | 48 giờ  | 36 giờ                 |
| Capacity toàn đội | 193 giờ | 181 giờ                |
| Mức giảm          | —       | 12 giờ                 |

Tác động: giảm năng lực Backend, có thể làm chậm API tạo đơn, xử lý trạng thái đơn và tích hợp thanh toán. Nhóm phải đánh giá lại phụ thuộc và phân công, không mặc định rằng thành viên khác có thể thay thế ngay toàn bộ công việc của Minh.

## 6. Task Breakdown cho các PBI được chọn

Bảng dưới đây phân rã CF01 và CF02; các task là hoạt động triển khai, không phải PBI mới. Đầu ra của từng task phải được kiểm tra theo Acceptance Criteria và DoD.

| PBI / Người phụ trách chính | Task có động từ                                                            | Đầu ra mong đợi                                             | Phụ thuộc / phối hợp                    |
| --------------------------- | -------------------------------------------------------------------------- | ----------------------------------------------------------- | --------------------------------------- |
| CF01 — Lan                  | Thiết kế giao diện thực đơn hôm nay và trạng thái còn/hết món              | Màn hình thực đơn hiển thị rõ trạng thái món                | Phối hợp Ngọc để thống nhất AC hiển thị |
| CF01 — Minh                 | Xây dựng API lấy danh sách món và trạng thái còn món                       | API trả dữ liệu thực đơn theo hợp đồng thống nhất           | Phối hợp Lan về cấu trúc dữ liệu        |
| CF01 — Ngọc                 | Viết và thực hiện kiểm thử thực đơn, món hết hàng và dữ liệu rỗng          | Kết quả kiểm thử, lỗi được ghi nhận                         | Cần API và giao diện tích hợp           |
| CF01 — Phúc                 | Tích hợp giao diện với API thực đơn                                        | Luồng xem thực đơn chạy trong môi trường thử                | Phụ thuộc API và giao diện              |
| CF02 — Ngọc                 | Làm rõ quy tắc tạo đơn, mã xác nhận và các trường hợp dữ liệu không hợp lệ | AC được thống nhất và có thể kiểm thử                       | Phối hợp PO, Minh và Lan                |
| CF02 — Minh                 | Xây dựng API tạo đơn và sinh mã xác nhận duy nhất                          | Đơn được lưu và trả mã xác nhận                             | Phụ thuộc dữ liệu món từ CF01           |
| CF02 — Lan                  | Xây dựng màn hình xác nhận đơn và hiển thị mã                              | Khách hàng thấy kết quả tạo đơn rõ ràng                     | Phụ thuộc hợp đồng API CF02             |
| CF02 — Phúc                 | Tích hợp giao diện, API và kiểm tra luồng tạo đơn                          | Luồng từ xem món đến tạo đơn hoạt động trong môi trường thử | Phụ thuộc các phần việc CF01, CF02      |
| CF02 — Ngọc                 | Kiểm thử tạo đơn, gửi yêu cầu lặp và lỗi phản hồi                          | Báo cáo kiểm thử và lỗi được ghi nhận                       | Cần bản tích hợp để kiểm thử            |

Đội có thể điều chỉnh người thực hiện khi cần; không nên để một thành viên chịu trách nhiệm toàn bộ từ phát triển đến kiểm thử mà không có review chéo.

### Các task khám phá rủi ro QR

Trước khi cam kết CF06, nhóm cần bổ sung task để:

- Xác nhận SLA, timeout và cơ chế callback của cổng QR với nhà cung cấp.
- Làm rõ cách xử lý giao dịch đang chờ, thất bại và thông báo thành công đến trễ.
- Kiểm tra khả năng tích hợp sandbox và xác định AC cho các trường hợp lỗi.

Các task khám phá này giúp giảm bất định; chúng không tự động có nghĩa CF06 đã hoàn thành hoặc đủ điều kiện Done.

# Phần 5.4 — Velocity và quyết định phạm vi

## 7. Tính Velocity và xu hướng

Velocity là tổng Story Point của các PBI thực sự hoàn thành theo DoD trong một Sprint.

| Sprint              | Velocity |
| ------------------- | -------- |
| Sprint 3            | 18 SP    |
| Sprint 4            | 21 SP    |
| Sprint 5            | 15 SP    |
| Trung bình 3 Sprint | 18 SP    |

\\[ \text{Velocity trung bình}=\frac{18+21+15}{3}=18\text{ SP} \\]

Xu hướng: Velocity tăng từ 18 lên 21 SP rồi giảm xuống 15 SP. Sprint 5 thấp hơn Sprint 4 là 6 SP, tương đương khoảng 28,6%.

PBI 8 SP mới hoàn thành 75% không được tính vào Velocity. Nhóm chỉ tính SP của PBI đã hoàn thành toàn bộ theo DoD; không tính 75% của 8 SP thành 6 SP.

## 8. So sánh hai cách lập kế hoạch

- Phương án A — Chủ yếu dựa vào Velocity: Chọn các PBI có tổng khoảng 18 SP vì Velocity trung bình ba Sprint là 18 SP.
- Phương án B — Dựa vào Capacity, độ sẵn sàng và rủi ro: Chọn PBI theo phụ thuộc, AC đã rõ, khả năng tích hợp và nguồn lực thực tế; dùng Velocity như dữ liệu tham khảo, không phải chỉ tiêu bắt buộc.

| Tiêu chí                           | Phương án A — Chủ yếu Velocity                                     | Phương án B — Capacity, sẵn sàng và rủi ro            |
| ---------------------------------- | ------------------------------------------------------------------ | ----------------------------------------------------- |
| Độ tin cậy                         | Dễ dự báo sơ bộ nhưng không bảo đảm Sprint này đạt 18 SP           | Thực tế hơn vì xét điều kiện hiện tại của từng PBI    |
| Nghỉ phép và gián đoạn             | Có thể bỏ qua việc Minh nghỉ thêm hoặc Phúc còn việc tích hợp cũ   | Trừ Capacity và điều chỉnh phạm vi khi có thay đổi    |
| Bảo vệ Sprint Goal                 | Dễ chọn đủ SP nhưng luồng nghiệp vụ có thể chưa chạy được          | Ưu tiên luồng giá trị và các phụ thuộc bắt buộc       |
| Áp lực và hành vi chạy theo chỉ số | Dễ phát sinh việc chọn PBI nhỏ, dễ hoàn thành chỉ để tăng Velocity | Khuyến khích ước lượng trung thực và công khai rủi ro |
| Độ sẵn sàng                        | Có thể đưa CF03, CF06 vào dù thiếu dữ liệu                         | Yêu cầu làm rõ AC và phụ thuộc trước khi cam kết      |

Lựa chọn: Phương án B. Velocity trung bình 18 SP chỉ là dữ liệu lịch sử. Capacity 193 giờ (hoặc 181 giờ nếu Minh nghỉ thêm), tình trạng sẵn sàng của CF03/CF06 và mục tiêu luồng dùng thử mới là căn cứ để quyết định phạm vi.

Không nên suy luận rằng Capacity 193 giờ tương đương một số SP cụ thể. Đội dùng Capacity để kiểm tra khả năng thực hiện công việc, còn SP để ước lượng độ lớn tương đối của PBI.

# Phần 5.5 — Burndown và thích nghi

## 9. Đọc dữ liệu Burndown

Dữ liệu đề bài là số SP còn lại vào cuối mỗi ngày:

| Ngày | SP còn lại thực tế |
| ---- | ------------------ |
| 0    | 21                 |
| 1    | 21                 |
| 2    | 18                 |
| 3    | 18                 |
| 4    | 23                 |
| 5    | 18                 |
| 6    | 18                 |
| 7    | 13                 |
| 8    | 8                  |
| 9    | 5                  |
| 10   | 5                  |

Đường lý tưởng dưới đây giả định phạm vi ban đầu là 21 SP và giảm đều về 0 vào cuối ngày 10. Đây là đường tham chiếu, không phải yêu cầu công việc phải giảm tuyến tính từng ngày.

CampusFood — Burndown Sprint 10 ngày

So sánh SP còn lại theo đường lý tưởng và dữ liệu thực tế. Phạm vi ban đầu giả định 21 SP.

Lý tưởngThực tế

0 SP6,25 SP12,5 SP18,75 SP25 SP012345678910

### Ít nhất 3 tín hiệu cần điều tra

| Tín hiệu                    | Giả thuyết ban đầu                                                                        | Dữ liệu cần kiểm tra                                                                     | Hành động                                                                                                                         |
| --------------------------- | ----------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Ngày 1 còn 21 SP, chưa giảm | Chưa có PBI nào hoàn thành hoặc task đang bị chặn                                         | Trạng thái task, lỗi build, phụ thuộc, kết quả kiểm thử                                  | Daily Scrum tập trung vào trở ngại và kế hoạch xử lý, không gây áp lực giảm SP bằng mọi giá                                       |
| Ngày 3 vẫn còn 18 SP        | Công việc tích hợp hoặc kiểm thử chưa xong; một số PBI lớn chưa đạt DoD                   | Danh sách PBI đang làm, thời gian chờ review, lỗi tồn đọng                               | Kiểm tra task bị chặn và hỗ trợ hoàn tất PBI đang gần Done                                                                        |
| Ngày 4 tăng từ 18 lên 23 SP | Phạm vi có thể đã tăng do yêu cầu mã khuyến mãi 5 SP                                      | Lịch sử thay đổi Sprint Backlog, thời điểm thêm yêu cầu, quyết định của PO và Developers | Ghi nhận thay đổi phạm vi công khai; đánh giá tác động tới Sprint Goal                                                            |
| Ngày 5 cổng QR chậm         | Tích hợp bên ngoài bị chặn hoặc giao dịch chờ phản hồi                                    | Log request/response, timeout, trạng thái sandbox, SLA nhà cung cấp                      | Phối hợp nhà cung cấp, thử cơ chế timeout và xác định phạm vi an toàn có thể tiếp tục                                             |
| Ngày 6 không giảm           | Có thể cuộc họp đã phát hiện vấn đề nhưng không có quyết định hoặc người chịu trách nhiệm | Biên bản họp, danh sách hành động, người phụ trách và hạn xử lý                          | Ghi lại quyết định, người thực hiện, thời hạn; rà soát ở Daily Scrum tiếp theo                                                    |
| Ngày 10 còn 5 SP            | Có công việc chưa đạt DoD khi Sprint kết thúc                                             | PBI chưa hoàn thành, test result, lỗi nghiêm trọng, trạng thái triển khai                | Không tính 5 SP chưa hoàn thành vào Velocity; công khai trong Sprint Review và đưa phần còn lại về Product Backlog để sắp xếp lại |

### Nguyên tắc sử dụng Burndown

- Không sửa dữ liệu ngày trước để đường biểu đồ trông đẹp hơn.
- Nếu phạm vi thay đổi, ghi nhận thay đổi tại thời điểm nó xảy ra và giữ lại lịch sử.
- Burndown cho thấy xu hướng công việc còn lại, nhưng không tự giải thích nguyên nhân; nhóm phải đối chiếu với trạng thái PBI, task, lỗi và các sự kiện trong Sprint.
- Không đồng nhất “đã code xong” với “đã hoàn thành”; chỉ giảm SP khi PBI đáp ứng DoD.

## 10. Cách thích nghi trong Sprint

1. Daily Scrum: Developers kiểm tra tiến độ hướng tới Sprint Goal, xác định trở ngại và điều chỉnh kế hoạch trong ngày.
2. Khi QR chậm: Ưu tiên điều tra tích hợp, công khai phụ thuộc và đánh giá phương án thử nghiệm an toàn; không bỏ qua kiểm thử để giữ tiến độ.
3. Khi có yêu cầu mới: PO làm rõ giá trị và thứ tự Product Backlog. Developers trao đổi với PO về tác động tới Sprint Goal và có thể thương lượng lại phạm vi Sprint Backlog.
4. Cuối Sprint: Review phần Increment thực sự Done; Retro tìm nguyên nhân gốc và thống nhất cải tiến cho Sprint sau.

# Phần 5.6 — Ngoại lệ và thay đổi

## 11. Xử lý bốn tình huống

| Tình huống                                        | Cách xử lý                                                                                                                                                                                                                                                                              | Tác động đến Sprint Goal, DoD, Velocity và Burndown                                                                                                                                                            |
| ------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1. QR lỗi sau khi đã tạo đơn                      | Giữ lại mã đơn và trạng thái thanh toán rõ ràng như “Chờ thanh toán” hoặc “Thanh toán thất bại”. Cho phép thử lại theo quy tắc đã xác nhận; kiểm tra callback lặp để tránh thu tiền hoặc ghi nhận thanh toán hai lần. Không đánh dấu đơn đã thanh toán nếu chưa có xác nhận hợp lệ.     | Có thể làm chậm luồng dùng thử đầu-cuối. DoD yêu cầu kiểm thử chính và lỗi, không còn lỗi nghiêm trọng. PBI chưa đạt DoD không được tính Velocity. Burndown giữ SP cho đến khi PBI Done; ghi nhận trở ngại QR. |
| 2. Thiếu SĐT hoặc chọn điểm nhận ngoài trường     | Không tự đoán quy tắc nghiệp vụ. Yêu cầu PO xác nhận trường dữ liệu bắt buộc, phạm vi giao hàng, cách xác thực và thông báo lỗi. Trong lúc chờ, ghi nhận PBI bị chặn và không cam kết phần phụ thuộc nếu chưa đủ rõ.                                                                    | Có thể khiến CF03/CF04 chưa đủ điều kiện đưa vào Sprint. DoD không thay thế AC còn thiếu. PBI chưa hoàn thành không tính Velocity; Burndown phản ánh công việc còn lại và nhóm công khai nguyên nhân bị chặn.  |
| 3. PO yêu cầu thêm mã khuyến mãi 5 SP vào ngày 4  | Làm rõ giá trị và mức khẩn cấp. Developers cùng PO đánh giá tác động tới Sprint Goal, phụ thuộc và công việc còn lại. Không tự động thêm chỉ vì PO yêu cầu; chỉ điều chỉnh phạm vi khi có trao đổi và vẫn bảo vệ Sprint Goal. Nếu cần, đưa vào Product Backlog để ưu tiên ở Sprint sau. | Phạm vi tăng có thể khiến Burndown tăng từ 18 lên 23 SP, cần ghi nhận đúng thời điểm. Nếu PBI chưa Done cuối Sprint thì không tính Velocity. Không hy sinh kiểm thử hay bỏ DoD để hoàn thành khuyến mãi.       |
| 4. PBI mới hoàn thành 80% nhưng chưa qua kiểm thử | Ghi nhận trạng thái chưa hoàn thành. Tiếp tục kiểm thử, sửa lỗi, review và triển khai môi trường thử theo DoD; nếu không kịp, đưa phần việc chưa hoàn thành về Product Backlog để PO sắp xếp lại.                                                                                       | PBI chưa đạt DoD không được tính Velocity, dù đã hoàn thành 80% công việc. Burndown vẫn thể hiện SP còn lại. Trong Sprint Review, minh bạch phần chưa Done và không trình bày nó như Increment hoàn chỉnh.     |

## 12. Cách công khai quyết định và kết quả

Để tránh việc thay đổi phạm vi hoặc lỗi tích hợp bị che giấu, nhóm áp dụng cơ chế sau:

- Product Backlog: PO cập nhật yêu cầu, mức ưu tiên, AC và phụ thuộc; lưu lại lịch sử thay đổi.
- Sprint Backlog: Developers cập nhật task, người phụ trách, trạng thái, trở ngại và kế hoạch xử lý.
- Daily Scrum: Công khai các vấn đề ảnh hưởng đến Sprint Goal, đặc biệt là QR chậm, thiếu quy tắc nghiệp vụ và việc tăng phạm vi.
- Burndown: Giữ nguyên dữ liệu lịch sử; nếu phạm vi tăng hoặc giảm, ghi nhận thay đổi và giải thích nguyên nhân.
- Sprint Review: Trình diễn các phần Increment thực sự Done, thông báo phần chưa hoàn thành, nêu rõ ảnh hưởng đến luồng đặt–thanh toán–nhận/giao.
- Sprint Retrospective: Xác định nguyên nhân và chọn hành động cải tiến cụ thể, chẳng hạn yêu cầu SLA tích hợp bên ngoài phải được làm rõ trước Sprint Planning.

## 13. Kết luận và quyết định cuối cùng

Kế hoạch CampusFood nên lấy giá trị của luồng dùng thử và chất lượng Increment làm trọng tâm, không lấy tổng SP làm mục tiêu độc lập.

1. Velocity trung bình ba Sprint là 18 SP, nhưng chỉ dùng để tham khảo.
2. Capacity ban đầu là 193 giờ; nếu Minh nghỉ thêm hai ngày làm việc, Capacity giảm còn 181 giờ.
3. CF01 và CF02 đã đủ rõ để đưa vào phạm vi dự kiến, nhưng riêng hai PBI này chưa tạo ra luồng đặt–thanh toán–nhận/giao hoàn chỉnh.
4. CF03 và CF06 cần được làm rõ trước khi cam kết phạm vi dùng thử đầu-cuối; CF04 và CF05 phụ thuộc vào các PBI trước đó.
5. Mọi PBI chưa đạt DoD đều không được tính vào Velocity, kể cả khi đã hoàn thành 75% hoặc 80%.
6. Khi yêu cầu thay đổi hoặc cổng QR gặp sự cố, nhóm cần ghi nhận tác động, điều chỉnh kế hoạch minh bạch và bảo vệ Sprint Goal thay vì âm thầm tăng phạm vi hoặc bỏ qua kiểm thử.

Quyết định quan trọng nhất: Trước khi chốt Sprint Planning, PO và Developers phải làm rõ cách xử lý lỗi QR cùng quy tắc điểm nhận. Nếu không giải quyết được các phụ thuộc này, nhóm phải công khai rằng mục tiêu dùng thử đầu-cuối đang có rủi ro và thống nhất lại phạm vi hoặc Sprint Goal một cách minh bạch.