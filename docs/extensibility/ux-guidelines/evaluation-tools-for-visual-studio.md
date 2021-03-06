---
title: Средств оценки для Visual Studio | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94e0e9a3-440c-4943-ad7b-772ed742e034
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a149d9163e61dd49105f123b373ecd9c7c1c278
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="evaluation-tools-for-visual-studio"></a>Средств оценки для Visual Studio
## <a name="craftsmanship-checklist-for-visual-studio"></a>Контрольный список мастерства для Visual Studio  
 Используйте этот контрольный список для оценки качества взаимодействие пользователя подробности визуального элемента и взаимодействия.  
  
### <a name="overview"></a>Обзор  
  
-   Убедитесь, что все команды приведет к обратной связи со сведениями о том, команды была выполнена.  
  
-   Убедитесь, что все элементы пользовательского интерфейса и элементов управления отображаются во всех темах и в режиме высокой контрастности.  
  
-   Убедитесь, что активным и неактивным выбора всегда отличаются, как стандартные и режим высокой контрастности.  
  
-   Убедитесь, что фокус всегда является видимым и очевидным.  
  
### <a name="performance"></a>Производительность  
  
-   Некоторые индикатор вида «занят» проверьте, отображается ли Если команда имеет более чем одну секунду.  
  
-   Убедитесь, что если команды занимает более 10 секунд для выполнения явного индикатор, либо определенный (предпочтительно) или не определен, отображается.  
  
### <a name="ui-text"></a>Текст пользовательского интерфейса  
  
-   Убедитесь, все метки предложения или заглавные буквы и что текст не является полностью нижний регистр.  
  
    ||Правильно|Неверный|  
    |-|-------------|---------------|  
    |**Текст команды (все)**|Регистр предложения:<br /><br /> **Имя каталога:**|Имя каталога:|  
    |**Текст кнопки (клиент)**|Заглавные:<br /><br /> **[Установить по умолчанию]**|ПО УМОЛЧАНИЮ НАБОР AS|  
    |**Текст кнопки (в сети)**|Регистр предложения:<br /><br /> **[Набор символов по умолчанию]**||  
  
-   Убедитесь, что все метки, за исключением заголовков групп и кнопок, заканчиваться точкой с запятой и предшествовать с которым связан элемент управления.  
  
-   Проверьте, кнопки, команды и ссылки на команды, запустить пользовательский Интерфейс для записи введенных данных оканчиваться на многоточие **[...]** .  
  
     Примеры  
  
    -   **[Дополнительно]**  кнопку в диалоговом окне.  
  
    -   Параметры команды в меню «Инструменты» (**Сервис > Параметры**) не следует получить многоточие, так как запуска самого диалогового окна есть необходимость команды.  
  
-   Убедитесь, что пользовательский Интерфейс содержит без сокращений, за исключением стандартных терминов. Например HTML ни TCP/IP необходимо уточнять, хотя нехватки памяти (недостаточно памяти) и PII (персональные данные) должны.  
  
### <a name="keyboard-access"></a>Доступ с клавиатуры  
  
-   Убедитесь, что способ для выполнения каждой задачи с помощью клавиатуры. Обычно это выполняется через доступ с клавиатуры для каждого элемента управления, но для некоторых наглядные областей допустима обходной путь, например, перейдите в представление кода.  
  
-   Убедитесь, что нажатии клавиши Tab между элементами управления в логическом порядке (слева направо и сверху вниз). Хотя это рекомендуется для большинства элементов управления, не все элементы управления требуют этого подхода. Например можно проверьте этого переключателя, элементы управления находятся в группе с одной позиции табуляции.  
  
-   Убедитесь, что все элементы управления имеют метки, а каждая метка имеет назначенный (исключения включают некоторые элементы управления не с меткой, которые может выполнить с меткой элемента управления на вкладке).  
  
-   Убедитесь, что нет назначенной конфликтов.  
  
### <a name="fonts"></a>Шрифты  
  
-   Убедитесь, что все шрифты (начертания, размера, цвета) используются постоянно и поддержания иерархии.  
  
-   Убедитесь, что все элементы пользовательского интерфейса используют службу шрифт среды. (См. [шрифты и форматирование для Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md))  
  
     Чтобы проверить, если служба используется, перейдите к **Сервис > Параметры > шрифты и цвета**. В раскрывающемся списке параметров выберите шрифт среды разработки и изменить начертание шрифта stylistically (например Шашков или комикс сетей SAN) и задайте размер 12 пт. Затем нажмите кнопку «ОК». Может потребоваться перезапустить IDE, но большая часть пользовательского интерфейса будет немедленно изменить. Области, которые не обнаружат изменение шрифта даже при перезапуске не используется шрифт среды разработки.  
  
