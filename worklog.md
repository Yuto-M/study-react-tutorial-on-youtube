# このドキュメントの目的
作業中に使用したコマンド・気づいた点・覚えておくべきことなどを書き残します。

## 以下項目
- reactライブラリがreactのcoreライブラリ。react-domがreactとdomをつないでくれるライブラリ。
- class based componentはrender()メソッドが必ず必要
- render()メソッドでreturnすることのできるhtml要素は１つのみ。ネストは可能。
- JSXでは、class属性はclassNameで設定。classはjsの予約語なので。
- {} curly brathesを使用すればその中ではjsが書ける
- reactの開発者ツールを使用してcomponentのpropsとstateが確認でき、一時的にデータを変更して表示を確認することもできる
  - reactのマークが青はproductionビルド、赤はdevelopmentビルドされた状態を表す。
- イベントハンドラーのメソッドの中でのthis.stateでthisがcomponentを参照できないのは、jsのthisがどこで書かれているかではなく、どのように呼び出されているかによって決まるため参照できない。ちなみに、render()の中でthisがcomponentを参照できるのは、render()がreactで実装されているbuilt-inメソッドで、reactが内部的に、thisで参照できるように設定しているから。
  - 通常のメソッド指定ではなく、arrow functionを使用してのメソッド呼び出しに変更するとthisでcomponentが指定できるようになる。arrow function内でのthisはthisが書かれている外側を参照するから。
- stateの変更はthis.setStateで{}を引数に渡して行う。stateの一部のプロパティのみを指定して変更することも可能。