## Обобщенная коробка

### Описание задачи

Создать обобщённый класс Box, который реализует концепцию «коробки», способной хранить один объект любого заданного типа. Класс должен:

- Хранить один произвольный объект в любой момент времени.  
- Позволять получить и разместить объект в коробке.  
- Обнулять ссылку на объект при его извлечении.  
- Вызывать исключение при попытке поместить новый объект, если коробка уже заполнена.  
- Иметь метод для проверки, пуста ли коробка.  
- Работать только с тем типом данных, который указан при создании объекта.  

Пример: создать коробку, которая может хранить целочисленное значение, поместить туда число 3, передать коробку в метод, извлечь значение и вывести его на экран.

---

### Код класса Box

```
public class Box<T> {
    private T obj;

    public void put(T obj) {
        if (this.obj != null) {
            throw new IllegalArgumentException("Ошибка. Коробка уже заполнена");
        }
        this.obj = obj;
    }

    public T take() {
        if (obj == null) {
            return null;
        } else {
            T saverOfObj = obj;
            this.obj = null;
            return saverOfObj;
        }
    }

    public boolean isEmpty() {
        return obj == null;
    }

    @Override
    public String toString() {
        return "В коробке лежит: " + obj;
    }
}
```

---

### Демонстрация работы

```
public class Main {
    public static void main(String[] args) {
        Box<Integer> intBox = new Box<>();
        intBox.put(3);
        System.out.println("После помещения: " + intBox);

        printBoxValue(intBox);

        System.out.println("Пуста ли коробка? " + intBox.isEmpty());
    }

    public static void printBoxValue(Box<Integer> box) {
        Integer value = box.take();
        System.out.println("Извлечённое значение: " + value);
    }
}
```

---

### Пример вывода программы

```
После помещения: В коробке лежит: 3
Извлечённое значение: 3
Пуста ли коробка? true
```
```
