# Power BI Hands-on training

## csv ファイルをソースとしたレポート作成

<br />

### **INDEX**

- [CSV ファイルからデータを取得](#CSV-ファイルからデータを取得)
- [Excel ブックからデータを取得](#Excel-ブックからデータを取得)
- [メジャーの作成](#メジャーの作成)
- [レポートの作成](#レポートの作成)

<br />

### **CSV ファイルからデータを取得**

- Power BI Desktop を起動

- **データを取得** - **テキスト/CSV** をクリック

  <img src="images/get-data-from-SQL-Database-01.png" />

- **商品マスタ.csv** を選択し **読み込み** を選択

  - 元のファイル： **65001: Unicode (UTF-8)**

  - 区切り記号： **コンマ**

  - データ型検出： **最初の 200 行に基づく**

    <img src="images/get-CSV-File-01.png" />

- **データを取得** - **テキスト/CSV** をクリック

- **売上データ.csv** を選択し、**データの変換** をクリック

  - 元のファイル： **65001: Unicode (UTF-8)**

  - 区切り記号： **コンマ**

  - データ型検出： **最初の 200 行に基づく**

    <img src="images/get-CSV-FIle-03.png" />

- Power Query エディターが起動

  <img src="images/power-Query-Editor-00.png" />

- **列の追加** タブを選択し **カスタム列** をクリック

  <img src="images/add-Custom-Column-01.png" />

- 列名、式を入力し **OK** をクリック

  - 新しい列名： **年**

  - カスタム列の式： 

    ```
    Text.From(Date.Year([年月日])) & "年"
    ```

    <img src="images/add-Custom-Column-02.png" />

- **年** 列が追加

- 年列をドラッグし、年月日列の右へドロップ

  <img src="images/add-Custom-Column-03.png" />

- 年列が左から２列目へ移動

  <img src="images/add-Custom-Column-04.png" />

- 行った操作がすべて記録されていることを確認

  <img src="images/add-Custom-Column-05.png" />

- **ホーム** タブを選択し **閉じて適用** をクリック

  <img src="images/add-Custom-Column-06.png" />

- フィールドに読み込んだデータが表示

  <img src="images/get-CSV-File-02.png" />

<br />

### **Excel ブックからデータを取得**

- **データを取得** - **Excel ブック** をクリック

- **都道府県.xlsx** を選択して開く

- **都道府県マスタ** シートを選択し **データの変換** をクリック

  <img src="images/get-Excel-File.png" />

- Power Query エディターが起動

  <img src="images/power-Query-Editor-01.png" />

- **行の削除** - **上位の行の削除** を選択

  <img src="images/delete-Top-2-Rows-01.png" />

- 削除する行数に **2** を入力し **OK** をクリック 

  <img src="images/delete-Top-2-Rows-02.png" />

- 不要な上位２行が削除

  <img src="images/delete-Top-2-Rows-03.png" />

  ※実行した処理はステップとして記録

  <img src="images/record-Operation-01.png" />

  ※ステップは追加・更新・削除が可

- **都道府県別地方一覧** 列を列名をクリックして選択

- **列の削除** - **列の削除** を選択

  <img src="images/delete-Column-01.png" />

- 不要な列を削除

  <img src="images/delete-Column-02.png" />

- **1 行目をヘッダーとして使用** をクリック

  <img src="images/set-Header-Row-01.png" />

- 地方区分、都道府県区分が列名に変換

  <img src="images/set-Header-Row-02.png" />

- **No** 列を選択

- **変換** メニューを表示し、**名前の変更** をクリック

  <img src="images/change-Column-Name-01.png" />

- 列名を **地方区分No** に変更

  <img src="images/change-Column-Name-02.png" />

- **地方区分No** 列と **地方区分** 列を選択

  <img src="images/fill-01.png" />

  ※Ctrl キーを押しながら２つの列を選択

- **フィル** - **下** をクリック

  <img src="images/fill-02.png" />

- null 値のレコードに上の行の値がコピー

  <img src="images/fill-03.png" />

- **インデックス列** - **1 から** をクリック

  <img src="images/create-Index-Column-01.png" />

- テーブルにインデックス列が追加

  <img src="images/create-Index-Column-02.png" />

- 列名を右クリックし **名前の変更** を選択

  <img src="images/create-Index-Column-03.png" />

- 列名を **都道府県No** に変更

  <img src="images/create-Index-Column-04.png" />

- **移動** - **先頭に移動** を選択

  <img src="images/move-Column-01.png" />

- **都道府県No** 列がテーブルの先頭へ移動

  <img src="images/move-Column-02.png" />

- 行った操作がすべて記録されていることを確認

  <img src="images/record-Operation-02.png" />

- **ホーム** タブを選択し **閉じて適用** をクリック

  <img src="images/close-Editor.png" />

- フィールドに **都道府県マスタ** が追加

  <img src="images/add-Prefecture-Master.png" />

- 画面左の **モデル** (<img src="images/icon-Model.png" width="15" />) をクリック

- 取り込んだデータがテーブルとして表示

  <img src="images/model-Sales-Data-01.png" />

- **都道府県マスタ** の **都道府県No** 列をドラッグし **売上データ** の **都道府県ID** へドロップ

- 売上データと都道府県マスタの間にリレーション シップが作成

  <img src="images/model-Sales-Data-02.png" />

- **都道府県マスタ** の **地方区分** を右クリックし、メニューから **階層の作成** をクリック

  <img src="images/add-Area-Hierarchy-01.png" />

- **地方区分 階層** が追加

  <img src="images/add-Area-Hierarchy-02.png" />

- **都道府県区分** を右クリックし、メニューから **階層に追加** - **地方区分 階層** を選択

  <img src="images/add-Area-Hierarchy-03.png" />

- **地方区分 階層** に **都道府県区分** が追加

  <img src="images/add-Area-Hierarchy-04.png" />


<br />

### **メジャーの作成**

- 画面左の **データ** (<img src="images/icon-Table.png" width="15" />) をクリック

- **売上データ** を選択

- **新しい列** をクリック

  <img src="images/add-Related-Column-01.png" />

- 数式を入力し Enter キーを押下

  ```
  販売単価 = RELATED('商品マスタ'[販売単価])
  ```

  <img src="images/add-Related-Column-02.png" />

- 書式を設定

  - 書式： **通貨**

  - ＄： **¥ 日本語 (日本)**

    <img src="images/add-Related-Column-03.png" />

- 同様の手順で３つの列を追加

  - 売上列

    ```
    売上 = [販売単価] * [数量]
    ```

    書式を通貨、日本円に設定

  - 仕入価格列

    ```
    仕入価格 = RELATED('商品マスタ'[仕入価格] 
    ```

    書式を通貨、日本円に設定

  - 粗利益列

    ```
    粗利益 = ([販売単価]-[仕入価格])*[数量]
    ```

    書式を通貨、日本円に設定

- **テーブル ツール** タブの **新しいメジャー** をクリック

  <img src="images/add-New-Measure-01.png" />

- 数式を入力し、書式を設定

  ```
  売上合計 = SUM('売上データ'[売上])
  ```

  <img src="images/add-New-Measure-02.png" />

  書式を通貨、日本円に設定

- 同様の手順で２つのメジャーを作成

  - 粗利益合計メジャー

    ```
    粗利益合計 = SUM('売上データ'[粗利益])
    ```

    書式を通貨、日本円に設定

  - 粗利率メジャー

    ```
    粗利率 = DIVIDE([粗利益合計], [売上合計])
    ```

    書式をパーセンテージ、小数点以下の桁数 2 に設定

- 売上データ

  <img src="images/field-Sales-Data.png" />

<br />

### **レポートの作成**

- 画面左のレポート (<img src="images/icon-Report.png" width="15" />) をクリック

- **視覚化** の **カード** をクリック

  <img src="images/visual-card.png" />

- **売上合計** をドラッグし **フィールド** にドロップ

  <img src="images/set-Card-01.png" />

- **書式** (<img src="images/icon-Format.png" width="15" />) をクリック

- **データ ラベル** を展開し **表示単位** を **百万** に変更

  <img src="images/set-Card-02.png" />

- **背景** を展開し、**テーマの色** を選択

  <img src="images/set-Card-03.png" />

- 幅、高さ、配置場所を調整

  <img src="images/set-Card-04.png" />

- 同様の手順でカードを配置し、フィールドに **数量** を設定

  <img src="images/set-Card-05.png" />

- 幅、高さ、配置場所を調整

  <img src="images/set-Card-06.png" />

- **視覚化** の **スライサー** をクリック

  <img src="images/visual-slicer.png" />

- **年月日** をドラッグし、**フィールド** にドロップ

  <img src="images/set-Slicer-Date.png" />

- 同様の手順でスライサーを配置

- **地方区分** をドラッグし、**フィールド** にドロップ

  <img src="images/set-Slicer-Area.png" />

- **書式** (<img src="images/icon-Format.png" width="15" />) をクリック

- **全般** を展開し **方向** を **横** に設定

  <img src="images/set-Slicer-Area-Format-01.png" />

- **項目** を展開し **フォントの色**、**背景** を設定

  <img src="images/set-Slicer-Area-Format-02.png" />

- 幅、高さ、配置場所を調整

  <img src="images/set-Slicer-Area-Format-03.png" />

- **視覚化** の **リボン** をクリック

  <img src="images/visual-Ribbon.png" />

- **軸**、**凡例**、**値** にフィールドを配置

  - 軸： **年月日** (売上データ)

  - 凡例： **商品名称** (商品マスタ)

  - 値： **売上合計** (売上データ)

    <img src="images/set-Ribbon-Graph.png" />

- 幅、高さ、配置場所を調整

  <img src="images/set-Ribbon-Graph-02.png" />

- <img src="images/icon-DrillDown.png" width="15" /> をクリック

  <img src="images/drill-Down-Ribbon-Graph-01.png" />

- １レベル下の階層（四半期）まで展開して表示

  <img src="images/drill-Down-Ribbon-Graph-02.png" />

- **視覚化** の **ドーナッツ グラフ** をクリック

  <img src="images/visual-Doughnutes.png" />

- **凡例**、**値** を指定

  - 凡例： **商品名称** (商品マスタ)

  - 値： **売上合計** (売上データ)

    <img src="images/set-Doughnutes-01.png" />

- 幅、高さ、配置場所を調整

  <img src="images/set-Doughnutes-02.png" />

- 同様の手順でドーナッツ グラフを設定

  - 凡例： **商品名称** (商品マスタ)

  - 値： **数量** (売上データ)

    <img src="images/set-Doughnutes-03.png" />

- 幅、高さ、配置場所を調整

  <img src="images/set-Doughnutes-04.png" />

- **視覚化** の **マトリックス** をクリック

  <img src="images/visual-Matrix.png" />

- **行**、**値** を指定

  - 行： **地方区分 階層** (都道府県マスタ)

  - 値： **売上合計**, **数量**, **粗利益合計**, **粗利率** (売上データ)

    <img src="images/set-Matrix-Area-01.png" />

- 幅、高さ、配置場所を調整

  <img src="images/set-Matrix-Area-02.png" />

- 画面左の **データ** (<img src="images/icon-Table.png" width="15" />) をクリック

- **都道府県マスタ** を選択し、**地方区分** 列を選択

  <img src="images/set-Sort-Area-No-01.png" />

- **列で並べ替え** - **地方区分No** を選択

  <img src="images/set-Sort-Area-No-02.png" />

- 同様の手順で **都道府県区分** を **都道府県区分No** で並べ替え

  <img src="images/set-Sort-Area-No-03.png" />

- 画面左のレポート (<img src="images/icon-Report.png" width="15" />) をクリック

- 地方区分が北海道から九州の順にソートされることを確認

  <img src="images/set-Sort-Area-No-04.png" />

- <img src="images/icon-DrillDown.png" width="15" /> をクリック

- 都道府県レベルまで展開されることを確認

  <img src="images/set-Matrix-Area-03.png" />

- **書式** (<img src="images/icon-Format.png" width="15" />) をクリック

- 検索ボックスに **階段** と入力

- **階段状レイアウト** を **オフ** に設定

  <img src="images/set-Matrix-Area-04.png" />

- 都道府県区分が列として表示されることを確認

  <img src="images/set-Matrix-Area-05.png" />

- レポートの完成

  <img src="images/report-Sales-Data-01.png" />

- スライサーのフィルタリングがすべてのビジュアルに反映されることを確認

  <img src="images/report-Sales-Data-02.png" />

- **ファイル** メニューの **名前を付けて保存** で作成したレポートを保存
