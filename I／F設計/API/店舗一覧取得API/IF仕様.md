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
### リクエストサンプル
```http
GET https://FQDN/search?keyword=検索文字列 HTTP/1.1
x-api-key: xxxxxxx
```

## 成功レスポンス
TODO
## 失敗レスポンス
TODO