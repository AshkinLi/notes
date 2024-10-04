---
title: App Bars
tags:
  - App bars
---

应用栏是屏幕顶部或底部的容器，它们为用户提供访问关键功能和导航项的入口：

| 类型             | 外观         | 用途                                                                 |
| :--------------- | :----------- | :------------------------------------------------------------------- |
| `Top app bar`    | 位于屏幕顶部 | 提供访问关键任务和信息的功能。通常包含标题、核心操作项和某些导航项。 |
| `Bottom app bar` | 位于屏幕底部 | 通常包括核心导航项。可能通过使用一个浮动操作按钮来访问其他操作。     |

## Top app bar

### Usage

=== "Small top app bar"

    ```Kotlin
    @Composable
    fun SmallTopAppBarExample() {
        Scaffold(
            topBar = {
                TopAppBar(
                    colors = TopAppBarDefaults.topAppBarColors(
                        containerColor = MaterialTheme.colorScheme.primaryContainer,
                        titleContentColor = MaterialTheme.colorScheme.primary,
                    ),
                    title = {
                        Text("Small Top App Bar")
                    }
                )
            },
        ) { innerPadding ->
            ScrollContent(innerPadding)
        }
    }
    ```

    <figure markdown="span">
        ![appbar-small](https://developer.android.com/static/develop/ui/compose/images/components/appbar-small.png)
        <figcaption><b>图 1.</b> <code>Small top app bar</code></figcaption>
    </figure>

=== "Center-aligned top app bar"

    ```Kotlin
    @Composable
    fun CenterAlignedTopAppBarExample() {
        val scrollBehavior = TopAppBarDefaults.pinnedScrollBehavior(rememberTopAppBarState())

        Scaffold(
            modifier = Modifier.nestedScroll(scrollBehavior.nestedScrollConnection),

            topBar = {
                CenterAlignedTopAppBar(
                    colors = TopAppBarDefaults.centerAlignedTopAppBarColors(
                        containerColor = MaterialTheme.colorScheme.primaryContainer,
                        titleContentColor = MaterialTheme.colorScheme.primary,
                    ),
                    title = {
                        Text(
                            "Centered Top App Bar",
                            maxLines = 1,
                            overflow = TextOverflow.Ellipsis
                        )
                    },
                    navigationIcon = {
                        IconButton(onClick = { /* do something */ }) {
                            Icon(
                                imageVector = Icons.AutoMirrored.Filled.ArrowBack,
                                contentDescription = "Localized description"
                            )
                        }
                    },
                    actions = {
                        IconButton(onClick = { /* do something */ }) {
                            Icon(
                                imageVector = Icons.Filled.Menu,
                                contentDescription = "Localized description"
                            )
                        }
                    },
                    scrollBehavior = scrollBehavior,
                )
            },
        ) { innerPadding ->
            ScrollContent(innerPadding)
        }
    }
    ```

    <figure markdown="span">
        ![appbar-centered](https://developer.android.com/static/develop/ui/compose/images/components/appbar-centered.png)
        <figcaption><b>图 2.</b> <code>Center-aligned top app bar</code></figcaption>
    </figure>

=== "Medium top app bar"

    ```Kotlin
    @Composable
    fun MediumTopAppBarExample() {
        val scrollBehavior = TopAppBarDefaults.enterAlwaysScrollBehavior(rememberTopAppBarState())

        Scaffold(
            modifier = Modifier.nestedScroll(scrollBehavior.nestedScrollConnection),
            topBar = {
                MediumTopAppBar(
                    colors = TopAppBarDefaults.topAppBarColors(
                        containerColor = MaterialTheme.colorScheme.primaryContainer,
                        titleContentColor = MaterialTheme.colorScheme.primary,
                    ),
                    title = {
                        Text(
                            "Medium Top App Bar",
                            maxLines = 1,
                            overflow = TextOverflow.Ellipsis
                        )
                    },
                    navigationIcon = {
                        IconButton(onClick = { /* do something */ }) {
                            Icon(
                                imageVector = Icons.AutoMirrored.Filled.ArrowBack,
                                contentDescription = "Localized description"
                            )
                        }
                    },
                    actions = {
                        IconButton(onClick = { /* do something */ }) {
                            Icon(
                                imageVector = Icons.Filled.Menu,
                                contentDescription = "Localized description"
                            )
                        }
                    },
                    scrollBehavior = scrollBehavior
                )
            },
        ) { innerPadding ->
            ScrollContent(innerPadding)
        }
    }
    ```

    <figure markdown="span">
        <video width="100%" autoplay loop muted>
            <source src="https://developer.android.com/static/develop/ui/compose/images/components/appbar-scroll.mp4" type="video/mp4">
        </video>
        <figcaption><b>图 3.</b> <code>Medium top app bar</code></figcaption>
    </figure>

=== "Large top app bar"

    ```Kotlin
    @Composable
    fun LargeTopAppBarExample() {
        val scrollBehavior = TopAppBarDefaults.exitUntilCollapsedScrollBehavior(rememberTopAppBarState())

        Scaffold(
            modifier = Modifier.nestedScroll(scrollBehavior.nestedScrollConnection),
            topBar = {
                LargeTopAppBar(
                    colors = TopAppBarDefaults.topAppBarColors(
                        containerColor = MaterialTheme.colorScheme.primaryContainer,
                        titleContentColor = MaterialTheme.colorScheme.primary,
                    ),
                    title = {
                        Text(
                            "Large Top App Bar",
                            maxLines = 1,
                            overflow = TextOverflow.Ellipsis
                        )
                    },
                    navigationIcon = {
                        IconButton(onClick = { /* do something */ }) {
                            Icon(
                                imageVector = Icons.AutoMirrored.Filled.ArrowBack,
                                contentDescription = "Localized description"
                            )
                        }
                    },
                    actions = {
                        IconButton(onClick = { /* do something */ }) {
                            Icon(
                                imageVector = Icons.Filled.Menu,
                                contentDescription = "Localized description"
                            )
                        }
                    },
                    scrollBehavior = scrollBehavior
                )
            },
        ) { innerPadding ->
            ScrollContent(innerPadding)
        }
    }
    ```

    <figure markdown="span">
        ![appbar-large](https://developer.android.com/static/develop/ui/compose/images/components/appbar-large.png)
        <figcaption><b>图 4.</b> <code>Large top app bar</code></figcaption>
    </figure>

## Bottom app bar

`BottomAppBar` 常用参数如下：

- `actions`：一系列图标出现在工具栏的左侧。这些通常是给定屏幕的关键操作或导航项。
- `floatingActionButton`：出现在栏右侧的浮动操作按钮。

### Usage

=== "Bottom app bar"

    ```Kotlin
    @Composable
    fun BottomAppBarExample() {
        Scaffold(
            bottomBar = {
                BottomAppBar(
                    actions = {
                        IconButton(onClick = { /* do something */ }) {
                            Icon(Icons.Filled.Check, contentDescription = "Localized description")
                        }
                        IconButton(onClick = { /* do something */ }) {
                            Icon(
                                Icons.Filled.Edit,
                                contentDescription = "Localized description",
                            )
                        }
                        IconButton(onClick = { /* do something */ }) {
                            Icon(
                                Icons.Filled.Mic,
                                contentDescription = "Localized description",
                            )
                        }
                        IconButton(onClick = { /* do something */ }) {
                            Icon(
                                Icons.Filled.Image,
                                contentDescription = "Localized description",
                            )
                        }
                    },
                    floatingActionButton = {
                        FloatingActionButton(
                            onClick = { /* do something */ },
                            containerColor = BottomAppBarDefaults.bottomAppBarFabColor,
                            elevation = FloatingActionButtonDefaults.bottomAppBarFabElevation()
                        ) {
                            Icon(Icons.Filled.Add, "Localized description")
                        }
                    }
                )
            },
        ) { innerPadding ->
            Text(
                modifier = Modifier.padding(innerPadding),
                text = "Example of a scaffold with a bottom app bar."
            )
        }
    }
    ```

    <figure markdown="span">
        ![appbar-bottom](https://developer.android.com/static/develop/ui/compose/images/components/appbar-bottom.png)
        <figcaption><b>图 5.</b> <code>Bottom app bar</code></figcaption>
    </figure>

## Key points

- 将 `app bars` 传递给 `Scaffold` 组合，它有特定的参数来接收它们。
- `Top app bar` 常用参数如下：
    - `title`：标题
    - `navigationIcon`：用于导航的主要图标，显示在 `Top app bar` 的左侧。
    - `actions`：提供用户访问关键操作的图标，出现在 `Top app bar` 的右侧。
    - `scrollBehavior`：确定顶部 `Top app bar` 如何响应 `Scaffold` 内部内容的滚动。
    - `colors`：决定 `Top app bar` 的外观。
- 使用 `TopAppBarScrollBehavior` 来控制 `Top app bar` 的行为，有 3 种类型可选：
    - `enterAlwaysScrollBehavior`：当用户向上滑动的时候，`Top app bar` 会折叠。当用户向下滑动时，`Top app bar` 会展开。
    - `exitUntilCollapsedScrollBehavior`：类似于 `enterAlwaysScrollBehavior`，不过当用户滚动到底部时，`Top app bar` 也会展开。
    - `pinnedScrollBehavior`：`Top app bar` 保持固定，不会随着滚动而变化。

## External links

**UI Specs**

- [Bottom app bar](https://m3.material.io/components/bottom-app-bar/overview)
- [Top app bars](https://m3.material.io/components/top-app-bar/overview)

**Quick Guides**

- [Display an app bar](https://developer.android.com/quick-guides/content/display-app-bar)
- [Display a bottom app bar](https://developer.android.com/quick-guides/content/display-bottom-app-bar)
- [Display a top app bar](https://developer.android.com/quick-guides/content/display-top-app-bar)

**References**

- [TopAppBar](https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary#TopAppBar(kotlin.Function0,androidx.compose.ui.Modifier,kotlin.Function0,kotlin.Function1,androidx.compose.ui.unit.Dp,androidx.compose.foundation.layout.WindowInsets,androidx.compose.material3.TopAppBarColors,androidx.compose.material3.TopAppBarScrollBehavior))
- [CenterAlignedTopAppBar](https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary#CenterAlignedTopAppBar(kotlin.Function0,androidx.compose.ui.Modifier,kotlin.Function0,kotlin.Function1,androidx.compose.ui.unit.Dp,androidx.compose.foundation.layout.WindowInsets,androidx.compose.material3.TopAppBarColors,androidx.compose.material3.TopAppBarScrollBehavior):~:text=on%20the%20card-,CenterAlignedTopAppBar,-Cmn)
- [MediumTopAppBar](https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary#MediumTopAppBar(kotlin.Function0,androidx.compose.ui.Modifier,kotlin.Function0,kotlin.Function1,androidx.compose.ui.unit.Dp,androidx.compose.ui.unit.Dp,androidx.compose.foundation.layout.WindowInsets,androidx.compose.material3.TopAppBarColors,androidx.compose.material3.TopAppBarScrollBehavior):~:text=typically%20an%20Icon-,MediumTopAppBar,-Cmn)
- [LargeTopAppBar](https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary#LargeTopAppBar(kotlin.Function0,androidx.compose.ui.Modifier,kotlin.Function0,kotlin.Function1,androidx.compose.ui.unit.Dp,androidx.compose.ui.unit.Dp,androidx.compose.foundation.layout.WindowInsets,androidx.compose.material3.TopAppBarColors,androidx.compose.material3.TopAppBarScrollBehavior):~:text=typically%20an%20Icon-,LargeTopAppBar,-Cmn)
- [BottomAppBar](https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary#BottomAppBar(androidx.compose.ui.Modifier,androidx.compose.ui.graphics.Color,androidx.compose.ui.graphics.Color,androidx.compose.ui.unit.Dp,androidx.compose.foundation.layout.PaddingValues,androidx.compose.foundation.layout.WindowInsets,kotlin.Function1))
