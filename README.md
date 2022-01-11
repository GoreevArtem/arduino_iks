## Проект Arduino + C#

- Сидягин Костя
- Гореев Артем
- Иван Морозов
- Докукин Данил
- Андрей Бобочков
- Маша Божко
- Катя Вахутина
- Ксения Сторожева
- Бурученко Иван

---
### ТЗ

написать ПАК состоящий из  softwarte (PC): язык С#  hardware (Arduino): язык C (любые библиотеки в том числе ардуино допустимы)
связь осуществляется по com порту.
на си в hardware написана структура в следующем формате

struct <имя> {
    <тип1> <поле1>; //<Комменты>
    <тип2> <поле2>;
                   //<Комменты>
    ...
    <типN> <полеN>;
};

Это структура для hardware и язык разметки для softwarte 
для softwarte 1 строка исходника соответствует 1й комманде


поддерживаются только типы: 
unsigned char
signed char
unsigned int
signed int
float

комментарий может быть отдельной строкой без переменной.
<Комменты> имеют вид <параметр>:<зн ач ен ие> <параметр2>:<зна че ни е 2> 
значение может содержать пробелы.

параметры:
min миимальное значение поля
max максимальное, 
def дефолтное 
type тип поля в по softwarte 
name имя поля в по softwarte 
timer комманда обновления поля раз в  n секунд (если фокуса на нем нет ес-но, обеспечивать сброс фокуса при неактивности 3 секунды)


Если какого либо значения нет то оно ставится исходя из ограничений типа данных, умолчание ставится нулем, тип ставится textbox, name именем 

переменной если нет переменной то пустая строка.

пример записи: min:0 max:200 def:100 name: поле первое


дополнительно в комментах указывается тип поля type:F  type:S type:H    F дефолт если не указано
поле textbox F, слайдбар горизонтальный ес-но S, Чекбокс H, Заголовок Z (без контрола и может быть пустой строкой), Кнопка B (для нее обязательна 

строка для оправки cmd: sendsting), информация (read-only) V это label в softwarte
задача написать по которое на компе при компляции читало структуру разметки из исходника и строило поля в форме при компиляции динамически, далее

обменнивалось с аппаратной частью данными.
аппаратная часть может принимать 1 поле данных, отправлять 1 поле, отправлять все поля (при открытии пО компа)
написать прерывания uart обмена данными со структурой.
обеспечить контрольные суммы при обмене информацией и эхо запись с последующим чтением со стороны softwarte для подтверждения правильности записи.
[Протокол](https://github.com/PhpGuys/arduino_iks/blob/main/hardware/sketch_nov17a/protocol.pdf)

