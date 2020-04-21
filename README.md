# ノートPCへPython環境構築

## はじめに

このページはWindows 8.1および10，macOS 10.15 (catalina), Linux (ubuntu 18.04)へのPythonと関連モジュールをインストールした経験メモです．**このページに記載された方法を試して何らかの不具合が生じても本ページ管理者は何ら責任を負いません**．pythonやlinuxのインストールは**自己責任**で行って下さい．</br>

注意：このページ管理者は「にわかプログラマー」です．</br>

PythonはWindows, macOS, Linuxに加えてiOS，アンドロイドでも利用できるプログラム言語です．特にWindows，macOS，Linuxではグラフィックユーザーインターフェイス（GUI）を含むプログラムを書けることに興味を持ち，いろいろ試した結果です．GUIモジュールは主にwxPython，すこしだけpyQtを使いました．wxPythonはライセンスがゆるめなのでpyQtよりも使いやすい気がします．</br>

Pythonは複数のバージョンやインストールされたモジュール数が異なる環境を使うことが多いようです．本ページでは複数バージョンのPython環境の構築が目的の一つであるため，[pythonの本家本元サイト](http://www.python.org)からダウンロードする方法は用いていません．</br>

## Windows編

WindowsへのPython環境構築には[Anaconda](https://www.anaconda.com/)と[WinPython](http://winpython.github.io/)を試しましたが，現在はWinPythonのみを使っています．Anacondaを使わなくなった理由は，インストールされているGPL版pyQtをCommercial版pyQtに置き換えられなかったためです．（数年前の話．Anadondaパッケージにはpython3.dllが含まれていないためでした）</br>

WinPythonフルバージョンはAnacondaと同様に様々なモジュールや統合開発環境ソフトがプレインストールされています．科学技術計算に必要なモジュールも多数含まれていることから大変便利です．</br></br>

WinPythonの場合，プレインストールされているモジュールの置き換えも簡単（逆にトラブルも起こりうる）で，pipでモジュールの追加や削除を実行できます．commercial版pyQtへの置換も簡単にできました．</br>

その他，WinPythonの場合，仮想環境の構築が容易でPath設定をしなくとも使用できることが魅力です．</br>

####  WinPythonのインストール方法

[WinPythonホームページ](http://winpython.github.io/)からダウンロードサイトに移動し，使いたいバージョンのPythonに相当するWinPython####.exeをダウンロードし適当なフォルダー保存します．####部分には32，64ビット，Pythonバージョン番号などが付きます．あとは保存したWinPython####.exeをダブルクリックして好きなフォルダーへ展開するだけです．</br>

WinPythonホームページにも記載されていますが，WinPython利用において，Windows 8..10ユーザーは[Microsoft Visual C++ Redistributable for Visual Studio 2017..2019](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) (WinPython 32bitにはvc_redist_x86.exe， WinPython 64bitには vc_redist_x64.exe）をインストールする必要がありそうです．実際にプログラムを走らせてみてエラーが出る場合など必要に応じてインストールして下さい．</br>

ファイル名末尾に"Zero"が付いているものは最小限のモジュールとIDEのみのバージョンです．自分で様々なモジュールをインストールするのが面倒であればファイルサイズが大きいものを選択すればよいです．</br>

#### WinPython利用法

Winpython64-3.8.1.0cod.exeをダブルクリックしてできるWPy64-3810フォルダー内ファイル構成です．</br>

![](WinPython3810_inFolder.gif)



license.txtを確認するとMITライセンスであることがわかります．MITライセンスについては[こちら](https://ja.wikipedia.org/wiki/MIT_License)．</br>

プログラム開発用の統合開発環境ソフトにはPyzo，Spyder，VSCodeがプレインストールされています．</br>

WindowsシステムにPath設定しなくともPyzo，Spyder，VSCode，JupyterNoteBookなどでPythonコードを走らせることができます．つまりWinPython####.exeを展開しただけの状態で使用すると仮想環境で利用することになります．（USBメモリーに展開すると持ち運び可能な開発環境になります）</br>

**注意**：ZeroバージョンのWInPythonにも同じ内容が表示されますが必要とするPythonモジュールが含まれていないためSpyder, WinPython Control Panelなどは使えません．</br>

仮想環境下でPython用モジュールをインストールする場合はWinPythn Command Prompt.exeまたはWinPython Powershell Prompt.exeを立ち上げ，通常のPython環境と同様にpipコマンドで行います．pipコマンドについてはググって下さい．その他，WInPython Control Panelからも行えます．こちらは[WinPythonのホームページ](https://winpython.github.io/)を参照して下さい．</br>

グローバル環境に設定したい場合はWinPython Control Panelをダブルクリックし，メインメニューにある"Advanced"から"Resister Distribution"を設定すればよいらしいです．←試したことはありません．自己責任で試して下さい．</br>

グローバル環境にするとスタートメニュー→Windowsシステムツール→コマンドプロンプトまたはスタートメニュー→Windows Powershellからpipコマンドを使えます（たぶん）</br>

#### その他，必要なモジュールのインストール

本管理者非線形最小自乗法を使うデータ解析とグラフ表示を行うため，Numpy, Scipy, lmfit, Matplotlibを使います．これらのモジュールはフルバージョンのWinPythonであればプレインストールされています．特にnumpyはIntel MKLビルド版とサービス満天です．Zero版の場合は自身でインストールしてください．pipコマンドでインストール可能です．</br>


#### wxPythonインストール

wxPythonモジュールはWinPythonにプレインストールされていません．wxPythonを使う場合は[wxPythonホームページ](https://www.wxpython.org/)のダウンロードページでサポートするPythonバージョンを確認し，使用するPythonバージョンを決めましょう．最新バージョンのPythonはサポートされていないことがあります．</br>

wxPythonのインストールはWinPython Command Prompt，WinPython Powershell Promptを立ち上げ，

`pip install wxpython`

と入力すればOKです．proxy設定についてはpipのヘルプまたはググって下さい．</br>



**補足情報**：Windows用のPython用バイナリーモジュールは[Unofficial Windows Binaries for Python Extension Packages](https://www.lfd.uci.edu/~gohlke/pythonlibs/)ページから取得することもできます．このページには各モジュールの簡単な説明が付いていますので，どんなモジュールがあるのか？辞書代わりになります．MKLビルド版numpyのバイナリーもアップロードされていますので，これらも簡単にインストールできます．</br>



## mac OS編

mac OSはシステムでPythonを使っています．したがってOSにインストールされているPythonとは異なる仮想環境下でPythonをインストールする必要があります．</br>

仮想環境下へのPythonインストールにはAnacondaあるいはHomebrew + pyenvを用いた方法などがあるようです．本ページ管理者はWIndowsの場合と同様にpyQtをcommercial版に置き換えたかったこと，複数バージョンのPython環境を構築したかったことからHomebrew + pyenvを用いた環境構築を採用しました．用いたのは2017年製MacBook Airです．</br>

現行のmac OS 10.15 (Cataline)へのHomebrewとpyenvのインストールについては「[MacOSとHomebrewとpyenvで快適python環境を。](https://qiita.com/crankcube/items/15f06b32ec56736fc43a)」ページの通りに行えばpyenvをインストールするところまでは同じ操作で大丈夫です．</br>

「[MacOSとHomebrewとpyenvで快適python環境を。](https://qiita.com/crankcube/items/15f06b32ec56736fc43a)」ページにも書かれていますがPythonのインストールは自前でコンパイルされます．（なのでXCodeのインストールが事前に必要）wxPythonはmac OSのライブラリーにアクセスするため，Pythonインストール時にOSライブラリーにリンクを張るオプションをつける必要があります．したがって（例えばPython3.8.1の）インストールは

```
pyenv install 3.8.1
```

ではなく

```
env PYTHON_CONFIGURE_OPTS="--enable-framework" pyenv insatll 3.8.1
```

とする必要があります．このオプションを付けないでインストールしたPythonでwxPythonコマンドを含むプログラムを走らせると

```
This program needs access to the screen. Please run with a
Framework build of python, and only when you are logged in
on the main display of your Mac.
```

というエラーメッセージが出て止まります．</br>

あとは「[MacOSとHomebrewとpyenvで快適python環境を。](https://qiita.com/crankcube/items/15f06b32ec56736fc43a)」ページと同じく普段使用するPythonを設定するためターミナルから下記コマンドを入力します．（Python 3.7.7の場合）

```
pyenv global 3.8.1
```

念のためPython設定が正しいかを

```
pyenv versions
```

または

```
python --version
```

で確認してください．



本ページ管理者は非線形最小自乗法によるデータ解析およびグラフ表示も行うためNumpy, Scipy, Matplotlib, lmfitもインストールしました．ターミナルから下記コマンドを入力するだけでインストールできます．

`pip install numpy scipy matplotlib lmfit`

普段使用するPythonの設定が正しければ，wxPythonのインストールはターミナルから

```
pip install wxpython
```

と入力すればOKです．</br></br>

Pythonの統合開発環境であるSpyderはpipでインストールできます．</br>

ターミナルから

```
pip install spyder
```

と入力すればインストールできます．インストール後ターミナルから

```
spder3
```

または

```
spyder3&
```

と入力すれば立ち上がります．</br>

**補足**：PYTHON_CONFIGURE_OPTS="--enable-framework"とPYTHON_CONFIGURE_OPTS="--enable-shared"については「[PYTHONビルド時の--enable-frameworkと--enable-sharedの違い](https://abrakatabura.hatenablog.com/entry/2017/07/08/130407)」に解説があります．</br>

**おまけ**：NumpyでIntel MKL (Math Kernel Library)を使うと計算が速くなるモジュールもあります．mac OSの場合，自身でMKLを導入してNumpy, Scipyをビルドしなおすのは大変です．この様な用途の場合は素直にAnacondaを使いましょう．Anacondaにはnumpy+mkl，scipy+mklがプレインストールされているようです．Anacondaパッケージはpyenvからインストールできます．</br>

**MKL Numpyインストール法**

Anacondaを使わない場合は[ここ](https://qiita.com/Ishotihadus/items/f7d82a1f3a3ca6900bf7)を参照してインストールできました．ただしMKL Numpyのみ成功</br>

(1) IntelからMKLをダウンロードしインストール．インストールパスはデフォルトの/opt/intelのまま</br>

(2) .numpy.cfgファイルをホームディレクトリに作成．内容は

```
[mkl]
library_dirs = /opt/intel/mkl/lib
include_dirs = /opt/intel/mkl/include
mkl_libs = mkl_rt
```

(3) pipでビルド（pip.conf）を書かない方法．

```
pip install --no-binary :all: numpy
```

(4) @rpathの追加．ターミナルで下記コマンドを実行（「[MacOSとHomebrewとpyenvで快適python環境を。](https://qiita.com/crankcube/items/15f06b32ec56736fc43a)」に記載されているパスにpyenvとPython3.8.1がインストールされている場合）

```
install_name_tool --add_rpath /opt/intel/mkl/lib /usr/local/var/pyenv/versions/3.8.1/Python.framework/Versions/3.8/lib/python3.8/site-packages/numpy/core/_multiarray_umath.cpython-38-darwin.so
```

/usr/local..以降はインストールされているパスに依存します．「[Mac に MKL 版 numpy / scipy をインストールする](https://qiita.com/Ishotihadus/items/f7d82a1f3a3ca6900bf7)」」のテストにあるようにPythonからimport numpyを実行し，出力されるエラーに含まれるパス名を確認して下さい．</br>

MKL Numpyのインストールに成功すればfacebookで開発されたpyTorchなどの機械学習モジュールが使えるようになります．

(5) Scipyについては「[[Mac に MKL 版 numpy / scipy をインストールする]](https://qiita.com/Ishotihadus/items/f7d82a1f3a3ca6900bf7)」ページとは異なりScipyをビルドしてインストールすることはできませんでした．同じ現象は「[MacにPython3とMKL+Numpyをインストール](https://tm23forest.com/contents/mac-python3-install-numpy-mkl)」ページにもあります．Scipyについてはpipで普通にバイナリーからインストールするしかありませんでした．(3)でpip.confを使わなかったのはこのため．pip.confでScipyもビルドモードにしてしまうとバイナリーからのインストールされなくなります．</br>



## Linux編

**注意**：Linux導入は敷居が高いです．またCドライブ内の情報が消去されてしまう可能性もありますのでサブマシンへの導入がよいと思います．Linuxは古いPCでも軽快に動きますので中古PCやサポートが終わってしまったOSがプレインストールされているPCに導入しても十分使えます．（例えば[こちら](http://www.gadgets-today.net/?p=3591)とか，[こちら](http://lioon.net/lubuntu-the-best-for-letsnote)とか，[こちら](https://note.com/you_kyan/n/n101d8a580286)のページ）</br>

#### Distribution選択

Linuxには様々なdistribution版があり，どれを選べばよいか？から既に挫けそうです．Linuxのdistributionについては[こちら](https://ja.wikipedia.org/wiki/Linux%E3%83%87%E3%82%A3%E3%82%B9%E3%83%88%E3%83%AA%E3%83%93%E3%83%A5%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3)．その他，[【2020年】初心者にオススメなLinuxディストリビューション](http://note.kurodigi.com/linux-distro-2020/)．本管理者はwxPythonを使える環境が欲しかったので，まず[wxPythonのホームページ](https://www.wxpython.org/)を確認しました．[wxPython Downloads](https://www.wxpython.org/pages/downloads/)にLinuxの注意が書かれています．さらに[wxPython Extras linuxのgtk3フォルダ](https://extras.wxpython.org/wxPython4/extras/linux/gtk3/)を確認するとcentos-7, debian-8, 9, fedra-24~28, ununtu-14.04-18.04ならインストールできそうだと思われます．

![](C:\Python備忘録\wxPython_extra_linux.gif)

ubuntuには[日本語Remix](https://www.ubuntulinux.jp/home)版がありサイト情報も多いことから私のような初心者でも何とかなりそう．そこでubuntuのデスクトップ版で長期サポートバージョンのUbuntu 18.04.3 LTSを選択しました（長期と言っても2023年まで）．導入を試みたPCはWIndows 8.1がインストールされたPanasonic製Let's Note CF-MX3です．SSD（250GB），RAM 8GB実装マシンです．</br>

#### ライブDVD作成とテスト起動

ubuntuには[日本語Remix](https://www.ubuntulinux.jp/home)版サイトから[ubuntu-ja-18.04.3-desktop-amd64.iso（ISOイメージ）](http://cdimage.ubuntulinux.jp/releases/18.04.3/ubuntu-ja-18.04.3-desktop-amd64.iso)をダウンロード，DVDに焼いて起動ディスク（ライブDVD）を作成します．[Ubuntu 18.04 その89 - UbuntuのライブDVDを作成するには（Windows編）](https://kledgeb.blogspot.com/2018/04/ubuntu-1804-89-ubuntudvdwindows.html)などを参考にしました．ubuntuをライブDVDから起動するとインストールしなくてもubuntuを試用することができます．（[Linux_OS　Ubuntuの試用、ライブＤＶＤ起動のすすめ](https://blog.goo.ne.jp/goosyun/e/5ae3456c18121843857be0b51c5d1e3c)）</br>

[UEFIモードでUbuntuをインストールする方法（Ubuntu 16.04 LTS）](https://www.archlinux.site/2018/02/uefiubuntuubuntu-1604-lts.html) を頼りに，ライブDVDから起動するための準備としてWindowsの「コントロールパネル」→「電源オプション」→「電源ボタンの動作を設定する（システム設定）」で**高速起動のチェックを外します**．（[windows8のPCにUbuntuをインストールしデュアルブート環境で使う](https://smartgoods.me/2014/07/windows8_ubuntu_dualboot/)も参照）．その後，windowsを再起動し，PCメーカーのロゴが表示されているタイミングでBios設定画面を呼び出し（今回のPCではF2キー連打で表示），メニューから光学ドライブ電源を「オン」，起動メニューにあるUEFI起動は初期設定の「有効」にしたまま，UEFI優先度でハードディスクUEFI起動を「無効」，光学ディスクドライブUEFI起動を「有効」に変更，セキュリティーメニューの「セキュアブート」にある「セキュアブート制御」を「無効」に変更し，ライブDVDをセットして再起動しました．が，この設定では起動途中でgrubプロンプトが表示されてとまってしまい，[Ubuntu 18.04 LTSインストールガイド【スクリーンショットつき解説】](https://linuxfan.info/ubuntu-18-04-install-guide)ページのようには進まず挫折  ○|￣|＿　</br>

気を取り直して今度はBios設定でUEFI起動を「無効」にし，光学ドライブの起動優先順位をハードディスクよりも先に変更したところ[Ubuntu 18.04 LTSインストールガイド【スクリーンショットつき解説】](https://linuxfan.info/ubuntu-18-04-install-guide)ページの通り試用画面が表示されました．この設定でインストールできそうなことを確認し，次はWindows Cドライブのパーティション切り変更を行います．</br>

#### Cドライブパーティションサイズ変更

Windows 8.1のサポートは継続されていることからWindows 8.1とubuntu-Desktop 18.04 LTSのデュアルブート化を目指します．UbuntuをインストールするにはCドライブのパーティションサイズを変更する必要があります．当然，Cドライブにある情報が消えるリスクも高いので必ず起動ディスク作成とバックアップを事前に行って下さい．さらにCドライブのプロパティーから「このディスクのクリーンアップ」を実行しデフラグします．「[Windows PCでOSをデュアルブートするときの覚え書き](https://www.cottpic.com/2019/01/dualboot-on-windows.html)」にあるように[MiniTool Partition Wizard Free Edition](https://www.partitionwizard.com/free-partition-manager.html)などのツールを使うとCドライブ内の情報を残したままパーティションサイズを変えられる様です．ただし**設定を間違えるとウンも言わさず工場出荷状態に戻されます**．工場出荷状態に戻っても良い場合はWindowsの「ディスクの管理」マネージャーでサイズ変更しても構いません．（もちろんバックアップと起動ディスクは必須です．細心の注意が必要です）今回はWindows用に150GB，Ubuntu用に100GBに分割しました．Ubuntu用に分割したパーティションはフォーマットなどせず未設定のママで大丈夫です．</br>

#### デュアルブートでUbuntuインストール．．．（やや不満あり．結果失敗）

Ubuntu 16.04での情報だが[【初心者でもわかる】Ubuntuのインストール方法](https://eng-entrance.com/ubuntu-install)まとめが参考になった．上記のテスト起動法でライブDVDを起動するとubuntuのインストールボタンがある画面が現れるので，"Ubuntuをインストール"ボタンをポチる．</br>

**危険：インストールの種類でデフォルトの「ディスクを削除してUbuntuをインストール」を選択すると，VirtualBoxをインストールしていなければハードディスクを丸ごと使われてしまうのでデュアルブートはできなくなる（当然Cドライブ内のWindows関係データは全て消える）．**</br>

デュアルブートにする場合は「その他」を選択し手動でパーティション設定をする．この後の設定は[【初心者でもわかる】Ubuntuのインストール方法](https://eng-entrance.com/ubuntu-install)とほぼ同じにしたが「基本パーティション，ext4ジャーナリングファイルシステム，マウントポイント"/"」のパーティションと「スワップ領域」のみ追加した．スワップ領域は物理メモリの1～2倍が適正値とあるので8GBとした．あとは言われるがままに設定入力するだけでインストールが終わる．最後に再起動すればUbuntuが立ち上がる．</br>

再起動すると最初に現れるUbuntuブートローダーにWindows Boot Managerが表示されないことに気付いた．Ubuntuのアクティビティーから端末アプリを立ち上げ

```
ls /sys/firmware/efi/
```

と入力すると，そんなフォルダはないと怒られた．インストールされたシステムはUEFIではなくレガシーBios起動設定でインストールされていた．この設定だとBiosを立ち上げUEFI起動を有効にするとWindows，無効にするとUbuntuがブートするシステムになった．できることならUbuntuもUEFIブートにしたいが，ネット検索した限りレガシーBiosブートシステムを後からUEFIブートに変えることは難しそうだった．挫折２ ○|￣|＿</br>
