# alexa_ai_akane
- アレクサからボイチェビの声出したいよねって話

## 構想メモ
### 案１(PC動かしっぱなし、アラームなどのシステム音は分岐できなさそう)
- グレーゾーンを踏み越えたうえで、まあまあな電気代
- 特化型なjetsonとかで解決できるかも？？？？？（未調査
1. ミドルローなグラボ付きPCを買う
2. mmvcでアレクサの声と、使いたい声を学習させる
3. アレクサのauxをPCからつなぐ
4. mmvcでリアルタイム変換
5. PCにつないだスピーカーから変換した音声を出力する
→常に声がずんだもん！！！（あふれる無能感

### 案２(lambdaから言語生成API)
1. ユーザ:アレクサに話しかける「アカネチャンを呼んで」
3. アレクサ：スキルを呼び出す
4. アレクサ：「なんや？」発話
5. ユーザ：質問「httpってなに？」
6. アレクサスキル：lambdaを呼ぶ
7. lambda：chatGPT_APIを呼ぶ、テキストデータ「httpってなに？」
8. chatGPT_API：「httpってなに？」に対する回答テキストを生成
9. chatGPT_API：回答データをwindows serverに渡す
10. windows sever：受け取ったデータからAIVoiceを使って音声データを生成
11. windows server：音声データをlambda or alexaスキルに音声データを返す

### 案３(windows serverから言語生成API)
1. ユーザ:アレクサに話しかける「アカネチャンを呼んで」
3. アレクサ：スキルを呼び出す
4. アレクサスキル：「なんや？」発話
5. ユーザ：alexaスキルに質問「httpってなに？」
6. アレクサスキル：lambdaを呼ぶ
7. lambda：windows serverにリクエスト、テキストデータ「httpってなに？」
8. windows server：lambdaからテキストデータを受け取る
8. windows server：chatGPTにリクエスト：「httpってなに？」
9. chatGPT：windows serverに生成したテキストを返す「Hypertext Transfer Protocolです（例）」
10. windows server：受け取ったテキストからAIvoiceを使って音声データ生成
11. windows server：mp3をlambda or alexaスキルに音声データを返す

## やること
### 1. アレクサスキル開発
1. アレクサ、「XXX」呼んで（例：茜ちゃん呼んで）でスキル起動
    - 関西弁がうまくいかなかったら葵ちゃん
2. 返答「なんや」
3. 質問
4. 質問をテキストデータにしてlambdaへ
5. とりあえずコンソール出力

### 2. windows server
1. 
