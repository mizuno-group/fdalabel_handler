# fdalabel_handler

## これはなに

FDA@label のデータを処理したコードです。

## データの概要

### データ数

* データ数は、220366 行です。
* 50000 行ごとに、45 個のファイルに分かれています。

### データベースの構成

* データは各医薬品ごとにまとまっています。
* 各テーブルの構成の概要は、以下のとおりです：
    * row_id：DB 内での通し番号（追加したもの）
    * set_id：医薬品に対して一意に定まる ID
    * id：ある医薬品の特定のバージョンに対して一意に定まる ID
    * その他のカラム：医薬品の特徴など
* 列名の詳細の説明は [ここ](https://open.fda.gov/apis/drug/label/searchable-fields/) か fdalabel_columns.csv を参照してください。

### set_id について

* https://nctr-crs.fda.gov/fdalabel/services/spl/set-ids/{setid}/spl-doc を置き換えることで、該当する医薬品の添付文書を見ることができます。
* [DAILYMED](https://dailymed.nlm.nih.gov/dailymed/dailymed-announcements-details.cfm?date=2019-09-19) にある通り、
    * https://dailymed.nlm.nih.gov/dailymed/drugInfo.cfm?setid={setid}&version={versionnumber} の置換により、特定のバージョンにアクセスすることもできます。
    * [labelling archives](https://dailymed.nlm.nih.gov/dailymed/archives/index.cfm) による検索で、過去のバージョンを探すこともできます。

## コードの概要

* analysis：階層構造になっていたデータをフラット化し、データの中身を確認するのに使ったコードなどです。
* make_db：列を絞り、データベース形式にするのに使用したコードです。
* pubchem：PubChem から Active ingredients の情報を取ってくるのに使ったコードです。

## データの保管場所

* NAS の text 直下の fdalabel フォルダにあります。
* カラムの説明は fdalabel_columns.csv にまとまっています。
