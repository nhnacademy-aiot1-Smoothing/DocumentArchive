# Code Style

### Naming Convention

DB : snake_case

DB 제외 전부 : camelCase

### if 다음 한 줄인 경우

```java
if(true) {
		method();
}
```

### Parameter가 2개 이상인 경우

```java
~~method(int a,
			int b,
			int c) {	
		
};~~
```

### Annotation 순서(글자길이 순)

```java
@Annotation1
@Annotation12
field a();
```

### method chaining(적당히 보기좋게)

```java
a()
.b()
.c()
```

### 전체 method 한 줄 띄우기

```java
method() {

	a();
}
```