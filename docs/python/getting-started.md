---
title: "Начало работы с Python в Visual Studio | Документация Майкрософт"
ms.custom: 
ms.date: 5/1/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a9087b19-275b-4cc1-8d0c-f9c4356c9ce8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: 8001036077b8b14af80fabceafad5d3aff9b25f4
ms.contentlocale: ru-ru
ms.lasthandoff: 05/09/2017

---

# <a name="getting-started-with-python-in-visual-studio"></a>Начало работы с Python в Visual Studio

Если у вас установлена среда Visual Studio с рабочей нагрузкой Python (Visual Studio 2017) или с Инструментами Python для Visual Studio (Visual Studio 2015 и более ранние версии), вы можете приступить к изучению возможностей разработки на Python. (При необходимости используйте раздел [Установка](installation.md).)

В этом пошаговом руководстве мы создадим пустое приложение Python, выберем среду Python для работы и напишем несколько строк кода, чтобы увидеть технологию IntelliSense в работе. Мы также поработаем с интерактивным окном REPL, чтобы создать код, а затем завершим работу программы и запустим ее саму по себе и в отладчике.

> [!Note]
> В этом пошаговом руководстве рассматриваются возможности Python в Visual Studio 2017. Другие версии будут отличаться только в деталях.

## <a name="create-a-new-python-project"></a>Создание нового проекта Python

Поддержка Python в Visual Studio включает в себя ряд [шаблонов проектов](python-projects.md), позволяющих приступить к работе с различными типами проектов, включая веб-приложения, на платформах Bottle, Flask и Django, а также на базе облачных служб Azure. Однако для целей данного пошагового руководства мы начнем с пустого проекта.

1. В Visual Studio выберите **Файл > Создать проект**, после чего откроется диалоговое окно **Создание проекта**. Здесь можно выбрать шаблон и указать папку, в которой нужно создать проект.

1. Чтобы перейти к шаблонам Python, выберите **Шаблоны > Другие языки > Python** в области слева или просто выполните поиск по слову "Python".

    ![Диалоговое окно создания проекта с показанными проектами Python](~/python/media/getting-started-new-project.png)

1. Выберите шаблон Python Application (Приложение Python), укажите папку для проекта и нажмите кнопку **ОК**. (Если вы хотите создать локальный репозиторий для вашего проекта прямо сейчас, также установите флажок **Добавить в систему управления версиями**.)

    > [!Tip]
    > Шаблон From existing Python Code (Из существующего кода Python) позволяет быстро создать проект Visual Studio из папки, которая уже содержит код Python, вместо того чтобы создавать новый пустой проект и импортировать в него существующий код.

1. Через несколько секунд проект откроется в окне обозревателя решений Visual Studio. Здесь можно просматривать файлы и папки в проекте, а также управлять средами.

    ![Обозреватель решений с проектом Python](~/python/media/getting-started-solution-explorer-1.png)

1. Разверните узел **Python Environments** (Среды Python), и вы увидите интерпретатор Python, используемый по умолчанию для этого проекта. Развернув узел этого интерпретатора, вы увидите список библиотек, доступных в этой среде.

    ![Обозреватель решений, где показана среда Python](~/python/media/getting-started-solution-explorer-2.png)

