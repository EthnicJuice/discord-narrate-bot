# notice
この解説では、音声合成にgTTSを使用することを前提に解説します。

# setup
## Java Install
### windows
は、次のURLから最新のJDKをインストールしてください
https://www.oracle.com/java/technologies/
### linux
は、次のコマンドをコンソールに入力してインストール
`sudo apt install openjdk-18-jdk`

## botの取得
releases から、最新版をダウンロードしてください。

https://github.com/EthnicJuice/discord-narrate-bot/releases

ダウンロードした、ファイルは、どこかのフォルダに移動しておいてください。
できれば、読み上げBOT用のフォルダがあるといいです。

## 音声合成のインストール(gTTS)
gTTSをインストールするにはpipを使うため、pythonがインストールされている必要がありますが、ここでは解説しません。
### windows
cmd を起動します。
cmdに、次のコマンドを入力
`pip install gTTS`
### linux
コンソールを起動します。
そこに次のコマンドを入力
`pip install gTTS`

## コンフィグの作成
### windows
次にbotを起動します。
botのファイルと同じディレクトリに、start.batを作ります。
start.batの内容
```
java -jar ./Discord-ChatReadBot-X.X.X.jar
```
X.X.Xは、バージョンによって適宜変えてください。
start.batをダブルクリックして、botを起動すると、`bot.config`ができるはずです。
### linux
botを起動します。
コンソールなどから、起動します。なお、start.sh等を作ってから起動してもOKです。
botを起動すると、`bot.config`ができるはずです。

## スクリプトや、フォルダの用意
### windows
botのファイルと同じディレクトリに、audio_gen.batを作ります。
次に、gTTSを使用したときのaudio_genのサンプルを示します。
```
@echo off
set TEMP_PATH=./audio/%2.wav
set "LANGUAGE=%3"
if "%LANGUAGE%"=="null" set "LANGUAGE=ja"
gtts-cli %1 -l %LANGUAGE% --output %TEMP_PATH%
```
次に、botのファイルと同じディレクトリに、audio と dictionary というフォルダを作ります。

### linux
botのファイルと同じディレクトリに、audio_gen.shを作ります。
次に、gTTSを使用したときのaudio_gen.shのサンプルを示します。
```
#!/bin/bash
TMP=./audio/"$2".wav
LANGUAGE=$3
if [ "$LANGUAGE" = "null" ]; then
    LANGUAGE=ja
fi
gtts-cli "$1" -l $LANGUAGE --output $TMP
```
次に、botのファイルと同じディレクトリに、audio と dictionary というフォルダを作ります。

### 共通
botのファイルと同じディレクトリに、`list.txt`というファイルを作ります。
このファイルは、`/voice`コマンドで出てくる音声の種類の候補を示すものとなります。
試しに、英語と日本語を試せるようにしましょう。
```
日本語,ja
英語,en
```
jpとenは、音声生成スクリプトに渡される引数です。

## コンフィグの編集
bot.configの内容を編集します。<br>
細かい コンフィグの編集に関しては 「bot.config　について」をご覧ください。
### windows
以上の説明手順に従った場合の bot.config のサンプルを示します。
```
NarrateExportPath=./audio
NarrateGenerateCommand=./audio_gen.bat
DictionarySavePath=./dictionary
DiscordToken=xxxxxxxxxxxxxxxxxxxxxx
```
token は、自分のDiscordのBOT のtokenを入力してください。
最後に、start.batをダブルクリックしてうまく起動するはずです。

### linux
以上の説明手順に従った場合の bot.config のサンプルを示します。
```
NarrateExportPath=./audio
NarrateGenerateCommand=sh audio_gen.sh
DictionarySavePath=./dictionary
DiscordToken=xxxxxxxxxxxxxxxxxxxxxx
```
token は、自分のDiscordのBOT のtokenを入力してください
最後に、起動すればOKです。
