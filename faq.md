<div style="text-align: right"><a href="../../en/latest/faq.html">🇺🇸 English</a> | <a href="../../zh-cn/latest/faq.html">🇨🇳 简体中文</a> | <a href="../../zh-tw/latest/faq.html">🇭🇰 繁體中文</a> | <a href="../../ja/latest/faq.html">🇯🇵 日本語</a></div>

# 常见问题

## 通用

- quardCRT是免费软件吗？
    - 是的，quardCRT是开源软件，遵循GPLv3协议。您可以在[GitHub](https://github.com/QQxiaoming/quardCRT)/[Gitee](https://gitee.com/QQxiaoming/quardCRT)获取完整可编译的源代码。

- quardCRT软件可以商用吗？
    - quardCRT遵循GPLv3开源协议，您可以在遵循GPLv3协议的前提下自由使用quardCRT软件，包括商业用途（但请仔细阅读相关条款）。您可以在[此处](./license.md)阅读许可协议。

- quardCRT软件为什么选择GPLv3协议，而不是其他开源协议？
    - quardCRT软件本身依赖众多其他开源软件，为了尊重其他开源软件的许可协议，符合协议条款，因此quardCRT选择了GPLv3协议。

- quardCRT软件是否安全？涉及密码等隐私信息是如何存储的？
    - quardCRT软件是开源软件，您可以查看源代码，了解软件的运行机制。quardCRT软件不会存储密码等关键隐私信息到磁盘。
    - quardCRT软件保存您的会话信息的原理是：将非密码信息（如主机名、端口号、用户名等）存储在配置文件中，配置文件路径可以阅读[配置](./configuration.md)页面了解。而密码信息是依赖开源软件[QtKeychain](https://github.com/frankosterfeld/qtkeychain)提供的系统密钥链服务，将密码信息提交给系统密钥链服务，由系统密钥链服务统一保存密码信息。密码的安全性取决于系统密钥链服务的安全性。通常情况下，受官方支持的Windows、macOS、Linux系统都提供了安全的密钥链服务，系统密钥链服务通常需要您登录系统时输入密码解锁（Windows）或者每次访问时验证登录密码或指纹（macOS）。但请注意，密码的安全性取决于系统密钥链服务，quardCRT软件本身不对密码安全性负责。
    - 如果您仍然对密码安全性有疑虑，可以选择不保存密码，每次连接时输入密码。

## 特定平台

### Windows

- quardCRT软件支持Windows 7/Windows XP吗？
    - 不支持。quardCRT软件支持Windows 10及更高版本。这是因为quardCRT依赖Qt版本至少为6.2，Qt6.2不支持Windows 7/Windows XP。

- windows本地终端如何指定最新版本的PowerShell？
    - quardCRT软件默认使用系统默认的PowerShell程序，如果您想使用最新版本的PowerShell，可以在[配置](./configuration.md)页面中，高级选项中，将“默认本地终端程序”设置为您的最新版本的PowerShell程序路径，这样您将使用指定的PowerShell程序并加载quardCRT自带的profile获得更好的体验。

- windows本地终端如何指定cmd程序？
    - quardCRT软件使用PowerShell作为默认的本地终端程序，不支持传统的cmd。

### macOS

- quardCRT软件支持macOS最低版本是多少？
    - quardCRT软件依赖Qt版本至少为6.2，Qt6.2支持macOS 10.14及更高版本。如果您通过源码编译quardCRT软件，理论上可以获得相同的支持。但目前发布的预编译版本分别在macOS 12构建Intel版本和在macOS 14构建Apple Silicon版本，因此我们建议您使用macOS 14及更高版本。

- 在macos上安装弹出“无法验证开发者”的提示，或安装包损坏，无法安装如何解决？
    - 这是macOS的安全机制导致的。因为我们目前发布的预构建二进制包没有经过 Apple 官方签名，如果你信任我们的程序，你可能需要打开终端并运行 `xattr -cr /Applications/quardCRT.app` 来移除隔离属性。但如果你不信任我们的程序，你不应该运行它。你可以选择自己从源代码编译quardCRT软件，这样可以避免这个问题。

### Linux

- quardCRT软件支持哪些Linux发行版？
    - 如果从源码编译，理论上支持所有支持Qt6.2的Linux发行版。但目前发布的预编译版本是通过在Ubuntu 20.04 LTS上构建的，我们已经尽可能地打包了所有依赖项，但由于测试覆盖有限，我们无法保证在所有Linux发行版上都能正常运行。
