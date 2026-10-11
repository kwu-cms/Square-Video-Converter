# HyperPixel 4.0 Square 動画変換

[HyperPixel 4.0 Square](https://www.switch-science.com/products/5901)（Raspberry Pi用高解像度ディスプレイ）向けの動画変換ツールです。ブラウザで動作し、動画はアップロードされません。

## 公開

`main` への push で、GitHub Actions（`.github/workflows/pages.yml`）が GitHub Pages にデプロイします。

https://kwu-cms.github.io/Square-Video-Converter/

## 動作

FFmpeg.wasm（シングルスレッド版）で、動画をブラウザ内で変換します。変換ライブラリ本体は同一オリジンの `vendor/` から読み込みます。Web Worker は別オリジンのスクリプトを起動できないためです。FFmpeg の WebAssembly 本体は jsDelivr から取得します。元動画データはアップロードされません。初回は約30MB以上のダウンロードが必要です。インターネット接続が必要です。

## 注意

- 大容量・長時間動画はブラウザのメモリ制限で失敗することがあります。
- Chrome / Edge のデスクトップ版を推奨します。
- 出力仕様：720x720, H.264 / yuv420p, 24/30/60fps, 音声削除（既定）またはAAC。
- 入力形式はFFmpeg.wasmのビルドに依存し、一部のMOV等で変換に失敗する可能性があります。
- 変換エンジン（WebAssembly）は jsDelivr 経由です。オフライン動作はしません。

## 設計

参照デザイン：
- https://kwu-cms.github.io/EZSignNFC-caption-generator/
- https://kwu-cms.github.io/url-slideshow/

利用コンポーネント：[@ffmpeg/ffmpeg](https://github.com/ffmpegwasm/ffmpeg.wasm)、[@ffmpeg/util](https://github.com/ffmpegwasm/ffmpeg.wasm)
