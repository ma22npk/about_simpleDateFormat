# about_simpleDateFormat
【Java】のSimpleDateFormatについて学んだことのアウトプットです。
<!-- タイトル -->
# 【タイトル】SimpleDateFormat
日時フォーマットの変換をする。

<!-- 説明 「〜〜とはなど」-->
## 【説明】

SimpleDateFormatクラスは、日付と時刻のフォーマット（書式）を扱う[クラス]です。

## 【使用場面】

- 年や月といったデータを処理中で使用したい場合
- ライブラリを使用する際、所定の形式へ変換する必要がある場合
- 日付操作の表示を任意で決めたいとき

[Calendar] 、[Date]、[Time] の日付や数値に代入された、「 **日付・時刻形式データを、任意の日付・時刻フォーマットに変換する** 」クラスとして重宝します。

<!-- 基本構文など -->
## 【書き方】
まずはこちらをJavaファイルの上部の[パッケージ]宣言の後に記述して[インポート]します。

```java
import java.text.SimpleDateFormat;
```

宣言後、下記の形式でフォーマットを指定します。(書式とパターンは後述)

```
SimpleDateFormat オブジェクト名 = new SimpleDateFormat(”フォーマットパターン”)
```

こちらは `SimpleDateFormat` で使用する **書式** と **パターン** をまとめたものになります。
こちらのアルファベットを用いてフォーマットを作成していきます。

| 書式 | 概要                | パターン          | 表示               | 
| ---- | ------------------- | ----------------- | ------------------ | 
| G    | 紀元                | G                 | AD                 | 
| y    | year, 年            | yyyy<br>yyy       | 2020<br>20         | 
| M    | Month, 月           | MM<br>MMM<br>MMMM | 03<br>Mar<br>March | 
| d    | day, 日             | d<br>dd           | 1<br>01            | 
| H    | 時(0-23)            | H<br>HH           | 0<br>00            | 
| K    | 午前/午後の時(0-11) | K<br>KK           | 0<br>00            | 
| h    | 午前/午後の時(1-12) | h<br>hh           | 1<br>01            | 
| m    | 分                  | m<br>mm           | 0<br>00            | 
| s    | 秒                  | s<br>ss           | 0<br>00            | 
| S    | ミリ秒              | S<br>SSS          | 1<br>001           | 
| z    | タイムゾーン        | z                  |Pacific Standard Time, PDT, GMT-08:00  | 
| Z    | タイムゾーン         | Z                 | -0800                | 


<!-- ここから キャプチャー -+-+-+-+-+-+-+ -->
<!-- キャプチャータイトル -->
## java.text.SimpleDateFormatクラスのメソッド

SimpleDateFormat を使用する時に扱うメソッドの紹介です。

### 【説明】
SimpleDateFormat のメソッドの一例です。

- setTimeZone (タイムゾーンを設定)
- format (指定されたDateを日付文字列にフォーマットする)
- parse (文字列から解析してDateオブジェクトを生成)

その中でも特に重要な `formatメソッド`について少し触れます。

## formatメソッド

指定されたDateを日付文字列にフォーマットする[メソッド]。

### 【説明】

SimpleDateFormat を扱う上で最もメインとなる、**「日時を設定したフォーマットの文字列へ変換する**」[メソッド]です。

## 【書き方】

```
SimpleDateFormatのオブジェクト名.format(日時を格納した変数名)
```
出力するときなどはこのような使い方です、

```java
System.out.println(sdf.format(date));
```



<!-- ここから サンプルコード ★☆★☆★☆★☆★ -->
<!-- サンプルコードタイトル -->
### 【サンプルコード】 

<!-- サンプルコード概要 -->

<!-- サンプルコード -->
```java
// ① ここで SimpleDateFormat と Dateをインポート
import java.text.SimpleDateFormat;
import java.util.Date;

public class MainSimpleDateFormat {

    public static void main(String[] args) {

        // ② 現在時刻を取得してくる値を 変数 date に格納
        Date date = new Date();
        // SimpleDateFormat をオブジェクト化し、任意のフォーマットを設定
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy年 MM月 dd日");
        // フォーマット指定なし
        System.out.println(date);
        // フォーマット指定あり
        System.out.println(sdf.format(date));
    }
}
```
<!-- 実行結果 -->
#### 【実行結果】

```
Sun Nov 29 20:11:31 JST 2020
2020年 11月 29日
```
<!-- サンプルコード説明があればここに記述 -->

<!-- ここまで サンプルコード ★☆★☆★☆★☆★ -->

<!-- ここまで  キャプチャー -+-+-+-+-+-+-+ -->


<!-- ここから サンプルコード ★☆★☆★☆★☆★ -->
<!-- サンプルコードタイトル -->
### 【サンプルコード】 現在日付をyyyyMMdd形式の文字列で取得する

現在日付をyyyyMMdd形式で取得するサンプルです。

<!-- サンプルコード -->
```java
// ① ここでSimpleDateFormat と Calendarをインポート
import java.text.SimpleDateFormat;
import java.util.Calendar;

public class MainSimpleDateFormat {

    public static void main(String[] args) {

        // ② Calendarをオブジェクト化
        Calendar cl = Calendar.getInstance();

        // ③ SimpleDateFormat のパターンを任意で設定する。
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy年 MM月 dd日");
        // ④ 文字列 str に SimpleDateFormat で整形した 日時 を格納する。
        String str = sdf.format(cl.getTime());
        // ⑤strを出力する
        System.out.println(str);
    }
}
```
<!-- 実行結果 -->
#### 【実行結果】

