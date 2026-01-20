![[Advanced/1/1/3/img1.png]]
![[Advanced/1/1/3/img2.png]]
![[Advanced/1/1/3/img3.png]]
![[Advanced/1/1/3/img4.png]]
![[Advanced/1/1/3/img5.png]]
![[Advanced/1/1/3/img6.png]]
```cpp
#include <iostream>
#include <string>
#include <cctype>
#include <cstdint>
#include <cmath>
#include <limits>

using namespace std;

bool isValidInput(const string& input, uint64_t& number) {
    if (input.empty()) {
        return false;
    }

    size_t start = 0;
    if (input[0] == '+') {
        start = 1;
        if (input.length() == 1) {
            return false;
        }
    }

    for (size_t i = start; i < input.length(); ++i) {
        if (!isdigit(static_cast<unsigned char>(input[i]))) {
            return false;
        }
    }

    if (input[start] == '0' && input.length() > start + 1) {
        return false;
    }

    try {
        if (input.length() - start > 20) {
            return false;
        }

        unsigned long long value = stoull(input.substr(start));

        if (value < 1 || value > 9223372036854775807ULL) {
            return false;
        }

        number = static_cast<uint64_t>(value);
        return true;
    }
    catch (const exception&) {
        return false;
    }
}

bool isTriangularNumber(uint64_t x, uint64_t& n) {

    uint64_t discriminant = 1 + 8 * x;

    uint64_t sqrt_disc = static_cast<uint64_t>(sqrt(discriminant));
    if (sqrt_disc * sqrt_disc != discriminant) {
        return false;
    }

    if ((sqrt_disc - 1) % 2 != 0) {
        return false;
    }

    n = (sqrt_disc - 1) / 2;
    return true;
}

int main() {
    string input;
    
    if (!getline(cin, input)) {
        cout << "0\n";
        return 0;
    }

    size_t start_pos = input.find_first_not_of(" \t\n\r");
    if (start_pos == string::npos) {
        cout << "0\n";
        return 0;
    }
    
    size_t end_pos = input.find_last_not_of(" \t\n\r");
    string trimmed_input = input.substr(start_pos, end_pos - start_pos + 1);

    uint64_t number;
    
    if (!isValidInput(trimmed_input, number)) {
        cout << "0\n";
        return 0;
    }

    uint64_t index;
    if (isTriangularNumber(number, index)) {
        cout << index << "\n";
    } else {
        cout << "0\n";
    }

    return 0;
}
```