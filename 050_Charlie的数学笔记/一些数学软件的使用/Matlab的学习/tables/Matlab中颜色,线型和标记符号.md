#table #matlab 


## 颜色color
```dataview 
table time-played, length, rating from "games" sort rating desc
```

| 颜色参数 | y   | b   | g   | c   | m     | w   | k   | r   |
| ---- | --- | --- | --- | --- | ----- | --- | --- | --- |
| 颜色   | 黄色  | 蓝色  | 绿色  | 青色  | 洋红/品红 | 白色  | 黑色  | 红色  |

## 线型参数

### 颜色参数

color 参数用于指定 MATLAB 绘图中对象的颜色。下表列出了颜色参数及其相应的值。

| Color Parameter | y   | b   | g   | c   | m     | w   | k   | r   |
| ---- | --- | --- | --- | --- | ----- | --- | --- | --- |
| Color    | Yellow  | Blue  | Green  | Cyan  | Orange/Red  | White  | Black  | Red  |

### Line Type Parameters

The line type parameter is used to specify the style of lines in a MATLAB plot. The following table lists the line type parameters and their corresponding values.

| Line Type Parameter | -           | :   | -.   | --  |
| ---- | ----------- | --- | ---- | --- |
| Line Type   | Solid (default) | Dashed | Dash-dot | Dotted  |

### Marker Symbols

The marker symbol is used to specify the shape of markers in a MATLAB plot. The following table lists the marker symbols and their corresponding values.

| Marker Symbol | p     | d   | x(小写字母) | *   | s   | +   | h    | v(小写) |
| ---- | ----- | --- | ------- | --- | --- | --- | ---- | ----- |
| Marker    | Plus sign  | Circle  | Cross (lowercase letter) | Asterisk  | Square  | Plus sign  | Hexagon  | Inverted triangle  |

#### Reference - Settings

Use the following shortcuts to access general help and display the current date, time, and datetime:

*   `__help settings__` for general help
*   `%date%` or `%datetime%` to display the current date and time
*   `%Y-%m-%d %H:%M:%S` to display the current date and time in ISO format

### Dice Roller Shortcuts

The following table lists dice roller shortcuts:

| Shortcut | Description |
| ---- | ----------- |
| `d{max}` | Rolls a single die with the specified maximum value. Example: `d20` rolls a 20-sided die. |
| `{count: >0, default: 1}d{max: >0}{add: + or - followed by >0, default: +0}` | Rolls multiple dice and adds the results together. Examples:
    *   `3d6` rolls three 6-sided dice and adds the results.
    *   `2d10-3` rolls two 10-sided dice and subtracts 3 from the result.

### Example Usage

Here are some examples of using the dice roller shortcuts:

*   Roll a single die with maximum value 20: `d20`
*   Roll three 6-sided dice and add the results: `2d6`
*   Roll two 10-sided dice, add the results together, and subtract 3 from the result: `2d10-3`

Note that you can modify the shortcuts to suit your needs by adjusting the `{max}`, `{count}`, `{add}`, and other parameters.


| 线型参数 | -           | :   | -.   | --  |
| ---- | ----------- | --- | ---- | --- |
| 线型   | 实型(default) | 点型  | 点划线型 | 虚线  |
|      |             |     |      |     |


## 标记符号


| 标记符号 | p     | d   | x(小写字母) | *   | s   | +   | h    | v(小写) |
| ---- | ----- | --- | ------- | --- | --- | --- | ---- | ----- |
| 标记   | 正五角星型 | 菱形  | 叉型      | 星号  | 方块  | 加号  | 正六角星 | v型    |
^date
2024/11/4
2024/11/4 18:57:49
Hello! How are you?
#### Reference - Settings
_Use shortcut __help settings__ for general help._
- __hi__ - Expands into "Hello! How are you?".  A simple shortcut to see if Inline Scripts plugin is running.
- __date__ - Expands into the current, local date.
- __time__ - Expands into the current, local time.
- __datetime__ - Expands into the current, local date and time.
- __d{max: >0}__ - A dice roller shortcut.  Expands into "🎲 {roll result} /D{max}".  {max} is the size of dice to roll.
    - Examples - d3, d20, d57, d999
- __{count: >0, default: 1}d{max: >0}{add: + or - followed by >0, default: +0}__ - A dice roller shortcut, same as d{max}, but with optional {count} and {add} parameters.  {count} is the number of dice to roll and add together.  {add} is "+" or "-" followed by an amount to adjust the result by.
    - Examples - d100, 3d20, d10+5, 3d6+6
d999
🎲 __610::__/D999
```dataview

```
