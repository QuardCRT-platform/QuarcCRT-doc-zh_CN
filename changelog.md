<div style="text-align: right"><a href="../../en/latest/changelog.html">🇺🇸 English</a> | <a href="../../zh-cn/latest/changelog.html">🇨🇳 简体中文</a> | <a href="../../zh-tw/latest/changelog.html">🇭🇰 繁體中文</a> | <a href="../../ja/latest/changelog.html">🇯🇵 日本語</a></div>

# 更新日志

## [[待发布](https://github.com/QQxiaoming/quardCRT)]

- 增加回显功能
- 修复部分会话类型无法重连问题
- 增加非连接状态下的会话可以通过单击回车键自动重连功能
- 增加串口自动检测物理连接断开功能
- 增加刷新串口按钮在选择串口页面中
- 增加了至多四窗口分屏模式以及多种布局模式
- 发送命令窗口增加单会话/组会话/全部会话三种模式
- 修复非英文环境下Telnet会话存储配置错误导致无法连接问题 [#IAADHZ](https://gitee.com/QQxiaoming/quardCRT/issues/IAADHZ)
- 新增预构建插件[timestamp](https://github.com/QuardCRT-platform/plugin-timestamp)

## [[V0.4.7](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.4.7)] - 2024-06-26

- 增加广播会话功能 [#36](https://github.com/QQxiaoming/quardCRT/issues/36)
- 增加标签标记颜色功能
- 增加块选择（Shift+click）和列选择（Alt+Shift+click）功能
- 增加用户自定义光标颜色设置
- 增加设置中可选项的工具提示
- 增加高级选项可以设置默认启动本地终端使用的Shell（Linux/MacOS下默认为$SHELL，Windows下默认为系统内置powershell，Windows下此功能仅用于调整PowerShell版本，而非启动其他Shell，其他Shell请使用本地Shell会话设定特定命令启动）
- 修复修改当前正在运行中的会话配置导致的崩溃问题
- 修复多屏幕的情况下，上下文菜单弹出位置错误问题
- 修改右击非当前标签页时，切换到该标签页
- 修复在windows msvc版本local shell光标对齐错误问题，需要禁用resizeQuirk [#39](https://github.com/QQxiaoming/quardCRT/issues/39)
- 修复多行文本粘贴确认无效问题，并允许用户自行设置启用/禁用
- 修复自动修剪文本粘贴内容中的空行问题，并允许用户自行设置启用/禁用
- 修复不稳定的SSH初始化终端大小问题 [#40](https://github.com/QQxiaoming/quardCRT/issues/40)
- 修复SSH远端主动结束后，概率崩溃问题
- 修复恢复字体设置到内建字体时，字体显示异常
- 修复在Linux上使用多屏幕时，窗口移动/大小调整等操作导致的窗口位置异常问题
- 新增集成预构建插件[TextStatistics](https://github.com/QuardCRT-platform/plugin-TextStatistics)，更新预构建插件[CharacterCode](https://github.com/QuardCRT-platform/plugin-CharacterCode)到V0.0.3版本

## [[V0.4.6](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.4.6)] - 2024-05-26

- 增加设置主界面主题色功能
- 增加状态栏显示会话信息功能
- 在Windows增加启动WSL终端工具栏按钮
- 增加用户自定义插件加载路径设置
- 修复某些shell环境下克隆标签时工作目录未能正确克隆的问题
- 修复键盘绑定设置中取消修改时也会保存的问题
- 修复关闭全部标签页时确认对话框无法选择取消的问题
- 修复会话管理器中修改会话属性后会话管理器内当前选中会话被错误切换问题
- 修复新会话可能创建在被隐藏的标签页组上的问题
- 新增集成预构建插件[CharacterCode](https://github.com/QuardCRT-platform/plugin-CharacterCode)、[ListSerial](https://github.com/QuardCRT-platform/plugin-ListSerial)，更新预构建插件[SearchOnWeb](https://github.com/QuardCRT-platform/plugin-SearchOnWeb)到V0.0.4版本

## [[V0.4.5](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.4.5)] - 2024-04-26

- 修改终端选中后文本强调色透明度50%，而非原本的100%
- 修复渲染符号'×' '÷' '‖'宽度异常问题
- 修复存在一小概率情况下程序崩溃的问题
- 修复光标定位问题 [#I8RB90](https://gitee.com/QQxiaoming/quardCRT/issues/I8RB90)
- 删除对Qt中core5compat的依赖（参考qtermwidget上游pr，但有修改）
- 禁止使用中键滚动查看历史信息（参考qtermwidget上游pr，但有修改）
- 修复渲染某些符号宽度异常问题
- 增加 ANSI OSC52 sequence 支持
- 修复断开会话会直接关闭标签而不是断开会话的问题
- 修复切换语言时快速连接窗口部分UI未能刷新问题
- 改进会话管理器页面宽度可自由调整
- Windows下通过MSVC构建的版本采用ConPty代替WinPty，Mingw构建版本继续使用WinPty
- 改进双击选中CJK字符时的表现
- 改进输入法预编辑区域的显示表现
- 增加终端配色方案调色板设置功能
- 增加切换主题时自动切换终端配色方案功能
- 增加删除会话时的确认对话框
- 修复上下文菜单过长时显示不全难以操作的问题
- 修复windows下的一些主题切换引起的显示异常问题
- 更新预构建插件[onestep](https://github.com/QuardCRT-platform/plugin-onestep)到V0.0.3版本

## [[V0.4.4](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.4.4)] - 2024-03-26

- 增加ascii发送/接收、Kermit发送/接收、xyzmodem发送/接收功能
- 修复启动tftp菜单项指示的状态可能出现错误问题
- 修复终端显示超过第一平面的Unicode字符时程序崩溃的问题
- 修复linux上拖拽窗口到屏幕边缘触发窗口大小调整后终端界面渲染不刷新的问题

## [[V0.4.3](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.4.3)] - 2024-02-26

- 终端链接增加tooltip，以及按下ctrl后鼠标形状修改对应形状
- 修改macos上默认LC_CTYPE配置为UTF-8，其他平台不做默认配置，可通过setting文件修改是否做配置
- 修复macos上预编译的版本遗漏打包部份翻译文件问题
- 修复linux上最大化窗口终端界面渲染未及时刷新问题
- 插件系统完成多语言支持
- 部分UI细节美化
- 新增一个新的帮助文档界面
- 增加德语/葡萄牙语(巴西)/捷克语/阿拉伯语支持

## [[V0.4.2](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.4.2)] - 2024-01-28

- 全屏模式下增加ESC退出全屏功能
- 插件平台支持动态启用/禁用插件功能
- 优化解决软件启动后固定占用CPU负载问题
- 优化windows下本地终端上下搜索历史命令时光标位置错误问题
- 修复tftpsever可能的错误ack处理问题
- 修复macos下全屏导致程序崩溃问题
- 修复macos native UI模式下标题按钮没有切换为macos风格问题
- 修复macos通过native UI样式标题按钮全屏后，无法显示界面上上下文菜单中退出全屏选项问题
- 预构建版本增加对于[插件生态平台](https://github.com/QuardCRT-platform)的预构建插件的打包，首次包含插件[SearchOnWeb](https://github.com/QuardCRT-platform/plugin-SearchOnWeb)、[onestep](https://github.com/QuardCRT-platform/plugin-onestep)、[quickcomplete](https://github.com/QuardCRT-platform/plugin-quickcomplete)

## [[V0.4.1](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.4.1)] - 2024-01-13

- 增加会话管理器中在新窗口打开会话功能
- 增加设置标签页加号按钮位模式可选为 新建会话/克隆会话/本地Shell会话 三种方式
- 增加会话管理器中过滤功能
- 修复在拖拽标签时预览窗口存在导致的窗口闪烁问题

## [[V0.4.0](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.4.0)] - 2023-12-20

- 主UI全面更新，整体风格更现代化，配套亮色/暗色主题更加美观
- 增加设置选项里打开当前设置文件功能
- 右上角增加实验室功能，SSH扫描迁移至实验室，开放插件接口以增加更多特定功能到实验室，访问[插件平台](https://github.com/QuardCRT-platform)
- SFTP窗口增加书签功能，改进SFTP操作逻辑。
- 改进优化HexView窗口
- 改进会话克隆功能，可克隆的会话类型（SSH、Telent等）直接克隆，不可克隆的会话类型（串口等）会弹出会话设置窗口
- 改进在拖拽标签时样式，现在鼠标能正确显示为抓握手势
- 修复打开会话属性存在历史页面未刷新
- 修复会话内line字符渲染错误
- 修复打开SSH会话后未变化过窗口大小的情况下，默认的终端大小不正确
- 修复切换主题时Tab Add New按钮样式未更新
- 修复终端配色方案修改后无法持久保存 [#I8PLTP](https://gitee.com/QQxiaoming/quardCRT/issues/I8PLTP)

## [[V0.3.1](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.3.1)] - 2023-12-05

- 增加密码输入框支持显示/隐藏功能
- 增加常用波特率提示
- 增加右键菜单请求翻译功能
- 增加实用工具，扫描本地网络SSH服务
- SFTP文件传输窗口增加传输进度显示
- 增加vnc协议支持
- 修复二次编辑存储串口会话port信息后无法正确连接问题
- 修复钥匙串授权失败使用错误信息的问题
- 修复端口号输入框最大值错误导致的无法正确保存会话信息问题

## [[V0.3.0](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.3.0)] - 2023-11-28

- 增加SSH2协议支持（目前仅支持密码认证，用户密码存储在本地系统密钥链中，不存储在本软件配置文件中）
- 增加SSH2会话打开SFTP文件传输窗口功能
- 增加自定义设置单词字符（Word Characters）功能，可以设置哪些字符为视为单词字符，方便快速选中单词
- 增加双击会话管理器内会话进行连接功能
- 增加会话管理器关闭按钮
- 修复修改会话属性后会话管理器内会话排序重新排列问题
- 修复串口连接正常但弹出错误提示“No Error”问题
- 修复连接失败的会话无法关闭问题

## [[V0.2.6](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.2.6)] - 2023-11-15

- 增加标签卡悬浮预览功能
- windows本地终端增强，现在可以像linux一样使用Tab键选择补全命令
- 增加会话状态查询，通过会话设置/属性-状态查看会话状态，目前仅支持本地Shell会话查询进程信息
- 终端内容匹配支持路径匹配，可以右键快速打开文件/目录
- 增加高亮显示匹配内容功能
- 修复中文全角引号渲染位置错误问题
- 修复macOS错误绑定了复制粘贴快捷键占用导致无法kill终端内进程问题
- 增加更多语言(西班牙语/法语/韩语/俄语/繁体中文)支持（由GitHub Copilot提供）

## [[V0.2.5](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.2.5)] - 2023-11-09

- 增加浮动窗口模式，且支持移回主窗口
- 增加标签页自由拖拽（拖拽成浮动窗口或拖拽至分屏）
- 修复移动标签后可能导致的严重崩溃问题/标签标题显示错误问题
- 增加高级设置选择UI样式为原生风格（单平台用户可能希望使用原生风格，多平台用户可能希望使用统一风格）
- 增加设置中一键清理选择的背景图片功能
- 优化退出应用/关闭会话时的二次确认功能，现在本地Shell会话根据是否有子进程决定是否需要二次确认，其他会话类型不变
- 增加设置标签标题模式，可以选择以简要/完整/滚动，三种方式显示会话标题

## [[V0.2.4](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.2.4)] - 2023-11-03

- 增加windows上NamedPipe协议支持（linux/macos上对应unix domain socket）
- 修复windows上无法启动打印机服务问题
- 修复关闭标签页部份内存未释放问题
- 增加退出应用/关闭会话时需要二次确认功能
- 增加会话链接状态显示功能（标签页以图标形式显示）
- 增加设置终端字体功能
- 增加设置终端滚动行数设置
- 增加设置光标形状和闪烁功能
- 终端背景支持Gif动画格式文件（需要在高级设置中启用动画支持）
- 终端背景支持mp4/avi/mkv/mov视频格式文件（需要在高级设置中启用动画支持）
- 更新全局设置界面，分类显示设置项
- 增加会话设置界面，现在可以修改编辑会话属性
- 增加分离启动新窗口功能
- 增加软件自身调试信息日志系统，用户默认上不打开的，必须手写config文件才会启动

## [[V0.2.3](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.2.3)] - 2023-10-26

- 修复错误ci环境，与V0.2.2无实质改动

## [[V0.2.2](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.2.2)] - 2023-10-26

- 修复会话信息保存错误导致右侧会话管理器内无法正确连接会话问题 [#I8AJN1](https://gitee.com/QQxiaoming/quardCRT/issues/I8AJN1)
- 快速连接支持选择仅打开会话和仅保存会话
- 改进书签管理功能
- 实现保存设置和实时保存设置按钮功能
- 增加ALT+'-'和ALT+'='全局快捷键切换当前标签
- 增加ALT+'{num}'全局快捷键切换到指定标签
- 增加ALT+LEFT、ALT+RIGHT全局快捷键映射到home和end按键（考虑macbook没有home和end按键）
- 增加高清截图当前终端功能
- 增加导出当前终端会话内容（pdf/txt）功能
- 增加打印机打印当前终端会话功能
- 增加锁定会话功能
- 增加配置启动新的本地终端默认的工作路径
- 终端背景图片支持平铺模式
- 持久化存储主界面布局信息
- 优化界面上下文菜单
- 优化打开文件对话框UI
- 修改windows上渲染粗体字体导致光标异常，暂时不支持粗体渲染保证光标位置正确
- 修复windows上执行命令后设置的工作路径不正确问题
- 增加macos上cmd+delete为delete按键功能（因为通常macos上delete按键为backspace）

## [[V0.2.1](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.2.1)] - 2023-10-19

- linux打包fcit插件以支持更多中文输入法
- linux修复中文字符渲染光标错误
- 修复HEX视图格式渲染错误和数据获取失败问题
- 持久化存储会话信息

## [[V0.2.0](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.2.0)] - 2023-10-18

- 增加使用alt+n/alt+J切换简约/标准UI
- 增加启动tftp服务器实用功能
- 优化hex view显示界面
- window安装程序增加使用quardCRT打开的系统集成的右键菜单
- 标签栏右键菜单增加个多个实用功能
- 修复window上中文等其他宽字符光标位置错误
- 增加配置终端背景图片功能
- 增加目录书签功能
- 增加持久存储用户设置功能
- 修复了一些UI细节错误
- 修复了一些小概率的可能崩溃问题

## [[V0.1.5](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.1.5)] - 2023-10-09

- 增加终端右侧滚动条
- 修复window/mac上鼠标中键不能执行复制并粘贴
- 增加双终端会话分屏显示
- 增加简约UI界面选项

## [[V0.1.4](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.1.4)] - 2023-10-08

- 增加侧边栏会话管理器
- 增加状态栏提示信息
- 增加命令输入栏
- 完善快捷键功能
- 修复会话克隆存在工作路径不一致问题
- 增加终端URL内容动态解析
- 修复可能的崩溃问题

## [[V0.1.3](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.1.3)] - 2023-09-29

- 再修复windows存在无法启动问题（V0.1.0引入）（这个版本彻底修复了V0.1.0问题）

## [[V0.1.2](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.1.2)] - 2023-09-29

- 再修复windows存在无法启动问题（V0.1.0引入）

## [[V0.1.1](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.1.1)] - 2023-09-29

- 修复windows存在无法启动问题（V0.1.0引入）

## [[V0.1.0](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.1.0)] - 2023-09-29

- 标签卡名称可双击切换长/短名称
- 增加存储log功能
- 增加快速打开本地Shell快捷键和克隆会话快捷键
- 增加windows下感知当前实时工作路径（像linux和mac一样的体验）
- 增加HEX查看器

## [[V0.0.2](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.0.2)] - 2023-09-27

- 主界面增加菜单栏、工具栏，完善更多右键菜单
- 增加更多终端界面配色风格
- 增加动态切换语言功能
- 增加动态切换主题功能

## [[V0.0.1](https://github.com/QQxiaoming/quardCRT/releases/tag/V0.0.1)] - 2023-09-26

- 实现主界面终端功能
- 增加标签卡分页管理
- 支持telnet协议
- 支持串口协议
- 支持RAW协议
- 支持本地Shell
- 界面支持简体中文/英文/日文
