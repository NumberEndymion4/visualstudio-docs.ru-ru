---
title: 'Как: использовать контекст пользовательского интерфейса на основе правил для расширений Visual Studio | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: 8597c413c899b54e61e848649c3c524cbdb20724
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Как: использовать контекст пользовательского интерфейса на основе правил для расширений Visual Studio
Visual Studio позволяет загружать пакеты VSPackage, когда некоторые хорошо известные <xref:Microsoft.VisualStudio.Shell.UIContext>активируются s. Эти контексты пользовательского интерфейса не являются мельчайшие Контролируемая, оставив расширение авторы нет выбора Однако выбирает доступный контекст пользовательского интерфейса, который активирует перед точкой действительно требуется VSPackage для загрузки. Список известных контекстов пользовательского интерфейса см. в разделе <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.  
  
 Загрузка пакетов может отрицательно повлиять на производительность и их загрузка раньше, чем они нужны не рекомендуется. Visual Studio 2015 представляет концепцию основанных на правилах контекстов пользовательского интерфейса, механизм, позволяющий разработчикам расширений определять точные условия, при которых активируется контекста пользовательского интерфейса и загрузить связанные пакеты VSPackage.  
  
## <a name="rule-based-ui-context"></a>Контекст пользовательского интерфейса на основе правила  
 «Правило» состоит из нового контекста пользовательского интерфейса (GUID) и логическое выражение, которое ссылается на один или несколько «условия» в сочетании с логического «и», «или», «не» операций. «Условия» вычисляются динамически во время выполнения и выражения вычисляется повторно, каждый раз, когда все изменения условия. Когда выражение принимает значение true, активируется связанный контекст пользовательского интерфейса. В противном случае контекст пользовательского интерфейса является активным.  
  
 На основе правила контекст пользовательского интерфейса может использоваться различными способами:  
  
1.  Задать ограничения на видимость для команд и окна инструментов. Можно скрыть команды и средства windows, пока не будет выполнено правило контекста пользовательского интерфейса.  
  
2.  Ограничений нагрузки auto: auto нагрузки пакеты только в том случае, когда правило выполняется  
  
3.  Задача отложенного: задержки загрузки, пока не истечет указанный интервал и по-прежнему выполняется правило.  
  
 Механизм может использоваться любое расширение Visual Studio.  
  
## <a name="create-a-rule-based-ui-context"></a>Создать контекст пользовательского интерфейса на основе правила  
 Предположим, что имеется модуль, называемый TestPackage, обеспечивающую команды меню, которая применяется только к файлам с расширением «конфигурации». До VS2015, наиболее подходящий вариант: для загрузки TestPackage при <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> контекста пользовательского интерфейса был активирован. Это не эффективным, так как загруженное решение не может даже содержать файл .config. Сообщите нам см. в разделе о том, как правила на основе контекста пользовательского интерфейса можно использовать для активации контекста пользовательского интерфейса, только если файл с расширением .config выбран и загружать TestPackage при активации этого контекста пользовательского интерфейса.  
  
1.  Определить новый идентификатор GUID UIContext и добавьте в класс VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> и <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.  
  
     Например, предположим, что новый UIContext «UIContextGuid» — для добавления. Идентификатор GUID, созданный (Создать GUID можно, щелкнув Сервис -> создать guid) — «8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B». Затем добавьте следующие внутри класса пакета:  
  
    ```csharp  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     Для атрибутов, добавьте следующий код: (сведения об этих атрибутов будут описаны позже)  
  
    ```csharp  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     Эти метаданные определить новый идентификатор GUID UIContext (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) и выражение ссылается на единственный термин «DotConfig». Термин «DotConfig» имеет значение true, каждый раз, когда текущее выделение в активной иерархии имеет имя, которое соответствует шаблону регулярного выражения «\\.config$» (заканчивается «.config»). Значение (по умолчанию) определяет необязательное имя для правила, которые полезны для отладки.  
  
     Pkgdef формируются во время построения впоследствии добавляются значения атрибута.  
  
2.  В VSCT-файле для команд TestPackage добавьте соответствующие команды флаг «DynamicVisibility»:  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  В области видимости VSCT привязать соответствующие команды для UIContext новый идентификатор GUID, определенный в #1:  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  В разделе «символы» добавьте определение UIContext:  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     Теперь команд контекстного меню для файлов *.config будут видны только в том случае, если элемент, выбранный в обозревателе решений это файл «конфигурации», пакет не будет загружен, пока не будет выбран один из этих команд.  
  
 Теперь давайте использовать отладчик, чтобы подтвердить, что загружает пакет, только если ожидается, что его. Чтобы выполнить отладку TestPackage:  
  
1.  Установите точку останова в <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> метод.  
  
2.  Построение TestPackage и начните отладку.  
  
3.  Создайте проект или откройте его.  
  
4.  Выберите любой файл с расширением, отличным от .config. Должен быть останова не.  
  
5.  Выберите файл App.Config.  
  
 TestPackage загружает и останавливается в точке останова.  
  
