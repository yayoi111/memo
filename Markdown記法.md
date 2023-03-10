本記事は、Markdownの記法についてまとめています。

# 見出し

行のはじめに`#`をつけることで見出しの形式になります。
見出しには、見出しの大きさを表すレベルがあり`#`の数が見出しのレベルとなります。レベルは1から6まであります。

`#`の記載の後は、必ず **半角スペースをあけて入力** をすることに注意してください。

``` HTML:example.md
# レベル1
## レベル2
### レベル3
#### レベル4
##### レベル5
###### レベル6
```
出力結果↓
# レベル1
## レベル2
### レベル3
#### レベル4
##### レベル5
###### レベル6
---
# 太字・斜字・打ち消し線
いずれも、記号の中に対象となる文字を囲むことで記載が可能となります。

|            | 記号 |      記入例      |    記入結果    |
| :--------- | ---: | :--------------: | :------------: |
| 太字       |   ** | `**こんにちは**` | **こんにちは** |
| 斜字       |    * |   `*おはよう*`   |   *おはよう*   |
| 打ち消し線 |   ~~ | `~~さようなら~~` | ~~さようなら~~ |

## 折りたたみ
HTMLの詳細折りたたみ要素を使用します。折りたたみをしたい内容は `<details> </details>` で囲みます。折りたたみのタイトルは`<summary> </summary>`
で囲みます。

```HTML:example.md
<details><summary>タイトル</summary>

~~~rb
puts 'Hello World'
~~~
</details>

```


出力結果↓
<details><summary>タイトル</summary>

~~~rb
puts 'Hello World'
~~~
</details>

## 引用
文頭に`>`を入力すると引用になります。改行する場合でも記号が必要になります。 **引用の上下に空行がないと正しく表示されない** ため注意が必要。

~~~
>自分自身を信じてみるだけでいい。
>きっと、生きる道が見えてくる。
>
>[ゲーテ](https://ja.wikipedia.org/wiki/%E3%83%A8%E3%83%8F%E3%83%B3%E3%83%BB%E3%83%B4%E3%82%A9%E3%83%AB%E3%83%95%E3%82%AC%E3%83%B3%E3%82%B0%E3%83%BB%E3%83%95%E3%82%A9%E3%83%B3%E3%83%BB%E3%82%B2%E3%83%BC%E3%83%86 "wikipedia")
>(ドイツの詩人、小説家/ *1749--1832*)
~~~

出力結果↓
>自分自身を信じてみるだけでいい。
>きっと、生きる道が見えてくる。
>
>[ゲーテ](https://ja.wikipedia.org/wiki/%E3%83%A8%E3%83%8F%E3%83%B3%E3%83%BB%E3%83%B4%E3%82%A9%E3%83%AB%E3%83%95%E3%82%AC%E3%83%B3%E3%82%B0%E3%83%BB%E3%83%95%E3%82%A9%E3%83%B3%E3%83%BB%E3%82%B2%E3%83%BC%E3%83%86 "wikipedia")
>(ドイツの詩人、小説家/ *1749--1832*)

## 画像埋め込み
`![代替テキスト](画像のURL "画像タイトル")` を入力すると画像が埋め込めることができます。

```
![花の画像](https://lh3.googleusercontent.com/blogger_img_proxy/ANbyha36LyrxzTm_2DD3DtznBK3ANO1mAgXxyaM6DbXRazhkvc2tX27Ks8-qWApQnC1rWu-Cpplq9wOf8cA5_vNUgA4uByTHWzUnVOWy-Eu8y_yhKx8vMihnror13hRG2pyJ40ZPZQ=s0-d "花のフリー画像")
```
![花の画像]( https://lh3.googleusercontent.com/blogger_img_proxy/ANbyha36LyrxzTm_2DD3DtznBK3ANO1mAgXxyaM6DbXRazhkvc2tX27Ks8-qWApQnC1rWu-Cpplq9wOf8cA5_vNUgA4uByTHWzUnVOWy-Eu8y_yhKx8vMihnror13hRG2pyJ40ZPZQ=s0-d "花のフリー画像")

## 水平線
下記の書き方は、すべて水平線として表示になります。

```
* * *
***
*****
---
------------
```

出力結果 ↓
* * *
***
*****
---
------------

## 補足説明
```
:::note info
Tips
:::

:::note warn
注意
:::

:::note alert
警告
:::

```
出力結果 ↓

:::note info
Tips
:::

:::note warn
注意
:::

:::note alert
警告
:::

# リスト

## 順序なしリスト

* 行の文頭文頭に`*` ,`+`, `-`のいずれかを入力すると順序なしリストが作成できます。
* ただし、`*` ,`+`, `-` の後には **半角スペース** が必要になります。
  
## 番号付きリスト 
1. 行の文頭に `数字.(コンマ)` を入力すると番号付きのリストになります。
2. `数字.`の後には、半角スペースが必要です。

3. ネストする場合は、**段落と同じ数のスペースが必要**。
   1.  記載例では、リストの段落が3つあるので半角スペースが3つ必要となります。

## 説明リスト
HTMLの `<dl>`タグで囲むことで使用できます。
```HTML:example.md
<dl>
    <dt>記入例A</dt>
    <dd>こんにちは</dd>
    <dt>記入例B</dt>
    <dd>さようなら</dd>
</dl>
```
出力結果↓
<dl>
    <dt>記入例A</dt>
    <dd>こんにちは</dd>
    <dt>記入例B</dt>
    <dd>さようなら</dd>
</dl>

:::note 
説明リスト内ではHTMLタグを用いて強調などの修飾をおこなう。
:::

<dl>
    <dt>記入例C</dt>
    <dd><strong>おはようございます</strong> </dd> 
</dl>

## チェックボックス
順序なしリストの記述の後ろに `
[ ]`を入れるとチェックボックスが生成されます。チェックを入れるには `[x]`と入力をします。
* [ ] 数学 30 min
* [x] 国語 30 min

## コードの挿入

### コードブロック
`~`もしくは、`` ` ``を行頭に3つ記載し、囲むことで使用可能。

```
~~~ruby:example.rb
puts 'Hello World!'
~~~
```

出力結果 ↓

```ruby:example.rb
puts 'Hello World!'
```

#### コードスパン内でバッククオートを使う

コードスパン内でバッククオートをn個使いたい場合は、コードスパンのクオートを n+1 個 で囲む 

```記入例
`` `バッククオート` ``を2個入力することで使用可能となります。
```
出力結果 ↓
`` `バッククオート` ``を2個入力することで使用可能となります。

#### 差分
文頭に `-`, `+`を記入することで差分が表現できる。
```diff_ruby
- puts 'Hello World'

+ puts 'Hoge Hoge'
```

#### コードスパンの中身がCSSの `<color> ` 型の場合 

```記入例

`#ffffff`
```

出力結果 ↓
`#ffffff`
