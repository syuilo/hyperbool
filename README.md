# hyperbool

宇宙線に耐性のある高信頼な論理演算を行うための(ジョーク)ライブラリ。

## Why
通常の真理値は、メモリ上の1bitのデータに過ぎないため、宇宙線などの放射線に脆弱です。
例えば以下のようなコードでも、if文が実行されないという保証はありません。

```ts
const normalBool = false;

if (normalBool) {
  // 宇宙線が normalBool を true に書き換えるかもしれないので、実行されることもある
  console.log('never reached (hopefully)');
}
```

hyperboolを使えば、このような宇宙線の影響を最小限に抑えることができます。

## 超真理値
hyperboolは宇宙線に耐性のある真理値(超真理値)を提供します。

超真理値の実態は通常の真理値の配列で、例えば真を表す超真理値は以下のようなデータとしてメモリに配置されます。

``` ts
[true, true, true, true, true,
 true, true, true, true, true,
 true, true, true, true, true,
 true, true, true, true, true,
 true, true, true, true, true]
```

超真理値が真であるかどうかは、配列内のtrueである要素の数が、falseである要素の数より多いか否かで決定されます。

仮に宇宙線がメモリに干渉して以下のようにデータが変わったとしても、

``` ts
[true, true, true, true, true,
 true, true, true, true, true,
 true, true, false, true, true,
 true, true, true, false, true,
 true, true, true, true, true]
```

依然 true の方が多いので超真理値としては 真 の状態が保たれます。

偽の扱いも真の場合と同様の考え方です。

## 耐性度
配列の中にどれくらい要素を格納するか設定できます。
当然多ければ多いほど宇宙線への耐性は高まりますが、メモリ使用量が増えます。
