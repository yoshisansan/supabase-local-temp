# Supabase ローカル開発環境の構築

## 環境構築

### supabase準備

```
brew install supabase/tap/supabase
brew upgrade supabase
```

```
supabase stop --no-backup
supabase start
```

ログイン時、https://supabase.com/dashboard/account/tokens でトークン生成する必要あり
```
supabase login
```

### psql用意

```
$ brew doctor
$ brew update
$ brew install libpq
$ echo 'export PATH="/opt/homebrew/opt/libpq/bin:$PATH"' >> ~/.zshrc
$ source ~/.zshrc
$ psql --version
psql (PostgreSQL) 16.0
$ psql 'postgresql://postgres:postgres@localhost:54322/postgres'

psql (16.0, server 15.1 (Ubuntu 15.1-1.pgdg20.04+1))
Type "help" for help.

postgres=>
```

## 始め方

```
supabase init
supabase start
```

### テーブル作成例

```
supabase migration new create_employees_table
```

### 変更反映

```
supabase db reset
```

## psgl関連

### psgl操作

```
psql 'postgresql://postgres:postgres@localhost:54322/postgres'
```

db確認
```
postgres=> \d
```

## デプロイ - リモートSupabaseと連携する場合

リンク
```
$ supabase link --project-ref <project-id>
```

```
supabase db push
```

### 参照
https://zubora-code.net/ja/articles/supabase-local-dev