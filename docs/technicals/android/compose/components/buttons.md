---
title: Buttons
tags:
  - Button
  - Floating action button
---

## Common Button

`Button` 允许用户触发特定的动作。通用的 `Button` 有 5 种：

| 类型       | 外观                     | 用途                                                                                                 |
| :--------- | :----------------------- | :--------------------------------------------------------------------------------------------------- |
| `Filled`   | 纯色背景与对比鲜明的文字 | 对于主要操作，例如“提交”和“保存”。阴影效果强调了按钮的重要性。                                       |
| `Tonal`    | 背景颜色随表面变化而变化 | 对于主要或重要操作。填充按钮提供视觉重量，适用于“添加到购物车”和“登录”等操作。                       |
| `Elevated` | 有突出的阴影             | 对于主要或重要操作。提高按钮的层次感，使其更加突出。                                                 |
| `Outlined` | 具有无填充的边框         | 对于重要但不是主要的操作。轮廓按钮与其他按钮搭配使用，用以指示替代的、次要的操作，如“取消”或“返回”。 |
| `Text`     | 无背景或边框的文本       | 对于不太重要的操作，例如导航链接，或者次要操作，如“了解更多”或“查看详情”。                           |

### Usage

=== "Filled Button"

    ```Kotlin
    @Composable
    fun FilledButtonExample(onClick: () -> Unit) {
        Button(onClick = { onClick() }) {
            Text("Filled")
        }
    }
    ```

    <figure markdown="span">
        ![button-filled](https://developer.android.com/static/develop/ui/compose/images/components/button-filled.png)
        <figcaption><b>图 1.</b> <code>Filled Button</code></figcaption>
    </figure>

=== "Tonal Button"

    ```Kotlin
    @Composable
    fun FilledTonalButtonExample(onClick: () -> Unit) {
        FilledTonalButton(onClick = { onClick() }) {
            Text("Tonal")
        }
    }
    ```

    <figure markdown="span">
        ![button-tonal](https://developer.android.com/static/develop/ui/compose/images/components/button-tonal.png)
        <figcaption><b>图 2.</b> <code>Tonal Button</code></figcaption>
    </figure>

=== "Elevated Button"

    ```Kotlin
    @Composable
    fun ElevatedButtonExample(onClick: () -> Unit) {
        ElevatedButton(onClick = { onClick() }) {
            Text("Elevated")
        }
    }
    ```

    <figure markdown="span">
      ![button-elevated](https://developer.android.com/static/develop/ui/compose/images/components/button-elevated.png)
      <figcaption><b>图 3.</b> <code>Elevated Button</code></figcaption>
    </figure>

=== "Outlined Button"

    ```Kotlin
    @Composable
    fun OutlinedButtonExample(onClick: () -> Unit) {
        OutlinedButton(onClick = { onClick() }) {
            Text("Outlined")
        }
    }
    ```

    <figure markdown="span">
        ![button-outlined](https://developer.android.com/static/develop/ui/compose/images/components/button-outlined.png)
        <figcaption><b>图 4.</b> <code>Outlined Button</code></figcaption>
    </figure>

=== "Text Button"

    ```Kotlin
    @Composable
    fun TextButtonExample(onClick: () -> Unit) {
        TextButton(onClick = { onClick() }) {
            Text("Text Button")
        }
    }
    ```

    <figure markdown="span">
        ![button-text](https://developer.android.com/static/develop/ui/compose/images/components/button-text.png)
        <figcaption><b>图 5.</b> <code>Text Button</code></figcaption>
    </figure>

### Key points

- `onClick`：用户按下按钮时调用的函数。
- `enabled`：当为 `false` 时，此参数会导致按钮看起来不可用且无效。
- `colors`：一个 `ButtonColors` 的实例，用于确定按钮中使用的颜色。
- `contentPadding`：按钮内的填充。

---

## Floating action buttons(FAB)

一个浮动操作按钮（FAB）是一个高强调按钮，允许用户在应用程序中执行一个主要操作。它促进一个单一、集中的操作，这是用户可能采取的最常见路径，通常固定在屏幕的右下角。通常有以下应用场景：

- 创建新项目（Create new item）：在笔记应用中，FAB 可用于快速创建新笔记。
- 添加新联系人（Add new contact）：在聊天应用中，一个浮动操作按钮可以打开一个界面，让用户将某人添加到对话中。
- 中心位置（Center location）：在地图界面中，一个浮动操作按钮可以将地图中心定位到用户的当前位置。

在 Material Design，有 4 种类型的 FAB：

- `FAB`：一个普通大小的浮动操作按钮。
- `Small FAB`：一个较小的浮动操作按钮。
- `Large FAB` ：一个较大的浮动操作按钮。
- `Extended FAB`：一个包含不仅仅是图标的浮动操作按钮。

### Usage

=== "Basic FAB"

    ```Kotlin
    @Composable
    fun Example(onClick: () -> Unit) {
        FloatingActionButton(
            onClick = { onClick() },
        ) {
            Icon(Icons.Filled.Add, "Floating action button.")
        }
    }
    ```

    <figure markdown="span">
        ![fab](https://developer.android.com/static/develop/ui/compose/images/components/fab.png)
        <figcaption><b>图 6.</b> <code>FloatingActionButton</code></figcaption>
    </figure>

=== "Small FAB"

    ```Kotlin
    @Composable
    fun SmallExample(onClick: () -> Unit) {
        SmallFloatingActionButton(
            onClick = { onClick() },
            containerColor = MaterialTheme.colorScheme.secondaryContainer,
            contentColor = MaterialTheme.colorScheme.secondary
        ) {
            Icon(Icons.Filled.Add, "Small floating action button.")
        }
    }
    ```

    <figure markdown="span">
        ![fab-small](https://developer.android.com/static/develop/ui/compose/images/components/fab-small.png)
        <figcaption><b>图 7.</b> <code>Small FAB</code></figcaption>
    </figure>

=== "Large FAB"

    ```Kotlin
    @Composable
    fun LargeExample(onClick: () -> Unit) {
        LargeFloatingActionButton(
            onClick = { onClick() },
            shape = CircleShape,
        ) {
            Icon(Icons.Filled.Add, "Large floating action button")
        }
    }
    ```

    <figure markdown="span">
        ![fab-large](https://developer.android.com/static/develop/ui/compose/images/components/fab-large.png)
        <figcaption><b>图 8.</b> <code>Large FAB</code></figcaption>
    </figure>

=== "Extended FAB"

    ```Kotlin
    @Composable
    fun ExtendedExample(onClick: () -> Unit) {
        ExtendedFloatingActionButton(
            onClick = { onClick() },
            icon = { Icon(Icons.Filled.Edit, "Extended floating action button.") },
            text = { Text(text = "Extended FAB") },
        )
    }
    ```
    
    <figure markdown="span">
        ![fab-extended](https://developer.android.com/static/develop/ui/compose/images/components/fab-extended.png)
        <figcaption><b>图 9.</b> <code>Extended FAB</code></figcaption>
    </figure>

### Key points

- `onClick`：点击函数
- `containerColor`：按钮颜色
- `contentColor`：图标颜色

---

## External links

**UI Specs**

- [Common Buttons](https://m3.material.io/components/buttons/overview)
- [Floating action buttons](https://m3.material.io/components/floating-action-button/overview)

**Quick Guides**

- [Create a button](https://developer.android.com/quick-guides/content/create-button)
- [Create a floating action button (FAB)](https://developer.android.com/quick-guides/content/create-floating-action-button)

**References**

- [Button](https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary?#Button(kotlin.Function0,androidx.compose.ui.Modifier,kotlin.Boolean,androidx.compose.ui.graphics.Shape,androidx.compose.material3.ButtonColors,androidx.compose.material3.ButtonElevation,androidx.compose.foundation.BorderStroke,androidx.compose.foundation.layout.PaddingValues,androidx.compose.foundation.interaction.MutableInteractionSource,kotlin.Function1))
- [FilledTonalButton](https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary#FilledTonalButton(kotlin.Function0,androidx.compose.ui.Modifier,kotlin.Boolean,androidx.compose.ui.graphics.Shape,androidx.compose.material3.ButtonColors,androidx.compose.material3.ButtonElevation,androidx.compose.foundation.BorderStroke,androidx.compose.foundation.layout.PaddingValues,androidx.compose.foundation.interaction.MutableInteractionSource,kotlin.Function1))
- [OutlinedButton](https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary#OutlinedButton(kotlin.Function0,androidx.compose.ui.Modifier,kotlin.Boolean,androidx.compose.ui.graphics.Shape,androidx.compose.material3.ButtonColors,androidx.compose.material3.ButtonElevation,androidx.compose.foundation.BorderStroke,androidx.compose.foundation.layout.PaddingValues,androidx.compose.foundation.interaction.MutableInteractionSource,kotlin.Function1))
- [ElevatedButton](https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary#ElevatedButton(kotlin.Function0,androidx.compose.ui.Modifier,kotlin.Boolean,androidx.compose.ui.graphics.Shape,androidx.compose.material3.ButtonColors,androidx.compose.material3.ButtonElevation,androidx.compose.foundation.BorderStroke,androidx.compose.foundation.layout.PaddingValues,androidx.compose.foundation.interaction.MutableInteractionSource,kotlin.Function1))
- [TextButton](https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary#TextButton(kotlin.Function0,androidx.compose.ui.Modifier,kotlin.Boolean,androidx.compose.ui.graphics.Shape,androidx.compose.material3.ButtonColors,androidx.compose.material3.ButtonElevation,androidx.compose.foundation.BorderStroke,androidx.compose.foundation.layout.PaddingValues,androidx.compose.foundation.interaction.MutableInteractionSource,kotlin.Function1))
- [FloatingActionButton](https://developer.android.com/reference/kotlin/androidx/compose/material3/FloatingActionButtonElevation#FloatingActionButton(kotlin.Function0,androidx.compose.ui.Modifier,androidx.compose.ui.graphics.Shape,androidx.compose.ui.graphics.Color,androidx.compose.ui.graphics.Color,androidx.compose.material3.FloatingActionButtonElevation,androidx.compose.foundation.interaction.MutableInteractionSource,kotlin.Function0))
- [SmallFloatingActionButton](https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary#SmallFloatingActionButton(kotlin.Function0,androidx.compose.ui.Modifier,androidx.compose.ui.graphics.Shape,androidx.compose.ui.graphics.Color,androidx.compose.ui.graphics.Color,androidx.compose.material3.FloatingActionButtonElevation,androidx.compose.foundation.interaction.MutableInteractionSource,kotlin.Function0))
- [LargeFloatingActionButton](https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary#LargeFloatingActionButton(kotlin.Function0,androidx.compose.ui.Modifier,androidx.compose.ui.graphics.Shape,androidx.compose.ui.graphics.Color,androidx.compose.ui.graphics.Color,androidx.compose.material3.FloatingActionButtonElevation,androidx.compose.foundation.interaction.MutableInteractionSource,kotlin.Function0))
- [ExtendedFloatingActionButton](https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary#ExtendedFloatingActionButton(kotlin.Function0,kotlin.Function0,kotlin.Function0,androidx.compose.ui.Modifier,kotlin.Boolean,androidx.compose.ui.graphics.Shape,androidx.compose.ui.graphics.Color,androidx.compose.ui.graphics.Color,androidx.compose.material3.FloatingActionButtonElevation,androidx.compose.foundation.interaction.MutableInteractionSource))
