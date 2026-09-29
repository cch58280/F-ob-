# サーフィン行こ 🌊

サーフィン仲間(10人くらい)で「いつ・どこへ行けるか」を共有するアプリです。
スマホのホーム画面に置いて使えます(PWA)。

> このREADMEは作りながら少しずつ書き足していきます。
> いまは **ステップ1〜3(Supabase側の準備)** まで書いてあります。

---

## セットアップ手順

### ステップ1 Supabaseで新しいプロジェクトを作る

経理アプリとは **別の、新しいプロジェクト** を作ります。

1. https://supabase.com/dashboard を開いてログイン
2. 左上のプロジェクト一覧(または「Projects」画面)で **「New project」** をクリック
3. 次のように入力します
   - **Organization**: 経理アプリと同じものでOK
   - **Project name**: `surf-iko`
   - **Database Password**: 「Generate a password」を押して自動作成
     (このパスワードは今後ほぼ使いませんが、念のためメモ帳などに保存)
   - **Region**: `Northeast Asia (Tokyo)`
   - プランは **Free** のまま
4. **「Create new project」** をクリック → 1〜2分待つと完成します

### ステップ1-2 匿名サインインを有効にする(必須)

これを忘れるとログインできません。

1. 左のメニューで **Authentication**(人のアイコン)をクリック
2. **「Sign In / Providers」**(古い画面では「Providers」)を開く
3. 上の方にある **「Allow anonymous sign-ins」** をオンにする
4. **「Save changes」** をクリック

### ステップ2 データベースを作る(SQLを貼って実行)

1. 左のメニューで **SQL Editor**(`>_` のアイコン)をクリック
2. 右上の **「+」→「Create a new snippet」**(または「New query」)をクリック
3. このリポジトリの **`supabase/schema.sql` の中身を全部コピー** して、白い入力欄に貼り付け
4. 右下の **「Run」**(または Ctrl+Enter / ⌘+Enter)をクリック
5. 画面下の結果欄に **`Yama` が1行** 表示されれば成功です 🎉

- 「destructive operation(危険な操作)」という確認が出たら **「Run this query」** を押してOKです
  (中で「もし既にあれば消して作り直す」という書き方をしているため出る表示です)
- 何度実行しても壊れないように作ってあるので、失敗したらもう一度 Run してOKです
- 最初の管理者 **Yama(PIN: 0000)** ができています。アプリに入ったら **すぐPINを変更** してください

### ステップ3 URLと鍵(anon key)をコピーする

アプリがSupabaseにつながるための「住所」と「合鍵」をコピーします。

1. 画面上部の **「Connect」** ボタンをクリック
   (見つからなければ、左下の歯車 **Project Settings** → **Data API** / **API Keys**)
2. 次の2つをコピーして、メモ帳などに一時保存
   - **Project URL** … `https://xxxxxxxx.supabase.co` の形
   - **anon key / publishable key** … `sb_publishable_...` または `eyJ...` で始まる長い文字列
3. ⚠️ **`service_role` / `secret` と書かれた鍵は絶対にコピーしない・人に渡さない** でください
   (anon / publishable の方は、アプリに書いて公開しても大丈夫な鍵です)

コピーした2つは、Claude Code に貼って渡してもらえれば `index.html` に組み込みます。
(自分で貼る場合は、`index.html` の先頭にある `SUPABASE_URL` と `SUPABASE_ANON_KEY` の `""` の中に貼ります)

---

### ステップ4〜8(このあと追記します)

4. GitHub に `surf-iko` リポジトリを作成してファイルを置く
5. GitHub Pages で公開
6. GitHub Secrets に `SUPABASE_URL` と `SUPABASE_ANON_KEY` を登録(自動ping用)
7. iPhoneで公開URLを開き、共有 → 「ホーム画面に追加」
8. Yama / 0000 でログイン → PINを変更 → 仲間を登録
