# Sublime 备忘录

![Sublime Text](http://7xix3g.com1.z0.glb.clouddn.com/15-7-14/49125259.jpg)

### [插件管理器](https://packagecontrol.io/)

![Package Control](https://packagecontrol.io/img/logo.svg)

**Package Control 安装**：点击菜单中的 “View”–“Show Console”（也可通过快捷键 Ctrl + ` 打开，不过可能因与系统其他软件快捷键冲突而打不开）调出 Console。然后把下面的代码粘贴进去后回车即可，需稍微等待一段时间。

> import urllib.request,os,hashlib; h = 'df21e130d211cfc94d9b0905775a7c0f' + '1e3d39e33b79698005270310898eea76'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)

### 常用插件

[ChineseLocalizations ](https://github.com/rexdf/ChineseLocalization) ： 中文化   
[AlignTab ](https://github.com/randy3k/AlignTab) ： 代码对齐   
[All Autocomplete ](https://github.com/alienhard/SublimeAllAutocomplete) ： 搜索所有打开的文件来寻找匹配的提示词   
[ConvertToUTF8 ](https://github.com/seanliang/ConvertToUTF8) ： GB2312编码改为UTF-8   
[Git ](https://github.com/kemayo/sublime-text-git) ： Git支持   
[GitGutter ](https://github.com/jisaacks/GitGutter) ： 显示代码中的编辑,添加或删除   
[SideBarEnhancements ](https://github.com/SideBarEnhancements-org/SideBarEnhancements) ： 增强侧边栏   
[Markdown Preview ](https://github.com/revolunet/sublimetext-markdown-preview) ： Markdown预览   
[MarkdownLivePreview ](https://github.com/math2001/MarkdownLivePreview) ： Markdown支持   
[ColorPicker ](https://github.com/weslly/ColorPicker) ： 取色器   
[Color Highlighter ](https://github.com/Monnoroch/ColorHighlighter) ： 显示选中颜色代码的视觉颜色   
[Emmet ](https://github.com/sergeche/emmet-sublime) ： 前端开发神器,提高代码编写的效率   
[SublimeCodeIntel ](https://github.com/SublimeCodeIntel/SublimeCodeIntel) ： 代码提示   
[A File Icon ](https://github.com/ihodev/a-file-icon) ： 侧边栏文件类型图标   
[BracketHighlighter ](https://github.com/facelessuser/BracketHighlighter) ： 提供括号、引号这类高亮功能   
[SyncedSidebarBg ](https://github.com/aziz/SublimeSyncedSidebarBg) ： 自动同步侧边栏底色为编辑窗口底色   
[SublimeREPL ](https://github.com/wuub/SublimeREPL) ： python shell交互   
[GPG ](https://github.com/dmitrievav/sublime_gpg) ： GPG加密解密   
[Evernote ](https://github.com/bordaigorl/sublime-evernote) ： Sublime上编辑浏览Evernote 

### 主题

[One dark theme](https://github.com/andresmichel/one-dark-theme) | [Material Theme](https://github.com/equinusocio/material-theme) | [Spacegray](https://github.com/kkga/spacegray) | [Agila Theme](https://github.com/arvi/Agila-Theme) | [Boxy Theme](https://github.com/ihodev/sublime-boxy)

### 应用技巧和诀窍

  * 基本编辑   
Ctrl + Enter 在当前行下面新增一行然后跳至该行   
Ctrl + Shift + Enter 在当前行上面增加一行并跳至该行   
Ctrl + ←/→ 进行逐词移动   
Ctrl + Shift + ←/→ 进行逐词选择 

  * 选择   
Ctrl + D 选中一个单词   
Ctrl + L 选中一行   
Ctrl + A 全选   
Ctrl 按住 Ctrl 键再点击想选中的行   
**Ctrl + D** (选中部分文本时) 直接选中下一次出现的该文本（使用 Ctrl + K 进行跳过，使用 Ctrl + U 进行回退，使用 Esc 退出多重编辑）   
**Ctrl + Shift + L** 可以将当前选中区域打散，然后进行同时编辑 Ctrl + J 可以把当前选中区域合并为一行 

  * 标准查找&替换   
Ctrl + F 调出搜索框   
Ctrl + H 进行替换   
Ctrl + P 会列出当前打开的文件   
Ctrl + G 然后输入行号以跳转到指定行   
Ctrl + R 列出Markdown文档目录
