# constant keyword
In the C, C++, D, JavaScript and Julia programming languages, const is a type qualifier:[a] a keyword applied to a data type that indicates that the data is read only. While this can be used to declare constants, const in the C family of languages differs from similar constructs in other languages in being part of the type, and thus has complicated behavior when combined with pointers, references, composite data types, and type-checking.
the various functions of the const keyword which is found in C++ are discussed. Whenever const keyword is attached with any method(), variable, pointer variable, and with the object of a class it prevents that specific object/method()/variable to modify its data items value.
### Constant Variables:
There are a certain set of rules for the declaration and initialization of the constant variables:
- The const variable cannot be left un-initialized at the time of the assignment.
- It cannot be assigned value anywhere in the program.
- Explicit value needed to be provided to the constant variable at the time of declaration of the constant variable.
```
// C++ program to demonstrate the above concept
#include <iostream>
using namespace std;
 // Driver Code
int main()
{
  // const int x;  CTE error
    // x = 9;   CTE error
    const int y = 10;
    cout << y;
 
    return 0;
}
```
### Const Keyword With Pointer Variables:
 Pointers can be declared with a const keyword. So, there are three possible ways to use a const keyword with a pointer, which are as follows:
When the pointer variable point to a const value:
Syntax: 
__const data_type* var_name;__
```
// C++ program to demonstrate the above concept
#include <iostream>
using namespace std;
 // Driver Code
int main()
{
    int x{ 10 };
    char y{ 'M' };
    const int* i = &x;
    const char* j = &y;
    // Value of x and y can be altered,
    // they are not constant variables
    x = 9;
    y = 'A';
    // Change of constant values because,
    // i and j are pointing to const-int
    // & const-char type value
    // *i = 6;
    // *j = 7;
    cout << *i << " " << *j;
}
```
### When the const pointer variable point to the value:
Syntax:
__data_type* const var_name;__
Below is the example to demonstrate the above concept:
```
// C++ program to demonstrate the
// above concept
#include <iostream>
using namespace std;
 // Driver Code
int main()
{
    // x and z non-const var
    int x = 5;
    int z = 6;
    // y and p non-const var
    char y = 'A';
    char p = 'C';
    // const pointer(i) pointing
    // to the var x's location
    int* const i = &x;
    // const pointer(j) pointing
    // to the var y's location
    char* const j = &y;
    // The values that is stored at the memory location can modified
    // even if we modify it through the pointer itself
    // No CTE error
    *i = 10;
    *j = 'D';
    // CTE because pointer variable
    // is const type so the address
    // pointed by the pointer variables
    // can't be changed
    // *i = &z;
    // *j = &p;
    cout << *i << " and " << *j
        << endl;
    cout << i << " and " << j;
    return 0;
}
```
### When const pointer pointing to a const variable:
Syntax:
__const data_type* const var_name;__
Below is the C++ program to demonstrate the above concept:
```
// C++ program to demonstrate
// the above concept
#include <iostream>
using namespace std;
 // Driver code
int main()
{
    int x{ 9 };
     const int* const i = &x;
      // *i=10;  
    // The above statement will give CTE
    // Once Ptr(*i) value is
    // assigned, later it can't
    // be modified(Error)
  char y{ 'A' };
    const char* const j = &y;
      // *j='B';
    // The above statement will give CTE
    // Once Ptr(*j) value is
    // assigned, later it can't
    // be modified(Error)
  cout << *i << " and " << *j;
    return 0;
}
```
### Constant Methods:
Like member functions and member function arguments, the objects of a class can also be declared as const. An object declared as const cannot be modified and hence, can invoke only const member functions as these functions ensure not to modify the object.
Syntax:
**const Class_Name Object_name;**
When a function is declared as const, it can be called on any type of object, const object as well as non-const objects.
Whenever an object is declared as const, it needs to be initialized at the time of declaration. However, the object initialization while declaring is possible only with the help of constructors.
There are two ways of a constant function declaration:
#### Ordinary const-function Declaration:
```
const void foo()
{
   //void foo() const Not valid
}                  
int main()
{
   foo(x);
}  
A const member function of the class:
class
{
   void foo() const
   {
       //.....
   }
}
```
Below is the example of a constant function:
// C++ program to demonstrate the
// constant function
```
#include <iostream>
using namespace std;
 // Class Test
class Test {
    int value;
 public:
    // Constructor
    Test(int v = 0)
    {
        value = v;
    }
    // We get compiler error if we
    // add a line like "value = 100;"
    // in this function.
    int getValue() const
    {
        return value;
    }
        // a nonconst function trying to modify value
    void setValue(int val) {
        value = val;
    }
};
 // Driver Code
int main()
{
    // Object of the class T
    Test t(20);
    // non-const object invoking const function, no error
    cout << t.getValue() << endl;
        // const object
      const Test t_const(10);
   // const object invoking const function, no error
    cout << t_const.getValue() << endl;
    // const object invoking non-const function, CTE
    // t_const.setValue(15);
      // non-const object invoking non-const function, no error
    t.setValue(12);
     cout << t.getValue() << endl;
 return 0;
}
```
### Constant Function Parameters And Return Type:
A function() parameters and return type of function() can be declared as constant. Constant values cannot be changed as any such attempt will generate a compile-time error.
Below is the C++ program to implement the above approach: 
```
// C++ program to demonstrate the
// above approach
#include <iostream>
using namespace std;
 // Function foo() with variable
// const int
void foo(const int y)
{
    // y = 6; const value
    // can't be change
    cout << y;
}
 // Function foo() with variable int
void foo1(int y)
{
    // Non-const value can be change
    y = 5;
    cout << '\n'
         << y;
}
 // Driver Code
int main()
{
    int x = 9;
    const int z = 10;
      foo(z);
    foo1(x);
  return 0;
}
```
### For const return type:
 The return type of the function() is const and so it returns a const integer value to us. Below is the C++ program to implement the above approach: 
 ```
// C++ program for the above approach
#include <iostream>
using namespace std;
 const int foo(int y)
{
    y--;
    return y;
}
 int main()
{
    int x = 9;
    const int z = 10;
    cout << foo(x) << '\n'
         << foo(z);
    return 0;
}
```
### For const return type and const parameter:
 Here, both return type and parameter of the function are of const types. Below is the C++ program to implement the above approach:
 ```
// C++ program for the above approach
#include <iostream>
using namespace std;
 const int foo(const int y)
{
    // y = 9; it'll give CTE error as
    // y is const var its value can't
    // be change
    return y;
}
 // Driver code
int main()
{
    int x = 9;
    const int z = 10;
    cout << foo(x) << '\n'
         << foo(z);
    return 0;
}
```
# operator &
## AND
A bitwise AND takes two binary representations of equal length and performs the logical AND operation on each pair of corresponding bits. For each pair, the result is 1 if the first bit is 1 AND the second bit is 1; otherwise, the result is 0.
For example:
    0101 (decimal 5)