## <a name="adding-more-rules-for-ui-context"></a>Добавление нескольких правил для контекста пользовательского интерфейса  
 Поскольку правила контекста пользовательского интерфейса — это логические выражения, можно добавить больше ограничений, правил для контекста пользовательского интерфейса. Например в выше контекста пользовательского интерфейса, можно указать, что правило применяется только при загрузке решения с проектом. Таким образом команды не отображаются при открытии файла «.config» как отдельный файл, а не как часть проекта.  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 Теперь выражение ссылается на три условия. Первые два условия, «SingleProject» и «MultipleProjects», см. другие хорошо известных контекстов пользовательского интерфейса (по идентификаторам GUID). Третий термин «DotConfig» является контекст пользовательского интерфейса на основе правило было определено ранее.  
  
## <a name="delayed-activation"></a>Задержки активации  
 Правила могут иметь необязательно «задержка». Задержка измеряется в миллисекундах. Если он имеется, задержка приводит активации или деактивации контекста пользовательского интерфейса правило задержан этого интервала времени. Если изменения правил обратно до истечения интервала задержки, затем ничего не происходит. Этот механизм может использоваться «сдвиг «инициализация - особенно одноразовую инициализацию, не полагаясь на таймеры и регистрация для получения уведомлений простоя.  
  
 Например можно указать правило нагрузочного теста установлена задержка 100 миллисекунд:  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## <a name="term-types"></a>Типы термин  
 Ниже приведены поддерживаемые различные типы термин.  
  
|||  
|-|-|  
|{nnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnn}|Идентификатор GUID ссылается на контекст пользовательского интерфейса. Термин будет иметь значение true, каждый раз, когда контекст пользовательского интерфейса, активные и false в противном случае.|  
|HierSingleSelectionName:\<шаблон >|Термин будет иметь значение true, каждый раз, когда выделение в активной иерархии является один элемент и имя выбранного элемента соответствует регулярное выражение .net в «узор».|  
|UserSettingsStoreQuery:\<запроса >|«запрос» представляет собой полный путь в хранилище настроек пользователя, которое должно быть равно ненулевое значение. Запрос разбивается на «коллекция» и «propertyName» в последней косой черты.|  
|ConfigSettingsStoreQuery:\<запроса >|«запрос» представляет собой полный путь в хранилище конфигураций параметров, которое должно вычисляться с ненулевое значение. Запрос разбивается на «коллекция» и «propertyName» в последней косой черты.|  
|ActiveProjectFlavor:\<projectTypeGuid >|Каждый раз, когда выбранный проект является специфической термин будет иметь значение true (совокупно) и сборки, соответствующие типу данного проекта GUID.|  
|ActiveEditorContentType:\<contentType >|Термин будет иметь значение true, если выбранный документ — это текстовый редактор с заданным типом содержимого.|  
|ActiveProjectCapability:\<выражения >|Термин имеет значение true, при возможности активного проекта соответствует указанного выражения. Выражение может быть примерно VB &#124; CSharp|  
|SolutionHasProjectCapability:\<выражения >|Аналогична выше, но термин имеет значение true, если решение содержит любой загруженный проект, который соответствует выражению.|  
|SolutionHasProjectFlavor:\<projectTypeGuid >|Термин будет иметь значение true, если решение содержит проект, который является специфической (совокупно) и сборки, соответствующие типу данного проекта GUID.|


  
## <a name="compatibility-with-cross-version-extension"></a>Совместимость с разными версиями расширения  
 Правила на основе контексты пользовательского интерфейса — это новая функция в Visual Studio 2015 и не может быть перенесена в более ранних версиях. Это создает проблему с расширениями или пакетов, предназначенных для нескольких версий Visual Studio, который был бы автоматически загружать в Visual Studio 2013 и более ранних версий, но может оказаться полезным контексты правила на основе пользовательского интерфейса для предотвращения выполняется автоматически загружать в Visual Studio 2015.  
  
 Чтобы обеспечить поддержку таких пакетов, AutoLoadPackages записи в реестре могут предоставлять флаг в поле значение для указания, что элемент должен быть пропущен в Visual Studio 2015 и более поздних версий. Это можно сделать, добавив возможность флаги <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Теперь можно добавить пакеты VSPackage **SkipWhenUIContextRulesActive** возможность их <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> атрибут для указания записи должен игнорироваться в Visual Studio 2015 и более поздних версий.  
  
## <a name="extensible-ui-context-rules"></a>Правила контекста расширенного пользовательского интерфейса  
 В некоторых случаях пакеты нельзя использовать статические правила для контекста пользовательского интерфейса. Например предположим, что для поддержки расширяемости, таким образом, что состояние команды на основании редактор типов, которые поддерживаются поставщиками MEF импортированных пакетов. Команда доступна, если поддержка изменить текущий тип расширения. В таких случаях сам пакет невозможно использовать правило статического контекста пользовательского интерфейса, поскольку условия мог измениться в зависимости от того, какие MEF расширения доступны.  
  
 Для поддержки таких пакетов, контексты правила на основе пользовательского интерфейса поддерживают выражения жестко закодировано «*» указывает все условия, приведенные ниже будет выполнить его соединение с или. Это обеспечивает главный пакет для определения известных правила на основе контекста пользовательского интерфейса и связать его состояние команды в этом контексте. После этого любое расширение MEF, предназначенные для главный пакет можно добавить условия для редакторов, поддерживаемых им без ущерба для других слов или master выражение.  
  
 Конструктор <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> документации показан синтаксис для расширенного правила контекста пользовательского интерфейса.