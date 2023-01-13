# Описание работы кода с точки зрения JVM

    public static void main(String[] args) {
        int i = 1;                      // 1 Объявлена переменная целочисленного типа с именем i. Храниться в Stack
        Object o = new Object();        // 2 ClassLoader загружает класс Object. Создается объект класса Object в куче, добавляется ссылка на этот объект в Stack
        Integer ii = 2;                 // 3 ClassLoader загружает класс Intejer. Значение переменной будет храниться в куче, а ссылка на нее в Stack
        printAll(o, i, ii);             // 4 Вызов метода printAll(), в Stack выделиться память для выполнения этого метода
        System.out.println("finished"); // 7 В куче создается объект типа String и передается методу println. 
                                             Работа метода Main завершена. Сборщик мусора освободит потраченную в Stack память
    

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5 в Stack создается переменная типа Integer, значение переменной будет храниться в куче
        System.out.println(o.toString() + i + ii);  // 6 В куче создается объект типа String и передается методу println. 
                                                         По завершении работы метода println сборщик мусора освободит потраченную в Stack память
    }
}