```
2020年 11月 29日
```
<!-- サンプルコード説明があればここに記述 -->

<!-- ここまで サンプルコード ★☆★☆★☆★☆★ -->



<!-- ここまで 各キャプチャー△▽△▽△▽△▽△▽△▽△▽△▽△ -->

<!-- まとめ -->
## 【まとめ】

<!-- 参考にした資料のリンクを貼る -->
## 参考文献・記事

- [【Java入門】SimpleDateFormatで日付フォーマットの設定](https://www.sejuku.net/blog/20994)
- [java.text.SimpleDateFormat](http://itref.fc2web.com/java/text/simpledateformat.html)

<!-- 以下リンク -->

[Time]:https://qiita.com/takahirocook/items/9caef0bb2409caedba55
[Calendar]:https://qiita.com/takahirocook/items/204dd7331db777eb6f3b
[日付操作]:https://qiita.com/takahirocook/items/9caef0bb2409caedba55
[Progate]:https://prog-8.com/
[ドットインストール]:https://dotinstall.com/
[インスタンス]:https://qiita.com/takahirocook/items/ec01cdcbb440cf0d1cc4
[インスタンス化]:https://qiita.com/takahirocook/items/ec01cdcbb440cf0d1cc4
[アクセス修飾子]:https://qiita.com/takahirocook/items/e51b0b9d37d95ad587fe
[フィールド]:https://qiita.com/takahirocook/items/28df75a133049a74ece1
[フィールド変数]:https://qiita.com/takahirocook/items/28df75a133049a74ece1
[new演算子]:https://qiita.com/takahirocook/items/00f9f97592bf50831d39
[new]:https://qiita.com/takahirocook/items/00f9f97592bf50831d39
[カプセル化]:https://qiita.com/takahirocook/items/e469a7c0539a0012868e
[クラス]:https://qiita.com/takahirocook/items/50cbbdca8e21539170e9
[メソッド]:https://qiita.com/takahirocook/items/5bfe43576d87a2a4006c
[mainメソッド]:https://qiita.com/takahirocook/items/f4635915337303de338c
[メソッドの呼び出し]:https://qiita.com/takahirocook/items/f4635915337303de338c
[コンストラクタ]:https://qiita.com/takahirocook/items/fa1822f2f22c3786593e
[引数]:https://qiita.com/takahirocook/items/5e5b0ba79e869f4a592e
[戻り値]:https://qiita.com/takahirocook/items/3b6fa670a1d6dd4a9386
[this]:https://qiita.com/takahirocook/items/d251ec4693c68f6b9538
[getter・setter]:https://qiita.com/takahirocook/items/27828bc8477735612021
[setter]:https://qiita.com/takahirocook/items/27828bc8477735612021
[getter]:https://qiita.com/takahirocook/items/27828bc8477735612021
[オブジェクト指向]:https://qiita.com/takahirocook/items/041ba7a096b71ab8ffd4
[継承]:https://qiita.com/takahirocook/items/6c84ea66a6e2ad536a37
[オーバーライド]:https://qiita.com/takahirocook/items/09dd8e5f56d6617ce45a
[オーバーロード]:https://qiita.com/takahirocook/items/b937c3c07126fe7e02a4
[this]:https://qiita.com/takahirocook/items/d251ec4693c68f6b9538
[super]:https://qiita.com/takahirocook/items/75a07131e7e791c8442c
[スーパークラス]:https://qiita.com/takahirocook/items/75a07131e7e791c8442c
[final]:https://qiita.com/takahirocook/items/5e0916d9bf28bcf68d0c
[final修飾子]:https://qiita.com/takahirocook/items/5e0916d9bf28bcf68d0c
[定数]:https://qiita.com/takahirocook/items/5e0916d9bf28bcf68d0c
[static修飾子]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[static]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[インスタンスフィールド]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735

[インスタンス変数]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[動的メソッド]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[インスタンス変数]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[静的メソッド]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[クラスメソッド]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[静的メソッド]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[クラスフィールド]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[クラス変数]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[静的変数]:https://qiita.com/takahirocook/items/cf527f85d17a5af86735
[インターフェイス]:https://qiita.com/takahirocook/items/ca84be8dfef664b19194
[インターフェース]:https://qiita.com/takahirocook/items/ca84be8dfef664b19194
[パッケージ]:https://qiita.com/takahirocook/items/39b58d17abcb159ef5c1
[インポート]:https://qiita.com/takahirocook/items/59a8a09cab6a98d3bca2
[import]:https://qiita.com/takahirocook/items/59a8a09cab6a98d3bca2
[配列]:https://qiita.com/takahirocook/items/16a123fb73b30869053b
[配列操作]:https://qiita.com/takahirocook/items/16a123fb73b30869053b
[List]:https://qiita.com/takahirocook/items/4d622fc6f271569783b5
[list]:https://qiita.com/takahirocook/items/4d622fc6f271569783b5
[Map]:https://qiita.com/takahirocook/items/49f46151ecb5e332db32
[map]:https://qiita.com/takahirocook/items/49f46151ecb5e332db32
[set]:https://qiita.com/takahirocook/items/d498329cd26e1500f476
[Set]:https://qiita.com/takahirocook/items/d498329cd26e1500f476
[Date]:https://qiita.com/takahirocook/items/a760e20ef2d9aa5c08fc
[拡張for文]:https://qiita.com/takahirocook/items/470b2858de1a4f99b334
