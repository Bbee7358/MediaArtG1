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

## クレジット

3Dモデル "Brain Areas" by [Versal](https://sketchfab.com/versal) — [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)。

リグ付き人物モデルは Quaternius の [Universal Base Characters](https://quaternius.com/packs/universalbasecharacters.html)（CC0 1.0 Universal）を使用しています。
