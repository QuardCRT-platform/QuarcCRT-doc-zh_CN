<div style="text-align: right"><a href="../../en/latest/scripts.html">🇺🇸 English</a> | <a href="../../zh-cn/latest/scripts.html">🇨🇳 简体中文</a> | <a href="../../zh-tw/latest/scripts.html">🇭🇰 繁體中文</a> | <a href="../../ja/latest/scripts.html">🇯🇵 日本語</a></div>

# 脚本

quardCRT从V0.5.0版本开始支持脚本功能。脚本以Python语言的形式加载，可以在脚本中调用quardCRT的API，以实现自动化操作。

## 加载脚本

打开主界面，点击菜单栏的`脚本`，选择`运行...`，选择脚本文件，点击`打开`即可加载脚本。

## 示例

以下是一个简单的脚本示例，用于显示quardCRT的版本信息。

```python
import sys
from quardCRT import crt

def main():
    # Display quardCRT's version
    crt.Dialog.MessageBox("quardCRT version is: " + crt.Version)

if __name__ == '__main__':
    main()
```

quardCRT加载的脚本与通常的Python脚本并无区别，现在我们逐行解释这个脚本。

- `import sys`：导入`sys`模块，用于获取命令行参数。
- `from quardCRT import crt`：导入quardCRT的API。
- `def main():`：定义一个`main`函数，用于执行脚本的主要逻辑。
- `# Display quardCRT's version`：注释，用于解释下一行代码的作用。
- `crt.Dialog.MessageBox("quardCRT version is: " + crt.Version)`：调用quardCRT的API，显示一个消息框，显示quardCRT的版本信息。
- `if __name__ == '__main__':`：判断脚本是否作为主程序运行。
- `main()`：调用`main`函数，执行脚本的主要逻辑。

## API

quardCRT的API包括以下几个部分：

- `crt`：quardCRT的主要API。
- `crt.Dialog`：用于显示对话框。
- `crt.Session`：用于管理当前激活的会话。
- `crt.Screen`：用于管理当前激活的屏幕。
- `crt.Window`：用于管理quardCRT的窗口。
- `crt.Arguments`：用于获取命令行参数。
- `crt.Clipboard`：用于操作剪贴板。
- `crt.FileTransfer`：用于操作文件传输。
- `crt.CommandWindow`：用于操作命令窗口。
- `crt.Tab`：用于管理标签页组。

### crt

`crt`是quardCRT的主要API，包括以下几个部分：

#### 方法

- `crt.GetActiveTab() -> object`：获取当前活动的标签页组。
    - 返回值：Tab对象。
    - 示例：

        ```python
        tab = crt.GetActiveTab()
        ```
    - 备注：如果当前没有活动的Tab组，则获取第一个Tab组。

- `crt.GetLastError() -> object`：获取最后一次发生的错误。
    - 返回值：Error对象。
    - 示例：

        ```python
        error = crt.GetLastError()
        ```

- `crt.GetLastErrorMessage() -> str`：获取最后一次发生的错误信息。
    - 返回值：错误信息。
    - 示例：

        ```python
        message = crt.GetLastErrorMessage()
        ```

- `crt.ClearLastError()`：清除最后一次发生的错误。
    - 示例：

        ```python
        crt.ClearLastError()
        ```

- `crt.Sleep(milliseconds: int)`：暂停脚本的执行。
    - 参数：
        - `milliseconds`：暂停的时间，单位为毫秒。
    - 示例：
    
        ```python
        crt.Sleep(1000)
        ```

- `crt.Cmd(cmd: str, [args:list]) -> str`：执行一个quardCRT的特殊命令。
    - 参数：
        - `cmd`：命令名称。
        - `args`：命令参数列表。
    - 返回值：命令执行结果。
    - 备注：命令名称和参数列表请参考quardCRT的命令帮助。
    - 示例：

        ```python
        result = crt.Cmd("show", ["version"])
        ```

- `crt.Quit()`：退出quardCRT。
    - 示例：
    
        ```python
        crt.Quit()
        ```

#### 属性

