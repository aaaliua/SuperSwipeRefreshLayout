# SuperSwipeRefreshLayout

A Custom SwipeRefreshLayout.

##Why？
本来SwipeRefreshLayout已经能够满足大部分的需求了。无奈，产品经理执意要做成下拉过程中，被嵌套的View也要跟随手指的滑动而滑动，并且下拉刷新头可以自定义。

##Feature
- 非侵入式，对原来的ListView、RecyclerView没有任何影响,用法和SwipeRefreshLayout类似。
- 可自定义头部View的样式，调用setHeaderView方法即可
- 支持RecyclerView，ListView，ScrollView，GridView等等。
- 被包含的View(RecyclerView,ListView etc.)可跟随手指的滑动而滑动<br>
  默认是跟随手指的滑动而滑动，也可以设置为不跟随：setTargetScrollWithLayout(false)
- 回调方法更多<br>
  比如：onRefresh() onPullDistance(int distance)和onPullEnable(boolean enable)<br>
  开发人员可以根据下拉过程中distance的值做一系列动画。
<br>
## How to use

### step 1

```xml
<net.mobctrl.views.SuperSwipeRefreshLayout
		android:id="@+id/swipe_refresh"
		android:layout_width="match_parent"
		android:layout_height="match_parent" >

		<android.support.v7.widget.RecyclerView
			android:id="@+id/recycler_view"
			android:layout_width="match_parent"
			android:layout_height="match_parent" />
</net.mobctrl.views.SuperSwipeRefreshLayout>
```
### step 2

```java

swipeRefreshLayout = (SuperSwipeRefreshLayout) findViewById(R.id.swipe_refresh);
		swipeRefreshLayout.setHeaderView(createHeaderView());// add headerView
		swipeRefreshLayout
				.setOnPullRefreshListener(new OnPullRefreshListener() {

					@Override
					public void onRefresh() {
						//TODO 开始刷新
					}

					@Override
					public void onPullDistance(int distance) {
						//TODO 下拉距离
					}

					@Override
					public void onPullEnable(boolean enable) {
						//TODO 下拉过程中，下拉的距离是否足够出发刷新
					}
				});

```
### step 3<br>
- create your header view

```java
swipeRefreshLayout.setHeaderView(createHeaderView());// add headerView

/**
 * create Header View
 */
private View createHeaderView(){
   //TODO 创建下拉刷新头部的View样式
}
```
### More
- setTargetScrollWithLayout(false/true);//default true
```java 
swipeRefreshLayout.setTargetScrollWithLayout(true);
```

## Support View
- RecyclerView.
- ListView
- SrcollView
- GridView
- etc.
## Demo

![gif](https://github.com/nuptboyzhb/SuperSwipeRefreshLayout/blob/master/demo.gif)


## About
@Author: Zheng Haibo 莫川<br>
@Website: www.mobctrl.net<br>

# License

Copyright 2015  [Zheng Haibo](https://github.com/nuptboyzhb/)

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.