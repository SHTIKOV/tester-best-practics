# Как правильно подкатывать к программисту для чайников
Небольшое собрание лучших практик о том, как правильно подходить с проблемой в работе кода к программисту.

## Содержание:
- [Введение](https://github.com/SHTIKOV/tester-best-practics#%D0%B2%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5)
- [Предварительные ласки (Изучение ТЗ)](https://github.com/SHTIKOV/tester-best-practics#%D0%B2%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D0%B5)
- [Путь к войну (Точность воспроизведения ошибки)](https://github.com/SHTIKOV/tester-best-practics#%D0%BF%D1%83%D1%82%D1%8C-%D0%BA-%D0%B2%D0%BE%D0%B9%D0%BD%D1%83)
- [Горячая картошка (Выяснение чья проблема - Клиент или Сервер)](https://github.com/SHTIKOV/tester-best-practics#%D0%B3%D0%BE%D1%80%D1%8F%D1%87%D0%B0%D1%8F-%D0%BA%D0%B0%D1%80%D1%82%D0%BE%D1%88%D0%BA%D0%B0)
- [Кульминация (Шаблон сбора информации для обращения)](https://github.com/SHTIKOV/tester-best-practics#%D0%BA%D1%83%D0%BB%D1%8C%D0%BC%D0%B8%D0%BD%D0%B0%D1%86%D0%B8%D1%8F)
- [Самое важное (Обязательная информация)](https://github.com/SHTIKOV/tester-best-practics#%D1%81%D0%B0%D0%BC%D0%BE%D0%B5-%D0%B2%D0%B0%D0%B6%D0%BD%D0%BE%D0%B5)

## Введение
Для того, что бы программисту было проще и быстрее разобраться в проблеме, необходимо создать полный пул данных, которые возможно получить используя все инструменты тестировщика. 

## Предварительные ласки
Прежде чем задавать программисту вопросы о том, "Почему оно не работает?", необходимо изучить работу функционала, как его задумывал заказчик функционала, самое простое - прочитать, хотя бы один раз, техническое задание (**ТЗ**) к функционалу и изучить структуру данных, если что-то не понятно. После того, как ТЗ было полностью изучено, нужно сверить логику работы ТЗ и того, что произошло в найденой Вами ошибке. 

Так же, если есть какие-либо настройки к этому функционалу, **ОБЯЗАТЕЛЬНО** нужно посмотреть что установлено и **учитывать** их в сравнении логики работы.

## Путь к войну
Если все учтено, а именно: логика работы функционала и его настройки, то необходимо убедиться, что проблема стабильная и повторяется довольно часто. Для этого необходимо вспомнить все свои действия, которые были сделаны перед выпадением ошибки и попытаться ее воспроизвести. После того, как мы убедились, что проблема воспроизводится  очень часто, очень важно разобраться, "Чья вина этой недоработки?", клиента или сервера?

## Горячая картошка
Очень важно на этапе обнаружения проблемы понять на чьей стороне проблема, клиент или сервер. Для этого нам понадобится программа, которой мы можем доверять (доверять в плане точности данных), называется [Fiddler](https://www.telerik.com/fiddler), только через нее (и ее аналоги) можно понять какими данными общается клиент-сервер, иначе если смотреть по логам клиента, то тут нужно учитывать, что клиентщик так же может сделать ошибку в своем коде и показать неверные данные.
Изучив логику работы функционала, узнав структуру данных и используя замечательный [Fiddler](https://www.telerik.com/fiddler), мы можем определить кто виноват, если данные не такие, какие должны быть по логике работы - то это виновен **Сервер**, если с сервера приходит верная информация, но на клиенте выводится что-то непонятно - то виновен **Клиент**, в редких случаях бывает, что не понятно кто из них отработал неверно, в таком случае нужно подключить обе стороны к этому вопросу.

`Примечание`: В [Fiddler](https://www.telerik.com/fiddler) не всегда можно увидеть что конкретно отправляет клиент серверу, в таком случае, если это важно для понимания вашей проблемы, пообщаться с клиентским программистом, что бы он мог показать, где возможно увидеть эту информацию.

## Кульминация
После того, как мы узнали суть проблемы и учли настройки, разобрались с помощью [Fiddler](https://www.telerik.com/fiddler) кто прав, а кто виноват, все это мы зафиксировали в один пул обращения, а именно:
##### Шаблон данных об ошибке
1. Фиксация ошибки
2. Действия, которые ты делал для его появления (Стектрейс)
3. Данные, которые вернул тебе **сервер** (Обязательно через [Fiddler](https://www.telerik.com/fiddler))
4. Данные, которые использует сервер (настройки и тп.) *Если виновен **сервер***

## Самое важное!
Самое важное в задаче - это **РАЗОБРАТЬСЯ КАК ОНА УСТРОЕНА**, что бы можно было адекватно оценивать ее работу, если ты не разобрался как она устроена, то сложно будет понимать к кому обращаться с этой проблемой и вообще проблема ли это. Если по какой то причине не смогли в этом разобраться - вам помогут программисты, которые это реализовывали. Очень важно при этом использовать правильные формулировки и термины.
