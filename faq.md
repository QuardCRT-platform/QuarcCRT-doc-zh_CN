<div style="text-align: right"><a href="../../en/latest/faq.html">🇺🇸 English</a> | <a href="../../zh-cn/latest/faq.html">🇨🇳 简体中文</a> | <a href="../../zh-tw/latest/faq.html">🇭🇰 繁體中文</a> | <a href="../../ja/latest/faq.html">🇯🇵 日本語</a></div>

# 常见问题

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