- `crt.Dialog`：全局对话框对象。
- `crt.Session`：当前会话对象。
- `crt.Screen`：当前屏幕对象。
- `crt.Window`：全局窗口对象。
- `crt.Arguments`：命令行参数对象。
- `crt.Clipboard`：剪贴板对象。
- `crt.FileTransfer`：文件传输对象。
- `crt.ScriptFullName`：当前脚本的完整路径。只读。
- `crt.ActivePrinter`：当前活动的打印机名称。
- `crt.Version`：quardCRT的版本信息。只读。

### Dialog

`Dialog`用于显示对话框，全局单例，通过crt对象调用，例如：

```python
dialog = crt.Dialog
```

包括以下几个部分：

#### 方法

- `Dialog.MessageBox(message: str, [title: str, buttons: int]) -> int`：显示一个消息框。
    - 参数：
        - `message`：消息内容。
        - `title`：消息标题。
        - `buttons`：按钮类型。
    - 返回值：执行结果。0表示正常，其他值表示异常。
    - 备注：按钮类型包括`Dialog.OK`、`Dialog.OK | Dialog.Cancel`、`Dialog.Abort | Dialog.Retry | Dialog.Ignore`、`Dialog.Yes | Dialog.No`等。
    - 示例：

        ```python
        result = crt.Dialog.MessageBox("Hello, quardCRT!", "Message", crt.Dialog.OK)
        ```

- `Dialog.Prompt(prompt: str, name: str, input: str, password: bool) -> str`：显示一个输入框。
    - 参数：
        - `prompt`：提示内容。
        - `name`：输入框名称。
        - `input`：输入框默认值。
        - `password`：是否密码输入。
    - 返回值：输入框的值。如果用户点击取消，则返回空字符串。
    - 示例：

        ```python
        value = crt.Dialog.Prompt("Please input your name:", "Name", "", False)
        password = crt.Dialog.Prompt("Please input your password:", "Password", "", True)
        ```

- `Dialog.FileOpenDialog(title: str, [buttonLabel: str, directory: str, filter: str]) -> str`：显示一个打开文件对话框。
    - 参数：
        - `title`：对话框标题。
        - `buttonLabel`：按钮标签。
        - `directory`：默认目录。
        - `filter`：文件过滤器。
    - 返回值：选择的文件路径。如果用户点击取消，则返回空字符串。
    - 示例：

        ```python
        file = crt.Dialog.FileOpenDialog("Open File", "Open", "", "All Files (*.*)|*.*")
        ```    

- `Dialog.FileSaveDialog(title: str, [buttonLabel: str, directory: str, filter: str]) -> str`：显示一个保存文件对话框。
    - 参数：
        - `title`：对话框标题。
        - `buttonLabel`：按钮标签。
        - `directory`：默认目录。
        - `filter`：文件过滤器。
    - 返回值：选择的文件路径。如果用户点击取消，则返回空字符串。
    - 示例：

        ```python
        file = crt.Dialog.FileSaveDialog("Save File", "Save", "", "All Files (*.*)|*.*")
        ```

#### 属性

- `Dialog.OK`：确定按钮。只读。
- `Dialog.Cancel`：取消按钮。只读。
- `Dialog.Abort`：中止按钮。只读。
- `Dialog.Retry`：重试按钮。只读。
- `Dialog.Ignore`：忽略按钮。只读。
- `Dialog.Yes`：是按钮。只读。
- `Dialog.No`：否按钮。只读。

### Session

`Session`用于管理会话，通过crt对象调用或Tab获取，例如：

```python
session = crt.Session # 获取当前会话
```

```python
tab = crt.GetActiveTab()    # 获取当前活动的标签页组
if tab.Number > 0:
    session = tab.GetSession(0) # 获取标签页组的第一个会话
```

包括以下几个部分：

#### 方法

