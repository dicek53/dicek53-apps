# dicek53 apps

個人開発アプリの一覧と、各アプリの紹介・プライバシーポリシー・サポートページ(静的サイト)。

## 公開先

- **現在(2026-09-20〜)**: xserver の `b-court-record.site` 配下。`notaflow/` だけを `public_html/notaflow/` に置いている
  - https://b-court-record.site/notaflow/
  - https://b-court-record.site/notaflow/privacy/
  - https://b-court-record.site/notaflow/support/
- **予定**: アプリ公開後に Cloudflare Pages へ移す(そのときはルートの `index.html` = アプリ一覧も公開する)

## 構成(xserver 側の他アプリと同じ「ディレクトリ + index.html」形式)

- `index.html` — アプリ一覧(xserver には置いていない)
- `notaflow/index.html` — NotaFlow 紹介
- `notaflow/privacy/index.html` — プライバシーポリシー(正本は notaflow リポの `docs/store/privacy-policy.html`。更新時はコピーする)
- `notaflow/support/index.html` — サポート(連絡先 = contact.nf@b-court-record.site)

## 反映(ローカル → xserver)

接続は `~/.ssh/config` の `xserver-bcr`(公開鍵認証)。先に `-n`(dry-run)で差分を確認する。`--delete` は付けない。

```bash
rsync -avn -e ssh ./notaflow/ xserver-bcr:~/b-court-record.site/public_html/notaflow/
rsync -av  -e ssh ./notaflow/ xserver-bcr:~/b-court-record.site/public_html/notaflow/
```
