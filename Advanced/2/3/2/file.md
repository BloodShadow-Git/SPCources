![[Advanced/2/3/2/img1.png]]
```cpp
// так как в задании не указан тип элементов,
// которые хранятся в списке, то давайте сделаем
// эту функцию шаблонной
// Параметр It — это тип итератора 
#include <algorithm>

template<class It>
size_t max_increasing_len(It p, It q)
{
    if (p == q) return 0;
    
    size_t max_len = 1;
    size_t current_len = 1;
    
    It prev = p++;
    for (; p != q; ++p) {
        if (*p > *prev) {
            ++current_len;
            max_len = std::max(max_len, current_len);
        } else {
            current_len = 1;
        }
        prev = p;
    }
    
    return max_len;
}
```
![[Advanced/2/3/2/img2.png]]