AND 0011 (decimal 3)
  = 0001 (decimal 1)
## Compound assignment (&=)
Compound assignment operators modify the current value of a variable by performing an operation on it. They are equivalent to assigning the result of an operation to the first operand

## The logical operators && ;
used when evaluating two expressions to obtain a single relational result. The operator && corresponds to the Boolean logical operation AND, which yields true if both its operands are true, and false otherwise.
```
if ( (i<10) && (++i<n) ) { /*...*/ }   // note that the condition increments i 
```
## The & (address) operator:
 yields a pointer to its operand. The operand must be an lvalue, a function designator, or a qualified name. It cannot be a bit field, nor can it have the storage class register.

If the operand is an lvalue or function, the resulting type is a pointer to the expression type. For example, if the expression has type int, the result is a pointer to an object having type int.

If the operand is a qualified name and the member is not static, the result is a pointer to a member of class and has the same type as the member. The result is not an lvalue.

If p_to_y is defined as a pointer to an int and y as an int, the following expression assigns the address of the variable y to the pointer p_to_y :
```
p_to_y = &y;
```
C++ Beginning of C++ only.

The ampersand symbol & is used in C++ as a reference declarator in addition to being the address operator. The meanings are related but not identical.
```
int target;
int &rTarg = target;  // rTarg is a reference to an integer.
                      // The reference is initialized to refer to target.
void f(int*& p);      // p is a reference to a pointer
```
If you take the address of a reference, it returns the address of its target. Using the previous declarations, &rTarg is the same memory address as &target.
You may take the address of a register variable.

You can use the & operator with overloaded functions only in an initialization or assignment where the left side uniquely determines which version of the overloaded function is used.