- `Session.Connect(cmd: str) -> int`：连接到一个主机。
    - 参数：
        - `cmd`：命令。
    - 返回值：连接结果。
    - 备注：命令格式为 `-<type> <arg>`，例如：
        - `-telnet <hostname> <port>`
        - `-serial <baudRate> <dataBits> <parity> <stopBits> <flowControl> <xEnable>`
        - `-localshell <path>`
        - `-raw <hostname> <port>`
        - `-namepipe <pipeName>`
        - `-ssh2 <hostname> <port> <username> <password>`
        - `-vnc <hostname> <port> <password>`
        - `-s <sessionName>`
        - `-clone`
    - 示例：

        ```python
        result = session.Connect("-ssh2 example.com 22 root 123456")
        ```

- `Session.Disconnect()`：断开当前会话。
    - 示例：

        ```python
        session.Disconnect()
        ```

- `Session.Log(enable: bool)`：启用或禁用日志记录。
    - 参数：
        - `enable`：是否启用日志记录。
    - 示例：

        ```python
        session.Log(True)
        ```

- `Session.Lock(prompt: str, password: str, lockallsessions: int) -> int`：锁定会话。
    - 参数：
        - `prompt`：提示内容。
        - `password`：密码。
        - `lockallsessions`：是否锁定所有会话。
    - 返回值：执行结果。
    - 示例：

        ```python
        result = session.Lock("Please input your password:", "password", 0)
        ```

- `Session.Unlock(prompt: str, password: str, lockallsessions: int) -> int`：解锁会话。
    - 参数：
        - `prompt`：提示内容。
        - `password`：密码。
        - `lockallsessions`：是否解锁所有会话。
    - 返回值：执行结果。
    - 示例：

        ```python
        result = session.Unlock("Please input your password:", "password", 0)
        ```

#### 属性

- `Session.Connected`：会话是否连接。只读。
- `Session.Locked`：会话是否锁定。只读。
- `Session.Logging`：会话是否启用日志记录。只读。
- `Session.Id`：会话的全局ID。只读。

### Screen

`Screen`用于管理屏幕，通过crt对象调用或Tab获取，例如：

```python
screen = crt.Screen # 获取当前屏幕
```

```python
tab = crt.GetActiveTab()    # 获取当前活动的标签页组
if tab.Number > 0:
    screen = tab.GetScreen(0) # 获取标签页组的第一个屏幕
```

包括以下几个部分：

- `Screen.WaitForString(str: str, timeout: int, bcaseInsensitive: bool) -> str`：等待屏幕出现指定的文本。
    - 参数：
        - `str`：指定的文本。
        - `timeout`：超时时间。
        - `bcaseInsensitive`：是否忽略大小写。
    - 返回值：匹配的文本。
    - 示例：

        ```python
        text = screen.WaitForString("Hello, quardCRT!", 1000, False)
        ```

- `Screen.WaitForStrings(strlist: list[str], timeout: int, bcaseInsensitive: bool) -> str`：等待屏幕出现指定的文本列表。
    - 参数：
        - `strlist`：指定的文本列表。
        - `timeout`：超时时间。
        - `bcaseInsensitive`：是否忽略大小写。
    - 返回值：匹配的文本。
    - 示例：

        ```python
        text = screen.WaitForStrings(["Hello", "quardCRT"], 1000, False)
        ```

- `Screen.Send(str: str) -> int`：发送文本到屏幕。
    - 参数：
        - `str`：发送的文本。
    - 返回值：发送的字符数。
    - 示例：

        ```python
        count = screen.Send("Hello, quardCRT!")
        ```

- `Screen.Clear()`：清空屏幕。
    - 示例：

        ```python
        screen.Clear()
        ```

- `Screen.Get(row1: int, col1: int, row2: int, col2: int) -> str`：获取屏幕指定区域的文本。
    - 参数：
        - `row1`：起始行。
        - `col1`：起始列。
        - `row2`：结束行。
        - `col2`：结束列。
    - 返回值：指定区域的文本。
    - 示例：

        ```python
        text = screen.Get(1, 1, 10, 80)
        ```

- `Screen.Get2(row1: int, col1: int, row2: int, col2: int) -> str`：获取屏幕指定区域的文本，插入换行符号。
    - 参数：
        - `row1`：起始行。
        - `col1`：起始列。
        - `row2`：结束行。
        - `col2`：结束列。
    - 返回值：指定区域的文本。
    - 示例：

        ```python
        text = screen.Get2(1, 1, 10, 80)
        ```

