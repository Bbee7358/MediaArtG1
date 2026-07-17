# MediaArt UI2 revised

`index.html` を Chrome または Edge で開いてください。メイン版と同じ実脳モデルはページ内へ埋め込まれているため、ローカルで直接開いても表示されます。最初の画面で再生ボタンを押すと、音声と操作が有効になります。

## 5つの分類

- `visual` — 後頭葉（視覚）
- `temporal` — 側頭葉（聴覚・言語・記憶）
- `parietal` — 頭頂葉（身体・空間・接触）
- `frontal` — 前頭葉（行為・制作・失敗）
- `limbic` — 辺縁系／深部（情動）

画面上の座標は「前 = +Z、上 = +Y、右 = +X」です。情動ノードは脳の深部に置かれ、粒子の中継点として表層4カテゴリへ滲む構成です。

## ポップアップ素材の追加

1. 素材を分類別フォルダ（`visual` / `temporal` / `parietal` / `frontal` / `limbic`）へ入れます。
2. `index.html` 内の `POPUP_MEDIA` にファイル名を追加します。

例：`frontal/new-action.mp4` を追加した場合

```js
frontal: [
  'new-action.mp4'
],
```

MP4（H.264映像・AAC音声を推奨）のほか、WebM、JPG、PNG、GIF、MP3、OGG、WAVを使用できます。複数登録した場合は、ポップアップのたびにランダムで1つが選ばれます。

## 操作

- ドラッグ：脳モデルを回転
- ホイール：ズーム
- 色付きノードにカーソルを重ねる：ポップアップを表示

## 現実の脳タッチとの接続

[medeiaart_jissen](https://github.com/Bbee7358/medeiaart_jissen.git) のiPhone ARセンサーとPC WebSocketサーバーに対応しています。画面は起動時に `ws://<表示中のPC>:8787` へ接続し、`touch_event` の接触開始・部位変更・接触終了を既存のポップアップ、音、人体への痕跡エフェクトへ渡します。通信がない場合も従来のマウス操作は使用できます。

1. `medeiaart_jissen/brain-touch-system/pc-dashboard` で `npm install` を一度実行します。
2. 同じフォルダで `npm run server` を実行し、8787番のサーバーを起動します。
3. iPhoneアプリの接続先を `ws://<MacまたはPCのIPアドレス>:8787` にして `Connect` を押します。
4. この `index.html` を開き、左上が `BRAIN TOUCH / READY` になれば接続完了です。

サーバーが別PCにある場合は、表示URLへ `?touchWs=ws://192.168.0.10:8787` のように追加します。通信を使わずマウスだけで確認する場合は `?touchWs=off` を指定します。

現行iPhone版の12ブロックは、模型上の前後・上下・左右を保ったまま次の分類へまとめます。左右は同じ分類でも画面上の発光位置に反映されます。

- `top/side_lower_front_left/right`: `frontal`
- `top_middle_left/right`: `parietal`
- `side_lower_middle_left/right`: `temporal`
- `top/side_lower_back_left/right`: `visual`
- `cerebellum` / `brainstem` / `center`: `limbic`

`limbic` は脳表面の12ブロックへ無理に割り当てず、深部の中継点として表層4分類の反応へ連鎖します。接触候補中は該当位置がぼやけて脈動し、接触確定後にだけ従来のポップアップ、音、軌跡エフェクトが始まります。接触イベントが1.2秒以上届かない場合は、通信断でエフェクトが出続けないよう自動的に接触終了として扱います。

## クレジット

3Dモデル "Brain Areas" by [Versal](https://sketchfab.com/versal) — [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)。

リグ付き人物モデルは Quaternius の [Universal Base Characters](https://quaternius.com/packs/universalbasecharacters.html)（CC0 1.0 Universal）を使用しています。
