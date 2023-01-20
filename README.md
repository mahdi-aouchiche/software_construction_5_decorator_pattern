# Software Construction: Decorator Pattern

> Author: Mahdi Aouchiche (<https://github.com/mahdi-aouchiche/software_construction_5_decorator_pattern>)

* Extending the system created in the Composite and Strategy Pattern labs.
* Use the decorator pattern to modify both the `evaluate()` and `stringify()` functions previously implemented in the expression tree. For example, to round the results of an expression (or the results of the subset of an expression) so you may create an expression like the following:

```code
ceil(3 + 7 * 4 - 2)
```

This expression would be represented with the following tree, with the top most node being a decorator:

![Equation tree for Decorator Pattern](https://github.com/cs100/lab05-decoratorPattern/blob/master/images/decorator.png)

* See how the ceiling function simply modifies the return of the statement, and that the return value at the top would be the ceiling of the equation below which it should transparently enclose. Build four separate decorator classes, three of which modify the `evaluate()` function and one which modifies the `stringify()` function.

* Evaluate Modifying Decorators:
  * Ceiling (`Ceil` class): performs the `ceil()` function on whatever composite it encloses and returns that value.
  * Floor (`Floor` class): performs the `floor()` function on whatever composite it encloses and returns that value.
  * Absolute value (`Abs` class): performs the `abs()` function on whatever compsite it encloses and returns that value.

* Stringify Modifying Decorators:
  * Truncate (`Trunc` class): shortens the expression tree so that whatever compsite it encloses will report its `evaluation()` value as its `stringify()` return rather than the full expression. Ex: The tree `5+Trunc(7-4)` would `stringify()` to `5+3` if called on the root node.
  * Parenthesies (`Paren` class): adds parenthesies before and after whatever composite it encloses. Ex: the tree `5+Paren(7-4)` would `stringify()` to `5+(7-4)` if called on the root node.

* In order to make this system extensible and save time from writing a lot of code, create a decorator base class that all of the above classes inherit from. To implement the functionality of the evaluate modifying decorators you may employ the cmath library (`math.h`).

> Note: It is important to not only test the decorator classes in combination with the composite pattern classes that have previously developed but also test the decorator objects so that they capable of working with each other as composability is an important aspect of the pattern. All the decorators should be able to not only enclose every composite pattern class but should also be able to enclose each other and in any combination.

## To run the project nicely use the following commands

```c++
cmake -S . -B build
cmake --build build/
```

## 6 executables are created, use one of the commands to run an executable

```c++
// composite pattern
./build/composite_tests
./build/composite_pattern
// strategy pattern
./build/strategy_tests
./build/strategy_pattern
// decorator pattern
./build/decorator_tests
./build/decorator_pattern
```
