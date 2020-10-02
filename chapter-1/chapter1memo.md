### gem
- パッケージ管理してステムRubyGemを扱うためのコマンド
ライブラリをgemパッケ-じ

> gem search rdefs
*** REMOTE GEMS ***
rdefs (0.0.2)

>rdefs sample.rb
class Sample
  def hi

rdefs ソースの構成を大まかに把握できる。

gem i (install)
gem help commands

### rake
Rakeビルドツールを実行
その他の定型処理を実行するためのコマンド
 Rakeで実行する処理の単位をタスクと呼ぶ

desc 'Hello,Rake Task'
説明
task :hello do
  puts 'Hello, Rake!'
end

>rake -T 一覧見える
rake hello  # Hello,Rake Task

### Bundlerでgemパッケージを束ねる
gemの仕組みを進化させselect、開発しているプロジェクトでどのgemを使っているのかバージョンないかusertableカル
Gemfileというファイルにgemをかく
Bundler経由の方がいい

install
update
kist
init Gemfile生成
exec コマンド名BUndlerでインストールされているgemを実行

Gemfile.lock現在のバージョン情報などメモ

Rails
CoC
Conversion ober DOnfiguration
-> 設定より規約
-> データベースのテーブル名はモデル名の複数形にする
/employees toiu => URLは社員の一覧を表す
/empoloyee/1

DRY
Dont repeat Youself

REST
Representional State Transfer
全てのリソースに一位となる識別
自動テスト
URI が指す内容リソース
リソース中心に考える
何を削除したいのか
何をどうしたいのか
何の情報をどうしたい

自動テスト
Rspec

レールに乗る
生産性

rails s サーバ起動
rails c 環境読み込んで実行
rails db dbconsole
rails g 雛形
rails r 実行

scafold CRUD操作を行うMVC

rake db:migrate:status
 Status   Migration ID    Migration Name
--------------------------------------------------
   up                      Create tasks

migrationファイルはUTCが使われる
Status up 適用
Status down 未適用

http://localhost:3000/rails/info/routes
rake routes
develop環境では現在ルート環境を表示する仕組みがRails4から

url

tasks(,:format) tasks#create
formatは.jsonやcsvなどによってレスポンスを変化させるため

HP5ではPUT/DELETEは採用していない
JSなどを使わずにブラウザからメソッドで悪せいこうとうすることはできないケースがたたある

_method パラムニHTTPメソッドを埋め込みPOSTスルコトでPUTで対応
overloaded POS

scafold
index 一覧
show 詳細
new 新規
edit 編集
create 新規登録をして詳細画面を表示
update 更新をして詳細画面を表示
destroy 削除して一覧を表示

rails 4 patch
putリソースの置き換え
Patch リソースの部分更新
パスワード変更フォーム
URLのリソースのうちパスワードのみPUT