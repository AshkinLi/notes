---
title: Scaffold
tags:
  - Scaffold
---

在 Material Design 中，`Scaffold` 是一种基本结构，为复杂的用户界面提供了一个标准化的平台。它将用户界面的不同部分，如应用栏和浮动操作按钮，固定在一起，赋予应用程序一个连贯的外观和感觉。

## Usage

=== "Scaffold"

    ```Kotlin
    @Composable
    fun ScaffoldExample() {
        var presses by remember { mutableIntStateOf(0) }

        Scaffold(
            topBar = {
                TopAppBar(
                    colors = topAppBarColors(
                        containerColor = MaterialTheme.colorScheme.primaryContainer,
                        titleContentColor = MaterialTheme.colorScheme.primary,
                    ),
                    title = {
                        Text("Top app bar")
                    }
                )
            },
            bottomBar = {
                BottomAppBar(
                    containerColor = MaterialTheme.colorScheme.primaryContainer,
                    contentColor = MaterialTheme.colorScheme.primary,
                ) {
                    Text(
                        modifier = Modifier
                            .fillMaxWidth(),
                        textAlign = TextAlign.Center,
                        text = "Bottom app bar",
                    )
                }
            },
            floatingActionButton = {
                FloatingActionButton(onClick = { presses++ }) {
                    Icon(Icons.Default.Add, contentDescription = "Add")
                }
            }
        ) { innerPadding ->
            Column(
                modifier = Modifier
                    .padding(innerPadding),
                verticalArrangement = Arrangement.spacedBy(16.dp),
            ) {
                Text(
                    modifier = Modifier.padding(8.dp),
                    text =
                    """
                        This is an example of a scaffold. It uses the Scaffold composable's parameters to create a screen with a simple top app bar, bottom app bar, and floating action button.

                        It also contains some basic inner content, such as this text.

                        You have pressed the floating action button $presses times.
                    """.trimIndent(),
                )
            }
        }
    }
    ```

    <figure markdown="span">
        ![scaffold](https://developer.android.com/static/develop/ui/compose/images/components/scaffold.png)
        <figcaption><b>图 1.</b> <code>Scaffold</code></figcaption>
    </figure>

## Key points

`Scaffold` 提供了简单的 API，可以使用它快速根据 Material Design 指南构建应用程序的结构。`Scaffold` 接受多个参数。其中包括以下几个：

- `topBar`：位于屏幕顶部的应用程序栏。
- `bottomBar`：位于屏幕底部的应用程序栏。
- `floatingActionButton`：一个悬浮在屏幕右下角的按钮，你可以使用它来暴露关键操作。

## External links

**Quick Guides**

- [Create a scaffold component to hold the UI together](https://developer.android.com/quick-guides/content/create-scaffold)
- [Create a home screen scaffold](https://developer.android.com/quick-guides/collections/create-a-home-screen-scaffold)

**References**

- [Scaffold](https://developer.android.com/reference/kotlin/androidx/compose/material/package-summary#Scaffold(androidx.compose.foundation.layout.WindowInsets,androidx.compose.ui.Modifier,androidx.compose.material.ScaffoldState,kotlin.Function0,kotlin.Function0,kotlin.Function1,kotlin.Function0,androidx.compose.material.FabPosition,kotlin.Boolean,kotlin.Function1,kotlin.Boolean,androidx.compose.ui.graphics.Shape,androidx.compose.ui.unit.Dp,androidx.compose.ui.graphics.Color,androidx.compose.ui.graphics.Color,androidx.compose.ui.graphics.Color,androidx.compose.ui.graphics.Color,androidx.compose.ui.graphics.Color,kotlin.Function1))