1. Если вы используете Visual Studio 2015 или более раннюю версию, интерпретатор Python не будет установлен по умолчанию. См. инструкции в разделе [Выбор и установка интерпретаторов Python](python-environments.md#selecting-and-installing-python-interpreters).

### <a name="going-deeper"></a>Дополнительные сведения

- [Проекты Python в Visual Studio](python-projects.md)
- [Шаблоны веб-проектов](template-web.md)
- [Шаблоны веб-проектов Django](template-django.md)
- [Шаблон облачной службы Azure](template-azure-cloud-service.md)

## <a name="writing-and-running-code"></a>Написание и выполнение кода

1. После создания нового проекта Python Application (Приложение Python) в редакторе Visual Studio откроется пустой файл по умолчанию с именем `PythonApplication1.py`. Чтобы переименовать его, щелкните его правой кнопкой мыши в обозревателе решений, выберите **Переименовать** и измените имя на `hello.py`.

1. Начните вводить `print("Hello world")`. По мере ввода функция IntelliSense в Visual Studio покажет варианты автозавершения. Выделенный параметр в раскрывающемся списке — это вариант завершения по умолчанию, который применяется при нажатии клавиши TAB. Это очень полезно при использовании длинных инструкций или идентификаторов.

    ![Всплывающее окно автозавершения IntelliSense](~/python/media/getting-started-coding-1.png)

1. Функция IntelliSense отображает различные сведения в зависимости от используемой инструкции, вызываемой функции и т. д. Если после функции `print` ввести `(` для вызова, отобразятся полные сведения об использовании этой функции с выделением текущего аргумента, который необходимо ввести (**value**, как показано ниже).

    ![Всплывающее окно автозавершения IntelliSense для функции](~/python/media/getting-started-coding-2.png)

1. Завершите инструкцию следующим образом:

  ```python
  print("Hello world")
  ```

1. Чтобы запустить код, нажмите кнопку **Запуск** на панели инструментов, как показано ниже, нажмите клавишу F5 или выберите пункт меню **Отладка > Начать отладку**.

    ![Кнопка "Запуск" на панели инструментов отладки](~/python/media/getting-started-coding-3.png)

    > [!Note]
    > Если в Visual Studio 2015 или более ранней версии отображается сообщение об отсутствии интерпретаторов, [выберите и установите интерпретатор Python](python-environments.md#selecting-and-installing-python-interpreters), так как он не установлен по умолчанию.

1. Visual Studio запустит код, используя среду по умолчанию в проекте, и выведет результаты в окне командной строки. Нажмите клавишу, чтобы закрыть это окно и завершить сеанс отладки.

    ![Кнопка "Запуск" на панели инструментов отладки](~/python/media/getting-started-coding-4.png)

1. Помимо инструкций и функций, IntelliSense выводит варианты для завершения инструкций `import`. Благодаря этому вы можете легко обнаружить, какие модули доступны в вашей среде и какие элементы доступны в определенном модуле. В редакторе удалите строку `print` и начните вводить `import`. Отобразится список модулей:

    ![Функция IntellSense отображает доступные модули для инструкции import](~/python/media/getting-started-coding-5.png)

1. Завершите строку, введя или выбрав `sys`.

1. В следующей строке введите `from`, чтобы снова вывести список модулей:

    ![Функция IntellSense отображает доступные модули для инструкции](~/python/media/getting-started-coding-6.png)

1. Выберите или введите `math`, а затем пробел и `import`, чтобы отобразился список элементов модуля:

    ![IntellSense отображает элементы модуля](~/python/media/getting-started-coding-7.png)

1. Затем импортируйте элементы `sin`, `cos` и `radians`. Обратите внимание, как для каждого из них будут выводиться варианты автозавершения. По завершении код должен выглядеть следующим образом:

  ```python
  import sys  
  from math import sin, cos, radians          
  ```

> [!Tip]
> Принцип функции завершения заключается в следующем — по мере ввода появляются подстроки со словами, в которых совпадают части или буквы в начале слова, и даже отображаются пропущенные символы. Дополнительные сведения см. в статье "Редактирование кода" в разделе [Завершения](code-editing.md#completions).

В следующем разделе мы напишем код, используя интерактивное окно REPL, чтобы сразу же протестировать его без запуска отладчика.

### <a name="going-deeper"></a>Дополнительные сведения

- [Редактирование кода](code-editing.md)
- [Форматирование кода](code-formatting.md)
- [Оптимизация кода](code-refactoring.md)
- [Использование PyLint](code-pylint.md)


## <a name="using-the-interactive-repl-window"></a>Использование интерактивного окна REPL

Интерактивное окно Visual Studio для Python предоставляет цикл "чтение — оценка — вывод" (REPL), который значительно сокращает обычный цикл "редактирование — сборка — отладка". Это тот же цикл, который используется в командной строке Python, но с некоторыми дополнительными возможностями.

1. Откройте интерактивное окно, выбрав **Просмотр > Другие окна > Python Interactive Windows** (Интерактивные окна Python) в главном меню Visual Studio. Откроется окно с обычной командной строкой Python REPL, начинающейся с >>>. Обратите внимание, что вы в любой момент можете изменить среду с помощью раскрывающегося меню на панели инструментов.

    ![Интерактивное окно Python](~/python/media/getting-started-interactive-1.png)

1. Введите несколько инструкций (например, `print("hello")`) и выражений (например, `123/567`), чтобы сразу увидеть результаты:

    ![Мгновенные результаты в интерактивном окне Python](~/python/media/getting-started-interactive-2.png)

1. Когда вы начнете вводить многострочную инструкцию, например определение функции, интерактивное окно отобразит командную строку с ... для продолжения строк, которая, в отличие от командной строки REPL, имеет автоматический отступ:

    ![Интерактивное окно Python с продолжением инструкции](~/python/media/getting-started-interactive-3.png)

1. Все элементы, вводимые в интерактивном окне, записываются в журнал. В нем также сохраняются многострочные элементы в отличие от командной строки REPL. Например, вместо того чтобы повторно создавать функцию по одной строке, можно просто отозвать все определение функции `f` выше как единое целое и изменить имя на `make_double`.

1. Еще одна очень удобная функция — возможность быстро отправить несколько строк кода из окна редактора в интерактивное окно, где можно работать с ним в среде мгновенных результатов REPL, вместо написания другого кода и выполнения его в отладчике. Чтобы испробовать эту возможность, добавьте следующий код в файл hello.py, открытый в редакторе:

  ```python
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'
  ```

1. Выделите весь код в файле hello.py (включая инструкции `import`), щелкните правой кнопкой мыши и выберите пункт **Отправить в Interactive** (CTRL+ВВОД). Код будет вставлен прямо в интерактивное окно, и начнется его выполнение. Так как код определяет функцию, можно быстро проверить эту функцию, вызвав ее несколько раз:

    ![Отправка кода в интерактивное окно](~/python/media/getting-started-interactive-4.png)

1. Команда **Отправить в Interactive** позволяет вставить в интерактивное окно несколько строк кода (например, код, который вы нашли в Интернете), чего нельзя сделать напрямую. Например, скопируйте приведенный ниже код и попробуйте вставить его (CTRL+V) в интерактивное окно. Вы увидите, что ничего не происходит. Тем не менее его можно вставить в редактор, выбрать и использовать команду **Отправить в Interactive**, чтобы увидеть, как он выполняется.

  ```python
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

    ![Вставка нескольких строк кода с помощью команды отправки в интерактивное окно](~/python/media/getting-started-interactive-5.png)

1. Определение функции хранится в журнале REPL как единое целое, поэтому можно легко вернуться и внести изменения, а затем еще раз проверить функцию.

1. Когда код будет готов, можно выбрать его в интерактивном окне, щелкнуть правой кнопкой мыши и выбрать пункт **Копировать код**, а затем вставить в редактор. Команда **Копировать код** автоматически пропускает выходные данные, а также символы ">>>" и "...". Например, если выделить код, как показано ниже, и выбрать эту команду:

  ![Интерактивное окно с командой "Копировать код"](~/python/media/getting-started-interactive-6.png)

  Будет вставлено следующее:

  ```python
  make_dot_string(180)
  make_dot_string(135)
  for i in range(360):
      s = make_dot_string(i)  
      print(s) 
  ```

1. Наконец, интерактивное окно предоставляет ряд метакоманд, которые позволяют загружать файлы, сбрасывать среду без потери журнала и вставлять комментарии по мере работы. Описание метакоманд см. статье "Работа с интерактивным окном Python" в разделе [Использование интерактивного окна](interactive-repl.md#meta-commands).

### <a name="going-deeper"></a>Дополнительные сведения

- [Работа с интерактивным окном Python](interactive-repl.md)
- [Использование IPython REPL](interactive-repl-ipython.md)

## <a name="running-code-in-the-debugger"></a>Выполнение кода в отладчике

Помимо возможности управления проектами, расширенных возможностей редактирования и интерактивного окна, Visual Studio предоставляет полнофункциональную поддержку отладки для кода Python.

1. Измените код в файле hello.py, чтобы он выглядел следующим образом:

  ```python  
  from math import sin, cos, radians  
  import sys  
    
  def make_dot_string(x):  
      return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
    
  def main():  
      for i in range(360 * 5):
          s = make_dot_string(i)  
          print(s)  
            
  main()
  ```  

1. Убедитесь, что код работает правильно, нажав кнопку **Запуск** на панели инструментов, нажав клавишу F5 или выбрав команду меню **Отладка > Начать отладку**. Это запустит выполнение кода в отладчике, но так как точки останова не заданы, будет выведен только волновой шаблон для нескольких итераций. Чтобы закрыть окно вывода на этом этапе, нажмите любую клавишу.

    > [!Tip]
    > Чтобы окно вывода закрывалось автоматически после завершения программы, замените вызов `main()` на следующий код:
    >
    > ```python    
    > if __name__ == "__main__":  
    >     sys.exit(int(main() or 0))      
    > ```
    > 
    > Кроме того, если возникают ситуации, когда окно вывода закрывается автоматически, хотя это не нужно, щелкните правой кнопкой мыши проект, выберите **Свойства**, откройте вкладку **Отладка**, а затем добавьте `-i` в поле **Аргументы интерпретатора**. В этом случае интерпретатор переходит в интерактивный режим после завершения программы, оставляя окно открытым, пока вы не нажмете клавиши CTRL+Z и ВВОД для выхода.

1. Установите точку останова на первой строке функции `main`, щелкнув возле нее в левом сером поле или поместив курсор в этой строке и выбрав команду *Отладка > Перейти к следующей точке останова** (F9). В сером поле появится красная точка для указания точки останова (как показано ниже синей стрелкой):

    ![Задание точки останова](~/python/media/getting-started-debugging-1.png)

1. Снова запустите отладчик, и вы увидите, что выполнение кода остановится в строке с этой точкой останова. Здесь можно просмотреть стек вызовов и локальные переменные в окне "Локальные":

    ![Пользовательский интерфейс с точкой останова для кода Python](~/python/media/getting-started-debugging-2.png)

1. Пошагово пройдите несколько итераций цикла `for` (построчно) с помощью клавиши F10, команды **Отладка > Шаг с обходом** или кнопки "Шаг с обходом" на панели инструментов. Это означает, что отладчик будет выполнять каждый вызов `make_dot_string`, но не будет останавливаться внутри этой функции (если не задать точку останова).

1. На панели инструментов содержатся три кнопки перехода (показаны ниже, слева направо): "Шаг с заходом", "Шаг с обходом" и "Шаг с выходом":

    ![Кнопки перехода на панели инструментов](~/python/media/getting-started-debugging-3.png)

1. Выполните шаг с заходом к `make_dot_string` с помощью команды "Шаг с заходом" (F11). Вы увидите, что будет выполнен переход из цикла `for` к этой функции. При следующем переходе вы снова вернетесь в цикл `for`, но если в этой функции есть другие строки, они будут пошагово пройдены. Если вы находитесь внутри функции и вам нужно выполнить оставшуюся часть строк функции и вернуться к вызывающему коду, используйте команду "Шаг с выходом" (SHIFT+F11).

1. Чтобы продолжить выполнение кода до следующей точки останова (или завершения программы), снова нажмите клавишу F5 либо нажмите на панели инструментов кнопку **Продолжить**, или выберите **Отладка > Продолжить**. Так как вы установили точку останова в цикле `for`, при следующей итерации произойдет остановка.

1. Пошаговое выполнение сотен итераций цикла — это достаточно утомительный процесс, поэтому для заданной ранее точки останова можно добавить условие, чтобы прерывать выполнение, если для параметра `i` превышается определенное значение, скажем 1600. Чтобы сделать это, щелкните правой кнопкой мыши красную точку, обозначающую точку останова, и выберите **Условие...**. В появившемся окне "Параметры точки останова" введите `i > 1600` в качестве выражения и выберите **Закрыть**. Теперь нажмите клавишу F5, чтобы продолжить, и вы увидите, что программа будет долго выполняться без прерывания. 

    ![Задание условия для точки останова](~/python/media/getting-started-debugging-4.png)

1. Чтобы завершить работу программы, можно снова переключить точку останова и нажать клавишу F5. После завершения отладки Visual Studio возвращается в режим правки.

### <a name="going-deeper"></a>Дополнительные сведения

- [Отладка кода Python](debugging.md).
- Полную документацию по возможностям отладки Visual Studio см. в статье [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md).

## <a name="next-steps"></a>Следующие шаги

Помимо ссылок, приведенных в разделах "Дополнительные сведения", дополнительные возможности при работе с Python в Visual Studio можно найти в следующих статьях.

- Сведения о том, как Visual Studio подключается к службе приложений Azure, см. в статье [Публикация веб-приложения в службе приложений Azure](publishing-to-azure.md).
- Сведения о том, как управлять разными средами, как глобально, так и для отдельных проектов, включая виртуальные среды, см. в статье [Среды Python](python-environments.md).
- Visual Studio предоставляет возможность отладки приложения на удаленных серверах, как описано в статьях [Удаленная отладка кода Python](debugging-cross-platform-remote.md) и [Удаленная отладка кода Python в Azure](debugging-azure-remote.md).
- Сведения о том, как оценить производительность кода Python, см. в статье [Профилирование кода Python](profiling.md).
- Модульные тесты, написанные на Python, напрямую интегрируются в Visual Studio Test Explorer, как это описано в статье [Настройка модульного тестирования для кода Python](unit-testing.md).
- [Бесплатные курсы Python в Microsoft Virtual Academy](https://mva.microsoft.com/search/SearchResults.aspx#!q=python)
