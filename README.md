# TranslationToolkit

![Plugin](https://user-images.githubusercontent.com/51815450/183342025-2f6691d8-a665-49cb-9e63-bed7b0cee14f.PNG)

<!--ts-->
  * [Description](#Description)
  * [Requirement](#Requirement)
  * [Installation](#Installation)
  * [Features And Usages](#features-and-usages)
    * [Translate](#translate)
    * [Translate And Replace](#translate-and-replace)
    * [Translate Tooltip](#translate-tooltip)
    * [Read Aloud Text](#read-aloud-text)
    * [Open Advanced Translation Panel](#open-advanced-translation-panel)
  * [Settings](#Settings)
    * [Translation engine provided by default](#translation-engine-provided-by-default)
      * [Google Translate (No API key required)](#google-translate-no-api-key-required)
      * [Libre Translate](#libre-translate)
      * [Microsoft Translator](#microsoft-translator)
    * [API used for reading text provided by default](#api-used-for-reading-text-provided-by-default)
      * [Google Text To Speech (No API key required)](#google-text-to-speech-no-api-key-required)
    * [Formatter class provided by default](#formatter-class-provided-by-default)
      * [DefaultFormatter](#defaultformatter)
  * [Console Command](#console-command)
  * [Author](#Author)
  * [History](#History)
<!--te-->

## Description

This plugin can translate text and tooltips in the Unreal Engine editor and display the results in a pop-up window.    
It also has the ability to translate the selected text and replace it with the translation result.  

## Requirement

Target version : UE4.25 ～ 5.0  
Target platform : Windows    

UE4.25 can only use Libre Translate as a translation engine and cannot read aloud.  

## Installation  

Install from the [marketplace](https://www.unrealengine.com/marketplace/en/product/translation-toolkit).  
If the feature is not available after installing the plugin, it is possible that the plugin has not been enabled, so please check if the plugin is enabled from Edit > Plugins.

## Features And Usages

### Translate

https://user-images.githubusercontent.com/51815450/183342098-c2a65691-2401-46e0-8859-811baf1c00c1.mp4

The default shortcut key is ```Shift + Ctrl + Z```, which translates the text under the mouse pointer and displays the result in a pop-up window.  

![SimpleTranslationPanel](https://user-images.githubusercontent.com/51815450/183342196-a25ce597-0f13-4f8f-bc2b-87929a1bd3b4.PNG)

Use the speaker buttons to read out the source and target text. (If the language is not supported, you will not be able to press the button.)    
The combo box next to the speaker button allows you to set the source and destination languages.  
Press the pin button in the upper right corner to view the results in the translation panel described below.    
This pop-up window will be automatically closed by clicking anywhere other than the window.  

### Translate And Replace

https://user-images.githubusercontent.com/51815450/183342242-446034f7-c05b-46d4-b1c9-d5f78db560d5.mp4

https://user-images.githubusercontent.com/51815450/183342269-fce16ad9-0f63-4f18-aabe-99b6eebe886e.mp4

The default shortcut key is ```Shift + Ctrl + X```, which translates the currently selected text and replaces it with the result.    
When used with text that does not contain line breaks, such as function or variable names, you can choose the format to replace them with.    
It is also possible to make the selector UI to choose the language to be translated into appear before the translation from the plugin settings described below.    

### Translate Tooltip

https://user-images.githubusercontent.com/51815450/183342335-3c5eaa17-2407-40f4-acb3-7d81941adb70.mp4

The default shortcut key is ```Shift + Ctrl + C```, which translates the currently displayed tooltip and replaces it with the result.    
The translation result will be kept until the tooltip is closed.    
You can also choose to display the results in a pop-up window similar to the text in the editor from the plugin settings described below.  

### Read Aloud Text

The default shortcut key is ```Shift + Ctrl + V```, which will read out the text under the mouse pointer.  

### Open Advanced Translation Panel

https://user-images.githubusercontent.com/51815450/183342413-270417d3-6968-4fb7-9094-88b0a46e1ba5.mp4

The default shortcut key is not assigned. If you assign it, you will be able to see the translation panel.  

![OpenTranslationPanelMenu](https://user-images.githubusercontent.com/51815450/183342454-cf985a4c-a5db-43d4-afd2-973e5b4a5514.PNG)

The translation panel can be displayed from the Window menu at the top of the level editor.  

![AdvancedTranslationPanel](https://user-images.githubusercontent.com/51815450/183342487-9be57407-e625-4fcf-b839-e5d447bf8f47.PNG)

Basically, it is the same as the pop-up window, but the translation panel has some additional features.

|**Button**|**Function**|
|---|---|
|Recycle bin button|Return the translation panel to its empty state.|
|History button|Display the list of translation history and show the selected history in the panel.|
|Copy button|Copy the translated text to the clipboard.|

Also, if the spelling or source language is wrong, suggestions for improvement will be displayed at the bottom of the panel, and clicking on the link will correct the spelling or source language.   

## Settings

![ShortcutKeySettings](https://user-images.githubusercontent.com/51815450/183342519-5972f6a2-32e0-4412-8b99-a877cd3b937b.PNG)

The shortcut keys introduced so far can be changed from Keyboard Shortcuts in the Editor Preferences.  

![Settings](https://user-images.githubusercontent.com/51815450/183342556-feee7b9d-0944-4890-bfce-d02e673d3e88.PNG)

|**Category**|**Item**|**Description**|
|---|---|---|
|General|Translator|Specify the translation engine. The translation engine provided by default are described later in this section.|
| |Speaker|Specifies the API to be used for text-to-speech. The APIs provided by default are described later in this section.|
| |Formatter|Specify the class to generate the conversion to text to be translated or the format of the string to be replaced. The classes provided by default are described later in this section.|
| |Primary Language|Specifies the language to be used as the highest priority. If you do not specify a language, this language will be used by default.|
| |Secondary Language|Specify the language to be used when the source language is the same as the Primary Language.|
|Font|Text Font|Specifies the font used for the source and target text in pop-up windows and translation panels.|
| |Pronunciation Font|Specifies the font used for the source and target pronunciation text in pop-up windows and translation panels.|
|Selector|Panel Size|Specifies the panel size of the selector UI. The Selector UI allows you to select the language to be translated into and the format of the text to be replaced.|
| |Is Select When Double Click|Specifies whether or not double-clicking is required to select an item in the selector UI.|
|Selector-Language Picker|Display Text Format|Specify the display format of the language for each item in the UI for language selection.|
|Selector-Language Picker|Can Search By Language Code|Specify whether or not you can search by language code in the search field of the UI for language selection.|
|Translate|Play Speaker Automatically|Specifies whether to automatically read out the source or target text when a pop-up window is displayed.|
| |Determine Panel Size Manually|Specifies whether to manually set the size of the panel that displays the translation results.|
| |Panel Height Scale|Panel height scale used when calculating the size of the panel displaying the translation results. It can be set when bDeterminePanelSizeManually is false.|
| |Panel Size|Specifies the size of the panel that displays the translation results. It can be set when bDeterminePanelSizeManually is true.|
|Translate And Replace|Is Select Target Language Before Translate|Specify whether or not to show the selector UI to select the target language before translation.|
|Translate Tooltip|Use Simple Translate Panel|Specifies whether to show the translation result in a pop-up window.|
|Read Aloud Text|Read Aloud Text Slowly|Specifies whether or not to slow down the speed of text reading.|
|Notification|Notification Severity|Specifies the severity to focus the message log of notifications issued by this plugin.|

### Translation engine provided by default

#### ・Google Translate (No API key required)
The translation is done using the [googletrans](https://pypi.org/project/googletrans) module in Python via PythonScriptPlugin.  
No API key is required, but there is a limit to the number of translation requests per hour.  

#### ・Libre Translate
The translation is done using the [Libre Translate web API](https://github.com/LibreTranslate/LibreTranslate).  
No API key is required, and there are no restrictions on the number of translation requests.    
Pronunciation text retrieval is not supported.  

#### ・Microsoft Translator
The translation is done using the [Microsoft Translator](https://api.rakuten.net/microsoft-azure-org-microsoft-cognitive-services/api/microsoft-translator-text/endpoints).  
Get your API key [here](https://api.rakuten.net/microsoft-azure-org-microsoft-cognitive-services/api/microsoft-translator-text/pricing).  
The number of translation requests depends on the contract plan, but the free plan is 500000/months.  
Pronunciation text retrieval is not supported.

### API used for reading text provided by default

#### ・Google Text To Speech (No API key required)
Text reading using Python's [gTTS](https://pypi.org/project/gTTS/) and [pyglet](https://pypi.org/project/pyglet/) modules via PythonScriptPlugin.  
No API key is required.  

### Formatter class provided by default

#### ・DefaultFormatter
Use ```FName::NameToDisplayString``` to convert the text to be translated.  
The format of the translation result produces a combination of several delimiters and several naming patterns.    
If the text contains line breaks in any of the conversions, no conversion will be performed.  

## Console Command

|**Command**|**Arguments**|**Description**|
|---|---|---|
|TranslationToolkit.Translator.Translate|Text[FString] Source Language Code[FName] Target Language Code[FName]|Specify the character string to be translated, the language code before translation, and the language code after translation, and start translation.|
|TranslationToolkit.Translator.DetectLanguage|Text[FString]|Detects what language the specified string is in.|
|TranslationToolkit.Translator.GetSupportedSourceLanguages| |Logs a list of supported translation source languages.|
|TranslationToolkit.Translator.GetSupportedTargetLanguages|SourceLanguage[FName]|Logs a list of supported translation target languages.|
|TranslationToolkit.Translator.GetHistories| |Logs a list of cached histories.|
|TranslationToolkit.Translator.ClearHistories| |Delete cached histories data and json data on disk.|
|TranslationToolkit.Speaker.PlaySpeaker|Text[FString] Source Language Code[FName] Is Slowly[bool]|Specify the sentence you want to read and the language code of that sentence, and start reading.|
|TranslationToolkit.Speaker.StopSpeaker| |Stop the currently playing audio.|
|TranslationToolkit.Speaker.IsPlayingSpeaker| |Logs whether the text is currently being read aloud.|
|TranslationToolkit.Speaker.GetCurrentProgress| |Logs the current playback progress.|
|TranslationToolkit.Speaker.GetSupportedLanguages| |Logs a list of supported languages.|
|TranslationToolkit.Formatter.ConvertToTranslatableText|Text[FString]|Converts the specified string to a translatable format and returns it.|
|TranslationToolkit.Formatter.ConvertToFormattedTexts|Text[FString]|Converts the translation result string to a string in various formats and returns it.|

## Author

[Naotsun](https://twitter.com/Naotsun_UE)

## History  

- (2022/08/08) v1.5   
  Added button to copy original and translated text in pop-up window

- (2022/04/06) v1.4   
  Added a button to open the plugin settings screen in the translation panel

- (2022/01/24) v1.3   
  Added translation engine for Microsoft Translator

- (2022/01/18) v1.2   
  Changed to save the changes in the editor environment settings to the ini file under the Saved folder

- (2021/12/13) v1.1   
  Supported to use the minimum functions even in versions prior to UE 4.25(It is not supported in the marketplace, so you will need to downgrade manually)  
  Pop-up window size can now be specified from editor preferences

- (2021/11/06) v1.0   
  Publish plugin
