# Tekla QR ビューア中継ページ

Tekla 図面の QR コードから Trimble Connect の 3D モデルを開き、指定した製品・部材だけを表示するページ。
QRコード連携ツール（QrLinkApp.exe）の「リダイレクトサービスを経由する」にこのページの URL を設定して使う。

## パラメータ

`https://…/qr-viewer/#pid=…&mid=…&stoken=…&apos=…` のように `#` 以降に指定する（`?` 以降も可）。
`#` 以降はブラウザからサーバーへ送信されないため、共有トークンがホスティング側のログに残らない。

| 名前 | 内容 |
|---|---|
| `pid` | Trimble Connect プロジェクト ID |
| `mid` | モデル（ファイル）ID |
| `stoken` | 共有トークン（公開リンク）。無い場合は Trimble Connect のビューアへ移動する |
| `org` | 共有リンクの発行元ホスト（例: `app21.connect.trimble.com`） |
| `apos` / `ppos` | 製品マーク / 部材マーク。`;` 区切り、`?` は任意の 1 文字 |
| `iso=1` | 対象以外を非表示 |
| `ap` / `pp` | 照合するプロパティ名を指定（既定は `ASSEMBLY_POS` / `PART_POS` などを自動判定） |
| `debug=1` | 診断情報を表示 |

Trimble Connect Workspace API（共有トークンによる埋め込み）を使用。ページ自体はトークンを保存しない。
