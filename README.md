



# 基于底部导航的多返回栈应用中跨返回栈跳转示例

本示例在google官方的多返回栈示例基础上展示跨返回栈跳转的情况。



## 演示用例

安卓并打开示例应用后，切换到Leaderboard页面，点击条目进入详情页，然后通过底部导航栏切回到home页面，点击进入about页面，点击跳转到第二个页面，可以看到页面被切换到了Leaderboard页面，且Leaderboard返回栈退回到了首页。

以上就是要达到的主要演示效果。进一步对该示例进行扩展，实际可以实现跳转到任意其他返回栈的任意界面。

## 主要原理概述

第一步使用BottomNavitagionView对返回栈进行切换

第二步获取相应返回栈的NavHostFragment实例后进一步获取到该返回栈顶部的fragment实例，通过对该示例生命周期的监听，在接收到ON_RESUME事件后执行栈内跳转。之所以要监听生命周期之后跳转而不是直接在切返回栈之后就直接执行栈内跳转，原因是那个时候栈顶的fragment还没有被attach到activity，这个时候执行跳转的代码无效。
