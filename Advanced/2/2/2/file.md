![[Advanced/2/2/2/img1.png]]
```cpp
template<class T>
struct Array
{
    // все объявленные ниже методы уже реализованы
    explicit Array(size_t size = 0);
    Array(Array const& a);
    Array & operator=(Array const& a);
    ~Array();

    size_t size() const;
    T &         operator[](size_t i);
    T const&    operator[](size_t i) const;

    // реализуйте перемещающий конструктор
    Array(Array&& a) noexcept
        : size_(0)
        , data_(nullptr)
    {
        swap(a);
    }

    Array& operator=(Array&& a) noexcept
    {
        if (this != &a)
        {
            Array<T> temp(std::move(a));
            swap(temp);
        }
        return *this;
    }
    
    void swap(Array& other) noexcept
    {
        std::swap(size_, other.size_);
        std::swap(data_, other.data_);
    }

private:    
    size_t  size_;
    T *     data_;    
};
```
![[Advanced/2/2/2/img2.png]]