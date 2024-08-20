# discord-narrate-bot
DISCORDのチャットを読み上げるBOTです。

# 要求
このBOTの最新版を起動するには以下の環境が必要です。
- JDK 21 or higher

# 導入方法
How_to_Install.md に書いてあります。

# コンフィグ（設定）
Bot_Config.md に書いてあります。

# 読み上げ音声変更
Voice_Change.md に書いてあります。

# BOTのコマンド(default)
このBOTは次のコマンドがあります。
## /join
ボイスチャンネル参加＆読み上げ開始
## /leave
ボイスチャンネル離脱＆読み上げ停止
## /dictionary add word:[単語] read:[読み]
辞書を追加します。
## /dictionary remove word:[単語]
辞書を削除します。
## /voice name:[音声の種類]
NarrateVoiceListで設定した音声一覧ファイルの中から選べます。<br>
コマンドで示せる候補は最大25個までなので、登録されている音声一覧が25個以上の時は、ランダムに選んだものが候補に出ます。<br>
