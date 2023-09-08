# TranslationToolkit

![Plugin](https://user-images.githubusercontent.com/51815450/183342025-2f6691d8-a665-49cb-9e63-bed7b0cee14f.PNG)

<!--ts-->
  * [概要](#概要)
  * [動作環境](#動作環境)
  * [インストール](#インストール)
  * [機能と使い方](#機能と使い方)
    * [Translate](#translate)
    * [Translate And Replace](#translate-and-replace)
    * [Translate Tooltip](#translate-tooltip)
    * [Read Aloud Text](#read-aloud-text)
    * [Open Advanced Translation Panel](#open-advanced-translation-panel)
  * [オプション](#オプション)
    * [デフォルトで用意されている翻訳エンジン](#デフォルトで用意されている翻訳エンジン)
      * [Google Translate (No API key required)](#google-translate-no-api-key-required)
      * [Libre Translate](#libre-translate)
      * [Microsoft Translator](#microsoft-translator)
      * [DeepL Translate (No API key required)](#deepl-translate-no-api-key-required)
    * [デフォルトで用意されているテキスト読み上げに使うAPI](#デフォルトで用意されているテキスト読み上げに使うAPI)
      * [Google Text To Speech (No API key required)](#google-text-to-speech-no-api-key-required)
    * [デフォルトで用意されているフォーマッタークラス](#デフォルトで用意されているフォーマッタークラス)
      * [DefaultFormatter](#defaultformatter)
  * [コンソールコマンド](#コンソールコマンド)
  * [作者](#作者)
  * [履歴](#履歴)
<!--te-->

## 概要

このプラグインはUnreal Engineのエディタ上のテキストやツールチップを翻訳し、結果をポップアップウィンドウで表示することができます。  
また、選択中のテキストを翻訳し、翻訳結果に置き換える機能などがあります。

## 動作環境

対象バージョン : UE4.25 ～ 5.3    
対象プラットフォーム : Windows  

UE4.25は使用できる翻訳エンジンがLibre TranslateとMicrosoft Translatorのみで、音声読み上げができません。  

## インストール  

[マーケットプレイス](https://www.unrealengine.com/marketplace/ja/product/translation-toolkit)からインストールしてください。  
プラグインのインストール後に機能が使用できない場合は、プラグインが有効化されていない可能性がありますので、編集 > プラグイン からプラグインの有効のチェックが入っているかをご確認ください。  

## 機能と使い方

### Translate

https://user-images.githubusercontent.com/51815450/183342098-c2a65691-2401-46e0-8859-811baf1c00c1.mp4

デフォルトのショートカットキーは```Shift + Ctrl + Z```で、マウスポインタ直下にあるテキストを翻訳し、結果をポップアップウィンドウで表示します。

![SimpleTranslationPanel](https://user-images.githubusercontent.com/51815450/183342196-a25ce597-0f13-4f8f-bc2b-87929a1bd3b4.PNG)

スピーカーボタンで翻訳元、翻訳先のテキストを読み上げます。(対応していない言語の場合はボタンが押せなくなります。)  
スピーカーボタンの隣のコンボボックスで翻訳元、翻訳先の言語を設定できます。  
右上のピンボタンを押すと後述する翻訳パネルで結果を表示することができます。  
このポップアップウィンドウはウィンドウ以外の場所をクリックすることで自動的に閉じられます。

### Translate And Replace

https://user-images.githubusercontent.com/51815450/183342242-446034f7-c05b-46d4-b1c9-d5f78db560d5.mp4

https://user-images.githubusercontent.com/51815450/183342269-fce16ad9-0f63-4f18-aabe-99b6eebe886e.mp4

デフォルトのショートカットキーは```Shift + Ctrl + X```で、選択中のテキストを翻訳し、結果に置き換えます。  
関数名や変数名など改行を含まないテキストで使用すると、置き換えるフォーマットを選択することができます。  
また、後述するプラグインの設定から翻訳前に翻訳後の言語を選択するセレクタUIを出すようにすることもできます。

### Translate Tooltip

https://user-images.githubusercontent.com/51815450/183342335-3c5eaa17-2407-40f4-acb3-7d81941adb70.mp4

デフォルトのショートカットキーは```Shift + Ctrl + C```で、現在表示されているツールチップを翻訳し、結果に置き換えます。  
翻訳結果はそのツールチップが閉じられるまで保持されます。  
また、後述するプラグインの設定からエディタ上のテキストと同様のポップアップウィンドウで結果を表示するようにもできます。

### Read Aloud Text

デフォルトのショートカットキーは```Shift + Ctrl + V```で、マウスポインタ直下にあるテキストを読み上げます。

### Open Advanced Translation Panel

https://user-images.githubusercontent.com/51815450/183342413-270417d3-6968-4fb7-9094-88b0a46e1ba5.mp4

デフォルトのショートカットキーは割り当てられていません。割り当てた場合、翻訳パネルを表示することができます。

![OpenTranslationPanelMenu](https://user-images.githubusercontent.com/51815450/183342454-cf985a4c-a5db-43d4-afd2-973e5b4a5514.PNG)

レベルエディタ上部のWindowメニューから翻訳パネルを表示することができます。

![AdvancedTranslationPanel](https://user-images.githubusercontent.com/51815450/183342487-9be57407-e625-4fcf-b839-e5d447bf8f47.PNG)

基本的にはポップアップウィンドウと変わりませんが、翻訳パネルではいくつか機能が追加されています。  

| **ボタン** | **機能**                           |
|---------|----------------------------------|
| ゴミ箱ボタン  | 翻訳パネルを空の状態に戻します。                 |
| 履歴ボタン   | 翻訳履歴のリストを表示して、選択された履歴をパネルに表示します。 |
| コピーボタン  | 翻訳後のテキストをクリップボードにコピーします。         |

また、スペルや翻訳元言語が間違っている場合は、改善案をパネル下部で表示し、リンクをクリックするとスペルや翻訳元言語が修正されます。

## オプション

![ShortcutKeySettings](https://user-images.githubusercontent.com/51815450/183342519-5972f6a2-32e0-4412-8b99-a877cd3b937b.PNG)

ここまででご紹介したショートカットキーはエディタ環境設定のキーボードショートカットから変更できます。

![Settings](https://user-images.githubusercontent.com/51815450/183342556-feee7b9d-0944-4890-bfce-d02e673d3e88.PNG)

| **カテゴリ**                 | **項目**                                     | **説明**                                                                                  |
|--------------------------|--------------------------------------------|-----------------------------------------------------------------------------------------|
| General                  | Translator                                 | 翻訳エンジンを指定します。デフォルトで用意されている翻訳エンジンについては後述します。                                             |
|                          | Speaker                                    | テキスト読み上げに使うAPIを指定します。デフォルトで用意されているAPIについては後述します。                                        |
|                          | Formatter                                  | 翻訳するテキストへの変換や、置き換える文字列のフォーマットを生成するクラスを指定します。デフォルトで用意されているクラスについては後述します。                 |
|                          | Primary Language                           | 最優先で使用される言語を指定します。言語を指定しない場合はこの言語がデフォルトで使用されます。                                         |
|                          | Secondary Language                         | 翻訳元の言語がPrimary Languageと同じだった場合などに使用される言語を指定します。                                        |
| Font                     | Text Font                                  | ポップアップウィンドウや翻訳パネルなどの翻訳元と翻訳後のテキストで使用されるフォントを指定します。                                       |
|                          | Pronunciation Font                         | ポップアップウィンドウや翻訳パネルなどの翻訳元と翻訳後の発音テキストで使用されるフォントを指定します。                                     |
| Selector                 | Panel Size                                 | 翻訳先の言語や置き換えるテキストのフォーマットなどのセレクタUIのパネルサイズを指定します。                                          |
|                          | Is Select When Double Click                | セレクタUIで項目を選択するのにダブルクリックをする必要があるかどうかを指定します。                                              |
| Selector-Language Picker | Display Text Format                        | 言語選択をするUIで各項目の言語の表示フォーマットを指定します。                                                        |
| Selector-Language Picker | Can Search By Language Code                | 言語選択をするUIの検索欄で言語コードでの検索ができるかどうかを指定します。                                                  |
| Translate                | Play Speaker Automatically                 | ポップアップウィンドウを表示した時に翻訳元、または翻訳後のテキストを自動的に読み上げるかどうかを指定します。                                  |
|                          | Determine Panel Size Manually              | ポップアップウィンドウのサイズを手動で設定するかどうかを指定します。                                                      |
|                          | Panel Height Scale                         | ポップアップウィンドウのサイズを計算するときに使用されるウィンドウの高さのスケール。 bDeterminePanelSizeManuallyがfalseの場合に設定できます。 |
|                          | Panel Size                                 | ポップアップウィンドウのサイズを指定します。 bDeterminePanelSizeManuallyがtrueの場合に設定できます。                      |
| Translate And Replace    | Is Select Target Language Before Translate | 翻訳前に翻訳先の言語を選択するセレクタUIを表示するかどうかを指定します。                                                   |
| Translate Tooltip        | Use Simple Translate Panel                 | 翻訳結果をポップアップウィンドウで表示するかどうかを指定します。                                                        |
| Read Aloud Text          | Read Aloud Text Slowly                     | テキスト読み上げの速度をゆっくりにするかどうかを指定します。                                                          |
| Notification             | Notification Severity                      | このプラグインによって発行される通知のメッセージログにフォーカスする重大度を指定します。                                            |

### デフォルトで用意されている翻訳エンジン

#### ・Google Translate (No API key required)  
PythonScriptPluginからPythonの [googletrans](https://pypi.org/project/googletrans) モジュールを使用して翻訳を行います。  
APIキーなどは不要ですが、１時間当たりの翻訳リクエストの数に制限があります。

#### ・Libre Translate  
[Libre TranslateのWeb API](https://github.com/LibreTranslate/LibreTranslate) を使用して翻訳を行います。
APIキーなどは不要で、翻訳リクエストの数などの制限はありません。  
発音テキストの取得はサポートされていません。

#### ・Microsoft Translator  
[Microsoft Translator](https://api.rakuten.net/microsoft-azure-org-microsoft-cognitive-services/api/microsoft-translator-text/endpoints) を使用して翻訳を行います。  
[こちら](https://api.rakuten.net/microsoft-azure-org-microsoft-cognitive-services/api/microsoft-translator-text/pricing) からAPIキーを取得してください。  
翻訳リクエストの数は契約プランによって違いますが、フリープランでは500000/月です。  
発音テキストの取得はサポートされていません。  

#### ・DeepL Translate (No API key required)  
PythonScriptPluginからPythonの [deepl-translate](https://pypi.org/project/deepl-translate/) モジュールを使用して翻訳を行います。  
APIキーなどは不要ですが、１時間当たりの翻訳リクエストの数に制限があります。  
発音テキストの取得はサポートされていません。  

### デフォルトで用意されているテキスト読み上げに使うAPI

#### ・Google Text To Speech (No API key required)
PythonScriptPluginからPythonの [gTTS](https://pypi.org/project/gTTS/) モジュールと [pyglet](https://pypi.org/project/pyglet/) モジュールを使用してテキストの読み上げを行います。  
APIキーなどは不要です。

### デフォルトで用意されているフォーマッタークラス

#### ・DefaultFormatter
翻訳するテキストへの変換には```FName::NameToDisplayString```を使用します。  
翻訳結果のフォーマットはいくつかの区切り文字といくつかの命名パターンの組み合わせを生成します。  
いずれの変換でもテキストに改行が含まれる場合は変換を行いません。

## コンソールコマンド

| **コマンド**                                                  | **引数**                                                                | **説明**                                     |
|-----------------------------------------------------------|-----------------------------------------------------------------------|--------------------------------------------|
| TranslationToolkit.Translator.Translate                   | Text[FString] Source Language Code[FName] Target Language Code[FName] | 翻訳する文字列、翻訳前の言語コード、翻訳後の言語コードを指定して、翻訳を開始します。 |
| TranslationToolkit.Translator.DetectLanguage              | Text[FString]                                                         | 指定された文字列がどの言語であるかを検出します。                   |
| TranslationToolkit.Translator.GetSupportedSourceLanguages |                                                                       | サポートされている翻訳ソース言語のリストをログ出力します。              |
| TranslationToolkit.Translator.GetSupportedTargetLanguages | SourceLanguage[FName]                                                 | サポートされている翻訳対象言語のリストをログ出力します。               |
| TranslationToolkit.Translator.GetHistories                |                                                                       | キャッシュされた履歴のリストをログ出力します。                    |
| TranslationToolkit.Translator.ClearHistories              |                                                                       | ディスク上のキャッシュされた履歴データを削除します。                 |
| TranslationToolkit.Speaker.PlaySpeaker                    | Text[FString] Source Language Code[FName] Is Slowly[bool]             | 読み上げる文字列とその文字列の言語コードを指定して、音声読み上げを開始します。    |
| TranslationToolkit.Speaker.StopSpeaker                    |                                                                       | 現在再生中のオーディオを停止します。                         |
| TranslationToolkit.Speaker.IsPlayingSpeaker               |                                                                       | テキストが現在読み上げられているかどうかをログ出力します。              |
| TranslationToolkit.Speaker.GetCurrentProgress             |                                                                       | 現在の再生の進行状況をログに記録します。                       |
| TranslationToolkit.Speaker.GetSupportedLanguages          |                                                                       | サポートされている言語のリストをログ出力します。                   |
| TranslationToolkit.Formatter.ConvertToTranslatableText    | Text[FString]                                                         | 指定された文字列を翻訳可能な形式に変換してログ出力します。              |
| TranslationToolkit.Formatter.ConvertToFormattedTexts      | Text[FString]                                                         | 翻訳結果の文字列をさまざまな形式の文字列に変換してログ出力します。          |

## 作者

[Naotsun](https://twitter.com/Naotsun_UE)

## 履歴

- (2023/09/09) v1.9   
  UE5.3に対応しました  
  エディタ環境設定にあるプラグインの設定を全てのプロジェクト共通で保存されるようにしました  

- (2023/05/13) v1.8   
  UE5.2に対応しました  

- (2023/02/28) v1.7   
  DeepLの翻訳エンジンを追加しました  

- (2022/11/08) v1.6   
  UE5.1に対応しました  

- (2022/08/08) v1.5   
  ポップアップウィンドウに翻訳元と翻訳後のテキストをコピーするボタンを追加しました

- (2022/04/06) v1.4   
  翻訳パネルにプラグインの設定画面を開くボタンを追加しました

- (2022/01/24) v1.3   
  Microsoft Translatorの翻訳エンジンを追加

- (2022/01/18) v1.2   
  エディタ環境設定での変更をSavedフォルダ以下のiniファイルにセーブするように

- (2021/12/13) v1.1   
  UE4.25以前のバージョンでも最低限の機能は使用できるように（マーケットプレイスではサポートしていないため、手動でダウングレードする必要があります）  
  ポップアップウィンドウのサイズをエディタ環境設定から指定できるように  

- (2021/11/06) v1.0   
  プラグインを公開
