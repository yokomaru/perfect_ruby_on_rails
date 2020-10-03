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

V View
Modelの内容を参照し視覚表現を行う部分
C Controller

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


