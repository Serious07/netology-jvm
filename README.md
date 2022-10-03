# netology-jvm

```java

// Срабатывает Подсистема загрузчиков классов, 
// в MetaSpace инициализируются все системные классы, 
// зависимости, после чего класс JvmComprehension
public class JvmComprehension {
    // В момент вызова создаётся кадр в стеке
    public static void main(String[] args) {
        int i = 1;                      // 1 Переменая i создаётся и помещается в стек, внутрь кадра для main
        Object o = new Object();        // 2 Объект типа Object помещается в кучу, а ссылка на объект "o" в стек, 
                                        // внутрь кадра для main, формируется связь
        Integer ii = 2;                 // 3 Объект типа Integer помещается в кучу, а ссылка на объект "ii" в стеке, 
                                        // внутрь кадра для main, формируется связь
        printAll(o, i, ii);             // 4 Создаётся новый кадр в стеке для метода printAll,
                                        // в куче находится ранее созданный объект типа Object, 
                                        // а ссылка на объект "o" создаётся в стеке,
                                        // внутри кадра для printAll, формируется связь
                                        // Переменая i создаётся и помещается в стек, внутрь кадра для printAll
                                        // в куче находится ранее созданный объект типа Integer, 
                                        // а ссылка на объект "ii" создаётся в стеке,
                                        // внутри кадра для printAll, формируется связь
        System.out.println("finished"); // 7 Срабатывает сборщик мусора после окончания работы printAll.
                                        // Создаётся новый кадр в стеке, "finished" помещается в кучу
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5 Объект типа Integer помещается в кучу, 
                                                    // а ссылка на объект в стек, внутрь кадра printAll, 
                                                    // формируется связь
        System.out.println(o.toString() + i + ii);  // 6 Создаётся новый кадр в стеке, 
                                                    // в нём создаётся ссылка на o, ii, 
                                                    // переменная i помещается в стек
    }
}
```
