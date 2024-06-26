**Итоговая работа по модулю "Анализ требований"**
=
***Контекст*** 
 
Вы — аналитик команды, которая разрабатывает программное обеспечение для автомата, печатающего фото из Instagram.  
На встрече с представителем заказчика выяснили, что автомат должен работать следующим образом:

1.  При нажатии на кнопку «Выбрать фото для печати» на главном экране пользователю предложены 2 способа — выбрать фото в Instagram или загрузить фото с телефона.
2.  Для выбора фото из Instagram пользователю необходимо указать свой логин. Профиль пользователя должен быть открытым.
3.  Для выбора фото с телефона, пользователю нужно соединить телефон с автоматом для печати фото через кабель для зарядки.
4.  Пользователь может выбрать количество фотографий для печати через экран автомата. Минимальное количество фото — 1, максимальное —100 (если в автомате достаточно бумаги).
5.  Оплатить печать фото можно только по карте через физический терминал бесконтактной оплаты.
6.  Печать фото запускается после успешной оплаты выбранного пакета фотографий.
7.  Если пользователь вводил логин Instagram для печати фотографий, то после завершения печати его страница в автомате должна быть закрыта.
8.  Если пользователь присоединял телефон для печати фотографий, то после завершения печати автомат будет сигнализировать о необходимости забрать телефон.
   
   **Задание 1**
-
   *Напишите минимум 5 формализованных требований к разрабатываемому программному обеспечению (желательно разных типов, но на ваше усмотрение).*

\
***Требования функционального характера***

Бт-001 Необходимо разработать программное обеспечение для автомата, печатающего фото из Instagram.

Пт-001 Пользователь должен иметь возможность выбрать количество фотографий для печати.\
Пт-002 Пользователь должен иметь возможность распечатать фото из Instagram.\
Пт-003 Пользователь должен иметь возможность распечатать фото с телефона.\
Пт-004 Пользователь должен иметь возможность оплатить фото.

Фт-001 Система должна предложить 2 способа печати фото - фото из Instagram или фото с телефона.\
Фт-002 Система должна запустить печать фото после успешной оплаты выбранного пакета фотографий.\
Фт-003 Система должна печатать фото в соответствии с заданным количеством фотографий.\
Фт-004 Система должна выводить сообщение на экран при недостаточном количестве бумаги.\
Фт-005 Система должна выводить сообщение на экран о необходимости забрать телефон. Если пользователь присоединял телефон для печати фотографий.


***Требования нефункционального характера***

Нфт-001 Система должна быть подключена к сети internrt.\
Нфт-002 Система должна иметь физический терминал бесконтактной оплаты.

О-001 Печать фото - минимальное количество фото — 1, максимальное —100.

<br>

   **Задание 2**
-
   *Подготовьте диаграмму вариантов использования, покрывающую описанные в контексте действия*
   
\
![диаграмма ВИ](<диаграмма ВИ итоговая работа.png>)

```
@startuml

:Пользователь:

rectangle {
:Система:
(Выбрать количество фото)
(Оплатить печать)
(ввести логин Instagram)
(закрыть страницу в Instagram)
(присоединить телефон)
(сигнал о необходимости забрать телефон)
(Выбрать источник фото)
(Напечатать фото)
(Печать с телефона)
(Печать из Instagram)
}

:Система: -up- (сигнал о необходимости забрать телефон)
:Система: -up- (закрыть страницу в Instagram)
:Пользователь: -down- (Напечатать фото)
(Напечатать фото).down.> (Выбрать источник фото) : include
(Печать из Instagram)<.down.(ввести логин Instagram) : exclude
(Выбрать источник фото)<.(Печать с телефона) : exclude
(Печать с телефона)<.(присоединить телефон) : exclude
(Выбрать источник фото)<.down.(Печать из Instagram) : exclude
(Оплатить печать) <. (Напечатать фото) : include
(Выбрать количество фото) <. (Напечатать фото) : include
(Напечатать фото) <. (сигнал о необходимости забрать телефон) : exclude
(Напечатать фото) <. (закрыть страницу в Instagram) : exclude

@enduml
```



<br>

**Задание 3**
-
   *Подготовьте текстовое описание любого варианта использования из получившейся на шаге 2 диаграммы.*

\
**BИ-1.** Распечатать фото в аппарате

**Краткое описание:** Потенциальный пользователь распечатывает фото в аппарате, выбирая количество фото, источник фото и оплачивая данный заказ.

**Действующие лица:** Пользователь, Система

**Триггер:** Пользователь выбирает распечатать фото с телефона

**Предусловия:**\
·  Покупатель активировал экран автомата\
·  Система отразила на главном экране пользователю 2 способа печати — выбрать фото в Instagram или загрузить фото с телефона

**Потоки**

***Основной поток***

1. Пользователь подключает телефон через кабель для зарядки.
2. Система предлагает пользователю выбрать количество фото от 1 до 100 штук.
3. Пользователь выбирает количество фото.
4. **Если** в автомате достаточно бумаги, то управление переходит на следующий шаг.
5. Покупатель оплачивает печать фото картой через физический терминал бесконтактной оплаты.
6. **Если** оплата прошла успешно, то система запускает печать выбранного пакета фотографий.
7. Пользователь забирает распечатанный пакет фотографий.
8. По завершении печати система сигнализирует (выводит на экран сообщение) о необходимости забрать телефон.
9. Пользователь отключает телефон от аппарата.
10. Вариант использования завершает свою работу.

\
 ***Альтернативный поток***

**4а.** В автомате недостаточно бумаги в указанном количестве.\
·  Система отображает уведомление о актуальном количестве бумаги.\
·  Управление переходит на шаг 2.

\
***Поток исключения***

**4а.** В автомате закончилась бумага.\
·  Система отображает уведомление о отсутствии бумаги в автомате.\
·  Управление переходит на шаг 8.

**6а**. Оплата выбранного пакета фотографий не прошла.\
• Система отображает уведомление о не успешности платежа.\
• Управление переходит на шаг 8.

\
**Постусловие.** В случае успешного выполнения основного потока, пользователь распечатывает фото.

\
**Результат.** Если ВИ выполнен успешно, то выбранный пакета фотографий распечатан.