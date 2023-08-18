# Link
[index](https://github.com/yuuki-naito/note/blob/main/README.md)  
[Linux](https://github.com/yuuki-naito/note/blob/main/Linux.md)  
[Git](https://github.com/yuuki-naito/note/blob/main/Git.md)  

<details>  
  <summary> ドライブフォルダ </summary><div>
  
  <a href="https://drive.google.com/drive/folders/1gBcU39HoN8ojK4kbKTYJj8MxPPMXkJnQ?usp=drive_link">ドライブフォルダ</a>
  </div></details> 

# Linux #

<details>
<summary>Linuxインストール<a href="https://gitlab.com/pascaliaasia/pav-training-program/basic-program/-/blob/tool/linux_basic/02.Install Linux virtual env.md">(Link)</a>
</summary><div>

  ## 2. Install Linux virtual environment
  - WIndowsへのInstall
  1. WindowsへのLinux環境として、まずはUbuntuをInstallする。
  1. WindowsでLinuxを動作可能にするために、「スタート」「設定」「アプリと機能」(右上に)「プログラムと機能」より、「Windowsの機能の有効化と無効化を選択。下記画像の「Linux用Windowsサブシステム」を有効にする。
  ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux1_WIndows%E3%81%AE%E8%A8%AD%E5%AE%9A.png)
  1. WindowsストアよりUbuntuを検索、インストールする。
  ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux2%EF%BC%BFUbuntu%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB.png)
  1. 少しの後、ユーザ名とPWを登録する。
  ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux3_Ubuntu%E3%83%A6%E3%83%BC%E3%82%B6%E7%99%BB%E9%8C%B2.png)

  [!NOTE]
  ユーザ名には入力規則があり、今回の例では「.」が引っ掛かった<br>
  PWの設定の際の入力時には画面上にPWの文字列が表示されないので注意

  </div></details> 

<details>
<summary>よく使うLinuxコマンド<a href="https://gitlab.com/pascaliaasia/pav-training-program/basic-program/-/blob/tool/linux_basic/03.Most often using Linux commands.md">(Link)</a>
</summary><div>

## 3. Most often using Linux commands ##
- ### 主要なコマンド ###
  <details><summary>cat</summary><div>

  catコマンド(concatenateの略)<br>
  ファイルに記載されている内容をコマンドラインに出力する。<br>
  エディタを使って中身を見るよりも素早く中身を確認でき、中身を変えてしまう危険もない。<br>
  /etc/passwdディレクトリで試してみる。
  ```
  cat /etc/passwd
  ``` 

  ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux4_Cat%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89.png)
