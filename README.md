# SANS TOI MAMIE（サントワマミー）ホームページ

長崎・思案橋のスナック「サントワマミー」の公式サイト一式です。
ビルド不要の静的サイト（HTML / CSS / JavaScript）なので、フォルダごとサーバーにアップロードすれば公開できます。

## ファイル構成

```
index.html          TOP（アニメーション演出あり）
gallery.html        GALLERY（ライトボックス）
access.html         ACCESS（住所・営業時間・地図）
contact.html        CONTACT
about.html / menu.html  旧URL用の転送ページ（TOPの #about / #menu へ移動）
css/style.css       全ページ共通のデザイン
css/top.css         TOPページ専用の演出
js/config.js        ★ 店舗情報・料金・ギャラリー写真の設定（ここだけ編集すればOK）
js/main.js          共通処理（メニュー開閉・設定の反映）
js/top.js           TOPページの演出
js/gallery.js       ライトボックス
images/             サイトで使う写真（WebP）・アイコン
images/hero.jpg     SNS共有（OGP）用の画像
favicon.ico / apple-touch-icon.png / site.webmanifest  ブラウザ・スマホ用アイコン
robots.txt / sitemap.xml  検索エンジン用
.vercelignore       公開対象から外すファイルの指定

_dev/               ★ 開発用（公開されません）
  preview.bat / preview-server.ps1  パソコンでのプレビュー（preview.bat をダブルクリック）
  original-images/  WebP変換前の元写真（JPG）
```

## 写真の差し替え

1. 元写真（JPG）は `_dev/original-images/` に保管しています。
2. サイトでは軽量な WebP 形式（`images/*.webp`）を表示しています。差し替えるときは、同じ名前の `.webp` ファイルで上書きしてください。
3. GALLERYの写真・順番は `js/config.js` の `GALLERY` で変更できます。

## 店舗情報・料金の変更

`js/config.js` を開いて書き換えます。

- `tel` / `hours` / `holiday` / `line` は **空欄（""）のままならサイトに表示されません**。確認できた情報だけ入力してください。
- TEL・LINEを入力すると、CONTACTページとACCESSページに自動で表示されます。
- 営業時間・定休日を変更するときは、`js/config.js`（hours / holiday）に加えて、`access.html` の OPEN / CLOSED 欄と、`index.html` の構造化データ（openingHoursSpecification）も同じ内容に直してください。
- 料金は `MENU` の `items` に `{ name: "項目名", price: "¥0,000", note: "補足" }` の形で追加します。空のカテゴリは「準備中」と表示されます。

## 確認方法

`_dev/preview.bat` をダブルクリックするとブラウザでプレビューできます（`index.html` を直接開いても確認できます）。
（Google マップの埋め込みはインターネット接続時のみ表示されます）
