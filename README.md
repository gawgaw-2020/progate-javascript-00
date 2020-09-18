# Progate JavaScript 学習コース 気になった所をメモ

## 学習コース I
console.logでコンソールに出力  
文字の連結は「+」  
変数は「let 変数名 = 値」として定義 $マークいらない  
更新する時は「let」は必要なく、「変数名 = 新しい値」と書けば値が変更される。  

$マークがないのが違和感

定数はconst PHPに定数があったか曖昧な記憶  
テンプレートリテラルという連結方法は「$」を用いる

```javascript
console.log(`私の名前は${name}です`);
```

if文、比較演算子あたりは同じ

## 学習コース Ⅱ
while,forも同じ

配列が入った定数を出力すると配列が出力される  
``配列.length``とすると配列の要素数を取得できる。  

オブジェクトは{}  
プロパティ:値  
オブジェクト.プロパティで値を取り出せる  

オブジェクトを要素に持つ配列を作ることができる  

存在しない要素のインデックス番号を指定したり、  
存在しないオブジェクトのプロパティを指定すると「undefined」と出力される

## 学習コース Ⅲ

関数の定義

```javascript
const greet = function() {
  console.log('ボンジョルノ');
}
```
```javascript
const greet = () => {
  console.log('ボンジョルノ');
}
```

引数や戻り値のイメージはPHPと同じ

## 学習コース Ⅳ

オブジェクトの「値」の部分には、関数を用いることができる  
定数名.プロパティ名()で呼び出し  

```javascript
const animal = {
  name: 'レオ',
  age: 3,
  greet: () => {
    console.log("こんにちは");
  }
};
```

クラスやコンストラクタなどの言葉も同じ  
考え方は同じ  

コンストラクタをオーバーライドする際は1行目に「super()」と記述する必要がある。  
parent::__constructみたいなイメージ？？

## 学習コース Ⅴ

ファイルからの読み込みと他のファイルへ値を渡す  
``export default Animal;``  
``import Animal from './animal';``

エクスポートできるのはクラスだけではなく、文字列や数値や関数など、どんな値でもエクスポートが可能。

export defaultはデフォルトエクスポートと呼ばれ、そのファイルがインポートされると自動的に「export default 値」の値がインポートされるので、そのためエクスポート時の値の名前と、インポート時の値の名前に違いがあっても問題無し。

**デフォルトエクスポートは1ファイル1つの値のみ**

複数の値をエクスポートしたい場合は、defaultを書かずに、名前を{}で囲んでエクスポートする名前付きエクスポートにする。

インポートする場合は、エクスポート時と同じ名前で値を指定。インポートする値は、エクスポート時と同様に、「import { 値の名前 } from "./ファイル名"」と{}で囲んで指定する。

## JavaScript 学習コース VI

配列の中の要素を引数として、1つずつ取り出して処理を行っている  
```javascript
characters.forEach((character) => {
   console.log(character);
});
```

filterメソッド
条件に当てはまった要素で新しい配列を返す
```javascript
const numbers = [1, 2, 3, 4];
const evenNumbers = numbers.filter((number) => {
  return number % 2 === 0;
});


const characters = [
  {id: 1, name:"にんじゃわんこ", age: 14},
  {id: 2, name:"ベイビーわんこ", age: 5},
  {id: 3, name:"ひつじ仙人", age: 100}
];
const underTwenty = characters.filter((character) => {
  return character.age < 20;
});
```

mapメソッド
全ての配列に対して同じ処理をして新しい配列を返す
```javascript
const numbers = [1, 2, 3, 4];
const doubledNumbers = numbers.map((number) => {
  return number * 2;
});


const names = [
  {firstName: "Kate", lastName: "Jones"},
	{firstName: "John", lastName: "Smith"},
	{firstName: "Denis", lastName: "Williams"},
	{firstName: "David", lastName: "Black"}
];
const fullNames = names.map((name) => {
  return name.firstName + name.Lastname;
});
```

今のところ何がコールバックなのかわからない


## JavaScript 学習コース Ⅶ
引数に関数が渡せる

```javascript

const printWanko = () => {
  console.log("にんじゃわんこ");
};

const call = (callback) => {
  console.log("コールバック関数を呼び出します。");
  callback();
};

call(printWanko);

```

引数の中で直接関数を定義できる

```javascript
const call = (callback) => {
  console.log("コールバック関数を呼び出します。");
  callback();
};

call(() => {
  console.log("ひつじ仙人");
});
```

コールバック関数は引数を渡すことができる（複数可）

```javascript
const call = (callback) => {
  callback("にんじゃわんこ", 14);
};

call((name, age) => {
  console.log(`${name}は${age}歳です。`);
});
```

呼び出す方向が変化するからコールバック関数