# 裴波那契数列

- 递归风格

```go
func Fibonacci(n uint) uint {
  if n <= 1 {
    return n
  }
  return Fibonacci(n-1) + Fibonacci(n-2)
}
```

- 顺序风格

```go
func Fibonacci(n uint) uint {
  if n <= 1 {
    return n
  }

  var n2, n1 uint = 0, 1

  for i := uint(2); i < n; i++ {
    n2, n1 = n1, n1+n2
  }

  return n2 + n1
}
```

Typescript

```typescript
const fib = (x: number): number => x <= 0 ? 0 : x === 1 ? x : fib(x - 1) + fib(x - 2)
``` 

JavaScript

```js
const fib = (x) => (function sub_fib(a, b) { return x-- > 0 ? sub_fib(b, a+b) : a})(0,1)
```

```js
const fib = (x, a = 0, b = 1) => x > 0 ? fib(x - 1, b, a + b) : a
```

```js
const fib = x => x <= 0 ? 0 : x === 1 ? 1 : fib(x - 1) + fib(x - 2)
```

Lisp

```lisp
(defun fib (n &optional (a 0) (b 1))
  (if (= n 0)
      a
      (fib (- n 1) b (+ a b))))
```

```lisp
(defun fib (n)
  (if (or (= n 0) (= n 1))
      n
      (+ (fib (- n 1)) (fib (- n 2)))))
```

```lisp
(fib 10)
```

Python

- Printing a list of the first 10 Fibonacci numbers, iterative

```python
def fibonacci(n, first=0, second=1):
    for _ in range(n):
        print(first) # side-effect
        first, second = second, first + second # assignment
fibonacci(10)
```

- Printing a list of the first 10 Fibonacci numbers, functional expression style

```python
fibonacci = (lambda n, first=0, second=1:
    "" if n == 0 else
    str(first) + "\n" + fibonacci(n - 1, second, first + second))
print(fibonacci(10), end="")
```

- Printing a list of the first 10 Fibonacci numbers, with generators

```python
def fibonacci(n, first=0, second=1):
    for _ in range(n):
        yield first
        first, second = second, first + second # assignment
print(list(fibonacci(10)))
```

- Printing a list of the first 10 Fibonacci numbers, functional expression style

```python
fibonacci = (lambda n, first=0, second=1:
    [] if n == 0 else
    [first] + fibonacci(n - 1, second, first + second))
print(fibonacci(10))
```

- Printing a list of the first 10 Fibonacci numbers, recursive style

```python
def fibonacci(n):
    if n <= 1:
        return n
    else:
        return fibonacci(n-2) + fibonacci(n-1)

for n in range(10):
    print(fibonacci(n))
```

PHP

- Printing first 10 Fibonacci numbers, using function

```php
function fib(int $n) : int {
    return ($n === 0 || $n === 1) ? $n : fib($n - 1) + fib($n - 2);
}

for ($i = 0; $i <= 10; $i++) echo fib($i) . PHP_EOL;
```

- Printing first 10 Fibonacci numbers, using closure

```php
$fib = function(int $n) use(&$fib) : int {
    return ($n === 0 || $n === 1) ? $n : $fib($n - 1) + $fib($n - 2);
};

for ($i = 0; $i <= 10; $i++) echo $fib($i) . PHP_EOL;
```

- Printing a list with first 10 Fibonacci numbers, with generators

```php
function fib(int $n) {
    yield 0; $n--;
    yield 1; $n--;
    $second = ($first = 2) + 1;
    while ($n-- !== 0) {
        yield $first;
        [$second, $first] = [$first + $second, $second];
    }
}

$fibo = fib(10);
foreach ($fibo as $value) {
    echo $value . PHP_EOL;
}
```

Java

Get Fibonacci number

```java
public UnaryOperator<Integer> fib(Integer acc, Integer incr) {
    return x -> {
        return (x > 0) ? fib(acc + incr, acc).apply(--x) : acc;
    };
}
System.out.println(fib(0, 1).apply(5));
```