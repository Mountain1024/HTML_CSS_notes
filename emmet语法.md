# Emmet语法

Vscode内置了Emmet语法，在html或者css文件里输入缩写后按Tab/Enter健即会自动生成相应代码

例如：！可以快速生成完整的html5代码

## > （子代）和 +（兄弟）

- `div>ul>li`
- `div+div>p>span+i`
- `div+p+ul>li`

## *（多个）和^（上一级）

- `ul>li*5`
- `div+div>p>span^h1`
- `div+div>p>span^^^h1`

## ()分组

`div>(header>ul>li*2>a)+footer>p`

## 属性（id、class、普通属性）{}(内容)

`div#header+div#main>.container>a[href]`

`a[href="http://www.baidu.com"]{百度一下}`

## $ 数字

`ul>li.item$*5`

## 隐式标签

`.box+.container`

`ul>.item*3`

## CSS Emmet

`w 100`	`w20+h30+m40+p50`	`m20-30-40-50`	`dib`

`bd1#cs`