[!note]
  対象のファイルについては、きちんと参照パスが現在位置から指定できる場所にいる必要がある。

  出力したいファイルの内容がコンソールの画面上よりも大きい場合には、「| less」オプションを指定することでlessモードに入ることができる<br>
  lessモードでは、十字キーやPageUp PageDownキーを使用してファイルの中身を閲覧可能になる。<br>
  lessモードはqキーで終了できる。
    </div></details>
    <details><summary>echo</summary><div>

      
      echoコマンドでは、文字列をコンソール画面に出力することができる。<br>
      例えば、環境変数として持っている下記のような変数の内容を出力することもできる。
      ```
      $USER    --ユーザ名
      $HOME    --ユーザのホームディレクトリ
      $PATH    --コマンド検索パス
      ```

      環境変数には、「ユーザ名」「ユーザのホームディレクトリ」や何かのコマンドで指定した際に、対応するディレクトリパスを検索・取得する「パス」の指定などが記載されている。
    [!NOTE]
     $PATH
      $PATHはコマンドサーチパスや、コマンド検索パスなどと呼ばれている。<br>
      Linuxの特徴として、**上記のパスに指定してあるディレクトリはパス名を省略してよい**という決まりがある。<br>
      Windowsと違い、カレントディレクトリにあったとしても**自分のファイルとは限らない**ため、コマンドを実行する際には必ずパス指定する必要がある。<br>

      下記のようにコマンドを実施してみる。
      ```
      echo $USER
      echo $HOME
      echo $PATH
      ```

      ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux5_Echo%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89.png)
      ユーザ名、ホームディレクトリ、パス内容が出力された。<br>
      下記のコマンドではビープ音/アラート音が出力される。
      ```
      echo -e "\a"
      ```
      ファイルに書き込むこともできる。
      ```
      echo 'line1
      line2
      line3' > test02
      ```
      ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux6_Echo%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%892.png)
    [!NOTE]
     改行
      シングルクォート(')で囲むことで、改行を含めてテキストファイルとして書き込みができる。


      </div></details>
      <details><summary>alias</summary><div>

      aliasは別名という意味のコマンド。<br>
      コマンドや、コマンドをまとめたものなどに別名をつけ、一度のCallで呼び出すことができるようにする。
      ```
      alias hello = "echo my name is"    --「echo my name is」というコマンドとキーワードにhelloという名前を付ける。
      hello yuuki    --hello コマンドに文字列「yuuki」をつける
      ```
      
      ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux7_Alias%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89.png)
      `my name is yuuki    --出力結果`<br>
      定義した別名は、ターミナルの終了とともに定義も消える。<br>
      もし以後常に使いたいのであれば、ホームディレクトリ配下に「.bash_aliases」ファイルを作成し、定義を追加する。
      </div></details>
      <details><summary>curl</summary><div>

      URLやインターネットアドレスより、情報・ファイルを収集するツール。<br>
      デフォルトのLinuxには存在しない場合があるため、apt-getコマンドを使用してインストールする必要がある。<br>
      `sudo apt-get install curl        --管理者権限を使用してapt-getコマンドを使用し、curlツールをインストール`<br>
      ※管理者権限のPWを聞かれる。
      
      ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux8_Curl%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89.png)
      実際に使ってみる。ここではGoogleのホームページより情報を取得する。
      ```
      curl https:://google.com -o google.com
      ```
      
      ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux9_Curl%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%892.png)
      取得結果を「google.com」という名前で格納しているので、確認する。
      
      ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux10_Curl%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%893.png)
      コマンド実行中には、進行状況が出力されるため、不要な場合には,`-s`オプションをつける
        
      </div></details>
      <details><summary>df</summary><div>

      コンピュータ情報を出力するコマンド。<br>
      `-h`オプションをつけることで、人間が読める文字で出力され、`-x`オプションで指定したディレクトリを除外することも可能。
        
      ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux11_Curl%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%894.png)

      </div></details>
      <details><summary>diff</summary><div>

      2つのテキストファイルを比較、差分を出力するコマンド。
      並べて表示するオプション`-y`、<br>
      幅の指定オプション`-W xx(Wは大文字xxは数字)`や、<br>
      記載内容が異なる点に焦点を当てるオプション`--suppress-common-lines`などがある。<br>
      ファイル作成から比較までを実施する。
      
      ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux12%E2%80%97Diff%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89.png)
        
      </div></details>
      <details><summary>exit</summary><div>

      ターミナル終了やシェルスクリプト実行終了、SSHのリモート接続の切断などで使用する。
      </div></details>
      
      <details><summary>find</summary><div>

      検索コマンド。<br>
      どのディレクトリから何のファイルを検索するかを指定することで実行可能。<br>
      ワイルドカードを使用することであいまい検索も可能で、`*`(任意の1文字以上)や、<br>
      `?`(任意の1文字)などを指定することで目的のファイルを探す。
      `-name` 名前の指定
      `-type` ファイルタイプの指定
      `-iname` 大文字小文字の区別なしでファイル名検索
      </div></details>
      
      <details><summary>finger</summary><div>

      ユーザの最終ログイン時刻、ユーザのホームディレクトリ、ユーザアカウントのフルネームなどのユーザ情報を表示する。
    [!NOTE]
      WindowsサブシステムのUnuntuでは正常動作しない可能性がある。<br>
      また、追加インストールの必要がある場合もある。<br>
      ※自環境では動作しなかった。

      
      </div></details>
      
      <details><summary>free</summary><div>

      freeコマンドは、メモリ使用量の情報が表示される。<br>
      RAMの情報などが表示され、`-h`オプションにて人が読めるようにできる。
      </div></details>
      
      <details><summary>grep</summary><div>

      grepコマンドは、一致検索を実施するコマンド。<br>
      ファイルの中身を確認することができるので、例えば、テキストの中に「line2」と書かれた行のあるファイル。といった検索が可能。
      ```
        grep "line2" *.txt
      ```
      
      ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux13_Grep%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89.png)
      ※拡張子がないファイルもあるので、ファイル名は正確に指定する必要がある。

      </div></details>
      
      <details><summary>groups</summary><div>

      ユーザが何グループ化を表示
      </div></details>
      
      <details><summary>gzip</summary><div>

      ファイル圧縮コマンド。デフォルトでは元ファイルは削除される。<br>
      オリジナルを確保したまま保存する場合には、`-k`オプションを設定する。
      
      ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux14_Gzip%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89.png)

      </div></details>
      
      <details><summary>head</summary><div>

      catに似たコマンドで、ファイルの先頭10行のみ出力する。<br>
      `-n xx`(xxは数字)オプションにて、表示行数を指定できる。
      </div></details>
      
      <details><summary>tail</summary><div>

      headの末尾Ver
      </div></details>
      
      <details><summary>history</summary><div>

      履歴コマンド。<br>
      発行したコマンドの履歴を表示する。<br>
      履歴にある`!`と行番号を指定することで指定のコマンドを繰り返すことができる。`!2`など<br>
      また、`!!`で1つ前のコマンドを繰り返せる。
      </div></details>
      
      <details><summary>kill</summary><div>

      実行中のタスクを停止することができる。
      使用するにはプロセスID(PID)を指定する必要がある。
      ```
      ps -aux | grep pav02
      ```
      sleepコマンドで発生させたプロセスを停止した画像。
        
      ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux15_Kill%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89.png)

      </div></details>
      
      <details><summary>less</summary><div>

      catコマンドの際にも触れたコマンド、エディタを開かずに中身を見ることができ、<br>
      ファイルの中身をキースクロールで確認可能。<br>
      `less [ファイル名]`とすることで、lessコマンド単体でも使用可能。<br>
      
      パイプでつなぐことで、ほかのコマンドの結果をlessで見ることも可能。<br>
      ```
        ls -l | less
      ```
      </div></details>
      
      <details><summary>man</summary><div>

      manコマンドは、lessコマンド画面の形式で、manコマンドの内容を表示する。<br>
      内容としては、指定したコマンドのユーザマニュアルが表示される
      ```
        man ls
      ```
      
      ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux16_Man%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89.png)

      </div></details>
      
      <details><summary>passwd</summary><div>

      パスワード変更コマンド。新しいPWを入力する。<br>
      PWの変更になるので、他ユーザのPWを変更するには管理者権限が必要<br>
      
      </div></details>
      
      <details><summary>ping</summary><div>

      pingを実施するコマンド。IPやアドレスを指定する。
      ```
        ping google.com
      ```
      
      ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux17_Ping%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89.png)
      `-c`オプションで指定の回数だけ実施することが可能<br>
      `Ctrl + C`で停止できる。
      </div></details>
      
      <details><summary>ps</summary><div>

      実行中のプロセスを表示するコマンド。デフォルトでは、現在のシェルでのプロセス一覧になる。<br>
      特定ユーザを表示するには`-u`オプションを指定する。<br>
      出力が長くなる可能性があるので、`| less`をつけることを推奨
      </div></details>
      
      <details><summary>shutdown</summary><div>

      システムのシャットダウンのコマンド。(Windowsアプリのターミナルでは仮想環境のため動作しない。)<br>
      実行すると1分以内にシステムが終了する。<br>
      今すぐに終了する際には、`now`パラメータを指定する。<br>
      shutdownをスケジュールすることもできる。スケジュールを設定すると、ログイン中のユーザすべてにブロードキャストされる。<br>
      シャットダウンを中止する場合には、`shutdown -c`を入力する。
        
      </div></details>
      
      <details><summary>SSH</summary><div>

      sshコマンドを使用して、Linuxのリモート操作が可能。<br>
      ssh接続には、ユーザ名、接続先IPアドレスorドメイン名の指定が必要。<br>
      ※仮想環境では動作しない可能性がある。
      </div></details>
      
      <details><summary>sudo</summary><div>

      root権限、管理者権限でコマンドを実行する際につけるコマンド。
      </div></details>
      
      <details><summary>tar</summary><div>

      複数ファイルをまとめて、1つのtarファイルと呼ばれるまとまりにするコマンド。<br>
      アーカイブファイルとも呼ばれ、基本的には圧縮をかけるが、非圧縮も可能。<br>

        | 短いオプション | 長いオプション | 意味 |
        | - | - | - |
        | -c | --create | 新しいアーカイブを作成する |
        | -r | --append | アーカイブの最後にファイルを追加する |
        | -A | --catenate, |
        | --concatenate | アーカイブにtarアーカイブを追加する |
        | -u | --update | アーカイブのファイルを更新する（アーカイブ内の同名ファイルより新しいものだけを追加する） |
        | -d | --diff, |
        | --compare | アーカイブとファイルシステムを比較する |
        | --delete | アーカイブから削除する |
        | -t | --list | アーカイブの内容の一覧を表示する |
        | -x | --extract,--get | アーカイブからファイルを抽出する |
        ```
      </div></details>
      
      <details><summary>top</summary><div>

      Linuxのマシン関連の情報をリアルタイムに表示する。<br>
      `E`キーを入力することで人間が見やすくできる。
      `Q`キーで終了する。
      </div></details>
      
      
      <details><summary>uname</summary><div>

      作業中のコンピュータにかかわるシステム情報を取得できる。
      ```
        -a  すべて表示
        -s  カーネルタイプ
        -r  カーネルリソース
        -v  バージョン
      ```
      </div></details>
      
      
      <details><summary>w</summary><div>

      ログインユーザ一覧
      </div></details>
      
      
      <details><summary>whoami</summary><div>

      現在のログインユーザがだれかを表示
      </div></details>
</div></details>

<details>
<summary>Linuxファイル操作<a href="https://gitlab.com/pascaliaasia/pav-training-program/basic-program/-/blob/tool/linux_basic/04.Working with Files and Directories.md">(Link)</a>
</summary><div>

## 4. Working with Files and Directories


- Linuxファイルシステムの機能<br>
  Linuxのファイルシステムは、ツリー構造で、最上位ディレクトリをルートと呼ぶ。<br>
  - パスの指定<br>
    Linuxのパスの指定はスラッシュを使用する。
  - パーティション、ディレクトリ、ドライブ<br>
    LinuxではWindowsのように、ドライブなのか、ネットワークドライブなのか、通常のディレクトリかを区別できない。
  - 大文字と小文字<br>
    Linuxでは大文字と小文字を区別する。
  - ファイル拡張子<br>
    ファイル拡張子は必須ではない
  - 隠しファイル<br>
    先頭に`.`をつけることで隠しファイルにすることができる。

1. ディレクトリの移動
    - `pwd`コマンドで現在地を取得する。<br>
    pwdには2つのオプションがある。<br>
    `-l` シンボリックリンクを解決しない。<br>
    `-p` シンボリックリンクなし、物理ディレクトリのみ表示

  [!NOTE]
    シンボリックリン区については次セクションに記載。
    コンピュータ上のファイル/フォルダを指し示すLinux上のファイル種別。Windowsのショートカットに似ている。

    - ディレクトリの移動には`cd`コマンドを使用する。<br>
      絶対パス、相対パスともに移動可能<br>
      また、自分のいるディレクトリの指定には`.`、一つ上のディレクトリには`..`で指定可能。<br>
      直前に作業をしていたディレクトリについては`-`で指定が可能である。
1. ファイルとディレクトリのリスト
    - ターミナルには基本的にはGUIがないので、ファイルリストについてはコマンドで取得する。<br>
    `ls`コマンドを使用する。このコマンドは別のパスも指定することが可能。
    `-l`オプションを使用することで、詳細情報を表示。<br>
  ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux18_%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E2%80%97%E3%83%87%E3%82%A3%E3%83%AC%E3%82%AF%E3%83%88%E3%83%AA%E3%83%AA%E3%82%B9%E3%83%88.png)
    先頭の10桁の文字列にはそれぞれ意味があり、1桁目がファイル属性、以降はそれぞれ3文字ずつ、所有者、グループ、他の人のアクセス権限(パーミッション)が表示されている。<br>
    1. ファイル種類<br>
    下記の属性がある。<br>
    `-`通常ファイル<br>
    `d`ディレクトリ<br>
    `l`シンボリックリンク<br>
    `c`キャラクタ型デバイスファイル(特殊ファイル)<br>
    `b`ブロック型デバイスファイル(特殊ファイル)<br>
    
    1. パーミッション<br>
    `r`読み出し<br>
    `w`書き込み<br>
    `x`実行許可
1. 作成と削除<br>
    - ディレクトリ<br>
  ディレクトリを作成する際には`mkdir`コマンドを使用する。<br>
  `-p`オプションを使用することで、存在しないディレクトリの配下にディレクトリを作成する。<br>
  つまり階層構造を丸ごと一度に作成可能ということ。
  
    - ファイル<br>
  まっさらな新しいファイルを作成するには`touch`コマンドを使用する。(空ファイル作成)<br>
  ファイル名を指定し、その名前の新しいファイルを作成する。
  
    - 削除<br>
  ディレクトリもファイルも、削除する際には共通のコマンドで削除が可能。<br>
  どちらも`rm`コマンドの後にディレクトリ名/ファイル名を指定する。<br>
  ただし、中身のあるディレクトリは削除できないので、ファイルごとディレクトリを強制的に削除する場合には、<br>
  `-rf`オプションを指定する。
  
1. コピーと移動<br>
  コピー/移動については、これも同じコマンドで実行可能である。<br>
    - コピー<br>
    `cp`コマンドでコピーを実行できる。<br>
    第一引数に元ネタ、第二引数に移動先のパス(絶対/相対)を指定する。
    
    - 移動
    `mv`コマンドで移動を実行できる。<br>
    引数の取り扱いは`cp`と同様<br>
    Windowsとの違いとして、「カット(切り取り)」という動作は存在しないので注意。

1. シンボリックリンク<br>
  Linuxでいう**リンク**とは、「ファイル名」と「実データ」との関係を表す。
  リンクには2種ある。
  
    - ハードリンク<br>
    対象ファイルのミラーリングとして、実物がオリジナルとコピーの2つあり、同期している状態。<br>
    オリジナルファイルで利用可能なデータにアクセスする。<br>
    元のファイルが移動/削除されたとしても、`inode`を参照しているためリンクへの影響はない。
  
    - ソフトリンク(シンボリックリンク)<br>
    ファイル名へのポインタとして機能するリンク。<br>
    オリジナルファイルで利用可能なデータにアクセスできない。<br>
    元のファイルが移動/削除されたりすると**無効になる**
    
    - inode<br>
    iノードとは、ファイルの所有者やサイズ、アクセス権限、作成日時、データ領域へのポインタなどの各種情報を記録するためのデータ。<br>
    とあるデータを**指し示す属性情報のデータ**のこと。属性情報
  
    - inode番号<br>
    inodeを指し示す番号。<br>
    上記のことからデータを見たい場合にシステム側では下記の手順で表示する。<br>
    １．ファイル名からinode番号をたどる<br>
    ２．inode番号からinodeをたどる<br>
    ３．inodeから実データをたどる<br>
    `ls -i`のコマンド+オプションで取得可能。
  
    - 各リンクの相違点を記載する。
    
    ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux19_%E3%82%B7%E3%83%B3%E3%83%9C%E3%83%AA%E3%83%83%E3%82%AF%E3%83%AA%E3%83%B3%E3%82%AF.png)
  
    [!NOTE]
      i ノード番号 – インデックス ノード番号は、Linux/Unix システム内のすべてのファイルに割り当てられる一意の番号です。<br>
      スーパーユーザー – スーパーユーザーには、通常のユーザーと比較してより多くの権限があります。ファイルの所有権を変更したり、アクセス許可を設定したりできます。
    :::
  
  1. リンクの作成方法<br>
    1. ソフトリンク(シンボリックリンク)<br>
      `ln -s <source><dest>`
    1. ハードリンク<br>
      `ln <source><dest>`
  
  1. ファイル/ディレクトリのサイズ
      - `du`コマンド<br>
      `du`コマンドを確認したいパスに対して使用するとファイル/ディレクトリのブロック数とサブディレクトリが表示される。<br>
      `-h`オプションで人間が読める形になる。<br>
      `-s`オプションでディレクトリの使用量の合計サイズを取得可能。<br>
      `-a`オプションを使用すると、すべてのファイルとディレクトリのディスク使用量が表示される。<br>
      どのオプションも`-h`と併用可能
  
        ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux20_Du%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89.png)
  
- アクセス許可<br>
  - 所有権<br>
  Linuxには所有権という考え方があり、以下の所有者の別がある。
    1. ユーザ<br>
    ファイルの所有者。基本的には作成者。
    1. グループ<br>
    ユーザグループ。複数ユーザが属するグループ。グループ全員に権限が降られるので個別に設定する必要がなく、共同管理するような場合に使える。
    1. その他<br>
    ファイルの制作者でもグループでもないほかの人。Publicのイメージ。
  
  - アクセス許可<br>
  3タイプのアクセス権の設定が可能。
    1. 読み取り`r`(read)<br>
    ファイルやディレクトリを開いて中身を読み取る権利。
    1. 書き込み`w`(write)<br>
    ファイルやディレクトリの中身に書き込む(中身を変更する)権利。<br>
    権限のないディレクトリにはファイルを保存することもできない。<br>
    中身のファイルに書き込み権限があった場合には、**ファイルの中身**には書き込めるが、名前の変更や移動など<br>
    **ディレクトリ上で見れるファイルに何かしらの変更が入る動作はできない。**
    1. 実行`x`(execute)
  
    各ファイルやディレクトリの権限の確認については、`ls -l`コマンドにて確認ができる。<br>
    また、それぞれの権限のパターンごとに数字が割り振られていて、下記の表のとおりになる。
      ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux21_%E6%A8%A9%E9%99%90.png)

  - `chmod`コマンド<br>
    上記で確認していたアクセス権限の変更については、`chmod`コマンドを実行する。
    ```
      chmod [権限] [対象ファイル]
      chmod [対象ユーザ] [+/=/-] [(付与/設定/削除)権限] [対象ファイル]
      example
      chmod 755 test.txt
      chmod g+rw test.txt      ---グループユーザに対して、読み取りと書き込み権限を付与
    ```
    付与方法はそれぞれ下記の通り。
    
    ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux22_%E6%A8%A9%E9%99%902.png)
    上記の数字を、それぞれ[ユーザ(u)][グループ(g)][その他(o)]の順に数値で設定の上ファイルを指定する。
    もしくは個別にu/g/oを指定し、各ユーザに対して追加`+`、設定`=`、削除`-`を記述する。
  
  - 所有者の変更(`chown`)
    オーナーを変更することが可能
  - グループの変更(`chgrp`)
    グループを変更することが可能。
  
  - 注意点<br>
    このファイルには、/etc/groupシステムで定義されているすべてのグループが含まれています<br>
このコマンドを使用すると、groups自分がメンバーとなっているすべてのグループを検索できます。このコマンドについては前の章で説明しました。<br>
2 つのグループが同じファイルを所有することはできません。<br>
Linux にはネストされたグループがありません。あるグループが他のグループのサブグループになることはできません<br>
x-実行許可とは、ディレクトリに「入る」ことと、サブディレクトリへのアクセスが許可されることを意味します。<br>
  
      
  
  
  

</div></details>

# Pacage Manager
- Linuxではアプリケーションソフトについて、基本パッケージという形で用意されており、各パッケージを管理するために** パッケージマネージャ ** と呼ばれるものが開発された。  
Ununtuで実装されている基本的なパッケージマネージャは`apt-get`になる。  
LinuxのOSではパッケージマネージャを使用してアプリが最新か、正常にインストールされているかを確認する。  
利用可能なソフトウェアの最新リストも保持しており、リポジトリと呼ばれる外部DBに保存される。  

- `apt-get`を使用したパッケージ管理
  - 前提条件
    1. Linuxであること
    2. ターミナルへアクセスできること
    3. Ubuntu　or　Debian　ベースのLinuxにインストールされているapt-getツールであること  
  - Ubuntuパッケージリポジトリを更新する。  
    基本的にアプリをインストールする際には、**現在のアプリケーションが最新か確認する**癖をつけたほうが良い。  
    
    最新Verかの確認  
    `sudo apt-get update`  
    システムがリポジトリ(外部DB)に最新Verがないかをチェックする。
    
  - パッケージのインストール  
    今回は`software-properties-common`というソフトをインストールする。  
    このアプリは`add-apt-repository`コマンドを追加する。
    
  - アプリのインストール  
    `sudo apt-get install software-properties-common`  
    apt-getツールがリポジトリ(外部DB)に接続し、対象のコマンドを実装したアプリを検索、  
    取得、インストールを実施する。  
    ※apt-getでアクセスできるリポジトリの追加をコマンドで実行できるようにするソフト
    
    実際にPHPのアプリを追加する。  
    `sudo add-apt-repository ppa:ondrej/php
    
    php8をインストールする。
    `sudo apt install php8.0 libapache2-mod-php8.0`  
    
    インストールされているアプリを更新する。  
    `sudo apt-get upgrade`  
    
    アプリのアンインストールを実施するには、下記のコマンドになる。  
    `sudo apt remove [パッケージ名]`  
    
  - `apt-get` と `apt`の違い  
    4つの違いがある。
    1. aptは、apt-getとapt-cacheの機能を統合している。
    2. 開発者か使いやすいような画面出力の追加。
    3. 既存機能/既存コマンドを使いやすいようにカスタムしたコマンド
    4. aptコマンド専用機能の追加
        1. `apt search <term>`　パッケージを検索できる。
        2. `apt list --upgradable`更新可能なパッケージを確認。
    
    `apt`と`apt-get`の使い分けは、aptがコマンドラインで、apt-getがスクリプトで使うのが良いと公式では言われている。
    

