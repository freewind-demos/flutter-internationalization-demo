# Flutter 国际化（Material 本地化委托）

## 简介

为 `MaterialApp` 配置 `localizationsDelegates` 与 `supportedLocales`，注册 Material、Widgets、Cupertino 的全局本地化委托。页面中央一句文案表示「委托已挂上」；未包含 ARB 代码生成，专注最小可用配置。

## 快速开始

### 环境要求

Flutter SDK。依赖里包含 `flutter_localizations`（SDK）与 `intl`。

### 运行

```bash
flutter pub get
flutter run
```

## 概念讲解

### 第一部分：`GlobalMaterialLocalizations` 等在干什么

它们把按钮语义、日期格式等与语言环境绑在一起。不接委托时，部分 Widget 在对应 locale 下行为不完整。

### 第二部分：与 `gen-l10n` 的关系

业务文案翻译通常再用 `flutter gen-l10n` 或手写 `ARB`。本 Demo 只铺基础设施，避免把代码生成目录摊进最小示例。

## 完整示例

见 `lib/main.dart`：`localizationsDelegates` 三件套与 `Locale('en')`、`Locale('zh')`。

## 注意事项

- 切换语言需配合 `locale` 状态管理或 `MaterialApp.localeListResolutionCallback` 等策略。
- 仅设 locale 不提供对应 ARB，文案不会自动变中文，需要你们后续补翻译资源。

## 完整讲解（中文）

国际化分两层：**系统层委托**（日期、Material 自带字符串）和 **你们业务文案**。很多人一上来就生成 ARB，却忘了 MaterialApp 的 delegates，结果日期格式仍不对。这个 Demo 先把底层委托摆对，你再在第二层填 `AppLocalizations`，心智负担会小很多。