- `Screen.IgnoreCase(enable: bool)`：启用或禁用忽略大小写。
    - 参数：
        - `enable`：是否启用忽略大小写。
    - 示例：

        ```python
        screen.IgnoreCase(True)
        ```

- `Screen.Print()`：打印屏幕内容。
    - 示例：

        ```python
        screen.Print()
        ```

- `Screen.Shortcut(path: str)`：截屏。
    - 参数：
        - `path`：截屏保存的路径。
    - 示例：

        ```python
        screen.Shortcut("C:\\screenshot.png")
        ```

- `Screen.SendKeys(keylist: list[str])`：发送组合按键。
    - 参数：
        - `keylist`：按键列表。
    - 示例：

        ```python
        screen.SendKeys(["Ctrl", "Alt", "Del"])
        ```

- `Screen.Screen_ReadString(strlist: list[str], timeout: int, bcaseInsensitive: bool) -> str`：读取文本数据，直到屏幕出现指定的文本列表。
    - 参数：
        - `strlist`：指定的文本列表。
        - `timeout`：超时时间。
        - `bcaseInsensitive`：是否忽略大小写。
    - 返回值：读取的文本。
    - 示例：

        ```python
        text = screen.Screen_ReadString(["Hello", "quardCRT"], 1000, False)
        ```

- `Screen.WaitForCursor(row: int, col: int, timeout: int) -> bool`：等待光标移动到指定位置。（暂未实现）
    - 参数：
        - `row`：指定行。
        - `col`：指定列。
        - `timeout`：超时时间。
    - 返回值：是否成功。
    - 示例：

        ```python
        result = screen.WaitForCursor(10, 10, 1000)
        ```

- `Screen.WaitForKey(keylist: list[str], timeout: int) -> bool`：等待按键输入。（暂未实现）
    - 参数：
        - `keylist`：按键列表。
        - `timeout`：超时时间。
    - 返回值：是否成功。
    - 示例：

        ```python
        result = screen.WaitForKey(["Enter"], 1000)
        ```

#### 属性

- `Screen.Synchronous`：同步模式。
- `Screen.CurrentColumn`：当前光标列。只读。
- `Screen.CurrentRow`：当前光标行。只读。
- `Screen.Rows`：屏幕行数。只读。
- `Screen.Columns`：屏幕列数。只读。
- `Screen.IgnoreCase`：是否忽略大小写。
- `Screen.MatchIndex`：匹配的索引。只读。
- `Screen.Selection`：选择的文本。只读。
- `Screen.Id`：屏幕的全局ID。只读。

### Window

`Window`用于管理应用窗口，全局单例，通过crt对象调用，例如：

```python
window = crt.Window
```

包括以下几个部分：

#### 方法

- `Window.Activate()`：激活窗口。
    - 示例：

        ```python
        window.Activate()
        ```

- `Window.Show(type: int)`：显示窗口。
    - 参数：
        - `type`：窗口显示类型。
    - 示例：

        ```python
        window.Show(crt.Window.ShowNormal)
        ```

#### 属性

- `Window.State`：当前窗口显示类型。
- `Window.Active`：当前窗口是否激活。
- `Window.Hide`：隐藏窗口。只读。
- `Window.ShowNormal`：正常显示窗口。只读。
- `Window.ShowMinimized`：最小化窗口。只读。
- `Window.ShowMaximized`：最大化窗口。只读。

### Arguments

`Arguments`用于获取命令行参数，全局单例，通过crt对象调用，例如：

```python
arguments = crt.Arguments
```

包括以下几个部分：

#### 方法

- `Arguments.GetArg(index: int) -> str`：获取指定索引的参数。
    - 参数：
        - `index`：参数索引。
    - 返回值：参数值。
    - 示例：

        ```python
        arg = arguments.GetArg(0)
        ```

#### 属性

- `Arguments.Count`：参数数量。只读。

### Clipboard

`Clipboard`用于操作剪贴板，全局单例，通过crt对象调用，例如：

```python
clipboard = crt.Clipboard
```

包括以下几个部分：

#### 属性

