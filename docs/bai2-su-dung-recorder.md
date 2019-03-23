# Bài xx: Hướng dẫn sử dụng Gatling Recoder (Đơn giản)
---
## Tổng quan

Gatling Recorder hỗ trợ người dùng sinh ra kịch bản test nhanh chóng bằng cách thu thập các request HTTP diễn ra giữa trình duyệt và trang web muốn kiếm thử mong muốn.

## Chuẩn bị

### Mô hình

Sau đây mình sẽ sử dụng công cụ Gatling Recoder để  quay lại thao tác giữa người dùng và một trang wordpress đơn giản

## Cách sử dụng Gatling Recoder

Mình sẽ tạo kịch bản với mục tiêu giải lập thao tác người dùng truy cập vào trang wordpress do mình triển khai.

Kịch bản một user truy cập sẽ là

- Bước 1: Người dùng truy cập trang chủ
- Bước 2: Chuyển sang đọc một bài viết
- Bước 3: Tìm kiếm một bài viết
- Bước 4: Truy cập một bài viết trong danh sách có được từ bước 3
- Bước 5: Người dùng trở về trang chủ

## Bước 1: Khởi động Gatling Recorder

Truy cập thư mục cài đặt gatling, khởi động gatling recorder

```
cd gatling-charts-highcharts-bundle-3.0.3/bin
./recorder.sh 
```

pic 1

Lưu ý:
- (1) - Port sử dụng cho proxy
- (2) - Tên Class hay tên kịch bản sẽ được tạo mới
- (3) - Khi chỉ định xong 2 thông tin trên, chọn `start`

Kết quả

pic 2

## Bước 2: Trỏ Proxy về Proxy server của Gatling Recorder

Trong bài mình sẽ sử dụng Google Chrome

pic 3

- Bước 2.1: Truy cập đường dẫn `chrome://settings/`
- Bước 2.2: Tìm kiếm từ khóa proxy
- Bước 2.2: Truy cập system - chọn Open proxy settings
- Bước 2.3: Mở settings Network Ubuntu

Kết quả

pic 4

- Bước 2.4: Tại giao diện quản trị Network, chọn settings

pic 5

- Bước 2.5: Lựa chọn Manual
- Bước 2.6: Nhập HTTP Proxy bằng localhost port 8000
- Bước 2.7: Chọn đóng popup Network Proxy

Sau khi trỏ thiết proxy Ubuntu về Proxy Server của Gatling Recorder, các thao tác trên trình duyệt sẽ được Gatling thu thập từ đó tạo ra các kịch bản test.

Lưu ý:
- Sau khi quay xong kịch bản test, bạn cần phải disable proxy tại Ubuntu để có thể truy cập Internet bình thường

pic 6

## Bước 3: Quay kịch bản

Sau đây, mình sẽ thực hiện các thao tác sau trên trình duyệt, để tạo ra kịch bản ban đầu.

Bước 1: Người dùng truy cập trang chủ

Kết quả

Bước 2: Chuyển sang đọc một bài viết

pic 8

Kết quả

pic 9

Bước 3: Tìm kiếm một bài viết

pic 10

pic 11

Bước 4: Truy cập một bài viết trong danh sách có được từ bước 3

pic 12

pic 13

Bước 5: Người dùng trở về trang chủ

pic 14

pic 15

## Bước 4: Lưu kịch bản

pic 16

pic 17

Kịch bản sau khi quay xong sẽ nằm trong được dẫn `Simulations folder`

## Kiểm tra

Kiểm tra đường dẫn `Simulations folder` và chúng ta được kết quả như sau

pic 18

## Tổng kết

Đến đây, mình đã hướng dẫn các bạn sử dụng Gatling Recorder, đến bài tiếp theo mình sẽ hướng dẫn các bạn sử dụng Gatling để chạy kịch bản vừa quay, thay đổi cách tạo tải. Cám ơn các bạn đã quan tâm