- シェル

  キーボードからのコマンドをOSに渡して実行するプログラム。
  
  昔はこれが唯一のUIだった。
  
  対話型の言語。
  
  Unixのshの発展形である、Bashという拡張子のファイルになる。その外にも、ksh,tcsh,zshなどがある。
  
  端末＝ターミナルエミュレータと呼ばれるもの。※いつも開いてコマンドを打っているもの。
  
- 変数

  値を代入する文字列。
  
  数値、テキスト、ファイル名、デバイスなど、各種データを保存可能。
  
  変数はあくまでもデータへのポインタ※名称やアドレスの情報ということ。
  
  シェル上で作成・割り当て・削除が可能
  
  変数は`$`で始まり、$の後TABを2回押すことですべての変数を確認できる。
  
  `printenv`コマンドですべての変数の値が表示できる。
  
  変数の作成は`[変数名]=[値]`で可能。
  
  `readonly`コマンドで、読み取り専用に設定ができる。
  
  - 変数の型
    1. ローカル変数
    
      シェルの現在のインスタンスに対して存在する変数。
      
      シェルによって起動されるプログラムでは使用できない。
      
      コマンドプロンプトで設定できる。
      
      ※`local`コマンドを使うことで、**関数内のみ**にスコープを設定できる。
      
      
    3. 環境変数
      
      シェルのすべての子プロセスで使用可能な変数。※広域変数。
      
      ※１変数名は大文字と小文字を区別される。
      
      ※２1変数に複数の値を割り振るにはコロン`:`で区切る必要がある。
      
      ※３`=`の前後のスペースは不要
      
    5. シェル変数
      
      シェルによって設定される特殊な変数。
      
      シェルが正常動作をするために必要。
      
      一部は環境変数だが、そのほかはローカル変数となる。
      
    1. 特殊な変数
    ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux23_%E3%82%B7%E3%82%A7%E3%83%AB%E7%89%B9%E6%AE%8A%E6%96%87%E5%AD%97.png)

      ```
          echo 'echo "\$0：" $0 ; echo "\$1：" $1; echo "\$#：" $# ;echo "\$*：" $* ;echo "\$@：" $@ ;echo "\$?：" $?;echo "\$$：" $$;echo "\$!：" $!;echo "\$-：" $-' >app
        ./app
      ```

