# Neuro Brain Visualization

暗い3D空間に半透明の脳メッシュを配置し、内部をニューロン発火（色付き粒子）が絶えず駆け巡るビジュアライゼーション。脳内に散らばった5種類のノード（視覚野・聴覚野・味覚野・海馬・扁桃体）にカーソルを重ねると、そのノードに対応する画像・動画・音がレトロなポップアップ広告のように画面周囲に増殖する。

Three.js を CDN から読み込む単一 HTML ファイル構成。

## 動かし方

`file://` で直接開くとブラウザのセキュリティ制限で脳モデル（`brain_areas/scene.bin`）が読めないため、簡易サーバー経由で開く。

```bash
cd brain-viz
python3 -m http.server 8123
```

ブラウザで <http://localhost:8123> を開く。

- ドラッグ：カメラ回転
- ホイール：ズーム
- ノード（発光する球）にカーソルを重ねる：ポップアップ出現

## 素材の追加

各ノードのフォルダ（`visual/ auditory/ gustatory/ hippocampus/ amygdala/`）に画像（jpg/png/gif）・動画（mp4/webm）・音声（mp3）を入れ、[index.html](index.html) 冒頭の `NODE_TYPES` の `files:` にファイル名を列挙する。素材が無い場合は `[not found]` のプレースホルダで代替される。

## 調整

ノードの配置・色・個数、粒子数、ポップアップの量や回避半径などは、すべて index.html 冒頭の設定ブロックでまとめて編集できる。

## クレジット

3Dモデル "Brain Areas" by [Versal](https://sketchfab.com/versal) — licensed under [CC-BY-4.0](http://creativecommons.org/licenses/by/4.0/).
This work is based on "Brain Areas" (https://sketchfab.com/3d-models/brain-areas-d64608a3978b47d8a39c5a15795ca8c4) by Versal licensed under CC-BY-4.0.
