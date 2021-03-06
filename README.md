# cist-timenav

本プロジェクトは以下の3つのサービスで構成されている。

1. pdf_retriever
2. timetable_miner
3. bus-timetable

## [pdf_retriever](https://github.com/k-oketa/cist-timenav/tree/develop/pdf_retriever)

公立千歳科学技術大学の[大学へのアクセス](https://www.chitose.ac.jp/info/access) からPDFを取得する。このプロジェクトはAPIを提供する。

### ベースURL

```
https://dia.spub.chitose.ac.jp/api/pdf
```

#### `/info`
「大学へのアクセス」に表示されているPDFの数とタイトルを取得する。

#### `/url/<number>`
「大学へのアクセス」の上から `<number>` 番目に表示されているPDFのURLを取得する。 `<number>` は0から数える。

#### `/name/<number>`
「大学へのアクセス」の上から `<number>` 番目に表示されているPDFの表示名を取得する。 `<number>` は0から数える。

#### `/title/<number>`
「大学へのアクセス」の上から `<number>` 番目に表示されているPDFファイルの名称を取得する。 `<number>` は0から数える。

#### `/bytes/<number>`
「大学へのアクセス」の上から `<number>` 番目のPDFファイルを取得する。 `<number>` は0から数える。

#### 備考

- `<number>` は `oldest` とすることで一番上のものを取得できる。


## [timetable_miner](https://github.com/k-oketa/cist-timenav/tree/develop/timetable_miner)

PDFから時刻表を抜き出し、JSON形式で返す。現在は大学発着の時刻表のみを抜き出し、市営のバスの時刻表は抜き出さない。

### ベースURL

```
https://dia.spub.chitose.ac.jp/api/time
```

#### `/info`
「大学へのアクセス」に表示されているPDFの数とタイトルを取得する。

#### `/table/to/school/<number>` (Timestamp対応)
「大学へのアクセス」の `<number>` 番目のPDFから往路を取得する。 `<number>` は0から数える。

#### `/table/to/chitose/<number>` (Timestamp対応)
「大学へのアクセス」の `<number>` 番目のPDFから復路を取得する。 `<number>` は0から数える。

#### `/date/<number>`
「大学へのアクセス」の `<number>` 番目のPDFのタイトルに含まれる日付部を取得する。 `<number>` は0から数える。

#### 備考

- (Timestamp対応)のものは、末尾に `/timestamp` を付与すると、Timestampの形式で取得する。
- `<number>` は `oldest` とすることで一番上のものを取得できる。

## [bus-timetable](https://github.com/k-oketa/cist-timenav/tree/develop/bus-timetable)

公立千歳科学技術大学のバスの時刻表を表示する。