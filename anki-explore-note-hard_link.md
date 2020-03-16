# day 1 2019/12/24
成功下载anki仓库
可以安装python依赖(二进制包)
win10 sdk 下载
wsl 安装 ,使用 linux toolchains

尝试flutter;win10 desktop 构建失败;无法使用 desktop版本.


# day 2 2019/12/25
尝试 使用 wsl 环境构建;嗯,,;还是环境问题..毕竟qt是有窗口;wsl构建中的还是只能生成在wsl下运行的;/

# day 3 2019/12/26
准备转移到 debian 环境下


开始阅读原码
## anki start trace
aqt.run
  \_run
    mv = aqt.main.AnkiQt
      app with AnkiQt (main)

AnkiQt
  __init__
    setupUI
    setupAddon
    ...

# day 4 2019/12/27
faulthandler

aqt.mediasrv.MediaServer

aqt.forms.main.Ui_MainWindow

aqt.webview.AnkiWebView


anki/

anki/storage.py

找到了数据库与数据操作的相关文件夹anki
aqt是qt的界面实现代码文件夹


# day 5

# 2020-02-17

关于 flutter 中 类似树的设计暂时有两种构建策略

一是,直接用 canvas,custompaint,,绘制

二是用类似stack来模拟效果.

还是 直接绘制吧

# 2020-03-14

## 确定版本为2.1.9

## 开始了解第一层结构

anki/                         : anki 核心程序文件夹？
aqt/                          : anki qt 界面程序
designer/                     : qt 界面 源文件
tests/                        : 测试程序文件夹
web/                          : 疑似web 版程序源文件
.gitignore                    : git  忽略文件数据
.travix.yml                   : travix
runanki                       : anki       启动文件
tools/                        : 实用工具文件夹？
anki-explore-note-hard_link.md: 笔记硬链接文件
anki.1                        : man page usage?
anki.desktop                  : desktop (图标)文件
anki.png                      : anki 图标
anki.xml                      : ?
anki.xpm                      : ?
LINCENSE                      : 协议说明文件
LICENSE.logo                  : anki logo 协议文件
Makefile                      : anki make 配置 文件
pkgkey.asc                    : 公钥文件?
README.contributing           : 贡献指南
README.development            : 开发者使用说明
README.md                     : anki git repo 说明
requirements.txt              : python 依赖文件

## 确定主要关注文件
aqt/,anki/

# 2020-03-15 , 2020-03-16
## 了解 aqt/ 结构
`__pycache__`   : python 缓存文件
forms/          : qt ui 界面 构造 程序源码
`__init__.py`   : ?
about.py        : 菜单栏/帮助/关于
addcards.py     : ?
addons.py       : ?
browser.py      : ?
clayout.py      : ?
customstudy.py  : ?
deckbrowser.py  : ?
deckchooser.py  : ?
deckconf.py     : ?
downloader.py   : ?
dyndeckconf.py  : ?
editcurrent.py  : ?
editor.py       : ?
errors.py       : ?
exporting.py    : ?
fields.py       : ?
importing.py    : dpkg 导入 | ?
main.py         : 主窗口构造程序, 组装部件 setupmainwindow
mediasrv.py     : 媒体服务器?
                :  something
                :
modelchooser.py : ?
models.py       : ?
overview.py     : ?
pinnedmodules.py: ?
preferences.py  : ?
profiles.py     : ?
progress.py     : ?
qt.py           : ?
reviewer.py     : ?
sound.py        : ?
stats.py        : ?
studydeck.py    : ?
sync.py         : 远程同步 源码
tagedit.py      : ?
taglimit.py     : ?
toolbar.py      : 工具栏 构建代码
update.py       : 软件更新 
utils.py        : 常用的Anki界面 组件与工具
webview.py      : 网页试图 构建 QWebEnginePage
winpaths.py     : 检索 win 系统路径


## tools/build_ui.sh
`从designer/*.ui 生成对应的 aqt/forms/*.py `
pyuic5 生成 中间 py 源码文件
perl 正则替换 指定特殊对象?

## forms/
界面构建模板 文件夹

