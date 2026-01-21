![[Advanced/2/3/5/img1.png]]
```cpp
#include <algorithm>
#include <iterator>

template<class FwdIt>
FwdIt remove_nth(FwdIt p, FwdIt q, size_t n)
{
    if (p == q) return q; // пустой диапазон
    
    FwdIt current = p;
    size_t count = 0;
    
    // Находим элемент с индексом n
    while (current != q && count < n) {
        ++current;
        ++count;
    }
    
    // Если индекс выходит за границы диапазона
    if (current == q) {
        return q;
    }
    
    // Сохраняем итератор на следующий элемент после удаляемого
    FwdIt next = current;
    ++next;
    
    // Сдвигаем все элементы после удаляемого на одну позицию влево
    while (next != q) {
        *current = std::move(*next);
        ++current;
        ++next;
    }
    
    return current;
}
```
![[Advanced/2/3/5/img2.png]]
![[Advanced/2/3/5/img3.png]]
![[Advanced/2/3/5/img4.png]]
```cpp
#include <algorithm>
#include <vector>

template<class Iterator>
size_t count_permutations(Iterator p, Iterator q)
{
    // Если диапазон пустой - 0 перестановок
    if (p == q) return 1;
    
    // Копируем последовательность
    using ValueType = typename std::iterator_traits<Iterator>::value_type;
    std::vector<ValueType> seq(p, q);
    
    // Если всего один элемент - 1 допустимая перестановка
    if (seq.size() == 1) return 1;
    
    // Сортируем для использования next_permutation
    // Важно: next_permutation генерирует только уникальные перестановки
    // при наличии повторяющихся элементов
    std::sort(seq.begin(), seq.end());
    
    size_t count = 0;
    
    // Проверяем первую перестановку (отсортированную)
    bool valid = true;
    auto it = seq.begin();
    auto prev = it++;
    while (it != seq.end()) {
        if (*prev == *it) {
            valid = false;
            break;
        }
        prev = it++;
    }
    
    if (valid) {
        ++count;
    }
    
    // Проверяем все оставшиеся уникальные перестановки
    while (std::next_permutation(seq.begin(), seq.end())) {
        valid = true;
        it = seq.begin();
        prev = it++;
        while (it != seq.end()) {
            if (*prev == *it) {
                valid = false;
                break;
            }
            prev = it++;
        }
        
        if (valid) {
            ++count;
        }
    }
    
    return count;
}
```