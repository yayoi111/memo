本記事は、Linux Professional Instituteの問題を解説しています。

# LPIC 101

## システムアーキテクチャ

## Linuxのインストールとパッケージ管理

## GNUとUnixのコマンド

### xzコマンド
ファイルを圧縮するコマンド
```オプション一覧
Usage: xz [OPTION]... [FILE]...

  -z, --compress      force compression
  -d, --decompress, --uncompress
                      force decompression
  -t, --test          test compressed file integrity
  -l, --list          list information about .xz files
  -k, --keep          keep (don't delete) input files
  -f, --force         force overwrite of output file and (de)compress links
  -c, --stdout, --to-stdout
                      write to standard output and don't delete input files
  -0 ... -9           compression preset; default is 6; take compressor *and*
                      decompressor memory usage into account before using 7-9!
  -e, --extreme       try to improve compression ratio by using more CPU time;
                      does not affect decompressor memory requirements
  -T, --threads=NUM   use at most NUM threads; the default is 1; set to 0
                      to use as many threads as there are processor cores
  -q, --quiet         suppress warnings; specify twice to suppress errors too
  -v, --verbose       be verbose; specify twice for even more verbose
  -h, --help          display this short help and exit
  -H, --long-help     display the long help (lists also the advanced options)
  -V, --version       display the version number and exit


```

## デバイス、Linuxファイルシステム、ファイルシステム階層標準




---

以下、問題とそれに関連する用語をまとめた。

# 執筆中


#### 問題
プロンプトの表示文字列が設定されている環境変数は？

+ PROMPT
+ PS1
+ PS2
+ PROMPT_STR

#### 回答
正解 : PS1

##### プロンプトとは、

`#` や `$` などの **プロンプトを表示させ**　ユーザーからの指示をまつ。



```例
[hogehoge@yayoi ~]$
```

プロンプトはシェルによって表示が若干異なりますが、bashのプロンプト表示は、
「$」が一般ユーザー、「#」がスーパーユーザ（root）として表示します。

また、「$」や「#」以外にもホスト名やユーザ名、カレントディレクトリなども表示でき、
これらの設定は <span style="color: blue; "> PS1 </span> という環境変数によって設定さています。

#### 問題
pkillコマンドで、完全一致するプロセスのみをKILLするためのオプションは？

+ -f
+ -x
+ -p
+ -m

#### 回答
正解 : -x

```例

オプション：
-sig, --signal sig        送信するシグナル（番号または名前のいずれか）
-e, --echo                何がKILLされたかを表示する
-c, --count               マッチングしたプロセス数
-f, --full                一致する完全なプロセス名を使用する
-g, --pgroup PGID,...     リストされたプロセスグループIDと一致する
-G, --group GID,...       実グループIDと一致する
-n, --newest              最近開始したものを選択
-o, --oldest              最も最近開始されたものを選択する
-P, --parent PPID,...     与えられた親の子プロセスのみと一致する
-s, --session SID,...     セッションIDに一致する
-t, --terminal tty,...    端末を制御して一致させる
-u, --euid ID,...         実効IDで一致する
-U, --uid ID,...          実際のIDで一致する
-x, --exact               コマンド名と正確に一致する
-F, --pidfile file        ファイルからPIDを読み込む
-L, --logpidfile          PIDファイルがロックされていないと失敗する
--ns PID                  pidと同じ名前空間に属するプロセスと一致する
--nslist ns,...           --nsオプションのためにどの名前空間が考慮されるかをリストする
                          使用可能な名前空間：ipc、mnt、net、pid、user、uts

```


##### プロセスとは、

プロセスとは、「** OS上で実行中のプログラム **」を指す。
プロセスが動いているということは、コンピュータリソース
（CPUやメモリなど）を消費している状態です。

##### killコマンド

プロセスを強制終了させること。( **プロセスを殺す** と表現 )
killコマンドを実行させると、実行中のプロセスを終了させます。

 どのプロセスを終了させるかは、「プロセスID」で指定します。
例えば、200番のプロセスならば `kill 200` と指定します。
プロセスIDは「ps」コマンドで調べることができます。

```例
kill 200

```
##### パターン

文字列から指定する **共通** の特定の文字を指す。
---

