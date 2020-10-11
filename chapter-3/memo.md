# アセット
## Sprocket
  - アセットファイルにアクセするためのパスを管理する
  - アセットのコンパイル
  - アセットファイル動詞の依存性を管理する
  - あセットファイルを配置するパスを管理して1つのディレクトリにあるかのように扱える
  - アプリのメイン app/assets
  - 共通で利用するライブラリ　lib/assets
  - vendor/assets
  - アセットファイルを段階的にコンパルしていくAssetPipeline
  require 引数として与えたファイルの内容を地震より前に挿入　ない場合はエラー　重複しても1どbのみ
  include requireと同様の重複して呼ばれた場合都度ファイルの内容が挿入
  require_directory引数として与えられたディレクトリの下にある同じフォーマットの不秋るを地震より前に挿入　アルファベット順
  require_tree   require_directoryと同様だけどディレクトリ下を再起的に検索して全てのファイルを対象にする
  require_self 自身のファイル内容を挿入する。順番を指定したい場合
  depend_on 依存関係だけを定義ファイルは読み込まない　キャッシュを無効化したい場合など
  depend_on_asset さらにディレクティブが記述されていただそのさきも再起的に依存関係の対象
  stub 他でrequireされていても無視するように変更する
## Turbolink
- pjax(PjaxとはHTML5のHistoryAPIであるpushStateとAjaxを組み合わせたページ繊維の方式同一の減ったーを再利用できる。javascriptmの読み込みなどを省略できる。)の簡易版。
- クリックイベントによってTurbolinksによる遷移を実行、Ajax実行HTML取得、headのアセットを確認し、現在のページのアセットであれば処理を続行する。異なっていればlocation.hrefを書き換え絵インクさきのURLにリダイレクト処理を終了する、HTMLのタイトルとbodyを抽出、入れ替え、pushStateを実行URLをリンク先に変更
- rails4辛く見込まれている。
- documentイベント
- gemj queryturbolink

# Railsのロードパスとレイヤーの定義
# MVC以外について
- モデルとして扱う
- libディレクトリで管理
- 新レイヤーを定義
- 考え方による、手段を多く覚えていた方がいい
- 本質に近い機能ならそのままモデルとして扱うのが良い

## libディレクトリ
- 元々requireパスが設定
- rakeタスクをおく lib/task.rake
- 命名規則に沿ったファイル名とクラスめいだと自動でファイルをrequireしてくれる　オートローディング
- ファイル名はスネークケース、クラス名をキャメルケーす
- クラスやモジュールのネームスペースはディレクトリで表現する
- aprication.rbでconfig.autoloading_pathで設定

# レイヤーを追加するgem
- active_decorator
  - モデルとビューを橋渡しする
  - クラスとサブクラスのみ
  - オートローでlオング
  - コントローラでインスタヌsへんすに代入してビューにわらされたモデルのインスタンス
  - 部分連プレートをrenderメソ度でレンタリングする際にlocalオプションで引き渡した

# Sidekiq　
- 非同期処理
- Sidekiqはrailsとは別にプロセスを立ち上げます
- railsからメッセージを受け取り、ワーカークラスに引き渡して実行する
- Workerクラスapp/worker入りぐち、sidekiqRedis
SidekiqWorkerをインクルードすることでワーカーとして起動する
performメソッドが必要です。performメソッドに実行したい非同期処理を記述していますが、実際はRailsのモデルを読み込んで処理を依頼する
- perform SidekiqのワーカプロセスがRedisから読み込んだ値ｗｐ引数として医療
- SidekiqはRailsからのメッセージはJSONresdinに保存
- 文字列、数値、ブーリアン、null配列ハッシュ以外外は利用しない Activerecordのオブジェクト利用したい倍はレコードのIDエオ引数として私、perforメソッド内でロードするのがいい
- モデルやコントローラーから非同期処理を呼び出す
- 結果をどうやって通知するか　少し時間かかるAjaxによるボーリングwebsocketなど
- 非同期処理はエラーハンドリングについても同期処理より複雑な処理が必要になります
- 際実行した時に同一の血クォーテ返すように設計できつ
ユーザーに失敗したことをどう通知するか
- 別途データベースに保存し後から確認できるようにする

# Pry
- コマンド
  - recognize-path
    - 引数に私た文字列などをルーディングのアクションやcontroller情報にパースする
  - show-middleware
    - 読み込んでいるRackmiddlewareを表示する
  - show-model
    - 引数にわらしたモデルの情報を出力する
  - show-models
    - 全てのモデルの情報を出力する
  - show-routes
    - ルーティング情報を出力する
- binding.pry　ブレークポイントとなる
- bye-bug
  - next
  - step

# Hirb
- hirb DBのコンソールで実行した表形式にできる
- pryを使う場合は設定が必要(ルートに.pryrc)
- BettorErrorsでエラー画面をよりリッチに表現する
- binding_ofcaller

# Spring
- Rails4,1
- railsの初期起動時のデータを読み込むSpringが追加される
- 短縮される
- binstaub
- help
- status
- stop
- rails

# rails-erb
- ER図出力
-