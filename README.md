# VR TARGET RUSH

公開URL: https://kou1030.github.io/vr-target-rush/

A-Frameで制作した、30秒間の視線操作VR射的ゲームです。外部キャラクター・画像・音源・3Dアセットは使用していません。

## 操作方法

1. iPhoneのSafariで公開URLを開き、画面回転ロックを解除して横向きにします。
2. 「遊ぶ」を押し、求められた場合は動作・方向センサーを許可します。スマートフォンでは左右分割が自動で選ばれます。
3. 左右分割を確認し、Google Cardboardにセットします。
4. 中央の的に0.25秒照準を合わせ、コルク玉を当てると開始します。照準を外すと待ち時間がリセットされます。
5. 360°の8方向に16個の的が浮かびます。高さと距離に違いがあり、半分は動きます。中心10点、中間5点、外側1点。命中した的は破片に割れ、別の方向に再出現します。
6. 画面上部に残り秒数と現在のスコアが表示されます。30秒後に「TIME UP!」と最終スコアが表示されます。少し下の的を撃つと再挑戦できます。

PCは「遊ぶ」を押し、マウスをドラッグして視点を変えます。PCでも的に照準を0.25秒合わせると発射します。左上の戻るアイコンまたは別タブへの移動はプレイを終了します。PCで左右分割を確認するときはURL末尾に `?mode=cardboard` を追加します。スマートフォンで通常画面を使う場合は `?mode=normal` を追加します。

## 起動・公開方法

ゲーム本体はindex.htmlのみ。npm・ビルドは不要です。A-Frame 1.7.0をCDNから読み込むためインターネット接続が必要です。PCでローカル確認する場合は、このフォルダーで `python -m http.server 8000` を実行して http://localhost:8000 を開きます。スマートフォンのセンサー操作にはHTTPSの公開URLを使用してください。

GitHubの `kou1030/vr-target-rush` のmainブランチ直下にファイルを保存し、Settings → Pages → Deploy from a branch → main → / (root) → Saveで公開します。更新後はPagesのデプロイ完了を待ち、ブラウザーを再読み込みします。

## VR表示の実装と制限

A-Frameのlook-controlsで視点を操作し、cursor / raycasterで中央方向への注視を判定します。発射時の交点で得点を決め、着弾時に加算します。左右分割にはA-Frame同梱のThree.js StereoCameraを使用しています。眼間距離は既定値64 mmで、残り時間、スコア、照準は両眼に表示します。

Cardboard SDKのレンズ歪み補正・QRプロファイル・個人別IPD調整は実装していません。iPhone実機、Safariのセンサー許可、頭部追従、実際のCardboardレンズでの快適さは未検証です。画面全体表示はブラウザーの対応範囲に依存します。二重像などが気になる場合は使用を中止してください。

## ファイル

- index.html: ゲーム本体
- README.md: 操作・起動・公開方法
- report.md: 授業提出用レポート原稿

参考: [A-Frame look-controls](https://github.com/aframevr/aframe/blob/v1.7.0/src/components/look-controls.js)、[Three.js StereoCamera](https://threejs.org/docs/pages/StereoCamera.html)
