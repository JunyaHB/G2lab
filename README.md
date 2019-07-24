# 仕事力診断テスト

あなたの会社に対する忠誠度を6つの質問から診断します。  
当初は適職診断テストでしたが、諸事情により変わりました。  

---

## fujikawa0726での改変箇所
* Gemfile  
下のエラーが出るためにchromedriver-helperは削除、webdrivers に変更  
WARN Selenium [DEPRECATION] Selenium::WebDriver::Chrome#driver_path= is deprecated. Use Selenium::WebDriver::Chrome::Service#driver_path= instead.  
詳細 https://blog.tamesuu.com/2019/06/08/274/  
* question1  
結果の詳細を追記
* check.html.erb  
"忠誠心度チェック"の文字列を追記

## 24-Jul-2019までの実装
* 最初から最後までの画面遷移には成功したので、一応動く物ができたと言えるようになった

## 今後の改善計画
* ちゃんとしたテストを書く
* 結果ページの内容をちゃんと書く
* 会社概要、コンタクトページ
* 未回答の質問があるときにエラーを出す
* 結果をDBに入れる、ここでRESTっぽい動きにできないか？
* メールを送信するか、ツイッター連携
* 問題数を増やす
* 選択肢の順番がランダムに入れ替わるようにする

## 検討したけどたぶんボツになったこと
* 最初にメールアドレスを入力させて、hidden属性のinputで値を渡す  
トップページにメールアドレスを入力→次のページのhiddenに入れる→DBに入れる  
トップページにメールアドレスを入力しない→次のページのhiddenにから文字列を入れる→DBに入れる  

## 主な担当範囲
* JunyaHB: 開始ページ、全体の背景、bootstrap周り
* TakeshiHora: 開始ページ、全体のページ遷移周り
* aiitkf: 設問ページ、結果表示の部分の計算など「動く」ところ、必要なマージ作業
* TakuyaKodama1014: 診断結果ページ、結果を収納するDB周り

## fujikawa0724での改変
* 上のバーを書き換えた。
* contact, aboutusのページを作った。
* helpページは消した。
* testを少し書き換えて通るようにした。
* 設問が6問になった。
* 結果がerbで出るようにした。
* questions1ファイルを追加
* 結果をスコアにして合計した値を表示、値により寸評を表示
* Usersモデル(DB)にscore1カラムを追加
* /usersでDBを見たときにもscore1カラムを追加
* editページにもscore1を追加
* score1のupdateに対応
