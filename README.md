## filtrite (Bromite用カスタム広告ブロックフィルター生成ツール)
xarantolus氏が作成した[filtrite](https://github.com/xarantolus/filtrite)のフォークです。
日本向けのフィルターリストを追加し、説明文`README.md`を日本語にしております。それ以外は改変しておりません。

フォーク元の[filtrite](https://github.com/xarantolus/filtrite)も併せてご確認ください。

[filtrite](https://github.com/xarantolus/filtrite)は、[Bromite](https://www.bromite.org/)用のフィルターリスト生成プロジェクトです。
より詳しい情報は、[Custom Ad Block filters](https://www.bromite.org/custom-filters)をご覧ください。

# リスト
以下から任意のリストを選択し、リンクをコピーしてBromiteの設定に追加できます。Bromiteの設定＞AdBlock settingsを選択し、コピーしたフィルターURLに設定します。

| リンク | 説明  |
| ------ | ------|
| [Bromite Default](https://github.com/xperiable/filtrite-jpn/releases/latest/download/bromite-default.dat) | Bromite[デフォルトフィルター](https://github.com/bromite/filters)リスト（filtriteで生成） |
| [Bromite Extended](https://github.com/xperiable/filtrite-jpn/releases/latest/download/bromite-extended.dat) | Bromiteデフォルトフィルターに、「デスクトップ用[uBlock Origin](https://github.com/gorhill/uBlock)で使用する迷惑ブロッカー」を追加したリスト |
| [Bromite Extended (Soft)](https://github.com/xperiable/filtrite-jpn/releases/latest/download/bromite-extended-soft.dat) | Bromite Extendedリストと同じですが、より積極的なフィルタリングを行いません（不具合が発生するサイトが少ないはずです） |
| [Default + 280](https://github.com/xperiable/filtrite-jpn/releases/latest/download/bromite-default_280.dat) | Bromiteデフォルトフィルターに、「[280blockerフィルタ](https://280blocker.net/)」を追加したリスト |
| [Default + Tamago](https://github.com/xperiable/filtrite-jpn/releases/latest/download/bromite-default_tamago.dat) | Bromiteデフォルトフィルターに、「[たまごフィルタ](https://raw.githubusercontent.com/eEIi0A5L/adblock_filter/master/tamago_filter.txt)」「[亀フィルタ](https://raw.githubusercontent.com/eEIi0A5L/adblock_filter/master/kame_filter.txt)」「[クジラフィルタ](https://raw.githubusercontent.com/eEIi0A5L/adblock_filter/master/kujira_filter.txt)」「[NoCoin Filter List](https://raw.githubusercontent.com/hoshsadiq/adblock-nocoin-list/master/nocoin.txt)」を追加したリスト |
| [Default + Yuki](https://github.com/xperiable/filtrite-jpn/releases/latest/download/bromite-default_yuki.dat) | Bromiteデフォルトフィルターに、「[雪フィルタ](https://raw.githubusercontent.com/Yuki2718/adblock/master/japanese/jp-filters.txt)」「[霜フィルタ](https://raw.githubusercontent.com/Yuki2718/adblock/master/japanese/jp-mob.txt)」を追加したリスト |

これらのリストは、GitHubアクションを使用して自動で定期的に更新されます。

**注意**： 使用されているすべてのリストフォーマットが実際に[ルールセット生成ツール](https://github.com/xarantolus/subresource_filter_tools)でサポートされているかは保証できません。（フィルタ生成に失敗する事例もあります）

### 独自フィルターリストを使用する
このプログラムは、新しいリストを簡単に追加できるように設計されています。

新しいリストを作成する方法：

1. このレポジトリをフォークします。
2. listsディレクトリの中にtxtファイルを作成します（add file→Create new fileを選択）。ファイル名が、生成されるフィルターリスト名になります。(例:`JPNfilter.txt`)
3. 作成したtxtファイルに、使用したいフィルターのURLを1行につき1つずつコピーして貼り付けます。
    ```
    # Lines starting with # are comments, empty lines are also allowed
    # List one URL per line:
    https://easylist.to/easylist/easylist.txt
    https://...

    # The following line doesn't work, only put either a comment or an URL in one line, not both
    http://  # Invalid comment on URL
    ```
4. "Actions"タブに移動し、Select workflow→Build filterlists→Enable workflowを選択してしばらく待ちます。
5. 黄色のクルクルが止まり、緑の✔が出たらフィルターリスト生成が完了します。
6. Codeに戻ると、Releasesの中に 2 で作成したファイル名が表示されているので、リンクURLをコピーします。この様なファイルがあれば成功です。`https://github.com/USERNAME/filtrite/releases/latest/download/FILENAME.dat`
7. BromiteのAdBlock settingsを開き、Filters URL欄に6でコピーしたURLを設定してBromiteを再起動すれば完了！

**注意1**： 生成できるフィルターのファイルサイズは最大[10 MB](https://github.com/bromite/bromite/blob/e5771ef891cf01dd5aeaaec5e092841929a9a541/build/patches/Bromite-AdBlockUpdaterService.patch#L1152-L)です。それ以上の場合はリストを削除する必要があります。

**注意2**： [GitHubは60日後にスケジュールされたワークフローを無効にする](https://docs.github.com/en/actions/managing-workflow-runs/disabling-and-enabling-a-workflow)ため、フォークを「生きた」状態に保つために何かをコミットしなければならない場合があります。

### [ライセンス](LICENSE)
ライセンスフリーのため、ご自由にお使いください。
