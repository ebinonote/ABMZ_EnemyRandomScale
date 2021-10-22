﻿

[RPGツクールMZ](https://tkool.jp/mz/)のプラグインです。


## どんなプラグイン？

敵キャラの大きさをランダムにし、能力値を変化させられるプラグインです。


## 機能



## 敵キャラのメモ：

&lt;scale:x&gt;
大きさをx倍にし、能力値を変化させます。小数点が使えます。
maxScale、minScaleと併用するとscaleが優先されます。

&lt;maxScale:x&gt;
&lt;minScale:y&gt;
大きさをminScale～maxScaleの中のランダムにし、能力値を変化させます。
小数点が使えます。
minScaleを省略するとminScaleは1になります。
maxScaleを省略するとmaxScaleは1になります。


【大きさ決定計算式】
Math.floor(((Math.random()(maxScale - minScale))
 + (Math.random()(maxScale - minScale))) /2*10)/10+minScale

サイコロを2回転がして2で割り、中間の大きさを出やすくしています。
サイコロを3回転がした方が正規分布には近くなりますが、ゲーム的にはいろいろな
パターンを見られた方が楽しいので2回にしました。


## プラグインコマンド


nextEnemyScales 敵キャラ1の大きさ 敵キャラ2の大きさ ... 敵キャラ8の大きさ
  次の戦闘で、敵キャラの大きさを指定します。
  0を指定すると、通常と同じく敵キャラのタグ通りになります。
  引数を省略すると0になります。
  設定した大きさは戦闘が終了するとリセットされます。

例）
nextEnemyScales 2.5 0 1
  次の戦闘で、敵キャラの大きさを、敵キャラ1は2.5倍、敵キャラ2は通常通り、
  敵キャラ3は1倍にします。
  敵キャラ4以降は通常通りです。


clearEnemyScales
  次の戦闘の敵キャラの大きさの設定をリセットします。


## デフォルトの計算式の意図の説明


【HPの計算式、MPの計算式】
valueMath.pow(scale, 3)

幅、高さ、奥行きがscale倍になっているので、体積はscaleの3乗倍になります。
体が大きくなった分HPもscaleの3乗倍にしてしまおうという計算式です。

【参考】HPがデフォルトの計算式の場合のscaleごとのHPの倍率
scale    HP
1.0  ：1.000倍
1.1  ：1.331倍
1.2  ：1.728倍
1.3  ：2.197倍
1.4  ：2.744倍
1.5  ：3.375倍
1.6  ：4.096倍
1.7  ：4.913倍
1.8  ：5.832倍
1.9  ：6.859倍
2.0  ：8.000倍


## 更新履歴


### Version 1.00
  公開


## 利用規約


・MITライセンスです。
・クレジット表記は不要
・営利目的で使用可
・ソースコードのライセンス表示以外は改変可
・素材だけの再配布も可
・アダルトゲーム、残酷なゲームでの使用も可