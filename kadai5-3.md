## 外部APIの呼び出しのミニレポート
### Q3-1. 郵便番号APIについて説明せよ。
* エンドポイントと機能 :エンドポイントはhttps://zipcloud.ibsnet.co.jp/api/search
機能は、日本の郵便番号から住所を取得できるWebAPI(無料である。)
* リクエストとレスポンスのフォーマット :リクエスト例 :https://zipcloud.ibsnet.co.jp/api/search?zipcode=1000001
レスポンスのフォーマット :
{
  "message": null,
  "results": [
    {
      "zipcode": "1000001",
      "prefcode": "13",
      "address1": "東京都",
      "address2": "千代田区",
      "address3": "千代田",
      "kana1": "ﾄｳｷｮｳﾄ",
      "kana2": "ﾁﾖﾀﾞｸ",
      "kana3": "ﾁﾖﾀﾞ"
    }
  ],
  "status": 200
}

エラー時 :
{
  "message": "該当するデータが見つかりませんでした。",
  "results": null,
  "status": 200
}

### Q3-2. 各自で調査したAPIについて説明せよ。
* APIの名称と参照URL :人生アドバイスAPI(https://api.adviceslip.com/advice)
* エンドポイントと機能 :エンドポイントはhttps://api.adviceslip.com/advice
機能は、ランダムなアドバイス取得、指定IDでのアドバイス取得、検索（キーワードで探す）といったもの。

* リクエストとレスポンスのフォーマット :ランダムアドバイス取得
GET https://api.adviceslip.com/advice
特定IDのアドバイス取得
GET https://api.adviceslip.com/advice/45
検索機能（キーワード検索）
GET https://api.adviceslip.com/advice/search/life

レスポンスフォーマット :
{
  "slip": {
    "id": 123,
    "advice": "Don't forget to enjoy the little things."
  }
}

エラー時 :
{
  "message": {
    "type": "notice",
    "text": "No advice slips found matching that search term."
  }
}

### Q3-3. 感想
* 今回の課題で苦労したこと :無料APIを探すにあたって、時間と回数制限に引っ掛かったり、多数のアクセスで早く制限されたりと上手く機能するAPIを探すのが非常大変だった。
* 演習を通して理解できたこと :外部のプログラムを利用するAPIの活用。エンドポイントやメソッドのWebAPIの構成要素。
* Web APIの利便性や課題など :今回の課題を通して、開発する際にシステムの連携が容易になることや、自前で機能を開発しなくても済むことから開発スピードの向上が見込まれる。
課題点・問題点、デメリットとして、外部APIの依存していることはそのAPIが停止、変更、廃止された場合、その利用しているシステムすべてに影響が出る。通信を行うAPIもあるため、オフライン環境だと利用できないようなシステムもある。
他にも、今回の課題にもあったようにAPIによっては、回数・使用制限が掛かっている場合があり、自由に扱えないものがある。
