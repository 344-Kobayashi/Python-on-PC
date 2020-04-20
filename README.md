# ノートPCへPython環境構築

## 1. はじめに

このページはWindows 8.1および10，macOS 10.15 (catalina), Linux (ubuntu 18.04)へのPythonと関連モジュールをインストールした経験メモです．**このページに記載された方法を試して何らかの不具合が生じても本ページ管理者は何ら責任は持ちません**．pythonやlinuxのインストールは**自己責任**で行って下さい．</br>

注意：このページ管理者は「にわかプログラマー」です．</br>

PythonはWindows, macOS, Linuxに加えてiOS，アンドロイドでも利用できるプログラム言語です．特にWindows，macOS，Linuxではグラフィックユーザーインターフェイス（GUI）を含むプログラムを書けることに興味を持ち，いろいろ試した結果です．GUIモジュールは主にwxPython，すこしだけpyQtを使いました．wxPythonはライセンスがゆるめなのでpyQtよりも使いやすい気がします．</br></br>

Pythonは複数のバージョンやインストールされたモジュール数が異なる環境を使うことが多いようです．本ページでは複数バージョンのPython環境の構築が目的の一つであるため，[pythonの本家本元サイト](http://www.python.org)からダウンロードする方法は用いていません．</br></br>

## 2. Windows

WindowsへのPython環境構築には[Anaconda](https://www.anaconda.com/)と[WinPython](http://winpython.github.io/)を試しましたが，現在はWinPythonのみを使っています．Anacondaを使わなくなった理由は，インストールされているGPL版pyQtをCommercial版pyQtに置き換えられなかったためです．（数年前の話．Anadondaパッケージにはpython3.dllが含まれていないためでした）</br></br>

WinPythonフルバージョンはAnacondaと同様に様々なモジュールや統合開発環境ソフトがプレインストールされています．科学技術計算に必要なモジュールも多数含まれていることから大変便利です．</br></br>

WinPythonの場合，プレインストールされているモジュールの置き換えも簡単（逆にトラブルも起こりうる）で，pipでモジュールの追加や削除を実行できます．commercial版pyQtへの置換も簡単にできました．</br></br>

その他，WinPythonの場合，仮想環境の構築が容易でPath設定をしなくとも使用できることが魅力です．</br></br>

#### 2. 1. WinPythonのインストール方法

[WinPythonホームページ](http://winpython.github.io/)からダウンロードサイトに移動し，使いたいバージョンのPythonに相当するWinPython####.exeをダウンロードし適当なフォルダー保存します．####部分には32，64ビット，Pythonバージョン番号などが付きます．あとは保存したWinPython####.exeをダブルクリックして好きなフォルダーへ展開するだけです．</br></br>

WinPythonホームページにも記載されていますが，WinPython利用において，Windows 8..10ユーザーは[Microsoft Visual C++ Redistributable for Visual Studio 2017..2019](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads) (WinPython 32bitにはvc_redist_x86.exe， WinPython 64bitには vc_redist_x64.exe）をインストールする必要がありそうです．実際にプログラムを走らせてみてエラーが出る場合など必要に応じてインストールして下さい．</br></br>

ファイル名末尾に"Zero"が付いているものは最小限のモジュールとIDEのみのバージョンです．自分で様々なモジュールをインストールするのが面倒であればファイルサイズが大きいものを選択すればよいです．</br></br>

#### 2. 2. WinPython利用法

Winpython64-3.8.1.0cod.exeをダブルクリックしてできるWPy64-3810フォルダー内ファイル構成です．</br>

![](C:\Python備忘録\WinPython3810_inFolder.gif)



license.txtを確認するとMITライセンスであることがわかります．MITライセンスについては[こちら](https://ja.wikipedia.org/wiki/MIT_License)．</br>

プログラム開発用の統合開発環境ソフトにはPyzo，Spyder，VSCodeがプレインストールされています．</br>

WindowsシステムにPath設定しなくともPyzo，Spyder，VSCode，JupyterNoteBookなどでPythonコードを走らせることができます．つまりWinPython####.exeを展開しただけの状態で使用すると仮想環境で利用することになります．（USBメモリーに展開すると持ち運び可能な開発環境になります）</br>

**注意**：ZeroバージョンのWInPythonにも同じ内容が表示されますが必要とするPythonモジュールが含まれていないためSpyder, WinPython Control Panelなどは使えません．</br></br>

仮想環境下でPython用モジュールをインストールする場合はWinPythn Command Prompt.exeまたはWinPython Powershell Prompt.exeを立ち上げ，通常のPython環境と同様にpipコマンドで行います．pipコマンドについてはググって下さい．その他，WInPython Control Panelからも行えます．こちらは[WinPythonのホームページ](https://winpython.github.io/)を参照して下さい．</br></br>

グローバル環境に設定したい場合はWinPython Control Panelをダブルクリックし，メインメニューにある"Advanced"から"Resister Distribution"を設定すればよいらしいです．←試したことはありません．自己責任で試して下さい．</br></br>

グローバル環境にするとスタートメニュー→Windowsシステムツール→コマンドプロンプトまたはスタートメニュー→Windows Powershellからpipコマンドを使えます（たぶん）</br></br>

#### 2. 3. その他，必要なモジュールのインストール

本管理者非線形最小自乗法を使うデータ解析とグラフ表示を行うため，Numpy, Scipy, lmfit, Matplotlibを使います．これらのモジュールはフルバージョンのWinPythonであればプレインストールされています．特にnumpyとscipyはIntel MKLビルド版とサービス満天です．Zero版の場合は自身でインストールしてください．pipコマンドでインストール可能です．</br></br>


#### 2. 4. wxPythonインストール

wxPythonモジュールはWinPythonにプレインストールされていません．wxPythonを使う場合は[wxPythonホームページ](https://www.wxpython.org/)のダウンロードページでサポートするPythonバージョンを確認し，使用するPythonバージョンを決めましょう．最新バージョンのPythonはサポートされていないことがあります．</br></br>

wxPythonのインストールはWinPython Command Prompt，WinPython Powershell Promptを立ち上げ，

`pip install wxpython`

と入力すればOKです．proxy設定についてはpipのヘルプまたはググって下さい．</br></br>



**補足情報**：Windows用のPython用バイナリーモジュールは[Unofficial Windows Binaries for Python Extension Packages](https://www.lfd.uci.edu/~gohlke/pythonlibs/)ページから取得することもできます．このページには各モジュールの簡単な説明が付いていますので，どんなモジュールがあるのか？辞書代わりになります．MKLビルド版numpyとscipyのバイナリーもアップロードされていますので，これらも簡単にインストールできます．</br></br>



## 3. mac OS

mac OSはシステムでPythonを使っています．したがってOSにインストールされているPythonとは異なる仮想環境下でPythonをインストールする必要があります．</br>

仮想環境下へのPythonインストールにはAnacondaあるいはHomebrew + pyenvを用いた方法などがあるようです．本ページ管理者はWIndowsの場合と同様にpyQtをcommercial版に置き換えたかったこと，複数バージョンのPython環境を構築したかったことからHomebrew + pyenvを用いた環境構築を採用しました．</br></br>



現行のmac OS 10.15 (Cataline)へのHomebrewとpyenvのインストールについては「[MacOSとHomebrewとpyenvで快適python環境を。](https://qiita.com/crankcube/items/15f06b32ec56736fc43a)」ページの通りに行えばpyenvをインストールするところまでは同じ操作で大丈夫です．</br></br>



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

というエラーメッセージが出て止まります．</br></br>



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

と入力すれば立ち上がります．</br></br>



**補足**：PYTHON_CONFIGURE_OPTS="--enable-framework"とPYTHON_CONFIGURE_OPTS="--enable-shared"については「[PYTHONビルド時の--enable-frameworkと--enable-sharedの違い](https://abrakatabura.hatenablog.com/entry/2017/07/08/130407)」に解説があります．</br>

**おまけ**：機械学習用モジュールの中にはNumpy, ScipyでIntel MKL (Math Kernel Library)を使う設定が必要なものもあります．mac OSの場合，自身でMKLを導入してNumpy, Scipyをビルドしなおすのは大変です．この様な用途の場合は素直にAnacondaを使いましょう．Anacondaにはnumpy+mkl，scipy+mklがプレインストールされているようです．Anacondaパッケージはpyenvからインストールできます．</br></br>



**MKL numpyインストール法**

Anacondaを使わない場合は[ここ](https://qiita.com/Ishotihadus/items/f7d82a1f3a3ca6900bf7)を参照してインストール可．ただしMKL Numpyのみ成功</br>

(1) IntelからMKLをダウンロードしインストール．インストールパスはデフォルトの/opt/intelのまま</br>

(2) .numpy.cfgファイルをホームディレクトリに作成．内容は

```
[mkl]
library_dirs = /opt/intel/mkl/lib
include_dirs = /opt/intel/mkl/include
mkl_libs = mkl_rt
```

(3) pipでビルド（pip.conf）を書かない方法．</br>

```
pip install --no-binary :all: numpy
```

(4) @rpathの追加．ターミナルで下記コマンドを実行（「[MacOSとHomebrewとpyenvで快適python環境を。](https://qiita.com/crankcube/items/15f06b32ec56736fc43a)」に記載されているパスにpyenvとPython3.8.1がインストールされている場合）

```
install_name_tool --add_rpath /opt/intel/mkl/lib /usr/local/var/pyenv/versions/3.8.1/Python.framework/Versions/3.8/lib/python3.8/site-packages/numpy/core/_multiarray_umath.cpython-38-darwin.so
```

/usr/local..以降はインストールされているパスに依存します．「[Mac に MKL 版 numpy / scipy をインストールする](https://qiita.com/Ishotihadus/items/f7d82a1f3a3ca6900bf7)」」のテストにあるようにPythonからimport numpyを実行し，出力されるエラーに含まれるパス名を確認して下さい．</br>

MKL Numpyのインストールに成功すればfacebookで開発されたpyTorchなどの機械学習モジュールが使えるようになります．

(5) Scipyについては「[[Mac に MKL 版 numpy / scipy をインストールする]](https://qiita.com/Ishotihadus/items/f7d82a1f3a3ca6900bf7)」ページとは異なりscipyをビルドしてインストールすることはできませんでした．同じ現象は「[MacにPython3とMKL+Numpyをインストール](https://tm23forest.com/contents/mac-python3-install-numpy-mkl)」ページにもあります．Scipyについてはpipで普通にバイナリーからインストールするしかありませんでした．(3)でpip.confを使わなかったのはこのため．pip.confでScipyもビルドモードにしてしまうとバイナリーからのインストールされなくなります．</br></br>



## 4. Linux編

**注意**：Linux導入は敷居が高いです．またCドライブ内の情報が消去されてしまう可能性もありますのでサブマシンへの導入がよいと思います．Linuxは古いPCでも軽快に動きますの．中古PC，サポートが終わってしまったOSがプレインストールされているPCに導入することもできます．（例えば[こちら](http://www.gadgets-today.net/?p=3591)とか，[こちら](http://lioon.net/lubuntu-the-best-for-letsnote)とか，[こちら](https://note.com/you_kyan/n/n101d8a580286)のページ）</br>

#### 4.1. Distribution選び

Linuxには様々なdistribution版があり，どれを選べばよいか？から挫けそうです．Linuxのdistributionについては[こちら](https://ja.wikipedia.org/wiki/Linux%E3%83%87%E3%82%A3%E3%82%B9%E3%83%88%E3%83%AA%E3%83%93%E3%83%A5%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3)．その他，[【2020年】初心者にオススメなLinuxディストリビューション](http://note.kurodigi.com/linux-distro-2020/)．本管理者はwxPythonを使える環境構築をしたかったので，[wxPythonのホームページ](https://www.wxpython.org/)を確認したところ，[wxPython Downloads](https://www.wxpython.org/pages/downloads/)にLinuxの注意が書かれています．さらに[wxPython Extras linuxのgtk3フォルダ](https://extras.wxpython.org/wxPython4/extras/linux/gtk3/)を確認するとcentos-7, debian-8, 9, fedra-24~28, ununtu-14.04-18.04ならインストールできそうです．

![](C:\Python備忘録\wxPython_extra_linux.gif)

ubuntuには[日本語Remix](https://www.ubuntulinux.jp/home)版がありサイト情報も多いことから私のような初心者でも何とかなりそうです．そこでubuntuのデスクトップ版で長期サポートバージョンのUbuntu 18.04.3 LTSを選択しました．導入を試みたPCはWIndows 8.1がインストールされたPanasonic製Let's Note CF-MX3です．</br></br>



