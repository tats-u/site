# scoped_lock
* mutex[meta header]
* std[meta namespace]
* class template[meta id-type]
* cpp17[meta cpp]

```cpp
namespace std {
  template <class... MutexTypes>
  class scoped_lock;
}
```

## 概要
`scoped_lock`は、複数のミューテックスに対するロック取得と解放を、コンストラクタとデストラクタで確実に実行するためのクラスである。

[`lock_guard`]クラスは単一のミューテックスのみを扱うが、このクラスは複数のミューテックスを一括して管理する。


## メンバ関数

| 名前 | 説明 | 対応バージョン |
|-----------------------------------------------|----------------|-------|
| [`(constructor)`](scoped_lock/op_constructor.md) | コンストラクタ | C++17 |
| [`(destructor)`](scoped_lock/op_destructor.md)   | デストラクタ   | C++17 |
| `operator=(const scoped_lock&) = delete`         | 代入演算子     | C++17 |


## メンバ型

| 名前 | 説明 | 対応バージョン |
|--------------|-------------------------|-------|
| `mutex_type` | ミューテックス型。`MutexTypes...`が単一要素の場合のみ、その別名として定義される | C++17 |


## 例
```cpp example
#include <iostream>
#include <mutex>

int main()
{
  std::mutex m1;
  std::timed_mutex m2;

  {
    // m1とm2のロックを取得
    std::scoped_lock lk{m1, m2};

    // m1のミューテックスで保護されたデータと、
    // m2のミューテックスで保護されたデータを操作・・・

  } // lkのデストラクタによって、m1とm2のロックを解放
}
```
* std::scoped_lock[color ff0000]

### 出力
```
1
2
```

## バージョン
### 言語
- C++17

### 処理系
- [Clang, C++17 mode](/implementation.md#clang): 5.0
- [GCC, C++17 mode](/implementation.md#gcc): 7.3
- [Visual C++](/implementation.md#visual_cpp): ??


## 参照
- [P0156R2 Variadic `lock_guard` (Rev. 5)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0156r2.html)
- [P0739R0 Some improvements to class template argument deduction integration into the standard library](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html)