# 透明カンペ PWA

## ファイル構成
```
index.html      ← メインアプリ
manifest.json   ← PWA設定
sw.js           ← Service Worker（オフライン対応）
icon-192.png    ← アイコン（自分で用意してください）
icon-512.png    ← アイコン（自分で用意してください）
```

## 使い方
1. Webサーバー（HTTPSが必要）にファイルをアップロード
2. スマホでページを開き「ホーム画面に追加」
3. ホーム画面からPWAとして起動

## 主な機能
- テキスト自動保存（localStorage）
- 透明度スライダー（テキストエリアの不透明度を調整）
- フォントサイズ変更（A− / A＋）
- ダーク/ライトモード切替
- 文字数カウント
- オフライン動作対応

## 元コードからの修正点
- `sw.js` の `[caches.open](http://caches.open)` バグを修正
- Service Worker に `activate` イベント追加（古いキャッシュ削除）
- iOS PWA 対応メタタグ追加（apple-mobile-web-app-capable 等）
- `safe-area-inset` 対応（ノッチ・ホームバー考慮）
- 透明度・フォントサイズ・ダークモードの設定をlocalStorageで永続化
- `skipWaiting()` / `clients.claim()` でSWの即時反映

## ローカルテスト（Pythonが必要）
```bash
cd このフォルダ
python3 -m http.server 8080
# ブラウザで http://localhost:8080 を開く
# ※ PWA機能はHTTPSまたはlocalhostのみ動作
```
