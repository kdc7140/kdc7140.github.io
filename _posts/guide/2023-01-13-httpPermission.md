---
title:  "[Android] 안드로이드 전체 도메인 허용"
excerpt: "http 통신 허용"

toc : true
toc_sticky : true

categories:
  - Error
tags: 
  - Android
  - http
  - 오류해결
  
---

<br/>

구글에서 안드로이드 9부터 보안상의 이유로 http 통신을 허용하지 않는데 아래와 같은 방법으로 설정을 하면 사용이 가능하다.

<br/>

## 1. 파일 생성

src > res > xml 경로에 network_security_config.xml 파일을 생성한다.

<br/>


## 2. http 통신 허용 코드 입력

```java
<?xml version="1.0" encoding="utf-8"?>
<network-security-config>
	<base-config cleartextTrafficPermitted="true">
		<trust-anchors>
			<certificates src="system" />
		</trust-anchors>
	</base-config>
</network-security-config>
```

<br/>


## 3. Manifest 설정

AndroidManifest에서 <application></application> 영역에 아래 코드를 입력한다.

```java
android:networkSecurityConfig="@xml/network_security_config"
```