#### 問題
xfs_fsrコマンドで、/etc/mtabファイルを参照して
XFSファイルシステムのデフラグを実施するためのオプションは？

+ -r /etc/mtab
+ -m /etc/mtab
+ -i /etc/mtab
+ -f /etc/mtab

#### 回答
正解 : -m /etc/mtab

##### xfs_fsr コマンドとは?
>「xfs_fsr」は、XFSファイルシステムの断片化（フラグメンテーション）を検査、解消するコマンドです（※1）。いわゆる「デフラグ」を実行できます。
>　Linuxを使い続け、ファイルの作成や削除を繰り返すと、利用していない連続した領域が次第に少なくなっていきます。このときHDDにファイルを保存すると、複数の部分に分かれて保存されることがあります。これを断片化といいます。
>　xfs_fsrコマンドは、ディスクの断片化を解消し、ファイルの配置を最適な状態にできます。HDDにファイルを保存する際、連続した領域を利用できるようになるため、ファイルの読み書きに要する時間が短くなります。

引用:[*【 xfs_fsr 】コマンド――XFSファイルシステムでデフラグを実行する* ](https://atmarkit.itmedia.co.jp/ait/articles/1804/06/news018.html "xfs_fsrについて") 


```例
xfs_fsr [オプション] [デバイス名またはファイル名]

mtab (※2)ファイルを指定し、そこに書かれているファイルのデフラグを実行する。
xfs_fsr -m /ets/mtab

```
※2 mtab（mounted file systems tableの略）は、
デバイスのマウント情報を記録したファイル。デフォルトは/etc/mtab。

#### 問題
バックグラウンドで実行しているジョブをフォアグラウンドに移行するコマンドは？

+ foreground
+ fgd
+ fg
+ fground

#### 回答
正解 : fg
バックグラウンドで実行中のコマンドをfgコマンドにジョブ番号を指定して実行する事でバックグラウンドに移行できます。

##### Linuxのジョブという考え方
ジョブとは、一つ以上のプログラム(コマンド)でまとまった処理を指す。

```ジョブ
# sleep 60 ← これもジョブ
# { sleep 60; sleep 60; } ← これもジョブ

```

##### フォアグラウンドジョブとバックグラウンドジョブ
ジョブは、ユーザー操作ができる **フォアグラウンド** と
ユーザーの操作対象にはなっていないが、処理自体は実行されている
**バックグラウンドジョブ**  に分かれています。


##### fg コマンド?
バックグラウンド処理しているジョブや
停止中のジョブをフォアグラウンド処理にすることができます。

```例
fg [%job番号] 

```
job番号は、`jobs`コマンドを入力することで実行中のジョブを
確認することができる。

#### 問題
mount -aコマンドでファイルシステムを
マウントする際に参照される設定ファイルは？

+ /etc/autofs
+ /etc/fs
+ /etc/mount
+ /etc/fstab

#### 回答
正解 : /etc/fstab

mount -a コマンドは /etc/fstab に記載されている
全てのファイルシステムをマウントします。

##### ファイルシステムのマウントとは?

###### 枝を追加すること
一般的にUSBメモリを始めとした外部記憶媒体装置をPCに接続すると
`D:` や `E:`ドライブとして認識される。これらは、 ``ドライブレター``とよばれる。

しかし、Linuxにはドライブレターという
概念がない。そのためLinuxは各パーティションに
ファイルシステムを作成し、作成したパーティションをマウントします。

イメージだと  `/`から始まるディレクトツリー、
**樹木構造(階層構造)** に 記憶媒体 という **枝** を追加する。

この枝を追加する行程を **マウント**という。




------------------------------------------------------------
```HTML:記入例.md
`**` で囲むと **太字** になります。
`*` で囲むと *斜字* になります。
`~~` で囲むと`~~打ち消し線~~ になります。
```
出力結果↓

`**` で囲むと **太字** 、`*` で囲むと *斜字* になります。
また、`~~` で囲むと ~~打ち消し線~~ になります。
---
# 折りたたみ

HTMLのdetailsタグを囲むことでリストを作ることができます。
また、summaryタグを囲むとリストのタイトルを作ることができます。
summaryタグで囲ったら必ず **空行** を入れる必要があるので注意してください。


<details><summary>サンプルコード</summary>

```rb
puts 'Hello'
```
</details>