- `Clipboard.Text`：剪贴板文本。只读。

### FileTransfer

`FileTransfer`用于操作文件传输，全局单例，通过crt对象调用，例如：

```python
filetransfer = crt.FileTransfer
```

包括以下几个部分：

#### 方法

- `FileTransfer.AddToUploadList(path: str)`：添加文件到zmodem上传列表。
    - 参数：
        - `path`：文件路径。
    - 示例：

        ```python
        filetransfer.AddToUploadList("C:\\example.txt")
        ```

- `FileTransfer.ClearUploadList()`：清空zmodem上传列表。
    - 示例：

        ```python
        filetransfer.ClearUploadList()
        ```

- `FileTransfer.ReceiveKermit() -> int`：接收kermit文件。
    - 返回值：是否成功。
    - 示例：

        ```python
        result = filetransfer.ReceiveKermit()
        ```

- `Filetransfer.SendKermit(path: str) -> int`：发送kermit文件。
    - 参数：
        - `path`：文件路径。
    - 返回值：是否成功。
    - 示例：

        ```python
        result = filetransfer.SendKermit("C:\\example.txt")
        ```

- `FileTransfer.ReceiveXmodem(path: str)`：接收xmodem文件。
    - 参数：
        - `path`：文件路径。
    - 返回值：是否成功。
    - 示例：

        ```python
        result = filetransfer.ReceiveXmodem("C:\\example.txt")
        ```

- `FileTransfer.SendXmodem(path: str) -> int`：发送xmodem文件。
    - 参数：
        - `path`：文件路径。
    - 返回值：是否成功。
    - 示例：

        ```python
        result = filetransfer.SendXmodem("C:\\example.txt")
        ```

- `FileTransfer.ReceiveYmodem() -> int`：接收ymodem文件。
    - 返回值：是否成功。
    - 示例：

        ```python
        result = filetransfer.ReceiveYmodem()
        ```

- `FileTransfer.SendYmodem(path: str) -> int`：发送ymodem文件。
    - 参数：
        - `path`：文件路径。
    - 返回值：是否成功。
    - 示例：

        ```python
        result = filetransfer.SendYmodem("C:\\example.txt")
        ```

- `FileTransfer.SendZmodem() -> int`：发送zmodem文件。
    - 返回值：是否成功。
    - 示例：

        ```python
        result = filetransfer.SendZmodem()
        ```

#### 属性

- `FileTransfer.DownloadFolder`：下载文件夹。

### CommandWindow

`CommandWindow`用于操作命令窗口，全局单例，通过crt对象调用，例如：

```python
commandwindow = crt.CommandWindow
```

包括以下几个部分：

#### 方法

- `CommandWindow.Send(str: str)`：发送文本到命令窗口。
    - 参数：
        - `str`：发送的文本。
    - 示例：

        ```python
        commandwindow.Send("Hello, quardCRT!")
        ```

#### 属性

- `CommandWindow.SendCharactersImmediately`：是否立即发送字符。
- `CommandWindow.SendToAllSessions`：是否发送到所有会话。
- `CommandWindow.Visible`：命令窗口是否可见。
- `CommandWindow.Text`：命令窗口文本。

### Tab

`Tab`用于管理标签页组，通过crt对象调用，例如：

```python
tab = crt.GetActiveTab()    # 获取当前活动的标签页组
```

包括以下几个部分：

#### 方法

- `Tab.GetScreen(index: int) -> object`：获取标签页组的屏幕。
    - 参数：
        - `index`：屏幕索引。
    - 返回值：Screen对象。
    - 示例：

        ```python
        screen = tab.GetScreen(0)
        ```

- `Tab.GetSession(index: int) -> object`：获取标签页组的会话。
    - 参数：
        - `index`：会话索引。
    - 返回值：Session对象。
    - 示例：

        ```python
        session = tab.GetSession(0)
        ```

- `Tab.Activate(index: int)`：激活标签页组的指定会话。
    - 参数：
        - `index`：会话索引。
    - 示例：

        ```python
        tab.Activate(0)
        ```

#### 属性

- `Tab.Number`：标签页组内会话数量。只读。
