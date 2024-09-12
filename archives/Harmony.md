- [HarmonyOS](#harmonyos)
  - [ArkUI](#arkui)
- [.gitignore](#gitignore)
- [鸿蒙 Sharing](#鸿蒙-sharing)
  - [关于 HarmonyOS Next](#关于-harmonyos-next)
  - [公司现有的 APP 现状（以 HACN 和 DaaSC 为例）](#公司现有的-app-现状以-hacn-和-daasc-为例)
  - [移植重点和难点](#移植重点和难点)

---

## HarmonyOS

- [开发者官网](https://developer.huawei.com/consumer/cn/)
  - [版本概览](https://developer.huawei.com/consumer/cn/doc/harmonyos-releases/releasenotes-overview-0000001602419138)
  - [设计理念](https://developer.huawei.com/consumer/cn/doc/design-guides/design-concepts-0000001795698445)
  - [指南](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/application-dev-guide-0000001630265101)
    - [HTTP 数据请求](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/http-request-0000001821000269)
  - [API 参考](https://developer.huawei.com/consumer/cn/doc/harmonyos-references/development-intro-0000001580026066)
  - [示例代码](https://developer.huawei.com/consumer/cn/doc/harmonyos-samples/samples-0000001162414961)
  - [FAQ](https://developer.huawei.com/consumer/cn/doc/harmonyos-faqs/faqs-development-0000001753952202)
  - [视频课程](https://developer.huawei.com/consumer/cn/doc/harmonyos-video-courses/video-tutorials-0000001443535745)
  - [Codelabs](https://developer.huawei.com/consumer/cn/doc/harmonyos-codelabs/codelabs-0000001443855957)
  - [工具下载](https://developer.huawei.com/consumer/cn/doc/harmonyos-tools/download-0000001822993593)
- [鸿蒙生态学堂 · 创新实训营](https://developer.huawei.com/consumer/cn/training/course/slightMooc/C101707204336594143)

### ArkUI

- [布局子元素在主轴上的排列方式](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides-V2/arkts-layout-development-linear-0000001504125349-V2#section18931145115433)

## .gitignore

```
.clang-format
.hvigor
.idea
entry/build
oh_modules 
local.properties
oh-package-lock.json5
```

## 鸿蒙 Sharing

进行了为期 3 天的培训，内容涉及很广，只会分享公司相关的部分

### 关于 HarmonyOS Next

- 预计 2024 年年底推向市场
- 在今年 1 月的时候，已经有 200+ 的应用会为该系统开发原生应用；到了 4 月份，该数量上升到 4000+
- 该系统的旧版本 HarmonyOS 兼容 Android 的 APK，不过年底推出的 HarmonyOS Next 将剥除对 Android APK 的支持
- 开发工具是 DevEco Studio，跟 Android Studio 相似，容易上手
- 开发文档比较齐全，但是更新不及时
- 该系统使用 ArkTS 作为开发语言，ArkUI 作为开发框架
  - ArkTS 基于 TypeScript，这是一种带类型的 JavaScript
  - ArkUI 是一种声明式 UI 框架，跟 Android 的 Compose 和 iOS 的 Swift UI 类似
  - 如果一名专业的 Android 或者 iOS 开发者，至少要花一周时间熟悉 ArkTS，花一周时间熟悉 ArkUI 的开发框架
- 公司现有的应用，在国内市场，有很大部分用户是该系统用户

### 公司现有的 APP 现状（以 HACN 和 DaaSC 为例）

- 使用 Kotlin 和 Swift 编写业务代码。
- 部分业务使用 Web 组件 Client Pack
- 使用内部工具 Copy Kitten 管理多语言文本
- 公司使用了大量的第三方 SDK，其中很多 SDK 是闭源的，开源的 SDK 也是平台深度绑定的
- 最近推出 platform hub，使用 Android Compose 和 iOS SwiftUI 作为声明式 UI 框架
- HACN 有大量的华为用户，DaaSC 也有不少

### 移植重点和难点

相对容易的部分：

- 该系统本身就提供 native 和 web 之间的交互，Client Pack 的部分相对容易迁移
- Copy Kitten 可以很容易支持该系统的多语言配置
- Platform Hub 开发的组件相对容易迁移，因为使用了 Android 的 Compose 和 iOS 的 SwiftUI，该框架和 ArkUI 一样是声明式框架

重点和难点：
- 使用 Kotlin 和 Swift 编写的业务代码，现阶段并没有任何工具可以无缝迁移，也没有兼容层可以直接运行已有代码，只能使用 ArkTS 重写。
   - 但是重写的地方，界面的部分使用的 ArkUI 跟公司现阶段使用的新框架 platform hub 是类似的，都是使用声明式 UI 编写界面
- 缺乏测试设备
