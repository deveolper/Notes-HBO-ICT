Tafelprinterij:

```java
public class Main {
    public static void main(String[] args) {
        for (int tafel = 1; tafel <= 10; tafel++) {
            System.out.println();
            for (int i = 1; i <= 10; i++) {
                System.out.printf("%d * %d = %d%n", i, tafel, i * tafel);
            }
        }
    }
}
```

Tafeloverslaan:

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Welke tafel wilt u overslaan?");
        int overslaan = scanner.nextInt();
        for (int tafel = 1; tafel <= 10; tafel++) {
            if (tafel == overslaan) {
                continue;
            }
            System.out.println();
            for (int i = 1; i <= 10; i++) {
                System.out.printf("%d * %d = %d%n", i, tafel, i * tafel);
            }
        }
    }
}
```

Voorkeursuitwerking volgens de docent:

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Welke tafel wilt u overslaan?");
        int overslaan = scanner.nextInt();
        for (int tafel = 1; tafel <= 10; tafel++) {
            if (tafel != overslaan) {
                System.out.println();
                for (int i = 1; i <= 10; i++) {
                    System.out.printf("%d * %d = %d%n", i, tafel, i * tafel);
                }
            }
        }
    }
}
```

Tafel en regel overslaan:

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Welke tafel wilt u overslaan?");
        int tafel_overslaan = scanner.nextInt();
        System.out.println("Welke regel wilt u overslaan?");
        int regel_overslaan = scanner.nextInt();
        for (int tafel = 1; tafel <= 10; tafel++) {
            if (tafel == tafel_overslaan) {
                continue;
            }
            System.out.println();
            for (int i = 1; i <= 10; i++) {
                if (regel_overslaan == i) {
                    continue;
                }
                System.out.printf("%d * %d = %d%n", i, tafel, i * tafel);
            }
        }
    }
}
```

Voorkeursuitwerking volgens de docent:

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Welke tafel wilt u overslaan?");
        int tafel_overslaan = scanner.nextInt();
        System.out.println("Welke regel wilt u overslaan?");
        int regel_overslaan = scanner.nextInt();
        for (int tafel = 1; tafel <= 10; tafel++) {
            if (tafel != tafel_overslaan) {
                System.out.println();
                for (int i = 1; i <= 10; i++) {
                    if (regel_overslaan != i) {
                        System.out.printf("%d * %d = %d%n", i, tafel, i * tafel);
                    }
                }
            }
        }
    }
}
```
