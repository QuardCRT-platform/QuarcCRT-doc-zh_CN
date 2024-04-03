<div style="text-align: right"><a href="../../en/latest/plugins.html">🇺🇸 English</a> | <a href="../../zh-cn/latest/plugins.html">🇨🇳 简体中文</a> | <a href="../../zh-tw/latest/plugins.html">🇭🇰 繁體中文</a> | <a href="../../ja/latest/plugins.html">🇯🇵 日本語</a></div>

# 插件

quardCRT从V0.4.0版本开始支持插件，插件将以Qt Plug-in插件的形式提供，以动态库的形式加载。

## 插件开发

### API

quardCRT的插件标准API规范位于[plugininterface](https://github.com/QuardCRT-platform/plugininterface)，如果要开发您的自定义插件步骤如下：

- 包含plugininterface.h头文件
- 定义您的插件类，并继承PluginInterface纯虚类
- 实现PluginInterface所需的相关方法
- 根据您的本机平台构建DLL/so/dylib并使用quardCRT主程序加载

以下是一个最简单的示例：

```c++
#include "plugininterface.h"

#include <QMap>
#include <QMessageBox>
#include <QDebug>

#define PLUGIN_NAME    "Hello World"
#define PLUGIN_VERSION "0.0.1"

class HelloWorld : public PluginInterface
{
    Q_OBJECT
    Q_PLUGIN_METADATA(IID "org.quardCRT.PluginInterface" FILE "../plugininterface.json")
    Q_INTERFACES(PluginInterface)

public:
    HelloWorld() : m_action(nullptr) {}
    virtual ~HelloWorld() {}

    int init(QMap<QString, QString> params, QWidget *parent) {
        foreach (QString key, params.keys()) {
            qDebug() << key << " : " << params[key];
        }
        qDebug() << "Hello World init";
        m_action = new QAction("Hello World", parent);
        connect(m_action, &QAction::triggered, [parent](){
            QMessageBox::information(parent, "Hello World", "Hello World");
        });

        return 0;
    }

    void setLanguage(const QLocale &language,QApplication *app) {Q_UNUSED(language);Q_UNUSED(app);}
    void retranslateUi() {}
    QString name() { return PLUGIN_NAME; }
    QString version() { return PLUGIN_VERSION; }

    QMap<QString,void *> metaObject() {
        QMap<QString,void *> ret;
        ret.insert("QAction", (void *)m_action);
        return ret;
    }

    QMenu *terminalContextMenu(QString selectedText, QString workingDirectory, QMenu *parentMenu) {Q_UNUSED(selectedText);Q_UNUSED(workingDirectory);Q_UNUSED(parentMenu); return nullptr;}
    QList<QAction *> terminalContextAction(QString selectedText, QString workingDirectory, QMenu *parentMenu) {Q_UNUSED(selectedText);Q_UNUSED(workingDirectory);Q_UNUSED(parentMenu); return QList<QAction *>();}
    
private:
    QAction *m_action;
};
```

### 模板工程

对于开发插件我们推荐使用我们提供的Github模板工程[plugin-template](https://github.com/QuardCRT-platform/plugin-template)，进入该git仓库，点击右上角的 use this template，您即可立即创建您的新的插件仓库，该模板仓库我们已经配置好了构建脚本，工程(pro)文件，并启用了github action作为CI/CD，您只需要专注您的C++代码开发并提交，就可以通过github action立即取得您的插件构建。

## 实例

目前quardCRT已经有一些插件并在发布二进制安装程序中打包，这些插件仍然是开源的，并且作为插件实例提供在此以供参考：

- [plugin-SearchOnWeb](https://github.com/QuardCRT-platform/plugin-SearchOnWeb)

增加右键上下文菜单，用于快速将选中的终端内容跳转到搜索引擎上，支持谷歌、必应、百度、Github、Stack Overflower。

- [plugin-quickcomplete](https://github.com/QuardCRT-platform/plugin-quickcomplete)

提供用户自定义命令，用于快速发送到会话。

- [plugin-onestep](https://github.com/QuardCRT-platform/plugin-onestep)

提供自定义的预填写ssh信息，在上下文中快速选择主机地址快速连接。（嵌入式开发常用操作初始化生产的设备）。

## 更多

想了解更多插件开发信息请参考插件开放平台[https://github.com/QuardCRT-platform](https://github.com/QuardCRT-platform)，目前插件功能仍处于早期开发阶段，如果您有好的想法或建议，欢迎在GitHub或Gitee上提交issue或discussion。
