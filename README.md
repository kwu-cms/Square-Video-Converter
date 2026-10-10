# Square Video Converter

GitHub Pagesに公開できる、720×720 MP4（H.264）ブラウザ変換ツールです。

## 公開方法

1. GitHubで新規リポジトリを作成します（例: `square-video-converter`）。
2. このフォルダの `index.html`、`style.css`、`app.js` をリポジトリ直下にアップロードします。
3. Settings → Pages → Build and deployment → Deploy from a branch を選択します。
4. Branch を `main`、フォルダを `/(root)` にして Save を押します。
5. `https://ユーザー名.github.io/square-video-converter/` でアクセスできます。

## 動作

FFmpeg.wasm（シングルスレッド版）をCDNから読み込み、動画をブラウザ内で変換します。元動画データはアップロードされません。初回は約30MB以上のFFmpeg本体のダウンロードが必要です。インターネット接続が必要です。

## 注意

- 大容量・長時間動画はブラウザのメモリ制限で失敗することがあります。
- Chrome / Edge のデスクトップ版を推奨します。
- 出力仕様：720x720, H.264 / yuv420p, 24/30/60fps, 音声削除（既定）またはAAC。
- 入力形式はFFmpeg.wasmのビルドに依存し、一部のMOV等で変換に失敗する可能性があります。
- 外部ライブラリはjsDelivr経由です。オフライン動作はしません。

## 設計

参照デザイン：
- https://kwu-cms.github.io/EZSignNFC-caption-generator/
- https://kwu-cms.github.io/url-slideshow/

利用コンポーネント：[@ffmpeg/ffmpeg](https://github.com/ffmpegwasm/ffmpeg.wasm)、[@ffmpeg/util](https://github.com/ffmpegwasm/ffmpeg.wasm)
