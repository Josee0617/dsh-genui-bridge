# GenUI Bridge

适配 **DeepSeek Harness Desktop 0.2.0-rc.2** 的 GenUI 分支，保留上游 0.11.4 的交互图表、表单、测验、面板、导出和模型动作。

由 Josee0617 维护，源自 [omdsh-dev/dsh-genui](https://github.com/omdsh-dev/dsh-genui)。保留上游 MIT 许可证和署名。[English](README.md)

## 桌面安装

打开 **插件 → 添加插件**，粘贴：

```text
https://github.com/Josee0617/dsh-genui-bridge/releases/download/v0.1.0/josee0617-dsh-genui-bridge-0.1.0.tgz
```

安装并启用后，完全退出并重新打开 Harness（macOS：⌘Q）。无需提前下载压缩包；此分支通过 GitHub Releases 分发，尚未发布至 npm。如果已安装上游 GenUI，请先禁用上游版本，避免重复注册。

新建会话并提问：

> 用 dsh-ui 制作一个使用虚构数据的销售看板，包括三个指标卡片、可排序表格和柱状图。

回复应显示交互界面。`/panel` 打开会话面板，`/panel <指令>` 定制面板，`/panel clear` 清空面板。完成的界面可通过 Export 导出 HTML 或 GenUI JSON；导出 HTML 保留本地交互，模型动作不在 Harness 外执行。

本地操作即时更新，需要模型处理的动作会发送至会话并可能产生模型费用。不要在生成的表单中输入密码或 API 密钥。

组件协议、渲染、交互和模型指令保持上游行为；仅调整包名及对应客户端标识、资源地址、反馈标识、安装测试和桌面文档。[组件参考](SKILL.md) · [上游完整文档](docs/upstream-README.zh-CN.md) · [验证说明](README.md#development-and-verification)
