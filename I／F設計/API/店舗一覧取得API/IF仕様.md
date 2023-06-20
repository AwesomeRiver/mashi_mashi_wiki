## GET /search
本IFはHTTPSプロトコルを使用する。  
本APIは検索処理のため、GETメソッドを使用する。  

## API Gateway
APIインタフェースを公開するAPIGatewayの情報
[APIGateway]()

## リクエスト
### リクエストヘッダ
- x-api-key ... APIを利用する事業者ごとに発行する文字列（画面から実行する場合のみ付与する）
### パスパラメータ
- なし
### クエリストリングパラメータ
- keyword  
**string**   
画面でインプットボックスに入力された`20`文字以下の検索文字列  
英語及び日本語（漢字も可）のみ可能
空文字も許容する  
### リクエストボディ
- なし
### 入力チェック
本APIはクエリストリングパラメータについて入力チェックを行う  
- keyword
  - 20文字以内であること
  - 英語、日本語の文字列または数字であること
  - 空文字、nullを許容する
  - 現時点で記号は入力チェックでエラーとする
### リクエストサンプル
```http
GET https://FQDN/search?keyword=検索文字列 HTTP/1.1
x-api-key: xxxxxxx
```
## 成功レスポンス
リクエストを受理し、データベースからデータの取得に成功した場合、ステータスコード`200`を返却する
### レスポンスボディ
- restaurant_list[]
  - 取得した店舗情報の一覧
  - Type: `Array<object>`  
### restaurant_list
- restaurant_name
  - 店舗の正式名称
  - Type: `string`
  - example: `三田本店`
- location
  - 店舗が存在する場所
  - Type: `string`
  - example: `${都道府県} ${市区町村}`
- amount_of_ramen
  - ラーメン小（スタンダード）の麺量(g)  
  - Type: `number`
  - example: `300`
- low_end_price
  - 店舗で最も安いラーメンの値段(円)
  - Type: `number`
  - example: `500`
- regular_holiday[]
  - 日本語表記
  - 毎週定休日ではない場合も配列内の文字列で表す
  - Type: `Array<string>`
  - example: `['日曜日','第二三土曜日']`

## 失敗レスポンス
リクエスト情報に不備があった場合（要素の構文が正しくない/必須プロパティの存在なし等）によって、データベースよりデータが取得できない場合はステータスコード`400`を返却する。 
また、ボディにエラーメッセージを格納し、返却する。
### レスポンスボディ
- message
  - エラー内容を表す文字列
  - Example: `検索文字列が不正です`
  - Type: `string` 
### レスポンスサンプル
```http
HTTP/1.1 400
Content-Type: application/json
{
    "message": "引数が不正です" 
}
```

## エラーレスポンス
サーバエラー等の予期せぬエラーが発生した場合、ステータスコード`500`を返却する

### レスポンスボディ
- message
  - エラー内容を表す文字列
  - Example: `サーバエラーが発生しました`
  - Type: `string` 
### レスポンスサンプル
```http
HTTP/1.1 500
Content-Type: application/json
{
    "message": "サーバエラーが発生しました" 
}
```