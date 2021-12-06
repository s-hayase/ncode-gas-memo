# リファレンス

  - [console](#console)
  - [SpreadsheetApp](#spreadsheetapp)
    - [Sheet](#sheet)
    - [Range](#range)
  - [MailApp](#mailapp)
  - [DocumentApp](#documentapp)
  - [DriveApp](#driveapp)
  - [File](#file)

## console
* [console.log(formatOrObject, values)](https://developers.google.com/apps-script/reference/base/console)
  * 実行時、もしくはデバッグ実行時にログへ文字列を出力する関数。

## SpreadsheetApp
* [openByUrl(url)](https://developers.google.com/apps-script/reference/spreadsheet/spreadsheet-app#openByUrl(String))
  * スプレッドシートのURLから、[Spreadsheet オブジェクト](https://developers.google.com/apps-script/reference/spreadsheet/spreadsheet) を返す。
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
  * ドキュメント全体(body)を扱う Body オブジェクトを取得できる
* [setText(text) ](https://developers.google.com/apps-script/reference/document/body#setText(String))
  * テキストを書き込むことができる

## DriveApp
* [getFileById(id) ](https://developers.google.com/apps-script/reference/drive/drive-app?hl=en#getfilebyidid)
  * 指定されたIDの[File オブジェクト](https://developers.google.com/apps-script/reference/drive/file)を取得する。

## File
* [getBlob() ](https://developers.google.com/apps-script/reference/drive/file?hl=en#getblob)
  * オブジェクト内のデータを[blob オブジェクト ](https://developers.google.com/apps-script/reference/base/blob.html)として返す。