-   Убедитесь, что шрифты, которые являются класс, наследуемый от службы (например, увеличенный или полужирным шрифтом) сохраните их размер и формат относительно текста «normal», когда изменяется размер шрифта среды.  
  
-   Убедитесь, что нет отсечения ошибок из-за увеличенную шрифты. Шрифты, получить обрезается скорее всего, в результате фиксированной высоты элементов управления или контейнеры фиксированную высоту.  
  
### <a name="dialogs"></a>Диалоговые окна  
  
-   Убедитесь, что заголовок диалогового окна таким же, как команды, в которой она была запущена.  
  
-   Убедитесь, что все стандартные элементы управления соответствуют операционной системы: цвет фона является стандартным и элементы управления не должны иметь специальные шаблонного re стиль, который делает их отличаться от стандартных элементов управления.  
  
-   Убедитесь, что поля в форме должен составлять 12 пикселей и должны отображаться в единую.  
  
-   Убедитесь, что диалоговые окна отображаются по центру в среду IDE или окне, которое порождается их.  
  
-   При полезны, диалоговые окна должен быть изменяемым размером. Для диалоговых окон, которые можно изменять убедитесь, что после изменения размера, соответствующие элементы управления необходимо изменить размеры во время остаются постоянными другие части диалогового окна.  
  
-   Проверьте, сохранение с раскрывающимися списками диалоговые окна любого размера скорректированы пользователя (размер, расположение, расширения элементов управления диалоговых окон и т. д.).  
  
-   Убедитесь, что нет значка в строке заголовка.  
  
-   Убедитесь, что нет кнопок свертывания и развертывания в строке заголовка.  
  
#### <a name="dialog-operation-buttons-vs-client-only"></a>Диалоговое окно кнопок операций (только клиент VS)  
  
-   Убедитесь, что кнопок операций в следующем порядке: **ОК**, **отменить**, **применить**.  
  
-   Убедитесь, что **ОК** и **отменить** находятся стандартный размер кнопки: 75 x 23 пикселей.  
  
-   Убедитесь, что **ОК** и **отменить** кнопки будут одинакового размера, независимо от длины строки.  
  
-   Если метка на кнопку операция требует кнопка будет больше, чем стандартные, убедитесь, что соответствующие **отменить** кнопка является одинакового размера.  
  
-   Убедитесь, что отступ 6 пикселей между кнопками и связанные элементы управления.  
  
-   Убедитесь, что **ОК** и **отменить** кнопки не имеют клавиш доступа определяется подчеркнутой буквой.  
  
-   Убедитесь, что одну кнопку (обычно **ОК**) по умолчанию имеет фокус.  
  
-   Убедитесь, что **Esc** отменяет диалогового окна  
  
-   Убедитесь, что **ввод** выполняет кнопку по умолчанию, если фокус находится не на элемент управления, который обрабатывает ввод.  
  
-   Убедитесь, что **ОК** и **отменить** кнопки располагаются в правом нижнем углу диалогового окна. В редких исключений является допустимым вертикально в правом верхнем углу.  
  
-   Убедитесь, что вертикальная конфигурация используется только в том случае, если другие кнопки находятся в горизонтальное выравнивание в диалоговом окне.  
  
### <a name="control-standards"></a>Стандартный элемент управления  
  
#### <a name="general"></a>Общие  
  
-   Убедитесь, что, если это возможно, хорошо по умолчанию значения для ускорения взаимодействия с пользователем и предоставить пользователям сторону безопасным или общий результат.  
  
-   Убедитесь, что стандартные элементы управления ведут себя так же, чтобы пользователи знали, что будет происходить на основе опыта предыдущих.  
  
#### <a name="label-controls"></a>Элементы управления Label  
  
-   Убедитесь, что каждый элемент управления имеет метку и что каждая метка визуально связан с его элемента управления (обычно в пределах диапазона пикселей 4 – 6) и ближе к его соответствующий контроль, чем для других элементов управления.  
  
-   Убедитесь, что метки располагаются очистить левого края, если разместить над слева с элементом управления и по центру горизонтально, чтобы базовой линии метки выравнивается с базовым планом входного текста, если располагается слева.  
  
-   Убедитесь, что если несколько с накоплением метки и элементы управления для ввода располагаются слева от элемента управления, метки сдвиг влево и одинаковом расстоянии от границы окна, никогда не диск справа и одинаковом расстоянии от элементов управления. Пары равномерно распределить Если необходимы дополнительные интервалы для указания группирования.  
  
#### <a name="input-controls-text-boxes-and-combo-boxes"></a>Элементы управления для ввода (текстовые поля и поля со списком)  
  
