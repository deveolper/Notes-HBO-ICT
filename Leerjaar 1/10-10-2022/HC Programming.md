Proeftoetsen staan op ook op Brightspace.

60 % van de punten voor een voldoende

# Scope
Scope van variabele:
```java
public static void f(int a) {
	int b = 3;
	if (a == b) {
		int c = 4;
		// Einde scope c
	}
	int c = 3; // kan, want c bestaat momenteel niet.
	// Einde scope b
}
```

# While loop
Blijft code herhalen tot de conditie niet meer waar is.

```java
while (/* conditie */) {
	// Code
}
```
