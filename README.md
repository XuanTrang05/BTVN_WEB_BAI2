Bài tập 02: Lập trình web.
==============================
NGÀY GIAO: 19/10/2025
==============================
DEADLINE: 26/10/2025
==============================
1. Sử dụng github để ghi lại quá trình làm, tạo repo mới, để truy cập public, edit file `readme.md`:
   chụp ảnh màn hình (CTRL+Prtsc) lúc đang làm, paste vào file `readme.md`, thêm mô tả cho ảnh.
2. NỘI DUNG BÀI TẬP:
2.1. Cài đặt Apache web server:
- Vô hiệu hoá IIS: nếu iis đang chạy thì mở cmd quyền admin để chạy lệnh: iisreset /stop
- Download apache server, giải nén ra ổ D, cấu hình các file:
  + D:\Apache24\conf\httpd.conf
  + D:Apache24\conf\extra\httpd-vhosts.conf
  để tạo website với domain: fullname.com
  code web sẽ đặt tại thư mục: `D:\Apache24\fullname` (fullname ko dấu, liền nhau)
- sử dụng file `c:\WINDOWS\SYSTEM32\Drivers\etc\hosts` để fake ip 127.0.0.1 cho domain này
  ví dụ sv tên là: `Đỗ Duy Cốp` thì tạo website với domain là fullname ko dấu, liền nhau: `doduycop.com`
- thao tác dòng lệnh trên file `D:\Apache24\bin\httpd.exe` với các tham số `-k install` và `-k start` để cài đặt và khởi động web server apache.
2.2. Cài đặt nodejs và nodered => Dùng làm backend:
- Cài đặt nodejs:
  + download file `https://nodejs.org/dist/v20.19.5/node-v20.19.5-x64.msi`  (đây ko phải bản mới nhất, nhưng ổn định)
  + cài đặt vào thư mục `D:\nodejs`
- Cài đặt nodered:
  + chạy cmd, vào thư mục `D:\nodejs`, chạy lệnh `npm install -g --unsafe-perm node-red --prefix "D:\nodejs\nodered"`
  + download file: https://nssm.cc/release/nssm-2.24.zip
    giải nén được file nssm.exe
    copy nssm.exe vào thư mục `D:\nodejs\nodered\`
  + tạo file "D:\nodejs\nodered\run-nodered.cmd" với nội dung (5 dòng sau):
@echo off
REM fix path
set PATH=D:\nodejs;%PATH%
REM Run Node-RED
node "D:\nodejs\nodered\node_modules\node-red\red.js" -u "D:\nodejs\nodered\work" %*
  + mở cmd, chuyển đến thư mục: `D:\nodejs\nodered`
  + cài đặt service `a1-nodered` bằng lệnh: nssm.exe install a1-nodered "D:\nodejs\nodered\run-nodered.cmd"
  + chạy service `a1-nodered` bằng lệnh: `nssm start a1-nodered`
2.3. Tạo csdl tuỳ ý trên mssql (sql server 2022), nhớ các thông số kết nối: ip, port, username, password, db_name, table_name
2.4. Cài đặt thư viện trên nodered:
- truy cập giao diện nodered bằng url: http://localhost:1880
- cài đặt các thư viện: node-red-contrib-mssql-plus, node-red-node-mysql, node-red-contrib-telegrambot, node-red-contrib-moment, node-red-contrib-influxdb, node-red-contrib-duckdns, node-red-contrib-cron-plus
- Sửa file `D:\nodejs\nodered\work\settings.js` : 
  tìm đến chỗ adminAuth, bỏ comment # ở đầu dòng (8 dòng), thay chuỗi mã hoá mật khẩu bằng chuỗi mới
    adminAuth: {
        type: "credentials",
        users: [{
            username: "admin",
            password: "chuỗi_mã_hoá_mật_khẩu",
            permissions: "*"
        }]
    },   
   với mã hoá mật khẩu có thể thiết lập bằng tool: https://tms.tnut.edu.vn/pw.php
- chạy lại nodered bằng cách: mở cmd, vào thư mục `D:\nodejs\nodered` và chạy lệnh `nssm restart a1-nodered`
  khi đó nodered sẽ yêu cầu nhập mật khẩu mới vào được giao diện cho admin tại: http://localhost:1880
2.5. tạo api back-end bằng nodered:
- tại flow1 trên nodered, sử dụnhình

2.2. Cài đặt nodejs và nodered => Dùng làm backend:
- Cài đặt nodejs:
- truy cập vào trang của nodejs để cài nodejs
<img width="1920" height="1080" alt="Ảnh chụp màn hình (37)" src="https://github.com/user-attachments/assets/beac01fb-7991-453a-9a65-4def0655d7c7" />
<img width="1920" height="1080" alt="Screenshot 2025-10-22 225435" src="https://github.com/user-attachments/assets/535cabc6-d154-4b20-a53a-ea721a0cfcc4" />
<img width="1920" height="1080" alt="Screenshot 2025-10-22 225505" src="https://github.com/user-attachments/assets/aa56511a-1647-4b6a-9232-329e75650a20" />
<img width="1920" height="1080" alt="Screenshot 2025-10-22 225515" src="https://github.com/user-attachments/assets/4c51020f-693e-4c3a-93e4-10e39b7af2dd" />
<img width="1920" height="1080" alt="Screenshot 2025-10-22 225535" src="https://github.com/user-attachments/assets/73edcaf0-ded2-432b-a6e3-18848f0baf04" />
<img width="1920" height="1080" alt="Screenshot 2025-10-22 225547" src="https://github.com/user-attachments/assets/918f464b-ed03-43c1-981a-0656b19791ef" />
<img width="1920" height="1080" alt="Screenshot 2025-10-22 225612" src="https://github.com/user-attachments/assets/d926c81f-184d-4bee-a31d-0826a37cc8be" />
<img width="1920" height="1080" alt="Screenshot 2025-10-22 225628" src="https://github.com/user-attachments/assets/38f86026-a284-422d-ba25-e8bd6c713398" />
+ cài đặt vào thư mục `D:\nodejs`
+ <img width="961" height="1073" alt="image" src="https://github.com/user-attachments/assets/2157d3fa-0fdb-4a7e-a0c9-ef34abd56172" />
- Cài đặt nodered:
-
-
-
-
-
-









