# VR TARGET RUSH

公開URL: https://kou1030.github.io/vr-target-rush/

A-Frameで制作した、30秒間の視線操作VR射的ゲームです。外部キャラクター・画像・音源・3Dアセットは使用していません。

## 操作方法

1. iPhoneのSafariで公開URLを開き、画面回転ロックを解除して横向きにします。
2. 「Cardboardで遊ぶ」を押し、求められた場合は動作・方向センサーを許可します。
3. 左右分割を確認し、Google Cardboardにセットします。
4. STARTを1秒見つめると開始。頭を動かし、中央の照準を的に1秒合わせます。照準を外すと待ち時間がリセットされます。
5. 中心10点、中間5点、外側1点。3個の的が出現し、命中した的は別の空き位置に再出現します。
6. 30秒後に合計得点を表示。少し下の「LOOK TO RESTART」を1秒見つめると再挑戦できます。

PCは「通常画面 / PC」を選び、マウスをドラッグして視点を変えます。クリックで得点する機能はなく、PCでも1秒の注視を使います。「設定へ戻る」または別タブへの移動はプレイを終了します。

## 起動・公開方法

ゲーム本体はindex.htmlのみ。npm・ビルドは不要です。A-Frame 1.7.0をCDNから読み込むためインターネット接続が必要です。PCでローカル確認する場合は、このフォルダーで `python -m http.server 8000` を実行して http://localhost:8000 を開きます。スマートフォンのセンサー操作にはHTTPSの公開URLを使用してください。

GitHubの `kou1030/vr-target-rush` のmainブランチ直下にファイルを保存し、Settings → Pages → Deploy from a branch → main → / (root) → Saveで公開します。更新後はPagesのデプロイ完了を待ち、ブラウザーを再読み込みします。

## VR表示の実装と制限

A-Frameのlook-controlsで視点を操作し、cursor / raycasterで中央方向への注視を判定します。WebXRが不要な左右分割レンダリングを実装し、A-Frame同梱のThree.js StereoCameraを使用しています。眼間距離は既定値64mm、左右それぞれに異なる視点を描画します。HUDと照準は3D空間で描画するため左右両方に表示されます。

Cardboard SDKのレンズ歪み補正・QRプロファイル・個人別IPD調整は実装していません。iPhone実機、Safariのセンサー許可、頭部追従、実際のCardboardレンズでの快適さは未検証です。画面全体表示はブラウザーの対応範囲に依存します。二重像などが気になる場合は使用を中止してください。

## ファイル

- index.html: ゲーム本体
- README.md: 操作・起動・公開方法
- report.md: 授業提出用レポート原稿

参考: [A-Frame look-controls](https://github.com/aframevr/aframe/blob/v1.7.0/src/components/look-controls.js)、[Three.js StereoCamera](https://threejs.org/docs/pages/StereoCamera.html)

