---
title: Sliders
tags:
  - Slider
---

## Override

`Slider` 组件允许用户从一系列值中进行选择。你可以使用滑块让用户执行以下操作：

- 调整使用一系列值的设置，例如音量和亮度。
- 在图表中过滤数据，如设置价格范围时。
- 用户输入，如在评论中设置评分。

滑块包含轨道、拇指、值标签和刻度线：

- 轨道（**Track**）：轨道是代表滑块可以取值范围的水平条。
- 拇指（**Thumb**）：拇指是滑块上的一个可拖动控制元素，允许用户在轨道定义的范围内选择特定的值。
- 刻度标记（**Tick marks**）：刻度标记是可选的视觉标记或指示器，沿着滑块的轨道出现。

## Usage

=== "Basic"

    ```Kotlin
    @Preview
    @Composable
    fun SliderMinimalExample() {
        var sliderPosition by remember { mutableFloatStateOf(0f) }
        Column {
            Slider(
                value = sliderPosition,
                onValueChange = { sliderPosition = it }
            )
            Text(text = sliderPosition.toString())
        }
    }
    ```

    <figure markdown="span">
        ![slider-basic](https://developer.android.com/static/develop/ui/compose/images/components/slider-basic.png){ loading=lazy }
        <figcaption><b>图 1.</b> <code>Slider</code></figcaption>
    </figure>

=== "Advanced"

    ```Kotlin
    @Preview
    @Composable
    fun SliderAdvancedExample() {
        var sliderPosition by remember { mutableFloatStateOf(0f) }
        Column {
            Slider(
                value = sliderPosition,
                onValueChange = { sliderPosition = it },
                colors = SliderDefaults.colors(
                    thumbColor = MaterialTheme.colorScheme.secondary,
                    activeTrackColor = MaterialTheme.colorScheme.secondary,
                    inactiveTrackColor = MaterialTheme.colorScheme.secondaryContainer,
                ),
                steps = 3,
                valueRange = 0f..50f
            )
            Text(text = sliderPosition.toString())
        }
    }
    ```

    <figure markdown="span">
        ![slider-advanced](https://developer.android.com/static/develop/ui/compose/images/components/slider-advanced.png){ loading=lazy }
        <figcaption><b>图 2.</b> 一个带有步骤和设定值范围的 <code>Slider</code>。</figcaption>
    </figure>

=== "Range"

    ```Kotlin
    @Preview
    @Composable
    fun RangeSliderExample() {
        var sliderPosition by remember { mutableStateOf(0f..100f) }
        Column {
            RangeSlider(
                value = sliderPosition,
                steps = 5,
                onValueChange = { range -> sliderPosition = range },
                valueRange = 0f..100f,
                onValueChangeFinished = {
                    // launch some business logic update with the state you hold
                    // viewModel.updateSelectedSliderValue(sliderPosition)
                },
            )
            Text(text = sliderPosition.toString())
        }
    }
    ```

    <figure markdown="span">
        ![slider-range](https://developer.android.com/static/develop/ui/compose/images/components/slider-range.png){ loading=lazy }
        <figcaption><b>图 3.</b> <code>RangeSlider</code></figcaption>
    </figure>

## Key points

一些关键的 `Slider` 可组合参数如下：

- `value`: 滑块的当前值。
- `onValueChange`：每次值改变时都会调用的一个 lambda 函数。
- `enabled`：一个布尔值，表示用户是否可以与滑块交互。

在实现更复杂的滑块时，您还可以使用以下参数。

- `colors`：一个 `SliderColors` 的实例，允许你控制滑块的颜色。
- `valueRange`：滑块可以取的值范围。
- `steps`：滑块上缺口的数量，滑块上的拇指会对准这些缺口。

## External links

**UI Specs**

- [Silders - Material Design 3](https://m3.material.io/components/sliders/overview)

**Quick Guides**

- [Create a slider for a range of values](https://developer.android.com/quick-guides/content/create-range-slider)

**References**

- [Slider](https://developer.android.com/reference/kotlin/androidx/compose/material3/package-summary#Slider(androidx.compose.material3.SliderState,androidx.compose.ui.Modifier,kotlin.Boolean,androidx.compose.material3.SliderColors,androidx.compose.foundation.interaction.MutableInteractionSource,kotlin.Function1,kotlin.Function1))
