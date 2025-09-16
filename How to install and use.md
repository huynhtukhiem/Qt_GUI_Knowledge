# Hướng dẫn cách lập trình giao diện trong C++ bằng Qt thông quan phần mềm Qt Creator và lập trình trên Visual Studio Code
**Bước 1: Cài Visual Studio Code**

Truy cập trang web sau để cài: https://code.visualstudio.com/download

**Bước 2: Cài Qt Creator**

Truy cập đường link sau: https://qt-creator.en.lo4d.com/download

**Bước 3: Hiểu bản chất**

Sau khi đã có VSCode và Qt Creator, chúng ta cần hiểu rằng:
- Qt Creator là một IDE cho C/C++, có sẳn compiler (MinGW) nó giống như DevC++ nhưng hỗ trợ phần lập trình giao diện rất đơn giản có thể bằng cách kéo thả.
- VS Code là một text editor, muốn chạy C/C++ thì phải cài thêm extension, nó cũng không có sẳn compiler mà mình phải tự cài và tự cấu hình

=> Vậy nên nếu chỉ quen dùng VSCode để lập trình thì mình phải cài thêm và tự cấu hình thêm các thứ sau:
1. Extension C/C++, Cmake tools, debugger,....: Để lập trình C/C++ thông thường
   
2. Cấu hình VSCode:
   - Tạo .vscode/tasks.json để build
   - Tạo .vscode/launch.json để debug.
     
3. Compiler: compiler ở đây là MinGW-w64 vì chỉ nó mới hỗ trợ tốt cho Qt
   
4. Qt SDK: Một gói cài đặt đầy đủ cho

**Bước 4: Cài QtSDK và compiler MinGW**

Nếu bạn đã có compiler MinGW thì hãy xóa nó đi để đỡ bị xung đột, rắc rối khi tải Qt về, bởi vì khi tải Qt thì nó sẽ cho phép tải MinGW về chung. Nếu không muốn xóa thì khi tải Qt đừng tick vào ô chọn tải MinGW về chung

Cách xóa MinGW-w64: 
 - Truy cập terminal: gõ g++ --version và kiểm tra xem đã tải MinGW về chưa nếu hiện dòng chữ: g++ is not recognize thì tức là chưa tải, nếu muốn xóa thì xóa hết tất cả compiler: 
 - Vào Control Panel → Programs and Features (hoặc Settings → Apps → Installed apps trên Windows 10/11) -> Tìm MinGW hoặc MSYS2 → nhấn Uninstall. Sau đó kiểm tra lại PATH để chắc chắn không còn trỏ tới MinGW cũ: win + R -> nhập: sysdm.cpl -> advance -> environt variables -> tìm phần Path trong system variables -> edit -> xóa đường dẫn liên quan đến compiler

Sau khi xóa sạch compiler, bắt đầu tải Qt

- Truy câp đường dẫn sau và tải Qt: https://www.qt.io/download-open-source
- Lưu ý tick chọn như hình sau trước khi tải:
<img width="1621" height="1067" alt="image" src="https://github.com/user-attachments/assets/d5d80e1b-ee4b-47e3-8388-38a97d69a3d3" />

<img width="1616" height="1071" alt="image" src="https://github.com/user-attachments/assets/d41f7b8b-def1-47a8-a3e5-5962ad996a74" />

<img width="805" height="639" alt="image" src="https://github.com/user-attachments/assets/711544f0-c6e5-45d3-89cc-1293c35e476f" />

Sau quá trình cài đặt lâu thì chúng ta đã có Qt

**Bước 5: Thêm đường dẫn vào Path**
 - Copy đường dẫn có địa chỉ ví dụ như sau trong máy tính của bạn: C:\Qt\Tools\mingw1310_64\bin 
 - Ấn win + R -> gõ sysdm.cpl -> chọn tab Advance -> chọn Environment Variables -> trong System variables chọn Path -> ấn Edit
 - Ấn New -> dán đường dẫn vừa này vào -> OK tất cả
 - Mở Command Prompt -> nhập g++ --version để xem MinGW đã được cài chưa, nếu rồi sẽ hiện như sau:
```
C:\Users\huynh>g++ --version
g++ (x86_64-posix-seh-rev1, Built by MinGW-Builds project) 13.1.0
Copyright (C) 2023 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```
# Sau khi thêm đường dẫn xong, bạn đã có thể code trên Qt rồi nhưng nếu muốn code trên VSCode thì làm theo các bước sau:
