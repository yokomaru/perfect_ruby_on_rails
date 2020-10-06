Ruby on RailsとMVC
M Model
データベースの接続、データに対する操作及ビジネスロジック

モデルとモデリング
相互の関係性を整理したりすることをモデリングと呼ぶ

ActiveRecordによるモデル
１。データベースと接続し、レコードとエンティティを結びつける
モデルに何も記述線でもカラムを取得ｍ自動で反映する
SEOの構築の抽象化、コネクション

2.バリデーションやコールバック
ActiveModelというモジュールを使う

CRUD

Create　レコード作成 create save
Read 探す all find
Update　更新 save update_attributes
Delete 削除 destroy delete

Activecor::Relation
(1..5).each do |i|
Book.create(name: "Book #{i}", published_on: i.month.ago, price: (i * 1000))
end

Book.find(1)

Book.find_by(name: "Book 3")
Book.where("price > ?", 2000)
Book.where("price > ?", 2000).limit(3).order(:name)
メソッドチェーン
Query Interface


select
where
limit
offset 上から数えら場合
order
group
joins
includes
not

Activerecord::Relation
Query Interfaceの結果をおぬジェクトとして
内部にどんなSERVICEを発行するかという情報
アクセスはない
ARにQIが呼ばれると、Activerecord::Relationのインスタンスが生成される
繰り返し呼び出したQIはActiverecord::Relationのインスタンスにし、どんなSQLを発行するかの情報が更新されていく
実際にデータが必要になった時点で蓄積された情報を元にSQLを発行
配列と同様
インターフェースを領することで配列と同じ王にできる
 Book.where("price > ?", 2000).limit(3).order(:name).to_a
  Book Load (0.4ms)  SELECT "books".* FROM "books" WHERE (price > 2000) ORDER BY "books"."name" ASC LIMIT ?  [["LIMIT", 3]]
=> [#<Book id: 3, name: "Book 3", published_on: "2020-07-03", price: 3000, number_of_page: nil, created_at: "2020-10-03 09:01:07", updated_at: "2020-10-03 09:01:07">, #<Book id: 4, name: "Book 4", published_on: "2020-06-03", price: 4000, number_of_page: nil, created_at: "2020-10-03 09:01:07", updated_at: "2020-10-03 09:01:07">, #<Book id: 5, name: "Book 5", published_on: "2020-05-03", price: 5000, number_of_page: nil, created_at: "2020-10-03 09:01:07", updated_at: "2020-10-03 09:01:07">]

Book.create(name: "Book test", published_on: Date.today, price: 2000)

validates_associated 関連先のレコード
confirmation　emailなどのように
exclusion ある値ではないこと
format フォーマットを満たすこと
inclusion ある値を含まれること
length ある長さを満たすこと
numericality 数値であること
presence 存在すること
absence 存在しないこと
uniqueless 値が一位であること

Book is deletes: {"id"=>1, "name"=>"Book test", "published_on"=>Sat, 03 Oct 2020, "price"=>2000, "number_of_page"=>nil, "created_at"=>Sat, 03 Oct 2020 10:01:31 UTC +00:00, "updated_at"=>Sat, 03 Oct 2020 10:01:31 UTC +00:00, "publisher_id"=>3}

before_validation create update
after_validation create update
before_save
around_save
before_create
around_create
before_update
around_update
after_update
before_destroy
around_destroy
after_destroy
after_initiaize モデルがインスタンスかしたおｔき
after_find first last find find_by　モデルのインスタンスを生成したときに実行

以下のメソッドではコールバックない
decrement
decrement_all
delete
delete_all
increment
increment_all
toggle
touch
update_column
update_columns
update_all
update_counters

ActiveRecordでenum

## コントローラーの役割
C Controller

before_action jikkouame

after_action　実行後
aroud_action 前後

before_action do end で囲める
親クラスで異定義したアクションコールバックをスキップするのもできる

resourcesの拡張

member do
end

collection
do
resourcesの中にresources
hoges/:hoges_id/hugas/:id

## resources以外のルーティング
一つしかない場合はresourde

POST /profile/(format)
GET/profile/new
GET/profile/wdit
GET/profile/(format)
PATCH/profile/(format)
PUT DELETE/profile/(format)
/profile/(format)

indexはなし

例外処理
rescure_from

class Login複数のコントローラにまたがった例外処理などをredcurefromをうt買えば見通しが良くなる
Failed < StandardError
end

StrongPrameters
# mass assignment
モデルをハッシュクラスを使って属性を設定できる
つかwな合わない
user = User.find(1)
user.name ~~

user.update(name:,)
class APplidationContoller

意図しない属性の変更を許してしまう
param社ユーザが送ってきたHTTPrikusesuo
admin=treu
うわがかれる
Stringparamerterはできるkeyを検査する

params.require(:user).permit(:name, :email)
parametermissing

def user_params
if current_user.admin?
params admin
else
params
end


# V View
Modelの内容を参照し視覚表現を行う部分
- 描画するための天日レートをさがす
- 探されたテンプレートを元にデータ展開し最終的なHTMLを生成する
- Rails_ROOT/app/viewe/コントロール名/アクション名.html.elb
ELB形式のテンプレートエンジン

- renderアクション省略する場合は一致させること
- renderのオプション

- :text ただのテキストを表示する render text: "OK"
- :plain text/plainでテキストそのまま render plain: "OK"
- :html テキストをそのまま表示 render html: "OK"
- :body :生データをブラウさにそのまま帰る render body: "data"
- :nothing :明示的に何も表示しない render body: "data"
- :template 特定のt根プレートを指定してレンダリング render template: "bools/edit.html.erb"
- :file　特定のファイルの内容をそのまま表示 render file: Rails.root.join('public/sample.html')
- :inline インラインでテンプレートの内容を書く render inline: "xml.p {'Sample'}, type: :builder
- :json to_jsonを用いてjsonを表示 render json: @book
- :xmkl to_xml render xmk: @book

- redirect_to
- :statusステータスコードの数値化文字列のシンボル
- partialテンプレートとlayout
  - :partialをつけると先頭が_で始まるファオルめいのテンプレートから検索する
   - layoutというディレクト
   - yieldにコンテンツが展開される
   - 特定のレイアウトを用いる場合はrenderメソッドをオプションを使えます
- variants接続してきた端末によってPCとは別のテンプレートを表示したい
  def detect_mobile_vatiant
    request.variant = :mobile if request.user_agent =~ /iPhone/
  end

  # テンプレートエンジンの紹介
  - 特殊な記法を用いてデータなどを展開し、HTMLを生成するようなライブ拉致をテンプレートエンジンと呼びます。

  - ERB
    - 標準
  - Haml
  - Slim

  # ヘルパーの利用
  - モデルから受け取ったデータをそのまま表示するのではなく、ユーザーにとってわかりやすいフォーマットに反感する組み込みヘルパー
  - url_for
    - Webアプリケーションのパスを構築する
    - url_for(controller: : users, avtion:: index)
  - form_tag(ダンジュんあフォーム)/form_fo(モデル)
  - styledheet_link_tag,javascriot_include_tag
    - CDATAセレクション
  - distance_of_time_in_worda_to_now
    - ある時刻と現在時刻の間にどの程度開きがあるか
    - helper.distance_of_time_in_words_to_now Time.current
  - number_with_delimiter
   - 長い数字に自動的に区切りの記号を入れてくれます。
  - 独自ヘルパーの定義
    - app/helper
    - 全てのアプリケーションのビューの内部から利用できる
    -
  # エスケープ処理
  - <% "<script>alert('sample');<script>"%>
  - raw(タグを含んだ文字列を構築してそのまま表示する)
  - String#html_safeを呼び出す
  - SafeBufferはStringクラスのサブクラス
  - "<script>alert('sampel')</script>".html_safe
  - Railsの内部で明治t系に安全であるとマークされた文字列とむなされた上で処理されれう
  - これは内部でこの文字列が安全かどうか（出力時にエスケープすべきかどうか）という情報を保持しています
 # API
  - JSON
    - Jbuilder
      - json.extract! @book, :id, :name, :price, :created_at
      - そのままJsonのキーになる
      - json.namewith_id "#{@book.id} - #{@book.name}"
      - json.publisher do
          json.name @book.publisher.name
          json.address  @book.publisher.adress
        end
       unless @book.high_price?
        json.low_price treu
       end

# まとめ
- Model
  - Activerecord、バリデーション、コールバック
- Contoller
  - ModelとViewを繋ぐ、リクエストオブジェクトやアクションコールバック、脆弱性への対処
- View
　- Viewについて受け取ったModelを表示、テンプレートエンジン、ヘルパー、フォーマットでの表示

