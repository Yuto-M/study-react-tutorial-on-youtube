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
- formがsubmitされた時のイベントハンドリングは、buttonのonClickではなく、formのonSubmitで指定しないとenterキー押下時のsubmitがハンドリングできない
  - formがsubmitされるとデフォルトでブラウザの更新がかかるため、e.preventDefault()で止める。
- create-react-appして作成される、serviceWorker.jsはassetsファイルのcacheをしてくれる。
- 配列の各要素をreactで記述した際には、それぞれの要素にidをもたせる必要がある。そうしないとreactがどの要素が変更されたかが特定できないため。
https://reactjs.org/docs/lists-and-keys.html#keys
- componentには2パターンあり、container componentとUI componentがある（概念的に）。
  - container componentはUIに関してではなく、dataに関係するcomponent。dataをstateとして保持する関係からclass componentとなる。
  - UI componentは、stateを持たず、dataはcontainer componentのstateをprops経由で受け取る形になる。その受け取ったdataをどのように表現するかのUI部分を担うのが主な役割。function componentとして実装する。
- functional componentでは、propsに自動的にpropsが参照できるわけではないので、引数で受け取ってそれを使用する形になる。
- domをreturnする中でdomの組み立てを実装するのはわかりにくいのでしない方がよい。domの組み立てのようなlogicが関わる部分はdomをreturnする箇所で実装するのではなく、外側でdomを変数として持たせる方がよい。