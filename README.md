# Nodularity-WebApp
 Web app for determining nodularity of graphite

# 概要
球状黒鉛鋳鉄品（FCD）の組織画像について、JIS G5502-2022 球状黒鉛鋳鉄品のISO法およびJIS法によって黒鉛球状化率を求めるプログラムです。ここで、組織画像とは下図のようなものです。

<img src="https://github.com/repositoryfiles/Nodularity-WebApp/assets/91704559/85a59827-c485-40f9-86cf-18aa6775d183.jpg" width="400">

図 球状黒鉛鋳鉄品の組織画像

# 動作環境
インターネットが接続された環境で動作します。このプログラムは実行時に画像処理のライブラリOpenCV Ver.4.4.0を読み込んでいます。

# 使い方
- ISO法の球状化率の測定にはnodularity_ISO.htmlとindex(ISO).jsを使い、JIS法の球状化率の測定にはnodularity_JIS.htmlとindex(JIS).jsを使います。ISO法、JIS法いずれの測定においても、拡張子htmlとjsのファイルは同じフォルダに置きます。
- EdgeやChromeなどのブラウザでnodularity_ISO.htmlまたはnodularity_JIS.htmlを開きます。以下の操作は、nodularity_ISO.html、nodularity_JIS.htmlいずれも同じです。
- 左上に「準備完了」と表示されれば使用可能です。
- 倍率100倍で撮影した組織画像をご用意ください。このURLにあるjpgファイルはテスト用です。
- **ファイルを選択**をクリックして画像ファイルを読み込むと画像が表示されます。
- 読み込んだ画像のパラメータを設定します。**画像の幅**は、組織画像の幅いっぱいにスケールバーを入れたと想定したときの数値をμm単位で入力します。テスト用画像については、**画像の幅**は**1420**となります。

<img src="https://github.com/repositoryfiles/Nodularity-WebApp/assets/91704559/1205c1c6-268d-4cc7-aba1-ed4fce7f25ab" width="400">

図　組織画像の幅いっぱいに入れたスケールバーと数値の例

- **黒鉛の長さ**には黒鉛として認識させる最小の長さ（JIS G5502：2022では10μmとされています）を入力します。
- **球状化率の評価**をクリックすると黒鉛の形状評価の結果が表示され、パラメータの下に「球状化率」の計算結果が表示されます。
- **画像のダウンロード**をクリックすると、形状評価の結果を保存できます。
- htmlファイルを開いたときに表示される画像の幅のデフォルト値（1420）を変えたい場合は、nodularity_ISO.htmlは36行、nodularity_JIS.htmlは37行の1420という数値を変更します。

# 注意事項

1. JIS G5502-2022 では、黒鉛の形状を次式で定義される丸み係数というパラメータで評価しますが
```math
\text{丸み係数} = \frac{\text{黒鉛の面積}}{\text{黒鉛の最大軸長を直径とする円の面積}}　　　(1)
```
&emsp;&emsp;このプログラムでは、式(1)の分母を
```math
\text{丸み係数の近似値} = \frac{\text{黒鉛の面積}}{\text{黒鉛の最小外接円を直径とする面の面積}}　　　(2)
```

&emsp;&emsp;と置いた「丸み係数の近似値」を使って球状化率を評価しています。<br>
&emsp;&emsp;「丸み係数の近似値」から求めた球状化率は「丸み係数」から求めた球状化率に比べて若干低い値になります。<br>
&emsp;&emsp;https://qiita.com/_Moony/items/4a0b84bca07e21f4b0fa

2. JIS G5502-2022の内容を理解の上、お使いください。<br>
3. プログラムの使用結果について当方は責任は負いません。

# 開発環境
- Windows11
- OpenCV.js 4.9.0




