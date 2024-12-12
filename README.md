// PROGRAM 1
#include <iostream>
using namespace std;

int main() {
    float v, u, a, t;
    cout << "Enter initial velocity \n";
    cin >> u;
    cout << "Enter acceleration \n";
    cin >> a;
    cout << "Enter time \n";
    cin >> t;
    v = u + a * t;
    cout << v;
    return 0;
}

/* OUTPUT:
Enter initial velocity 
Enter acceleration
Enter time
8.24
*/

// PROGRAM 2
#include <iostream>
using namespace std;

void swap(int, float);

int main() {
    int a;
    float b;
    cout << "Enter the Two Numbers to Swap in C++: ";
    cin >> a >> b;
    cout << "\nAfter Swapping of Two Numbers:";
    swap(a, b);
    return 0;
}

void swap(int x, float y) {
    int z;
    z = x;
    x = y;
    y = z;
    cout << " " << x << " " << y;
}

/* OUTPUT:
Enter the Two Numbers to Swap in C++: 8 6
After Swapping of Two Numbers: 6 8
*/

// PROGRAM 3
#include <iostream>
using namespace std;

class Count {
private:
    int value;

public:
    // Constructor to initialize count to 5
    Count() : value(5) {}

    // Overload ++ when used as prefix
    void operator++() {
        ++value;
    }

    void display() {
        cout << "Count: " << value << endl;
    }
};

int main() {
    Count count1;
    // Call the "void operator ++ ()" function
    ++count1;
    count1.display();
    return 0;
}

/* OUTPUT:
Count: 6
*/

// PROGRAM 4
#include <iostream>
using namespace std;

class Complex {
private:
    float real;
    float imag;

public:
    Complex() : real(0), imag(0) {}

    void input() {
        cout << "Enter real and imaginary parts respectively: ";
        cin >> real >> imag;
    }

    Complex operator+(Complex c2) {
        Complex temp;
        temp.real = real + c2.real;
        temp.imag = imag + c2.imag;
        return temp;
    }

    void output() {
        if (imag < 0)
            cout << "Output Complex number: " << real << imag << "i";
        else
            cout << "Output Complex number: " << real << "+" << imag << "i";
    }
};

int main() {
    Complex c1, c2, result;
    cout << "Enter first complex number:\n";
    c1.input();
    cout << "Enter second complex number:\n";
    c2.input();
    result = c1 + c2;
    result.output();
    return 0;
}

/* OUTPUT:
Enter first complex number:
Enter real and imaginary parts respectively:
2
8
Enter second complex number:
Enter real and imaginary parts respectively:
4
3
Output Complex number: 6+11i
*/

// PROGRAM 5
#include <iostream>
using namespace std;

class base {
    int val1, val2;

public:
    void get() {
        cout << "\nEnter 1st value :: ";
        cin >> val1;
        cout << "\nEnter 2nd value :: ";
        cin >> val2;
    }

    friend float mean(base ob);
};

float mean(base ob) {
    return float(ob.val1 + ob.val2) / 2;
}

int main() {
    base obj;
    obj.get();
    cout << "\nMean value is :: " << mean(obj) << "\n";
    return 0;
}

/* OUTPUT:
Enter 1st value :: 5
Enter 2nd value :: 8
Mean value is :: 6.5
*/

// PROGRAM 6
#include <iostream>
using namespace std;

class operation {
    int a, b, mul;
    float div;

public:
    void get();
    void product();
    void division();
};

inline void operation::get() {
    cout << "Enter first value: ";
    cin >> a;
    cout << "Enter second value: ";
    cin >> b;
}

inline void operation::product() {
    mul = a * b;
    cout << "Product of two numbers: " << a * b << "\n";
}

inline void operation::division() {
    div = float(a) / b;
    cout << "Division of two numbers: " << div << "\n";
}

int main() {
    cout << "Program using inline function\n";
    operation s;
    s.get();
    s.product();
    s.division();
    return 0;
}

/* OUTPUT:
Enter first value: 45
Enter second value: 15
Product of two numbers: 675
Division of two numbers: 3
*/

/ PROGRAM 8
#include <iostream>
using namespace std;

class Agent {
protected:
    float commissionRate;

public:
    Agent(float rate) : commissionRate(rate) {}

    float calculateCommission(float saleValue) {
        return commissionRate * saleValue;
    }
};

class Salesperson : public Agent {
public:
    Salesperson(float rate) : Agent(rate) {}

    void printCommission(float saleValue) {
        float commission = calculateCommission(saleValue);
        cout << "Agent's commission for sale value $" << saleValue << " is $" << commission << endl;
    }
};

int main() {
    float commissionRate;
    cout << "Enter the commission rate for the salesperson (in decimal): ";
    cin >> commissionRate;
    Salesperson salesAgent(commissionRate);

    float saleValue;
    cout << "Enter the sale value: $";
    cin >> saleValue;
    salesAgent.printCommission(saleValue);

    return 0;
}

/* OUTPUT:
Enter the commission rate for the salesperson (in decimal): 0.1
Enter the sale value: $1000
Agent's commission for sale value $1000 is $100
*/

//program 13:

#include<iostream>
#include<string>
using namespace std;

class Counter {
public:
    virtual int countWords(const std::string &text) = 0;
    virtual int countCharacters(const std::string &text) = 0;
};

class WordCharacterCounter : public Counter {
public:
    int countWords(const std::string &text) override {
        int words = 0;
        bool inWord = false;
        for (char c : text) {
            if (std::isalpha(c) && !inWord) {
                inWord = true;
                words++;
            } else if (!std::isalpha(c)) {
                inWord = false;
            }
        }
        return words;
    }

    int countCharacters(const std::string &text) override {
        return text.length();
    }
};

int main() {
    WordCharacterCounter counter;
    std::string input_text = "This is a sample text.";
    int word_count = counter.countWords(input_text);
    int char_count = counter.countCharacters(input_text);

    std::cout << "Word count: " << word_count << std::endl;
    std::cout << "Character count: " << char_count << std::endl;
    return 0;
}

//program 15:

#include<iostream>
using namespace std;

Application Development using C++
Dept. of AIML

int main()
{
    int var1, var2;
    float var3;

    cout << "enter the dividend:";
    cin >> var1;
    cout << "\n";
    cout << "enter the divisor:";
    cin >> var2;
    cout << "\n";

    // Exception handling begins here
    try // try block
    {
        if (var2 != 0) // checking if divisor is zero
        {
            var3 = var1 / var2;
            cout << "outcome :" << var3;
        }
        else
        {
            throw (var2); // throwing the exception found
        }
    }
    // catch block
    catch (int exc)
    {
        cout << "division by zero is not possible. Please try again with different value of variables";
    }

    return 0;
}

