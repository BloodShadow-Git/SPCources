![[Advanced/2/3/3/img1.png]]
![[Advanced/2/3/3/img2.png]]
![[Advanced/2/3/3/img3.png]]
```cpp
#include <typeinfo>
#include <typeindex>
#include <functional>
#include <map>
#include <utility>

template<class Base, class Result, bool Commutative>
struct Multimethod2
{
private:
    // Тип для хранения функции
    using Function = std::function<Result(Base*, Base*)>;
    
    // Ключ для карты - пара type_index
    using Key = std::pair<std::type_index, std::type_index>;
    
    // Карта реализаций
    std::map<Key, Function> implementations;

    // Вспомогательная функция для создания ключа
    Key makeKey(const std::type_info& t1, const std::type_info& t2) const
    {
        return std::make_pair(std::type_index(t1), std::type_index(t2));
    }

    // Вспомогательная функция для поиска реализации
    typename std::map<Key, Function>::const_iterator 
    findImpl(const std::type_info& t1, const std::type_info& t2) const
    {
        auto key = makeKey(t1, t2);
        auto it = implementations.find(key);
        
        if (it != implementations.end())
            return it;
            
        // Если коммутативный и не нашли прямой порядок, пробуем обратный
        if (Commutative)
        {
            auto reverseKey = makeKey(t2, t1);
            return implementations.find(reverseKey);
        }
        
        return implementations.end();
    }

public:
    // устанавливает реализацию мультиметода
    void addImpl(const std::type_info& t1, const std::type_info& t2, Function f)
    {
        implementations[makeKey(t1, t2)] = std::move(f);
    }
    
    // проверяет, есть ли реализация мультиметода
    bool hasImpl(Base* a, Base* b) const
    {
        if (!a || !b) return false;
        return findImpl(typeid(*a), typeid(*b)) != implementations.end();
    }
    
    // Применяет мультиметод к объектам
    Result call(Base* a, Base* b) const
    {
        if (!a || !b) 
            throw std::runtime_error("Null pointer passed to Multimethod2::call");
            
        const std::type_info& t1 = typeid(*a);
        const std::type_info& t2 = typeid(*b);
        
        auto it = findImpl(t1, t2);
        
        if (it == implementations.end())
            throw std::runtime_error("No implementation found for given types");
            
        // Если нашли в прямом порядке, вызываем напрямую
        if (implementations.find(makeKey(t1, t2)) != implementations.end())
        {
            return it->second(a, b);
        }
        else
        {
            // Если нашли в обратном порядке (только для коммутативного случая),
            // вызываем с переставленными аргументами
            return it->second(b, a);
        }
    }
};
```