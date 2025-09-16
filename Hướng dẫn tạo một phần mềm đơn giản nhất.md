# Tạo một phần mềm đơn giản
Mô tả: Phần mềm có một nút nhấn, ấn vào sẽ hiện ra một cửa sổ có dòng chữ "hello world"
Đối với cách code thuần
Bước 1: Tạo một file Qt
- Truy cập Qt Creator
- Ở trang giao diện, chọn tab file trên thanh công cụ hoặc chọn mục "Create project"  để tạo một file mới
- Ở cửa sổ hiện ra (choose a template), tick chọn Qt Widget Application, ấn choose
- Ở cửa sổ tiếp theo (location), đặt tên cho dự án và chọn nơi lưu dự án.
- Ở cửa sổ tiếp theo (Build system), chọn qmake  
- Ở cửa sổ class information và các cửa sổ khác, chọn next hết
- Bước 2: Viết code vào file main.cpp
```
#include <QApplication>
#include <QPushButton>
#include <QWidget>
#include <QLabel>

class SecondWindow : public QWidget {
public:
    SecondWindow() {
        setWindowTitle("Second Window");
        resize(200, 100);
        QLabel *label = new QLabel("Hello", this);
        label->move(80, 40);  // canh vị trí chữ
    }
};

int main(int argc, char *argv[]) {
    QApplication app(argc, argv);

    QWidget mainWindow;
    mainWindow.setWindowTitle("Main Window");
    mainWindow.resize(250, 150);

    QPushButton *btn = new QPushButton("Open", &mainWindow);
    btn->setGeometry(80, 50, 100, 40);

    // Khi bấm nút -> mở cửa sổ mới
    QObject::connect(btn, &QPushButton::clicked, [&]() {
        SecondWindow *win = new SecondWindow();
        win->show();
    });

    mainWindow.show();
    return app.exec();
}

```
- Bước 3: Ctrl B và chạy
