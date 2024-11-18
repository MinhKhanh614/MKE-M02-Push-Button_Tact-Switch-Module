# Mạch nút nhấn MKE-M02 push button tact switch module

![](/image/tact1.jpg)

## Giới thiệu

Mạch nút nhấn MKE-M02 push button tact switch module sử dụng nút nhấn kích thước lớn giúp dễ dàng lắp đặt, thao tác, nút nhấn sử dụng trong loại là loại nhấn nhả (tact switch) thường được dùng để kích tín hiệu, nút nhấn có nắp chụp với nhiều màu sắc khác nhau để dễ phân biệt.

Mạch nút nhấn MKE-M02 push button tact switch module thuộc hệ sinh thái phần cứng Robotics MakerEdu nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.

## Thông số kỹ thuật

- Loại nút nhấn: nhấn nhả (tact switch)
- Điện áp hoạt động: 5VDC
- Chuẩn giao tiếp: Digital
- Điện áp giao tiếp: TTL 3.3/5VDC
- Có 4 phiên bản màu sắc: Xanh Lá, Xanh Dương, Vàng, Đỏ.
- Sử dụng trực tiếp an toàn với các board mạch giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
- Bổ sung thêm các thiết kế ổn định, chống nhiễu.
- Chuẩn kết nối: connector XH2.54 3Pins
- Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.

> **Lưu ý:**  
Khi nhấn nút, chân SIG sẽ xuất ra 0V. Khi nhả nút, chân SIG sẽ xuất ra 3V3 !

## Kích thước

![](/image/tact2.jpg)

## Các chân tín hiệu

![](/image/tact3.jpg)

<table><thead>
  <tr>
    <th>MKE-M02</th>
    <th>Ghi chú</th>
  </tr></thead>
<tbody>
  <tr>
    <td>GND</td>
    <td>Chân cấp nguồn âm 0VDC</td>
  </tr>
  <tr>
    <td>5V</td>
    <td>Chân cấp nguồn dương 5VDC</td>
  </tr>
  <tr>
    <td>SIG</td>
    <td>Chân tín hiệu Digital Out</td>
  </tr>
</tbody>
</table>

<table><thead>
  <tr>
    <th>SIG (Digital Out)</th>
    <th>Trạng thái</th>
  </tr></thead>
<tbody>
  <tr>
    <td>TTL HIGH</td>
    <td>Hoạt động (On)</td>
  </tr>
  <tr>
    <td>TTL LOW</td>
    <td>Không hoạt động (Off)</td>
  </tr>
</tbody>
</table>

## Hướng dẫn sử dụng với phần mềm Arduino và Vietduino

### Phần cứng cần chuẩn bị

- Mạch nút nhấn MKE-M02 push button tact switch module
- Mạch Vietduino Uno (Arduino Uno Compatible)
- Mạch MakerEdu Shield for Vietduino
- Cáp USB để nạp chương trình và cấp nguồn

> **Lưu ý:**  
Nếu không có mạch Vietduino Uno bạn vẫn có thể sử dụng mạch Vietduino Mega 2560, Arduino Uno, Arduino Mega 2560 hoặc các mạch phần cứng có cấu trúc các chân GPIO tương tự.

### Phần mềm cần chuẩn bị

- Tải và cài đặt phần mềm Arduino theo hướng dẫn.
- Tải và cài đặt Driver, cấu hình cho mạch Vietduino Uno trên phần mềm Arduino theo hướng dẫn.
- Tải và cài đặt bộ thư viện nút nhấn theo hướng dẫn.

### Chương trình mẫu

```ino
// Thêm bộ thư viện Nút nhấn.
// Add the Button library.

# include <OneButton.h>

// Chọn chân Digital cho Nút nhấn.
// Select the Digital pin for Button.

# define BUTTON_PIN 11

// Khởi tạo "OneButton" cho Nút nhấn với cấu hình sau.
// Initialize "OneButton" for the Button with the following config.
OneButton btn = OneButton(
    BUTTON_PIN, // Cấu hình đây là chân Digital Input.
    true,       // Nút nhấn kích hoạt LOW.
    false       // Kích hoạt điện trở nội "Pull-Up".
);

// Lưu số lần thực hiện 1 Click vào nút.
// Save the number of times make 1 Click on the Button.
int value = 0;

void setup()
{
  // Khởi động kết nối Serial UART ở tốc độ 9600 để truyền dữ liệu lên máy tính.
  // Start the Serial UART connection at 9600 to transfer data to the computer.
  Serial.begin(9600);

  // Liên kết hàm "count" được gọi trên một sự kiện 1 Click.
  // Link the "count" function to be called on a single click event.
  btn.attachClick(count);
}

void loop()
{
  // Tiếp tục theo dõi Nút nhấn.
  // Keep watching the Button.
  btn.tick();
}

void count()
{
  // Ghi lại đây là 1 Click.
  // Record this is 1 Click.
  value++;

  // Truyền giá trị lên máy tính.
  // Transmit the value to the computer.
  Serial.print("Count: ");
  Serial.println(value);
}
```

### Sơ đồ kết nối

