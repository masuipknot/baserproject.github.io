# コンテンツの存在確認

指定したコンテンツが存在するか確認する

### 実行可能な権限
```
ログインユーザー以上
```
 
### リクエスト
```
GET /baser/api/admin/baser-core/contents/exists/{contentId}.json
``` 

### パスパラメーター

| パラメーター名         | 型   | 内容            |
|-----------------|-----|---------------|
| contentId | 数値  | コンテンツのID |

### レスポンス例
#### レスポンスボディ
```json
{
    "exists": false
}
```