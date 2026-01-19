![[Base/1/8/4/img1.png]]
![[Base/1/8/4/img2.png]]
![[Base/1/8/4/img3.png]]
```cpp
#include <iostream>
#include <string>
#include <fstream>
using namespace std;

int main()
{
    // Здесь будет твой код . . . 
    fstream rw("Лермонтов.txt", ios::app);
    rw << "Волнам их воля и холод дороже\nЗнойных полудня лучей;\nЛюди хотят иметь души… И что же?\nДуши в них волн холодней!" << endl;
}
```
![[Base/1/8/4/img4.png]]
```cpp
#include <iostream>
#include <string>
#include <fstream>
using namespace std;

// Функция для печати файла
// НЕ ИЗМЕНЯТЬ!
void print_file(string filename)
{
    ifstream myfile(filename, ios::ate);

    int size = myfile.tellg();
    myfile.seekg(0);

    char content[size];
    myfile.read(content, size);

    cout.write(content, size);
}

void replace_text(string filename, string text, int pos)
{
    fstream rw(filename);
    rw.seekg(pos);
    string buf;
    rw >> buf;
    char c[text.length() + 1];
    strcpy(c, text.c_str());
    rw.seekg(pos);
    rw.write(c, buf.length());
    rw.flush();
    rw.close();
}

// НЕ ИЗМЕНЯТЬ!
int main()
{
    // Ввод данных
    string filename;
    getline(cin, filename);

    string text;
    getline(cin, text);

    int pos;
    cin >> pos;

    // Вызов твоей функции
    replace_text(filename, text, pos);

    // Вывод ответа
    print_file(filename);
}
```