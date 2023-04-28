---
title:  "화면 로드될 때 input에 focus 주기"
excerpt: "input focus"

toc : true
toc_sticky : true

categories:
  - Error
tags: 
  - AOS
  - JavaScript
  - JQuery
  - focus
---


화면이 로드되고 input 요소에 focus를 주었음에도 제대로 focus가 들어가지 않는 경우가 있다.

input 요소를 클릭해서 포커스가 한 번 들어간 경우에는 포커스를 줬을 때 정상적으로 들어가지만 화면에 클릭이나 별다른 이벤트가 없이 로드만 된 상태에서 포커스를 주게 되면 포커스가 들어가지 않는 현상이 발생한다.

그럴땐 아래 코드를 추가해서 문제를 해결할 수 있다.


```java
@Override
	public void onCreate(Bundle savedInstanceState) {
		super.onCreate(savedInstanceState);

		getWebView().requestFocus();
		getWebView().setOnTouchListener(new View.OnTouchListener() {
			@Override
			public boolean onTouch(View v, MotionEvent event) {
				switch (event.getAction()) {
					case MotionEvent.ACTION_DOWN:
					case MotionEvent.ACTION_UP:
						if (!v.hasFocus()) {
							v.requestFocus();
						}
						break;
				}
				return false;
			}
		});
  }
```

위 코드를 적용하고 다시 빌드한 뒤 화면이 로드되고 나서 별다른 이벤트 없이 포커스를 줘도 바로 적용이 되는 모습을 볼 수 있다.