-   Убедитесь, что при использовании шрифта среды по умолчанию, отображаемой высоты текстовые поля, раскрывающиеся списки и кнопки всех 23 пикселя.  
  
-   Если используется текст подсказки, убедитесь, что цвет `Environment.ControlEditHintText` с помощью службы цвета.  
  
-   Если поле является обязательное поле, которое должно быть идентифицировано таким образом, проверьте:  
  
    -   которому присвоены фон `Environment.ControlEditRequiredBackground` и переднего плана `Environment.ControlEditRequiredHintText`  
  
    -   Это пояснительный текст в элементе управления, который отображается в виде **»\<необходимые >»**  
  
#### <a name="button-controls"></a>Элементы управления "Кнопка"  
  
-   Убедитесь, что кнопки минимальный размер 75 x 23 пикселя, если не позволяет более длинный текст.  
  
-   Убедитесь, что кнопки покинувших и правой поля 3-5 пикселей, а также заполнение для содержимого.  
  
-   Можно использовать небольшое квадратную кнопку с многоточием только **[...]**  на его вместо **[Обзор...]**  кнопки (или аналогичные функциональные возможности). При использовании убедитесь, что кнопки — 23 x 23, размер.  
  
-   Если имеется более одного **[Обзор...]**  в диалоговом окне, а затем убедитесь, что укороченная версия (только с многоточием **[...]** ) используется для всех.  
  
-   Убедитесь, что многоточие **[...]**  кнопки имеют назначенный. Когда фокус установлен на элемент управления рядом с ней, одна вкладка следует переместить фокус на кнопку с многоточием.  
  
-   Убедитесь, что кнопки, команды и ссылки на команды, запустите дополнительного пользовательского интерфейса, которое собирает дополнительные входные данные пользователя должны оканчиваться на многоточие **[...]** .  
  
#### <a name="hyperlinks"></a>Гиперссылки  
  
-   Убедитесь, что элемент управления гиперссылки никогда не мигает красный цвет, когда активны. Это является признаком цвет служба не выполняется использования  
  
-   Убедитесь, что используемые цвета VS:  
  
    -   `Environment.ControlLinkText`  
  
    -   `Environment.ControlLinkTextHover`  
  
    -   `Environment.ControlLinkTextPressed`  
  
-   Убедитесь, что гиперссылки отображаются синим не линией, если встроен в абзаце.  
  
#### <a name="check-boxes"></a>Флажки  
  
-   Если флажок имеет многострочный текст, проверьте, поле ли с первой строки текста, не вертикально по центру по всем строкам.  
  
-   Убедитесь, что флажки всегда указывать двоичных значений и не перенаправлен пользователь или откройте новое окно или страницы.  
  
-   Если флажок представляет параметр, связанные с элементом управления вводом, убедитесь, что он расположен непосредственно слева и очень близко под этим элементом управления, чтобы указать его связь.  
  
-   Убедитесь, что установлен флажок **никогда не** использоваться в качестве средства, чтобы включить все содержимое диалогового окна или страницы.  
  
#### <a name="group-boxes"></a>Группы  
  
-   Убедитесь, что диалоговое окно содержит внутри одной группы полем, содержащим все содержимое диалогового окна.  
  
-   Убедитесь, что по крайней мере два элемента управления в каждой группы.  
  
-   Редко должно быть более две группы в диалоговом окне.  
  
-   Убедитесь, что нет вложенных групп.  
  
### <a name="icons"></a>Значки  
  
-   Убедитесь, что значки отображаются правильно инвертированный в "темной" теме.  
  
-   Убедитесь, что все значки основаны на основные понятия.  
  
-   Убедитесь, что каждый значок distinct, легко распознавать и не содержит более двух основных понятиях (без модификатора состояния и язык).  
  
-   Убедитесь, что базовый значок отображается по центру в пространстве.  
  
-   Убедитесь, что все значки отображаются правильно в режиме высокой контрастности.  
  
-   Проверьте, цвет, используемый ли стандартам использование цвета.  
  
-   Убедитесь, что не ореола (границ) вокруг значков. (Если он имеется, гало должен соответствовать цвет фона соседних элементов пользовательского интерфейса).  
  
### <a name="touch-enabled-ui"></a>Сенсорные пользовательского интерфейса  
  
-   Убедитесь, что интерактивных элементов управления достаточно велик, чтобы быть легко физические - минимальный **пикселей 23 x 23** размер  
  
-   Убедитесь, что наиболее часто используемые элементы управления по крайней мере **40 x 40 пикселей** в размере.  
  
-   Убедитесь, что интерактивных элементов управления есть по крайней мере **5 точек интервала** между ними