- パイプコマンド
  pipeコマンドを使用することで、コマンドの出力結果を別のコマンドに送信できる。
  
  出力、入力、エラーなどの情報を別のプロセスへリダイレクトし、後続処理を実行可能。
  
  `cat file | grep -Po "\d+"`
  fileの中身を出力し、出力結果から、grepによって数値のみを出力する。というコマンド
  
- `sudo su`コマンドによるユーザの切り替え
  `sudo`管理者権限でのコマンド実行
  
  `su`sudoコマンドの引数、スーパーユーザ※管理者権限保持ユーザ
  
  - プロセス

  Lonuxではすべてのプログラムはプロセスと呼ばれ、OSによって常にいくつか起動している。
  
  Linuxでは各プロセスにID or PID が設定されていて、数字でプロセスを管理できる。
  
  バックグラウンド、フォアグラウンドの別がある。
  
- プロセスの種類

  プログラム実行中にはプロセスは生き続ける。
  
  `foreground process`と`background process`の二つがあるが、どちらも出力は同じになる。
  
  違いは、**ユーザが操作などの介入ができるもの**がフォアグラウンド※きーぼど入力など
  
  **操作できず、他プロセスと並列で実行できるもの**がバックグラウンド
  
  コマンドの最後に`&`をつけることでバックグラウンドのコマンドになる。
  
  - バックグラウンドコマンドの確認
  
    `job`コマンドを実行することで、バックグラウンドコマンドの状況を確認できる。
    
  - プロセスの状態変化
    1. `Running`実行中、または実行準備完了のプロセス。※CPU待ちなど
    2. `Waiting`待機中、イベントの発生やリソース待ちなど。

      割り込み可能か不可能かによって分けられる。
    1. `Stopped`シグナルの受信によって中断している状態。※デバッグなど
    2. `Zombie`プロセスが停止しているが、プロセステーブルに残っている状態。

  - アクティブプロセスの確認
    - `ps`コマンド
  
      システム上でアクティブなプロセスに関する情報を表示する。
      
    - `top`コマンド
    
      リアルタイムにプロセスの状況を表示する。※動的

    - `fg`コマンド

    バックグラウンドプロセスをフォアグラウンドにする。※PIDを指定
    - `bg`コマンド

    フォアグラウンドプロセスをバックグラウンドにする。※PIDを指定
    - `nice`コマンド

    プログラムを、優先度を指定して起動可能。
    - `renice`コマンド

    実行中の優先度を変更可能。
