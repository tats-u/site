# operator-=
* chrono[meta header]
* std::chrono[meta namespace]
* year_month_day[meta class]
* function[meta id-type]
* cpp20[meta cpp]

```cpp
constexpr year_month_day& operator-=(const months& m) noexcept; // (1) C++20
constexpr year_month_day& operator-=(const years& y) noexcept;  // (2) C++20
```

## 概要
`year_month_day`の値に対して減算の複合代入を行う。

- (1) : 月の時間間隔を減算する
- (2) : 年の時間間隔を減算する

パラメータの型が、カレンダー時間の[`month`](/reference/chrono/month.md)、[`year`](/reference/chrono/year.md)ではなく、時間間隔を表す[`months`](/reference/chrono/duration_aliases.md)、[`years`](/reference/chrono/duration_aliases.md)であることに注意。


## 効果
- (1) : `*this = *this + m`
- (2) : `*this = *this + y`


## 戻り値
- (1), (2) : `*this`


## 例外
投げない


## 例
```cpp example
#include <iostream>
#include <chrono>

namespace chrono = std::chrono;
using namespace std::chrono_literals;

int main()
{
  chrono::year_month_day date = 2020y/3/1;

  date += chrono::months{1}; // 1ヶ月進める
  date += chrono::years{1};  // 1年進める

  std::cout << date << std::endl;
}
```
* 2020y[link /reference/chrono/year/op_y.md]

### 出力
```
2021-04-01
```

## バージョン
### 言語
- C++20

### 処理系
- [Clang](/implementation.md#clang): 8.0
- [GCC](/implementation.md#gcc): (9.2時点で実装なし)
- [Visual C++](/implementation.md#visual_cpp): (2019 Update 3時点で実装なし)
