# 目次

- [リファレンス](#リファレンス)
  - [console](#console)
  - [SpreadsheetApp](#spreadsheetapp)
    - [Spreadsheet](#spreadsheet)
    - [Sheet](#sheet)
    - [Range](#range)
  - [MailApp](#mailapp)
  - [DocumentApp](#documentapp)
  - [DriveApp](#driveapp)
  - [FormApp](#formapp)
    - [Form](#form)
    - [Item](#item)
    - [MultipleChoiceItem](#multiplechoiceitem)
    - [Choice](#choice)
  - [CalendarApp](#calendarapp)
    - [Calendar](#calendar)
    - [CalendarEvent](#calendarevent)
  - [File](#file)
  - [UrlFetchApp](#urlfetchapp)
  - [Utilities](#utilities)
- [グラフ関連](#グラフ関連)
  - [Sheet](#sheet-1)
    - [EmbeddedChartBuilder](#embeddedchartbuilder)
    - [EmbeddedColumn/Line/PieChartBuilder](#embeddedcolumnlinepiechartbuilder)
    - [PieChartBuilder](#piechartbuilder)
    - [setOption(option, value)関連](#setoptionoption-value関連)
      - [Column chart](#column-chart)
      - [Line chart](#line-chart)
      - [Pie chart](#pie-chart)
- [ライブラリ](#ライブラリ)
  - [Parser](#parser)

# リファレンス
## console
* [console.log(formatOrObject, values)](https://developers.google.com/apps-script/reference/base/console)
  * 実行時、もしくはデバッグ実行時にログへ文字列を出力する関数。

## SpreadsheetApp
* [openByUrl(url)](https://developers.google.com/apps-script/reference/spreadsheet/spreadsheet-app#openByUrl(String))
  * スプレッドシートのURLから、[Spreadsheet オブジェクト](https://developers.google.com/apps-script/reference/spreadsheet/spreadsheet) を返す。

### Spreadsheet
* [getSheetByName(name)](https://developers.google.com/apps-script/reference/spreadsheet/spreadsheet#getSheetByName(String))
  * スプレッドシートからシート名を指定してシートを取得し、[Sheet オブジェクト](https://developers.google.com/apps-script/reference/spreadsheet/sheet) を返す。

### Sheet
* [getRange(a1Notation)](https://developers.google.com/apps-script/reference/spreadsheet/sheet#getRange(String))
  * `'A1'` のような特定のセルを指定して範囲を取得し [Range オブジェクト](https://developers.google.com/apps-script/reference/spreadsheet/range) を返す。
* [getRange(row, column, numRows, numColumns)](https://developers.google.com/apps-script/reference/spreadsheet/sheet#getRange(Integer,Integer,Integer,Integer))
  * 基準となるセルを座標で指定し、そこから何行・何列の範囲をとるか指定することで範囲を取得できる。
    * row：基準となるセルの行
    * colum：基準となるセルの列
    * numRows：取得したい範囲の行数
    * numColumns：取得したい範囲の列数
* [getActiveSheet()](https://developers.google.com/apps-script/reference/spreadsheet/spreadsheet-app#getActiveSheet())
  * 現在開かれているシートの [Sheet オブジェクト](https://developers.google.com/apps-script/reference/spreadsheet/sheet) を取得する。
* [getLastRow](https://developers.google.com/apps-script/reference/spreadsheet/sheet?hl=en#getlastrow)
  * 一番最後の行を取得する

### Range
* [getValue()](https://developers.google.com/apps-script/reference/spreadsheet/range#getValue())
  * 範囲の左上の値を取得。セルのデータによっては、数値や真偽値、日付や文字列など様々な値を返す。
  * またセルの中身が空の場合は空の文字列を返す。
* [setValue(value)](https://developers.google.com/apps-script/reference/spreadsheet/range#setValue(Object))
  * 範囲に１つだけ値（数値、文字列、日付、式など）を書き込む関数。
* [getValues()](https://developers.google.com/apps-script/reference/spreadsheet/range#getValues())
  * 範囲の表データを取得し2次元配列を返す。  
  セルのデータによっては、数値や真偽値、日付や文字列など様々な値を返す。またセルの中身が空の場合は空の文字列を返す。  
  * 表は座標 `1, 1` から始まるが、JavaScript の配列は `[0][0]` から始まるので注意。
* [setBackground(color)](https://developers.google.com/apps-script/reference/spreadsheet/range#setBackground(String))
  * 引数に設定したい背景色を指定すると、範囲の全てのセルの背景色を設定することができる。
* [setFontColor(color)](https://developers.google.com/apps-script/reference/spreadsheet/range#setFontColor(String))
  * 引数に設定したい文字色を指定すると、範囲の全てのセルの文字色を設定することができる。

## MailApp
* [sendEmail(recipient, subject, body) ](https://developers.google.com/apps-script/reference/mail/mail-app#sendEmail(String,String,String))
  * 現在ログインしているアカウントからメールを送信。
    * recipient：送信先
    * subject：件名
    * body：本文

## DocumentApp
* [getBody()](https://developers.google.com/apps-script/reference/document/document#getBody())
  * ドキュメント全体(body)を扱う [Body オブジェクト](https://developers.google.com/apps-script/reference/document/body)を取得できる
* [setText(text) ](https://developers.google.com/apps-script/reference/document/body#setText(String))
  * テキストを書き込むことができる

## DriveApp
* [getFileById(id) ](https://developers.google.com/apps-script/reference/drive/drive-app?hl=en#getfilebyidid)
  * 指定されたIDの[File オブジェクト](https://developers.google.com/apps-script/reference/drive/file)を取得する。

## FormApp
* [openById()](https://developers.google.com/apps-script/reference/forms/form-app#openById(String))
  * フォームの ID でそのフォームの情報を持つ [Form オブジェクトを取得します。ただしこれを使ってフォームの情報を取得できるのは権限を持つユーザのみ。

### Form
* [getResponses()](https://developers.google.com/apps-script/reference/forms/form#getResponses())
  * フォームの全ての回答データ [FormResponse](https://developers.google.com/apps-script/reference/forms/form-response) を配列で取得します。
* [getItems()](https://developers.google.com/apps-script/reference/forms/form#getItems())
  * フォームの全ての質問項目 [Item](https://developers.google.com/apps-script/reference/forms/item) を配列で取得。

### Item
* [getTitle()](https://developers.google.com/apps-script/reference/forms/item#getTitle())
  * 質問のタイトルを取得
* [asMultipleChoiceItem](https://developers.google.com/apps-script/reference/forms/item#asMultipleChoiceItem())
  * 複数の項目の中から選択する質問の場合は、[MultipleChoiceItem](https://developers.google.com/apps-script/reference/forms/multiple-choice-item) を取得。
### MultipleChoiceItem
* [getChoices()](https://developers.google.com/apps-script/reference/forms/multiple-choice-item#getChoices())
  * 複数項目から選択する質問の全ての選択肢 [Choice](https://developers.google.com/apps-script/reference/forms/choice) を配列で取得できる。

### Choice

* [getValue()](https://developers.google.com/apps-script/reference/forms/choice#getValue())
  * 選択肢の値を取得する。

## CalendarApp
* [getCalendarById(id)](https://developers.google.com/apps-script/reference/calendar/calendar-app#getCalendarById(String))
  * IDを指定して[Calendar オブジェクト](https://developers.google.com/apps-script/reference/calendar/calendar)を取得できる。
### Calendar
* [getEventsForDay(date)](https://developers.google.com/apps-script/reference/calendar/calendar#getEventsForDay(Date))
  * 指定した日付のイベントを全て取得できる。
    * date：Dateオブジェクトで指定
### CalendarEvent
* [getTitle()](https://developers.google.com/apps-script/reference/calendar/calendar-event#getTitle())
  * 予定の題名を取得
* [getStartTime()](https://developers.google.com/apps-script/reference/calendar/calendar-event#getStartTime())
  * 予定の開始時刻を取得
* [getEndTime()](https://developers.google.com/apps-script/reference/calendar/calendar-event#getEndTime())
  * 予定の終了時刻を取得

## File
* [getBlob() ](https://developers.google.com/apps-script/reference/drive/file?hl=en#getblob)
  * オブジェクト内のデータを[blob オブジェクト ](https://developers.google.com/apps-script/reference/base/blob.html)として返す。

## UrlFetchApp

* [UrlFetchApp.fetch(url) ](https://developers.google.com/apps-script/reference/url-fetch/url-fetch-app)
  * URL を関数の引数に指定すると、その URL のページにアクセスして HTML を取得する。
* [getContentText(charset) ](https://developers.google.com/apps-script/reference/url-fetch/http-response#getcontenttextcharset)
  * 指定した文字コードに変換する。

## Utilities
* [formatDate(Date,String,String)](https://developers.google.com/apps-script/reference/utilities/utilities#formatDate(Date,String,String))
  * 見やすい日時に変換する。

# グラフ関連

## Sheet
* [newChart()](https://developers.google.com/apps-script/reference/spreadsheet/sheet#newChart())
  * チャートを構築するための汎用のチャートビルダーを返す。
* [insertChart(chart)](https://developers.google.com/apps-script/reference/spreadsheet/sheet?hl=en#insertChart(EmbeddedChart))
  * 表にチャートを埋め込む。

### EmbeddedChartBuilder
* [asColumnChart()](https://developers.google.com/apps-script/reference/spreadsheet/embedded-chart-builder?hl=en#ascolumnchart)
  * 縦棒グラフ用のチャートビルダーを返す。
* [asLineChart()](https://developers.google.com/apps-script/reference/spreadsheet/embedded-chart-builder?hl=en#aslinechart)
  * 線グラフ用のチャートビルダーを返す。
* [asPieChart()](https://developers.google.com/apps-script/reference/spreadsheet/embedded-chart-builder?hl=en#aspiechart)
  * 円グラフ用のチャートビルダーを返す。



### EmbeddedColumn/Line/PieChartBuilder
※リンクはすべてColumn
* [addRange(range)](https://developers.google.com/apps-script/reference/spreadsheet/embedded-column-chart-builder?hl=en#addRange(Range))
  * チャートに含めるデータの範囲を設定する。
* [setNumHeaders(headers)](https://developers.google.com/apps-script/reference/spreadsheet/embedded-column-chart-builder?hl=en#setNumHeaders(Integer))
  * 見出しの行数が何個あるのかを設定する。
* [setPosition(anchorRowPos, anchorColPos, offsetX, offsetY)](https://developers.google.com/apps-script/reference/spreadsheet/embedded-column-chart-builder?hl=en#setPosition(Integer,Integer,Integer,Integer))
  * チャートを書き出すセルの指定と位置を微調整できる。
第一引数と第二引数でセルの行と列を指定し、第三引数と第四引数で何ピクセルかずらして表示することも可能。
* [setOption(option, value)](https://developers.google.com/apps-script/reference/spreadsheet/embedded-column-chart-builder?hl=en#setPosition(Integer,Integer,Integer,Integer))
  * チャートに様々なオプションを設定できる。
* [build()](https://developers.google.com/apps-script/reference/spreadsheet/embedded-column-chart-builder?hl=en#build())
  * チャートを生成。

### PieChartBuilder
* [setTransposeRowsAndColumns(transpose)](https://developers.google.com/apps-script/reference/spreadsheet/embedded-pie-chart-builder#setTransposeRowsAndColumns(Boolean))
  * チャートの行と列を入れ替える。

### setOption(option, value)関連
※詳細は[configuration options](https://developers.google.com/apps-script/chart-configuration-options?hl=en)にて該当する各項目を参照されたし。
#### Column chart
* title
  * グラフのタイトル
* hAxis.direction
  * Horizontal axis(横軸)の方向

#### Line chart
* title
  * グラフのタイトル
* hAxis.direction
  * Horizontal axis(横軸)の方向

#### Pie chart
* title
  * グラフのタイトル


# ライブラリ

## Parser
* データを解析できる簡単なライブラリ
  * library_key: M1lugvAXKKtUxn_vdAG9JZleS6DrsjUUV
    * .data(content)：調べたい要素
    * .setLog()：解析中のログを確認したければつける
    * .from(fromText)：どこから
    * .to(toText)：どこまで
    * .build();：一致する要素を見つけたらそこで解析を終了(その後一致する要素があっても無視する)