- SSH  
  Secure Shellの略で、リモートコンピュータ/サーバにアクセスできるようにするプロトコル。  
  ローカルコンピュータの入力を、サーバ/リモートコンピュータへ送信・操作が可能になる。  
  
  - 環境設定  
    Linuxのほとんどでは、OSの一部としてsshコマンドがある。  
    WindowsのサブシステムUbuntuではサーバ用に追加のsshをインストールする必要がある。
  
  `sudo apt-get update -y` すべてのプログラムの更新  
  `sudo apt-get install openssh-server`sshサーバのインストール  
  `sudo service ssh --full-restart`sshサーバの起動  
  `ip addr`ipアドレスの取得  
  
  ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux24_Ip_Addr%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%89.png)

  ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux25_Ip_Addr%E3%82%B3%E3%83%9E%E3%83%B3%E3%83%892.png)

  取得したIPアドレス：169.254.255.255
  
- SSHクライアント環境  
  MACかLinuxの場合には、sshクライアントコマンドが利用可能。  
  ターミナルを開いて`ssh`と入力するだけ。  
  Windowsでは追加ソフトをInstallする必要がある。
  
  1. gitのbashターミナルからssh接続で接続する。  
    ※`<BROADCAST,MULTICAST,UP>`と記載のあった`eth1`の接続で接続成功。
  ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux26%E2%80%97SSH%E6%8E%A5%E7%B6%9A.png)

  2. 接続後sshキーの存在を確認、作成  
    ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux27_SSH%E3%82%AD%E3%83%BC.png)
    ![image.png](https://github.com/yuuki-naito/note/blob/main/image/Linux28%E2%80%97SSH%E3%82%AD%E3%83%BC2.png)
    この設定で、今後PW入力なしで接続可能になる。
