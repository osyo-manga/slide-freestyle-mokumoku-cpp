# 最近の C++ 事情

[第33回【フリースタイル】PORTもくもく会【学生歓迎！】](https://freestyle-mokumoku.connpass.com/event/68385/)  
([@pink_bangbi](https://twitter.com/pink_bangbi))  
2017/10/21


---

# 自己紹介

* なまえ  : おしょー
* Twitter : [@pink_bangbi](https://twitter.com/pink_bangbi)
* github  : [osyo-manga](https://github.com/osyo-manga)
* ブログ  : [Secret Garden(Instrumental)](http://secret-garden.hatenablog.com)
* 言語    : C++ / Ruby
* エディタ: Vim

---

# おねがい

* プロ C++er の方は石を投げないでください

---

# 今回話す内容

---

# 最近の C++ 事情

---

### 内容

- - -

* C++ の歴史          <!-- .element: class="fragment" -->
* コンパイラ事情      <!-- .element: class="fragment" -->
* 最新の言語機能紹介  <!-- .element: class="fragment" -->

---

# C++ とは

---

### C++ とは
- - -

C言語の拡張として開発された言語  
クラス、仮想関数、多重継承、テンプレート、例外処理などの機能が追加された  
手続き型プログラミング・データ抽象・オブジェクト指向プログラミング・ジェネリックプログラミングなど、複数のプログラミングパラダイムを組み合わせている

---

# つまりすごい C言語

---

# C++ の歴史

---

### C++ の歴史

- - -

* 1998年 : C++98(最初のバージョン)  <!-- .element: class="fragment" -->
* 2003年 : C++03                    <!-- .element: class="fragment" -->
* 2011年 : C++11                    <!-- .element: class="fragment" -->
* 2014年 : C++14(現行のバージョン)  <!-- .element: class="fragment" -->
* 2017年 : C++17(リリース予定)      <!-- .element: class="fragment" -->
* 2020年 : C++20(リリース予定)      <!-- .element: class="fragment" -->

2011年以降は 3年周期に次のバージョンが策定されている  <!-- .element: class="fragment" -->

---

# コンパイラ事情

---

### コンパイラ事情

- - -

C++ はいくつかの処理系(コンパイラ)によって実装されている  
各処理系やバージョンによって実装されている言語機能が違うので注意する必要がある

---

## 代表的なコンパイラ

- - -

* GCC(最新版 v7.2)                   <!-- .element: class="fragment" -->
  * GNUコンパイラコレクション
  * 最新版では C++17 までの言語仕様を実装済み
* Clang(最新版 v5.0.0)               <!-- .element: class="fragment" -->
  * LLVM の一部として開発されている
  * 最新版では C++17 までの言語仕様を実装済み
* MSVC(Visual Studio 2017 15.4)      <!-- .element: class="fragment" -->
  * 最新版 C++14 の言語仕様は実装済み
  * C++11 と C++17 まだ実装中

詳しくは ↓ ↓ ↓                    <!-- .element: class="fragment" -->

>>>

## 各処理系の言語仕様対応状況

>>>

## GCC(最新版 v7.2)

- - -

* C++11
  * 4.8.1 にて実装完了
* C++14
  * 5.1 にて実装完了
* C++17
  * 7.1 にて現行の言語仕様の実装を完了

>>>

## Clang(最新版 v5.0.0)

- - -

* C++11
  * 3.3 にて実装完了
* C++14
  * 3.4 にて実装完了
* C++17
  * 5.0.0 にて現行の言語仕様の実装を完了

>>>

## MSVC(Visual Studio 2017 15.4)

- - -

* C++11
  * Visual Studio 2015 にてだいたい実装済み
  * 最新版でも全ての機能は未対応
* C++14
  * Visual Studio 2017 にて実装完了
* C++17
  * Visual Studio 2015 から対応開始
  * Visual Studio 2017 15.4 にて対応中

>>>

MSVC はバージョンによって実装している機能がバラバラなので正直 よくわからん！！

>>>

C++ の最新の言語機能を使いたい場合は
処理系やバージョンによって使用できる機能が異なるので事前に調べてください

---

# 最新の言語機能紹介

---

## [nullptr(C++11)](https://cpprefjp.github.io/lang/cpp11/nullptr.html)

---

### [nullptr(C++11)](https://cpprefjp.github.io/lang/cpp11/nullptr.html)
- - -

C++11 からは `NULL` や `0` の代わりに `nullptr` というキーワードが追加された  

```cpp
// C++03
int* p = NULL;

// C++11
int* p2 = nullptr;

int a = 42;
// NULL は 0 として定義されているのでこういう比較ができてしまう
if( a == NULL ){ /* ... */ }

// nullptr はポインタ型でのみ比較するのでこれはエラーになる
if( a == nullptr ){ /* ... */ }
```


---

### [非静的メンバ変数の初期化(C++11)](https://cpprefjp.github.io/lang/cpp11/non_static_data_member_initializers.html)

---

### [非静的メンバ変数の初期化(C++11)](https://cpprefjp.github.io/lang/cpp11/non_static_data_member_initializers.html)
- - -

C++11 では非静的メンバ変数の定義時に初期値を設定できる

```cpp
struct person{
    // メンバ変数の定義時に初期値が設定できる
    std::string name = "homu";
    int age = 14;
};

person p;

assert(p.name == "homu");
assert(p.age  == 14);
```

---

## [初期化リスト(C++11)](https://cpprefjp.github.io/lang/cpp11/initializer_lists.html)

---

### [初期化リスト(C++11)](https://cpprefjp.github.io/lang/cpp11/initializer_lists.html)
- - -

C++11 では波括弧`{}` によりリストを初期化する事が出来る

```cpp
// 従来の配列の初期化
int array[] = {1, 2, 3, 4, 5};

// C++11 では配列と同じような感じで初期化することができる
std::vector<int> v = {1, 2, 3, 4, 5};

// std::map もこんな感じで初期化できる
std::map<int, std::string> table = {
    {1, "homu"},
    {2, "mami"},
    {3, "mado"},
};
```

---

## [std::stringリテラル(C++14)](https://cpprefjp.github.io/reference/string/basic_string/op_s.html)

---


## [std::stringリテラル(C++14)](https://cpprefjp.github.io/reference/string/basic_string/op_s.html)
- - -

C++14 では文字列を `std::string` として定義するためのリテラルが追加された。

```cpp
#include <string>

// s リテラルを使うための下処理
using namespace std::literals::string_literals;

// 文字列に s リテラルを追加することで
// std::string として扱われる
// str は std::string 型
auto str = "homu"s;

assert(str + str == "homuhomu");
```

---

## 型推論

---

### 型推論

- - -

C++11 以降では `auto` というキーワードを使用して型を推論する事が出来る

>>>

### 型推論 - [変数定義(C++11)](https://cpprefjp.github.io/lang/cpp11/auto.html)
- - -
C++11 では変数定義時に右辺値から型を推論して変数型を定義することが出来る

```cpp
// 右辺値から型を推論して定義する
// この場合 n は int 型になる
auto n = 42;

// c は char 型
auto c = 'X';

// 右辺値から型を推論するのでこういう書き方は出来ない
auto m;		// Error

std::vector<int> v;
// このように長い型を定義する場合に便利
// std::vector<int>::iterator it = v.begin();
auto it = v.begin();
```

>>>

### 型推論 - [戻り値型(C++14)](https://cpprefjp.github.io/lang/cpp14/return_type_deduction_for_normal_functions.html)
- - -
C++14 では戻り値型を推論することも出来る

```cpp
auto
range1_5(){
	std::vector<int> result{1, 2, 3, 4, 5};
	return result;
}


template<typename T, typename U>
auto
plus(T a, U b){
	return a + b;
}
assert(plus(1, 2) == 3);
assert(plus(std::string("homu"), "mami") == "homumami");
```

---

## ラムダ式

---

### [ラムダ式(C++11)](https://cpprefjp.github.io/lang/cpp11/lambda_expressions.html)
- - -

C++11 で無名関数を定義するための構文が新しく追加された

```cpp
// [キャプチャする変数](引数型) -> 戻り値型 { 関数の中身 }
auto plus = [](int a, int b) -> int {
	return a + b;
};

// クロージャっぽいもの
int count = 0;
auto counter = [count]() mutable -> int {
	return count++;
};
assert(counter() == 0);
assert(counter() == 1);
assert(counter() == 2);
```

>>>

### [多相ラムダ(C++14)](https://cpprefjp.github.io/lang/cpp14/generic_lambdas.html)
- - -

C++14 では引数に `auto` を使って型推論出来るようになった

```cpp
// 引数型を auto にすることで型推論される
// 戻り値型も省略可能（戻り値型の省略は C++11 でも一部可能）
auto plus = [](auto a, auto b){
    return a + b;
};

assert(plus(1, 2) == 3);
assert(plus("homu"s, "mami") == "homumami");
```

---

## [範囲for文(C++11)](https://cpprefjp.github.io/lang/cpp11/range_based_for.html)

---

### [範囲for文(C++11)](https://cpprefjp.github.io/lang/cpp11/range_based_for.html)
- - -

C++11 では配列やコンテナに対して簡潔に for 文をかけるようになった

```cpp
int xs[] = {1, 2, 3, 4, 5};
// for( 変数定義 : コンテナ（配列） )
for(int x : xs){
	// ...
}

std::vector<int> v{1, 2, 3, 4, 5};
// 変数定義を型推論することも出来る
for(auto n : v){
	// ...
}
```

---

## その他の機能

---

### その他の機能
- - -

* 可変長テンプレート引数型(C++11)
* `constexpr` を使ったコンパイル時処理(C++11)
* 右辺値参照とムーブセマンティクス(C++11)
* スレッドライブラリ`<thread>`(C++11)
* 時間ユーティリティライブラリ`<chrono>`(C++11)
* 正規表現ライブラリ`<regex>`(C++11)
* ファイルシステムライブラリ`<filesystem>`(C++17)
* `constexpr` ラムダ式(C++17)
* `if constexpr` 文(C++17)
* etc...

---

# まとめ

---

### まとめ

- - -

* C++ はいまも進化し続けている
* C++ を使うときはどのコンパイラのどのバージョンなのか確認する
* C++03 の時に比べて言語仕様は増えているが格段に書きやすくなっている
* 今回は言語仕様しか紹介できなかったが標準ライブラリも強化されているので気になる人は調べてみるとよい

---

# C++ は趣味でやると
# とても楽しいので
# みんなやろう

---

# 質問

---

# 便利サイト

* [Wandbox](https://wandbox.org/)
  * オンラインでコードが実行できるサイト
* [cpprefjp - C++日本語リファレンス](https://cpprefjp.github.io/)
  * 日本語で最新の C++ 情報がまとまってる
* [cppreference.com](http://en.cppreference.com/w/)
  * 英語のリファレンスサイト

---

## ご清聴
## ありがとうございました

