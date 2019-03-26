# Bài 5: Hướng dẫn ước lượng tải của Web bằng Gatling
---
## Tổng quan

Gatling là công cụ phục vụ cho công việc kiểm thử hiệu năng của hệ thống. Vậy làm sao để có thể đánh giá hiệu năng của Web bằng Gatling? Sau đây mình sẽ hướng dẫn các bạn sử dụng Gatling, tìm ra ngưỡng tải của một trang web.

## Chuẩn bị

Mình sẽ sử dụng Gatling để kiểm thử hiệu năng trang Web Wordpress đơn giản với template tiểu chuẩn của Wordpress. Trang wordpress của mình được deploy trên Cloud VPS có cấu hình 3 core, 2 GB Ram, 2 GB Swap, 50 GB ổ đĩa, chạy hệ điều hành CentOS 7. Mình sẽ sử dụng lại kịch bản có được từ bài 2 - "Hướng dẫn sử dụng Gatling Recorder".

Đồng thời mình có cái đặt thêm script giám sát nhỏ. Các bạn tham khảo tại [đây](https://github.com/lacoski/monitor-web)

## Bắt đầu

Để đánh giá được ngưỡng của trang Web, mình sử dụng dụng 3 loại test là Load test, Stress test, Spike test

### Load test

Để thực hiện bài load test đơn giản, mình sẽ lần lượt thử inject user theo kịch bản "có n user truy cập đồng thời" và tăng dần n từ 20 tới 60 user đồng thời.

Tại lần thử thực hiện 60 user truy cập đồng thời, mình nhận thấy trang web đã tới ngưỡng. Đế đánh giá được trang web đã tới ngưỡng mình theo dõi file log và kết quả report có được

Phân tích log

pic1

Tại thời điểm đỉnh, tài nguyên CPU đã sử dụng tới 100%, Ram sử dụng 1.6G trên tổng 1.8G, Swap sử dụng 2.0G trên 2.0G. Load trung bình của Web trong 1 phút là 20. Tổng số kết nối tới là 824.

Phân tích report

pic2

Đánh giá bài test 60 user truy cập đồng thời:
- Tổng thực hiện 2640 request
- Tất cả request đều thành công
- Trung bình thực hiện 18.592 request trên 1 giây
- Phản hồi nhanh nhất 3 ms
- Phản hồi chậm nhất 21373 ms tức hơn 21s (Phản hồi rất chậm)

pic3

Tại thời điểm 23:19:57, biểu đồ phân phối phản hồi theo thời gian:
- Phản hồi chậm nhất là 21373 ms tức hơn 21s
- Có 60 user truy cập cùng thời điểm

Nhận xét:
- Nếu đối sánh với file log có được, thời điểm 23 giờ 19 phút 57 giây tài nguyên của Cloud VPS đã sử dụng hết, nên xảy ra hiện tượng tác nghẽn hoặc bị treo tạm thời vì vậy phản hồi lại sẽ rất chậm

Tới bài load test thứ 2, mình sẽ lần lượt inject user theo kịch bản "có n user truy cập trong vòng 300 giây" và tăng dần n từ 100 - 150 user.








