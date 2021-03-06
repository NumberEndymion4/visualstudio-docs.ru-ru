---
title: Устранение неполадок и известные проблемы (инструменты Visual Studio для Unity) | Документы Майкрософт
ms.custom: ''
ms.date: 04/10/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: cb1da2ec2c41fcbec78864868d116bcd1684a5b2
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Устранение неполадок и известные проблемы (набор средств Visual Studio для Unity)
В этом разделе рассмотрены решения по устранению проблем, типичных для набора средств Visual Studio для Unity, приведено описание известных проблем и показано, как улучшить функционирование набора средств Visual Studio для Unity с помощью отчетов об ошибках.

## <a name="troubleshooting"></a>Устранение неполадок
Сведения об устранении некоторых типичных проблем, характерных для набора средств Visual Studio для Unity, см. в следующих разделах.

### <a name="visual-studio-crashes"></a>Сбои Visual Studio
Это может быть вызвано повреждением кэша MEF в Visual Studio.

Вам нужно удалить следующую папку, чтобы сбросить кэш MEF (перед этим закройте Visual Studio):

```batch
%localappdata%\Microsoft\VisualStudio\<version>\ComponentModelCache
```

Это должно исправить проблему. Если проблема не устранена, запустите командную строку разработчика для Visual Studio от имени администратора и выполните следующую команду:

```batch
 devenv /setup
```

### <a name="issues-with-visual-studio-2015-and-intellisense-or-code-coloration"></a>Проблемы с Visual Studio 2015 и IntelliSense или с раскраской кода
Попробуйте установить для Visual Studio 2015 обновление 3.

### <a name="shader-files-without-code-coloration-when-using-visual-studio-2017"></a>Файлы шейдеров без раскраски кода при использовании Visual Studio 2017
Убедитесь в том, что в вашем экземпляре Visual Studio 2017 установлена рабочая нагрузка "Разработка классических приложений на C++". Средство синтаксического анализа C/C++, используемое для раскраски кода, входит в состав этой рабочей нагрузки.

### <a name="visual-studio-hangs"></a>Visual Studio перестает отвечать на запросы
Некоторые подключаемые модули Unity, такие как Parse, FMOD, UMP (Universal Media Player), ZFBrowser или Embedded Browser, используют собственные потоки. Эта проблема возникает, когда подключаемый модуль подключает собственный поток к среде выполнения, что блокирует вызовы ОС. Это означает, что Unity не может прервать этот поток для отладчика (или перезагрузить домен) и перестает отвечать на запросы.