<table><thead>
  <tr>
    <th>MakerEdu Shield for Vietduino</th>
    <th>Arduino / Vietduino</th>
    <th>Devices</th>
  </tr></thead>
<tbody>
  <tr>
    <td>Port D11</td>
    <td>D11</td>
    <td>Mạch nút nhấn MKE-M02 push button tact switch module</td>
  </tr>
</tbody>
</table>

### Các bước tiến hành

1. Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
1. Kết nối Mạch Nút Nhấn MKE-M02 với mạch MakerEDU Shied for Vietduino qua Port D11.
1. Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
1. Nạp chương trình mẫu vào mạch Vietduino Uno.
1. Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

Kết quả:
...pic

## Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator

### Phần cứng cần chuẩn bị

- Mạch nút nhấn MKE-M02 push button tact switch module
- Mạch hiển thị MKE-M07 LCD1602 I2C module
- Mạch MakerEdu Creator
- Cáp USB để nạp chương trình và cấp nguồn

### Phần mềm cần chuẩn bị

- Tải và cài đặt phần mềm mBlock theo hướng dẫn.
- Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo hướng dẫn.
- Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo hướng dẫn.

### Chương trình mẫu

- Mỗi khi bạn nhấn "1 Click" trên nút nhấn, mạch MakerEdu Creator sẽ đếm và hiển thị số lần bạn nhấn nút lên màn hình LCD.

#### Blocks

![](/image/tact4.png)

### Sơ đồ kết nối

<table><thead>
  <tr>
    <th>MakerEdu Creator</th>
    <th>Devices</th>
  </tr></thead>
<tbody>
  <tr>
    <td>Port D11</td>
    <td>Mạch Nút Nhấn MKE-M02 Push Button Tact Switch Module</td>
  </tr>
  <tr>
    <td>Port I2C</td>
    <td>Mạch Hiển Thị MKE-M07 LCD1602 I2C Module</td>
  </tr>
</tbody>
</table>

### Các bước tiến hành

- Kết nối Mạch Nút Nhấn MKE-M02 với mạch MakerEdu Creator qua Port D11.
- Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEdu Creator qua Port I2C.
- Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
- Nạp chương trình mẫu vào mạch MakerEdu Creator.
- Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.

Kết quả:
...pic

## Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit

### Phần cứng cần chuẩn bị

- Mạch nút nhấn MKE-M02 push button tact switch module
- Mạch MakerEdu Shield for Micro:bit
- Mạch Micro:Bit
- Cáp USB để nạp chương trình và cấp nguồn

### Phần mềm cần chuẩn bị

1. Khởi động phần mềm MakeCode theo hướng dẫn.
1. Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo hướng dẫn.
1. Tham khảo cách kết nối và nạp chương trình cho Micro:bit trên máy tính hoặc điện thoại, máy tính bảng.

### Chương trình mẫu

1. Trên bo mạch Micro:Bit có sẵn bảng mạch 25 LED để sử dụng.
1. Trong chương trình này, mỗi khi nhấn nút Micro:bit sẽ lấy ngẫu nhiên một số từ 1 đến 6, và cho hiển thị mặt "xúc xắc" tương ứng lên 25 LED kia.

#### Blocks

![](/image/tact5.png)

#### Javascript

```java
// Giá trị của "xúc xắc"
let random = 0

// Khi nhấn nút (P0) sẽ đổ "xúc xắc"
input.onPinPressed(TouchPin.P0, function () {
  basic.showLeds(`
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        `)
  // Lấy một số ngẫu nhiên trong khoảng 1 đến 6
  random = randint(1, 6)

  // Cho hiển thị mặt "xúc xắc" theo số tương ứng
  if (random == 1) {
    basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . .
            `)
  } else if (random == 2) {
    basic.showLeds(`
            . . # . .
            . . . . .
            . . . . .
            . . . . .
            . . # . .
            `)
  } else if (random == 3) {
    basic.showLeds(`
            . . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . .
            `)
  } else if (random == 4) {
    basic.showLeds(`
            # . . . #
            . . . . .
            . . . . .
            . . . . .
            # . . . #
            `)
  } else if (random == 5) {
    basic.showLeds(`
            # . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . #
            `)
  } else if (random == 6) {
    basic.showLeds(`
            # . . . #
            . . . . .
            # . . . #
            . . . . .
            # . . . #
            `)
  }
})
```

### Sơ đồ kết nối

<table><thead>
  <tr>
    <th>MakerEDU Shield for Micro:bit</th>
    <th>Devices</th>
  </tr></thead>
<tbody>
  <tr>
    <td>Port P0</td>
    <td>Mạch Nút Nhấn MKE-M02 Push Button Tact Switch Module</td>
  </tr>
</tbody>
</table>

### Các bước tiến hành

1. Kết nối Mạch Nút Nhấn MKE-M02 với mạch MakerEDU Shield For Micro:Bit qua Port P0.
1. Gắn bo Micro:Bit lên mạch MakerEDU Shield.
1. Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
1. Nạp chương trình mẫu vào mạch Micro:Bit.
1. Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.  

Kết quả:
...pic

## Nhà phân phối

Có thể mua Mạch nút nhấn MKE-M02 push button tact switch module tại các nhà phân phối sau:

- Hshop.vn - Điện tử & Robot.
