description: 正しいように見えて、コンパイルエラーになる C++ コードの紹介

# なぜかコンパイルできない

正しいように見えて、コンパイルエラーになるコードの紹介です。

## 添字とラムダ式
```C++
#include <iostream>

int main()
{
	int a[3] = { 10, 20, 30 };

	std::cout << a[[](){ return 1; }()] << '\n';
}
```

## 使えない変数
```C++
#include <memory>

int main()
{
	std::shared_ptr<int> p();

	p.reset();
}
```

## ポインタ型のデフォルト引数
```C++
void Func(int*=nullptr)
{

}

int main()
{
	Func();
}
```

## 関数のオーバーロード

```C++
#include <iostream>

using T = int&;

void f(T&)
{
	std::cout << "A\n";
}

void f(const T&)
{
	std::cout << "B\n";
}

int main()
{
	int x;
	f(x);
}
```