Для FMOD существует обходной путь. Вы можете передать [флаг](https://www.fmod.org/docs/content/generated/FMOD_STUDIO_INITFLAGS.html) инициализации FMOD_STUDIO_INIT_SYNCHRONOUS_UPDATE, чтобы отключить асинхронную обработку и выполнять всю обработку в основном потоке.

### <a name="incompatible-project-in-visual-studio"></a>Несовместимый проект в Visual Studio
Во-первых, убедитесь, что Visual Studio используется в качестве внешнего редактора скриптов в Unity (Правка/Параметры/Внешние инструменты). Затем убедитесь, что в Unity установлен подключаемый модуль Visual Studio (команда "Справка"/"О программе" должна отобразить внизу сообщение о том, что инструменты Microsoft Visual Studio для Unity включены). Затем убедитесь, что это расширение правильно установлено в Visual Studio ("Справка"/"О программе").

### <a name="extra-reloads-or-visual-studio-losing-all-open-windows"></a>Дополнительные перезагрузки или закрытие всех открытых окон в Visual Studio
Никогда не работайте с файлами проектов непосредственно из обработчика ресурсов или иного средства. Если вам действительно необходимо совершить операции с файлом проекта, мы предоставляем для этого интерфейс API. См. раздел [Проблемы со ссылками на сборку](#Assembly-reference-issues).

Если происходят лишние перезагрузки или если при перезагрузке в Visual Studio закрываются все открытые окна, убедитесь в том, что установлены все необходимые целевые пакеты .NET. Дополнительные сведения см. в следующем разделе, посвященном платформам.

###  <a name="the-debugger-does-not-break-on-exceptions"></a>В случае исключений не происходит останов отладчика
При использовании предыдущей версии среды выполнения Unity (эквивалентной версии .NET 3.5), в случае необработанного исключения (вне блока try/catch) всегда происходит останов отладчика. Если исключение обрабатывается, отладчик использует окно параметров исключений для определения того, требуется ли останов.

В новой среде выполнения Unity (эквивалентной версии .NET 4.6) появился новый способ управления пользовательскими исключениями. В результате все исключения считаются "обработанными пользователем", даже если они произошли вне блока try/catch. Поэтому их необходимо явным образом задавать в окне параметров исключений, если требуется останов отладчика.

В окне "Параметры исключений" ("Отладка" > "Окна" > "Параметры исключений") разверните узел для категории исключений (например, "Исключения среды CLR", то есть исключения .NET) и установите флажок для конкретного исключения, которое необходимо перехватывать, в этой категории (например, System.NullReferenceException). Можно также выбрать всю категорию исключений.

### <a name="on-windows-visual-studio-asks-to-download-the-unity-target-framework"></a>В ОС Windows система Visual Studio предлагает скачать целевую платформу Unity
Инструментам Visual Studio для Unity требуется платформа .NET Framework 3.5, которая не установлена по умолчанию в Windows 8 или Windows 10. Чтобы устранить эту проблему, следуйте инструкциям по скачиванию и установке .NET Framework 3.5.

При использовании новой среды выполнения Unity также требуются пакеты нацеливания .NET версий 4.6 и 4.7.1. Чтобы быстро установить их (изменить экземпляр Visual Studio 2017, отдельные компоненты, категорию .NET, выбрать все пакеты нацеливания 4.x), можно использовать установщик Visual Studio 2017.

### <a name="assembly-reference-issues"></a>Проблемы со ссылками на сборку
Если ваш проект довольно сложен с точки зрения ссылок или требуется лучше контролировать этот этап создания, вы можете использовать наш [API](../cross-platform/customize-project-files-created-by-vstu.md) для работы с созданным содержимым проекта или решения. Вы также можете использовать [файлы ответов](https://docs.unity3d.com/Manual/PlatformDependentCompilation.html) в своем проекте Unity и обрабатывать их.

### <a name="breakpoints-with-a-warning"></a>Точки останова с предупреждением
Если Visual Studio не удается найти исходное расположение для определенной точки останова, рядом с ней отображается предупреждение. Убедитесь, что используемая вами процедура правильно загружена и используется в текущей сцене Unity.

### <a name="breakpoints-not-hit"></a>Точки останова не срабатывают
Убедитесь, что используемая вами процедура правильно загружена и используется в текущей сцене Unity. Закройте Visual Studio и Unity, а затем удалите все созданные файлы (CSPROJ, SLN) и всю папку библиотеки.

### <a name="unable-to-attach"></a>Не удается подключить
-   Попробуйте временно отключить антивирусную программу или создать правила исключения для VS и Unity.
-   Попробуйте временно отключить брандмауэр или создать правила, разрешающие сетевое взаимодействие между VS и Unity по протоколам TCP/UDP.
-   Мы выяснили, что такие программы, как Team Viewer, мешают обнаружению процессов. Возможно, вы можете на некоторое время остановить все лишнее программное обеспечение, чтобы выяснить, повлияет ли это на что-либо.
-   Не переименовывайте основной исполняемый файл Unity, так как VSTU отслеживают только процессы "Unity.exe".

### <a name="unable-to-debug-android-players"></a>Не удается выполнить отладку проигрывателей Android
Мы используем для обнаружения проигрывателей многоадресную рассылку (это стандартный механизм, применяемый в Unity), но затем применяется простое соединение TCP для подключения отладчика. Этап обнаружения — основная проблема для устройств Android.

Связь через Wi-Fi универсальна, однако она слишком медленная по сравнению с USB из-за задержки. Мы наблюдали отсутствие должной поддержки многоадресной рассылки у некоторых маршрутизаторов или устройств (этим известна серия Nexus).

Связь по USB обладает отличной скоростью для отладки. Инструменты Visual Studio для Unity теперь могут обнаруживать устройства USB и согласовывать с сервером ADB правильную переадресацию портов для отладки.

### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Миграция из UnityVS в набор средств Visual Studio для Unity
 В случае миграции из UnityVS в набор средств Visual Studio для Unity необходимо создать новые решения Visual Studio для ваших проектов Unity.

##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Перенос проекта Unity из UnityVS 1.8 в набор средств Visual Studio для Unity 1.9

1.  Удалите старые файлы решения и проекта из проекта Unity. В корневом каталоге проекта Unity найдите файлы SLN и PROJ (специфические для Visual Studio) и удалите их все.

2.  Импортируйте пакет набора средств Visual Studio для Unity в свой пакет Unity. Дополнительные сведения о том, как импортировать пакет VSTU, см. в разделе "Настройка набора средств Visual Studio для Unity" на странице [Начало работы](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) .

3.  Создайте новые файлы решения и проекта. Если их нужно создать сейчас, в редакторе Unity в главном меню выберите **Средства Visual Studio**, **Создать файлы проекта**. В противном случае этот шаг можно пропустить. Набор средств Visual Studio для Unity автоматически создаст новые файлы при выборе **Средства Visual Studio**, **Открыть в Visual Studio**.

## <a name="known-issues"></a>Известные проблемы
 Применительно к набору средств Visual Studio для Unity существуют известные проблемы, которые возникают вследствие взаимодействия отладчика со старой версией компилятора C# в Unity. Мы работаем над устранением этих проблем, но в то же время могут возникать другие проблемы.

-   При отладке Unity иногда аварийно завершает работу.

-   При отладке Unity иногда зависает.

-   Пошаговая отладка с заходом и выходом из методов иногда ведет себя некорректно, особенно в итераторах или внутри инструкций switch.

## <a name="reporting-errors"></a>Ведение отчетов об ошибках
 Помогите нам улучшить качество набора средств Visual Studio для Unity: отправляйте нам отчеты об ошибках при аварийном выходе, зависании или в случае других ошибок. Эти сведения помогают нам определять причину и устранять проблемы в наборе средств Visual Studio для Unity. Спасибо!

### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Как сообщить об ошибке в случае зависания Visual Studio
 Существуют отчеты о том, что иногда Visual Studio  зависает при отладке с помощью набора средств Visual Studio для Unity, но чтобы разобраться в проблеме, нам требуется больше данных. Вы можете помочь нам разобраться с проблемой, если выполните следующие действия.

##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Создание отчета о зависании Visual Studio во время отладки с помощью набора средств Visual Studio для Unity

*В Windows:*

1.  Откройте новый экземпляр Visual Studio.

2.  Откройте диалоговое окно "Присоединение к процессу". В новом экземпляре Visual Studio в главном меню выберите **Отладка**, **Присоединение к процессу**.

3.  Присоедините отладчик к замороженному экземпляру Visual Studio. В диалоговом окне **Присоединение к процессу** выберите замороженный экземпляр Visual Studio в таблице **Доступные процессы** , а затем нажмите кнопку **Присоединить** .

4.  Приостановите отладчик. В новом экземпляре Visual Studio в главном меню выберите **Отладка**, **Прервать все** или просто нажмите **CTRL+ALT+BREAK**.

5.  Создайте дамп потока. В окне командной строки введите следующую команду и нажмите клавишу **ВВОД**:

    ```powershell
    Debug.ListCallStack /AllThreads /ShowExternalCode
    ```

    Возможно, сначала будет нужно отобразить окно **Команда** . В Visual Studio в главном меню выберите **Представление**, **Другие окна**, **Командное окно**.

*На Mac:*

1. Откройте терминал и получите идентификатор процесса Visual Studio для Mac:

    ```shell
    ps aux | grep "[V]isual Studio.app"
    ```

1. Запустите отладчик lldb.

    ```shell
    lldb
    ```

1. Подключитесь к экземпляру Visual Studio для Mac, используя идентификатор процесса:

    ```shell
    process attach --pid THE_PID_OF_THE_VSFM_PROCESS
    ```

1. Извлеките трассировку стека для всех потоков:

    ```shell
    bt all
    ```

Наконец, отправьте дамп потока по адресу [vstusp@microsoft.com](mailto:vstusp@microsoft.com), а также опишите, что вы делали, когда среда Visual Studio зависла.
