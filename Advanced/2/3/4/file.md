![[Advanced/2/3/4/img1.png]]
![[Advanced/2/3/4/img2.png]]
![[Advanced/2/3/4/img3.png]]
![[Advanced/2/3/4/img4.png]]
```cpp
#include <vector>
#include <list>
#include <iterator>
#include <cassert>

template<class T>
class VectorList
{
private:
    using VectT = std::vector<T>;
    using ListT = std::list<VectT>;

public:
    using value_type = T;

    VectorList() = default;
    VectorList(VectorList const &) = default;
    VectorList(VectorList &&) = default;

    VectorList & operator=(VectorList &&) = default;
    VectorList & operator=(VectorList const &) = default;

    // метод, который будет использоваться для заполнения VectorList
    // гарантирует, что в списке не будет пустых массивов
    template<class It>
    void append(It p, It q); // определена снаружи
/*  {
        if (p != q)
            data_.push_back(VectT(p,q));
    } 
*/

    bool empty() const { return size() == 0; }

    // определите метод size
    size_t size() const 
    {
        size_t total = 0;
        for (const auto& vec : data_) {
            total += vec.size();
        }
        return total;
    }

    // определите const_iterator
    class const_iterator 
    {
    public:
        using iterator_category = std::bidirectional_iterator_tag;
        using value_type = T;
        using difference_type = std::ptrdiff_t;
        using pointer = const T*;
        using reference = const T&;

        const_iterator() = default;

        reference operator*() const 
        {
            assert(list_it != list_end);
            assert(vec_it != (*list_it).end());
            return *vec_it;
        }

        pointer operator->() const 
        {
            assert(list_it != list_end);
            assert(vec_it != (*list_it).end());
            return &(*vec_it);
        }

        const_iterator& operator++() 
        {
            assert(list_it != list_end);
            assert(vec_it != (*list_it).end());
            
            ++vec_it;
            if (vec_it == (*list_it).end()) {
                ++list_it;
                if (list_it != list_end) {
                    vec_it = (*list_it).begin();
                }
            }
            return *this;
        }

        const_iterator operator++(int) 
        {
            const_iterator temp = *this;
            ++(*this);
            return temp;
        }

        const_iterator& operator--() 
        {
            // Если итератор указывает на end()
            if (list_it == list_end) {
                --list_it;
                vec_it = (*list_it).end();
            }
            
            // Переход к предыдущему вектору
            if (vec_it == (*list_it).begin()) {
                if (list_it != data_begin) {
                    --list_it;
                    vec_it = (*list_it).end();
                } else {
                    // Нельзя уменьшать begin() итератор
                    assert(false);
                }
            }
            
            --vec_it;
            return *this;
        }

        const_iterator operator--(int) 
        {
            const_iterator temp = *this;
            --(*this);
            return temp;
        }

        bool operator==(const const_iterator& other) const 
        {
            return list_it == other.list_it && vec_it == other.vec_it;
        }

        bool operator!=(const const_iterator& other) const 
        {
            return !(*this == other);
        }

    private:
        friend class VectorList;
        
        using ListIterator = typename ListT::const_iterator;
        using VecIterator = typename VectT::const_iterator;
        
        ListIterator list_it;
        ListIterator list_end;
        ListIterator data_begin;
        VecIterator vec_it;

        const_iterator(ListIterator list_it, ListIterator list_end, 
                      ListIterator data_begin, VecIterator vec_it)
            : list_it(list_it), list_end(list_end), 
              data_begin(data_begin), vec_it(vec_it) {}
    };

    // определите методы begin / end
    const_iterator begin() const 
    {
        if (data_.empty()) {
            return end();
        }
        return const_iterator(data_.begin(), data_.end(), 
                              data_.begin(), data_.front().begin());
    }
    
    const_iterator end() const 
    {
        if (data_.empty()) {
            return const_iterator(data_.end(), data_.end(), 
                                  data_.begin(), typename VectT::const_iterator());
        }
        // end() должен указывать за последний элемент
        // Для этого нужно взять последний вектор и его end()
        auto last_vec = --data_.end();
        return const_iterator(data_.end(), data_.end(), 
                              data_.begin(), (*last_vec).end());
    }

    // определите const_reverse_iterator
    using const_reverse_iterator = std::reverse_iterator<const_iterator>;

    // определите методы rbegin / rend
    const_reverse_iterator rbegin() const 
    {
        return const_reverse_iterator(end());
    }
    
    const_reverse_iterator rend() const 
    {
        return const_reverse_iterator(begin());
    }

private:
    ListT data_;
};
```