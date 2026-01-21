![[Advanced/2/5/1/img1.png]]
```cpp
#include <vector>

template<typename InputIt, typename UnaryFunc, typename BinaryFunc>
auto map_reduce(InputIt p, InputIt q, UnaryFunc f1, BinaryFunc f2, size_t threads) ->
    decltype(f2(f1(*p), f1(*p)))
{
    using ResultType = decltype(f1(*p));
    using ReturnType = decltype(f2(f1(*p), f1(*p)));
    
    // Если последовательность пуста, возвращаем значение по умолчанию
    if (p == q) {
        return ReturnType();
    }
    
    auto total_size = std::distance(p, q);
    
    // Если потоков больше чем элементов, ограничиваем количество потоков
    if (static_cast<size_t>(total_size) < threads) {
        threads = total_size;
    }
    
    // Вычисляем размер каждого блока
    auto block_size = total_size / threads;
    auto remainder = total_size % threads;
    
    std::vector<std::future<ResultType>> futures;
    futures.reserve(threads);
    
    // Запускаем потоки для обработки блоков
    for (size_t i = 0; i < threads; ++i) {
        auto start = p;
        std::advance(p, block_size + (i < remainder ? 1 : 0));
        auto end = p;
        
        futures.push_back(std::async(std::launch::async, 
            [start, end, &f1, &f2]() -> ResultType {
                auto it = start;
                if (it == end) {
                    return ResultType();
                }
                
                auto result = f1(*it);
                ++it;
                
                while (it != end) {
                    result = f2(result, f1(*it));
                    ++it;
                }
                
                return result;
            }
        ));
    }
    
    // Собираем результаты из всех потоков
    ReturnType final_result;
    bool first = true;
    
    for (auto& future : futures) {
        auto thread_result = future.get();
        
        if (first) {
            final_result = thread_result;
            first = false;
        } else {
            final_result = f2(final_result, thread_result);
        }
    }
    
    return final_result;
}
```
![[Advanced/2/5/1/img2.png]]
```cpp
#include <vector>

template<typename InputIt, typename UnaryFunc, typename BinaryFunc>
auto map_reduce(InputIt p, InputIt q, UnaryFunc f1, BinaryFunc f2, size_t threads) ->
    decltype(f2(f1(*p), f1(*p)))
{
    using ResultType = decltype(f1(*p));
    using ReturnType = decltype(f2(f1(*p), f1(*p)));
    
    // Если последовательность пуста, возвращаем значение по умолчанию
    if (p == q) {
        return ReturnType();
    }
    
    auto total_size = std::distance(p, q);
    
    // Если потоков больше чем элементов, ограничиваем количество потоков
    if (static_cast<size_t>(total_size) < threads) {
        threads = total_size;
    }
    
    // Вычисляем размер каждого блока
    auto block_size = total_size / threads;
    auto remainder = total_size % threads;
    
    std::vector<std::thread> workers;
    std::vector<ResultType> results(threads);
    std::vector<InputIt> block_starts(threads + 1);
    
    // Определяем границы блоков
    InputIt current = p;
    for (size_t i = 0; i < threads; ++i) {
        block_starts[i] = current;
        auto advance_by = block_size + (i < remainder ? 1 : 0);
        std::advance(current, advance_by);
    }
    block_starts[threads] = current;  // конечная граница
    
    // Запускаем потоки для обработки блоков
    for (size_t i = 0; i < threads; ++i) {
        workers.emplace_back(
            [&results, i, &f1, &f2, &block_starts]() {
                InputIt start = block_starts[i];
                InputIt end = block_starts[i + 1];
                
                if (start == end) {
                    results[i] = ResultType();
                    return;
                }
                
                auto it = start;
                auto result = f1(*it);
                ++it;
                
                while (it != end) {
                    result = f2(result, f1(*it));
                    ++it;
                }
                
                results[i] = result;
            }
        );
    }
    
    // Дожидаемся завершения всех потоков
    for (auto& worker : workers) {
        worker.join();
    }
    
    // Объединяем результаты из всех потоков
    ReturnType final_result;
    bool first = true;
    
    for (const auto& thread_result : results) {
        if (first) {
            final_result = thread_result;
            first = false;
        } else {
            final_result = f2(final_result, thread_result);
        }
    }
    
    return final_result;
}
```
![[Advanced/2/5/1/img3.png]]