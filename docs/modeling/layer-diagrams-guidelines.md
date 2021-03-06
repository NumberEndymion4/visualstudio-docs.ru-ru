---
title: 'Схемы зависимостей: рекомендации'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 9ce90746d89dd41c1f53d7150d83afaa2e2bad46
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="dependency-diagrams-guidelines"></a>Схемы зависимостей: рекомендации
Описание архитектуры приложения на высоком уровне, создавая *схемы зависимостей* в Visual Studio. Убедитесь, что кода дизайну это путем проверки кода с помощью диаграммы зависимостей. В процесс сборки также можно включить проверку слоев. В разделе [видео Channel 9: проектирования и проверки архитектуры с использованием схем зависимостей](http://go.microsoft.com/fwlink/?LinkID=252073).

 Чтобы узнать, какие версии Visual Studio поддерживают эту функцию, см. раздел [Поддержка версий для инструментов моделирования и архитектуры](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="what-is-a-dependency-diagram"></a>Что такое диаграммы зависимостей
 Подобно традиционной схемы архитектуры Диаграмма зависимостей определяет основные компоненты или функциональные единицы разработки и их взаимозависимости. Каждый узел на схеме, который называется *слой*, представляет собой логическую группу пространств имен, проектов или другие артефакты. Можно нарисовать зависимости для своей разработки. В отличие от традиционной схемы архитектуры, можно проверить, соответствуют ли действительные зависимости заданным вами предполагаемым зависимостям. Делая проверку частью стандартного построения в [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], можно добиться того, чтобы программный код продолжал придерживаться архитектуры системы при дальнейших изменениях. В разделе [схемы зависимостей: ссылка](../modeling/layer-diagrams-reference.md).

##  <a name="Update"></a> Разработка или обновление приложения с помощью схемы зависимостей
 Ниже приведены общие сведения о использовании схем зависимостей в процессе разработки. Каждый шаг более подробно описан в последующих подразделах данного раздела. Если ведется разработка нового проекта, можно пропустить шаги, которые относятся к существующему коду.

> [!NOTE]
>  Эти шаги приведены в примерном порядке. Возможно, понадобится перекрыть задачи, заново упорядочить их, чтобы они подходили по ситуации, а также возвратиться к ним в начале каждой итерации в проекте.

1.  [Создание диаграммы зависимостей](#Create) для всего приложения или для слоя в нем.

2.  [Определение слоев, представляющих основные функциональные области или компоненты](#CreateLayers) приложения. Дайте этим слоям имена согласно их функциям, например "Презентация" или "Службы". Если у вас есть [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] решений, можно связать каждый слой с коллекцией *артефакты*, таких как проекты, пространства имен, файлы и т. д.

3.  [Обнаружение существующих зависимостей](#Generate) между слоями.

4.  [Изменение слоев и зависимостей](#EditArchitecture) чтобы показать обновленную разработку, которая должна отражаться в коде.

5.  [Разработка новых областей приложения](#NewAreas) , создав слои, представляющие основные архитектурные блоки или компоненты и определив зависимости, чтобы показать, как каждый слой использует остальные.

6.  [Изменить макет и внешний вид схемы](#EditLayout) помогут обсуждать ее с коллегами.

7.  [Проверка кода по схеме зависимостей](#Validate) конфликтов между кодом и архитектурой, требуется выделить.

8.  [Обновление кода для обеспечения соответствия новой архитектуре](#UpdateCode). Итерационно разрабатывайте и оптимизируйте код до тех пор, пока проверка не укажет, что конфликты отсутствуют.

9. [Включение проверки слоев в процесс построения](#BuildValidation) чтобы убедиться, что код продолжал придерживаться макета.

##  <a name="Create"></a> Создание диаграммы зависимостей
 Диаграмма зависимостей должна создаваться внутри проекта моделирования. Можно добавить новую диаграмму зависимостей в существующий проект моделирования, создайте новый проект моделирования для диаграммы зависимостей или Копировать существующую схему зависимостей в том же проекте моделирования.

> [!IMPORTANT]
>  Не добавлять, перетаскивать или Копировать существующую схему зависимостей из проекта моделирования в другой проект моделирования или в другое расположение в решении. Диаграмма зависимостей, которые копируются в этом случае будет иметь те же ссылки, что и исходная схема, даже если изменения схемы. Это может привести к тому, что проверка схемы будет работать неправильно, а также к другим потенциальным проблемам, таким как отсутствующие элементы или другие ошибки при попытке открыть схему.

 В разделе [создавать диаграммы зависимостей в коде](../modeling/create-layer-diagrams-from-your-code.md).

##  <a name="CreateLayers"></a> Определение уровней для представления функциональных областей или компонентов
 Слои представляют собой логические группы *артефакты*, таких как проекты, файлы кода, пространства имен, классы и методы. Можно создать слои из артефактов из проектов Visual C# и Visual Basic, или можно привязать спецификации или планы к слою путем связывания документов, таких как файлы Word или презентации PowerPoint. Каждый слой представляет собой прямоугольник на схеме и показывает количество артефактов, связанных с ним. Слой может содержать вложенные слои, описывающие более конкретные задачи.

 Рекомендуется называть слои согласно их функциям, например "Презентация" или "Службы". Если артефакты тесно взаимосвязаны, поместите их в один слой. Если артефакты могут быть обновлены отдельно или использованы в разных приложениях, поместите их на разные слои. Сведения о шаблонах слоев посетите сайт шаблоны и рекомендации по [ http://go.microsoft.com/fwlink/?LinkId=145794 ](http://go.microsoft.com/fwlink/?LinkId=145794).

> [!TIP]
>  Существуют некоторые типы артефактов, которые можно связать со слоями, но которые не поддерживают проверку относительно схемы зависимостей. Чтобы узнать, является ли артефакт проводить проверку, откройте **обозреватель слоев** для изучения **поддерживает проверку** свойства ссылки на артефакт. В разделе [обнаружение существующих зависимостей между слоями](#Generate).

 При обновлении незнакомого приложения можно также создать карты кода. Они помогают обнаружить закономерности и зависимости при анализе кода. Воспользуйтесь обозревателем решений, чтобы изучить пространства имен и классы, которые часто находятся в точном соответствии с существующими слоями. Назначьте эти артефакты кода со слоями, перетаскивая их из обозревателя решений схемы зависимостей. Затем можно использовать схемы зависимостей для обновления кода и поддержания согласованности с вашей разработки.

 Пример

-   [Создание схем зависимостей на основе кода](../modeling/create-layer-diagrams-from-your-code.md)

-   [Использование карт кода для отладки приложений](../modeling/use-code-maps-to-debug-your-applications.md)

-   [Сопоставление зависимостей во всех решениях](../modeling/map-dependencies-across-your-solutions.md)

##  <a name="Generate"></a> Обнаружение существующих зависимостей между слоями
 Зависимости существуют там, где артефакт, связанный с одним слоем, ссылается на артефакт, связанный с другим слоем. Например, класс в одном слое объявляет переменную, которая имеет класс в другом слое. Существующие зависимости можно обнаружить путем их реконструирования.

> [!NOTE]
>  Для определенных видов артефактов реконструировать зависимости невозможно. Например, зависимости не могут быть реконструированы из или в слой, связанный с текстовым файлом. Чтобы увидеть, какие артефакты имеют зависимости, которые можно реконструировать, щелкните правой кнопкой мыши один или несколько слоев и нажмите кнопку **Просмотр ссылок**. В **обозреватель слоев**, изучите **поддержка проверки** столбца. Зависимости не будут реконструированы для артефактов, для которых этот столбец показывает **False**.

#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Чтобы выполнить реконструирование существующих зависимостей между слоями

-   Выберите один или несколько слоев, щелкните правой кнопкой мыши выбранный слой и выберите команду **создать зависимости**.

 Как правило, на этом этапе можно увидеть некоторые зависимости, которых быть не должно. Эти зависимости можно изменить для соответствия предполагаемой структуре.

##  <a name="EditArchitecture"></a> Изменение слоев и зависимостей для отображения предполагаемой структуры
 Чтобы описать изменения, которые планируется внести в систему или предполагаемую архитектуру, выполните следующие действия, чтобы изменить диаграмму зависимостей. Можно также сделать некоторые оптимизационные изменения для улучшения структуры кода перед его расширением. В разделе [Совершенствование структуры кода](#Improving).

|**Задача**|**Выполните следующие действия**|
|------------|-----------------------------|
|Удаление зависимости, которой не должно существовать|Щелкните зависимость и нажмите клавишу **удалить**.|
|Изменить или ограничить направление зависимости|Задайте его **направление** свойство.|
|Создать новые зависимости|Используйте **зависимостей** и **Двунаправленная зависимость** средства.<br /><br /> Чтобы нарисовать несколько зависимостей, дважды щелкните средство. Когда вы закончите, нажмите кнопку **указатель** или нажмите клавишу **ESC** ключа.|
|Указание, что артефакт, связанный со слоем, не может зависеть от указанного пространства имен|Введите пространства имен в свойстве слоя **Запрещенные зависимости пространства имен** свойство. Используйте точку с запятой (**;**) для разделения пространств имен.|
|Указание, что артефакт, связанный со слоем, не должен более принадлежать указанному пространству имен|Введите пространства имен в свойстве слоя **Запрещенные пространства имен** свойство. Используйте точку с запятой (**;**) для разделения пространств имен.|
|Указание, что артефакт, связанный со слоем, должен принадлежать одному из указанных пространств имен|Введите пространство имен в свойстве слоя **обязательные пространства имен** свойство. Используйте точку с запятой (**;**) для разделения пространств имен.|

###  <a name="Improving"></a> Совершенствование структуры кода
 Оптимизация изменений — это улучшения, которые не влияют на поведение приложения, но помогают сделать код более легким для изменения или расширения в будущем. Хорошо структурированный код имеет вид, который потом легко можно поместить диаграмму зависимостей.

 Например, если создается слой для каждого пространства имен в коде и затем разбираются зависимости, то необходимо, чтобы был минимальный набор односторонних зависимостей между слоями. Если создается более детальная схема с использованием классов или методов в качестве слоев, то результат должен иметь такие же характеристики.

 Если это не так, код будет более сложным для изменения в течение всего времени и менее подходящим для проверки с использованием схемы зависимостей.

##  <a name="NewAreas"></a> Разработка новых областей приложения
 При начале разработки нового проекта или новой области в новом проекте, можно нарисовать слои и зависимости, чтобы облегчить определение основных компонентов перед началом разработки кода.

-   **Покажите идентифицируемые архитектурные шаблоны** на схемах зависимостей, если это возможно. Например на диаграмме зависимостей, которая описывает настольное приложение может включать слои презентацию, доменную логику и хранилище данных. Схема зависимостей, которая относится к одному компоненту приложения может иметь слои модели, представления и контроллера. Дополнительные сведения о таких шаблонах см. в разделе [шаблоны и рекомендации: архитектура приложения](http://go.microsoft.com/fwlink/?LinkId=145794).

-   **Создать артефакт кода для каждого слоя** например пространства имен, класса или компонента. Это облегчит отслеживание кода и поможет связывать артефакты кода со слоями. Сразу после создания артефакта свяжите его с соответствующим слоем.

-   **Необходимо связать со слоями большинство классов и других артефактов** так, как они попадают в больших артефакты, такие как пространства имен, которые уже связаны со слоями.

-   **Создайте новую схему для новой функции**. Как правило будет иметь одну или несколько зависимостей схем, описывающих все приложение. Если вы разрабатываете новую возможность в приложении, то не добавляйте и не изменяйте существующие схемы. Вместо этого создайте свою схему, которая отражает новые части кода. Слои в новой схеме могут включать в себя презентацию, доменную логику и слои базы данных для новой функции.

     При построении приложения код будет проверяться как в отношении всей схемы , так и в отношении более детальной схемы возможности.

##  <a name="EditLayout"></a> Изменение макета для представления и обсуждения
 Чтобы облегчить определение слоев и зависимостей или обсудить их с членами команды, измените вид и разметку схемы следующим образом.

-   Измените размеры, формы и положение слоев.

-   Измените цвета слоев и зависимостей.

    -   Выберите один или несколько слоев или зависимостей, щелкните правой кнопкой мыши и выберите команду **свойства**. В **свойства** окна, изменить **цвет** свойство.

##  <a name="Validate"></a> Проверка кода по схеме
 После изменения схемы можно проверить код вручную в любое время или автоматически при каждом запуске локального построения или [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].

 Пример

-   [Проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md)

-   [Включение проверки слоев в процесс построения](#BuildValidation)

##  <a name="UpdateCode"></a> Обновление кода для обеспечения соответствия новой архитектуре
 Как правило ошибки будут отображаться в первый раз, проверки кода в схеме обновленные зависимостей. Ошибки могут возникать вследствие нескольких причин.

-   Артефакт назначен неправильному слою. В этом случае следует переместить артефакт.

-   Способ использования артефактом (например, классом) другого класса конфликтует с имеющейся архитектурой. В этом случае необходимо выполнить рефакторинг кода, чтобы устранить зависимость.

 Для устранения этих ошибок следует обновлять код до тех пор, пока в процессе проверки не перестанут происходить ошибки. Обычно это итерационный процесс. Дополнительные сведения об этих ошибках см. в разделе [проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
>  Во время разработки или оптимизации кода, может потребоваться новые артефакты для связывания диаграмму зависимостей. Однако это может не потребоваться, например, когда слои представляют собой существующие пространства имен, а новый код только добавляет больше материала для них.

 В процессе разработки может понадобиться подавить некоторые конфликты, выявленные в ходе проверки. Например, можно подавлять ошибки, над которыми уже ведется работа, а также ошибки, не имеющие отношения к конкретному сценарию. При подавлении ошибки рекомендуется фиксировать рабочий элемент в журнале в [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]. Для выполнения этой задачи, в разделе [проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md).

##  <a name="BuildValidation"></a> Включение проверки слоев в процесс построения
 Чтобы убедиться, что будущие изменения в коде соответствуют схеме зависимостей, включите проверку слоев в стандартный процесс построения вашего решения. Каждый раз, когда другая команда начинает построение решения, любые изменения между зависимостями в коде и диаграммы зависимостей будет отображаться как ошибки построения. Дополнительные сведения о включении проверки слоев в процесс построения см. в разделе [проверка кода по схемам зависимостей](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>См. также

- [Схемы зависимостей: справочные материалы](../modeling/layer-diagrams-reference.md)
- [Создание схем зависимостей на основе кода](../modeling/create-layer-diagrams-from-your-code.md)
