![[Advanced/1/1/4/img1.png]]
![[Advanced/1/1/4/img2.png]]
![[Advanced/1/1/4/img3.png]]
![[Advanced/1/1/4/img4.png]]
![[Advanced/1/1/4/img5.png]]
![[Advanced/1/1/4/img6.png]]
```cpp
#include <iostream>
#include <string>
#include <sstream>
#include <vector>
#include <cstdlib>
#include <limits>

using namespace std;

bool isInteger(const string& s) {
    if (s.empty()) return false;
    
    size_t start = 0;
    if (s[0] == '+') start = 1;
    
    for (size_t i = start; i < s.length(); i++) {
        if (!isdigit(s[i])) return false;
    }
    
    return true;
}

bool parseDouble(const string& s, double& value) {
    char* endptr;
    value = strtod(s.c_str(), &endptr);
    
    if (endptr == s.c_str()) return false;
    
    while (*endptr != '\0') {
        if (!isspace(static_cast<unsigned char>(*endptr))) {
            return false;
        }
        endptr++;
    }
    
    return true;
}

int main() {
    string line;
    if (!getline(cin, line)) {
        cout << "[error]" << endl;
        return 0;
    }
    
    istringstream iss(line);
    string nStr;
    
    if (!(iss >> nStr)) {
        cout << "[error]" << endl;
        return 0;
    }
    
    if (!isInteger(nStr)) {
        cout << "[error]" << endl;
        return 0;
    }
    
    long long N = atoll(nStr.c_str());
    
    if (N < 2) {
        cout << "[error]" << endl;
        return 0;
    }
    
    vector<double> sequence;
    double num;
    string token;
    
    while (iss >> token) {
        if (!parseDouble(token, num)) {
            cout << "[error]" << endl;
            return 0;
        }
        sequence.push_back(num);
        
        if (sequence.size() >= static_cast<size_t>(N)) {
            break;
        }
    }
    
    if (sequence.size() < static_cast<size_t>(N)) {
        while (sequence.size() < static_cast<size_t>(N)) {
            if (!(cin >> token)) {
                cout << "[error]" << endl;
                return 0;
            }
            
            if (!parseDouble(token, num)) {
                cout << "[error]" << endl;
                return 0;
            }
            sequence.push_back(num);
        }
    }
    
    int maxLength = 0;
    int startPos = -1;
    int currentLength = 1;
    int currentStart = 0;
    
    for (int i = 1; i < N; i++) {
        if (sequence[i] >= sequence[i - 1]) {
            currentLength++;
        } else {
            if (currentLength > maxLength) {
                maxLength = currentLength;
                startPos = currentStart;
            }
            currentLength = 1;
            currentStart = i;
        }
    }
    
    if (currentLength > maxLength) {
        maxLength = currentLength;
        startPos = currentStart;
    }
    
    if (maxLength >= 2) {
        cout << maxLength << " " << startPos + 1 << endl;
    } else {
        cout << 0 << endl;
    }
    
    return 0;
}
```