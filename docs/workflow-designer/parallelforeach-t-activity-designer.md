---
title: Конструктор рабочих процессов - ParallelForEach&lt;T&gt; конструктора действий
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.ParallelForEach`1.UI
ms.assetid: e93a4843-aef2-4d3e-9a0a-a2d3d1411aa7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfd7d3220bc67b764b96033ad516eb857bec6014
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="parallelforeach-activity-designer"></a>Конструктор действия ParallelForEach

Действие <xref:System.Activities.Statements.ParallelForEach%601> перечисляет элементы коллекции и выполняет вложенную инструкцию для каждого элемента коллекции параллельно, асинхронно в том же потоке. Это действие управления потоком следует использовать вместо действия <xref:System.Activities.Statements.Sequence>, если ожидается, что вложенные действия перейдут в режим бездействия.

<xref:System.Activities.Statements.ParallelForEach%601> Действие имеет <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> свойство имеет значение, указанное выражение Visual Basic. Действие <xref:System.Activities.Statements.ParallelForEach%601> вычисляет это свойство после завершения каждого участка кода. Если значение равно **true**, то <xref:System.Activities.Statements.ParallelForEach%601> действие завершается без выполнения других участков кода. Если <xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A> не вычисляется **true**, то <xref:System.Activities.Statements.ParallelForEach%601> завершается после того, все его дочерние действия будут завершены.

## <a name="the-parallelforeacht-activity"></a>ParallelForEach < T\> действия

<xref:System.Activities.Statements.ParallelForEach%601> перечисляет свои значения и планирует для каждого из них <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Планируются только <xref:System.Activities.Statements.ParallelForEach%601.Body%2A>. Выполнение тела зависит от перехода <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> в состояние простоя.

Если <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> не переходит в состояние простоя, то выполнение производится в обратном порядке, так как запланированные действия помещаются в стек, то есть последнее запланированное действие выполняется первым. Например, если имеется коллекция {1,2,3,4}в <xref:System.Activities.Statements.ParallelForEach%601> и использовать **WriteLine** как текст для записи значения. На консоль выводятся значения 4, 3, 2, 1. Это вызвано **WriteLine** не переходит в состояние простоя и после 4 **WriteLine** запланированных действий, их выполнение производится из стека (первый выполняется последним).

Но если в <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> имеются действия, которые могут перейти в состояние простоя, например <xref:System.ServiceModel.Activities.Receive> или <xref:System.Activities.Statements.Delay>, Нет необходимости ожидать их завершения. <xref:System.Activities.Statements.ParallelForEach%601> переходит к следующему запланированному действию текста и пытается выполнить его. Если и это действие перешло в режим простоя, то <xref:System.Activities.Statements.ParallelForEach%601> опять переходит к следующему действию тела.

### <a name="using-the-parallelforeacht-activity-designer"></a>С помощью ParallelForEach\<T > конструктора действий

**ParallelForEach\<T >** конструктора действий можно найти в **поток управления** категории **элементов**, который нажав  **Панель элементов** вкладка в левой части конструктора рабочих процессов (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

**ParallelForEach\<T >** конструктора можно перетащить из **элементов** и удалена на поверхности конструктора рабочих процессов, везде, где обычно помещаются конструкторы для Например, внутри **последовательности** конструктора действий. После помещения его в конструкторе рабочих процессов, он создает <xref:System.Activities.Statements.ParallelForEach%601> действия, которое по умолчанию содержит <xref:System.Activities.Activity.DisplayName%2A> из **ParallelForEach < Int32\>.**

### <a name="parallelforeacht-properties-in-the-workflow-designer"></a>ParallelForEach < T\> свойств в конструкторе рабочих процессов

В следующей таблице показаны свойства действия <xref:System.Activities.Statements.ParallelForEach%601>, которые применяются чаще всего, а также приводится описание их использования в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает понятное отображаемое имя действия конструктора в заголовке. Значение по умолчанию — **ParallelForEach\<Int32 >**. Значение можно дополнительно изменить в **свойства** сетки или напрямую в заголовке конструктора действий.|
|<xref:System.Activities.Statements.ParallelForEach%601.Body%2A>|False|Действие, выполняемое для каждого элемента в коллекции. Чтобы добавить <xref:System.Activities.Statements.ParallelForEach%601.Body%2A> действие, перетащите действие из панели элементов в **текст** поле на **ParallelForEach\<T >** конструктора действий с текстом подсказки «Перетащить действие сюда».|
|**TypeArgument**|Да|Тип элементов в <xref:System.Activities.Statements.ParallelForEach%601.Values%2A> коллекции, указанное в универсальном параметре *T*. По умолчанию **TypeArgument** равно **Int32**. Чтобы изменить тип T в **ParallelForEach < T\>**  конструктора действий, измените значение **TypeArgument** поле со списком в сетке свойств.|
|<xref:System.Activities.Statements.ParallelForEach%601.Values%2A>|Да|Коллекция элементов для итерации. Чтобы задать <xref:System.Activities.Statements.ParallelForEach%601.Values%2A>, введите выражение Visual Basic в **значения** поле на **ForEach < T\>**  конструктора действий, в поле с текстом подсказки «Введите выражение VB» или  **Значения** поле на **свойства** окна.|
|<xref:System.Activities.Statements.ParallelForEach%601.CompletionCondition%2A>||Оценивается после каждого выполнения итерации. Если результат оценки равен true, то запланированные ожидающие итерации отменяются. Если это свойство не задано, все запланированные инструкции выполняются до завершения.|

По умолчанию итератор цикла является именованным элементом. Можно изменить имя переменной итератора в **ForEach** поле **ParallelForEach\<T >** конструктора действий. Цикличный итератор можно использовать в выражениях в дочерних действиях действия <xref:System.Activities.Statements.ParallelForEach%601>.

## <a name="see-also"></a>См. также

- [последовательности](../workflow-designer/sequence-activity-designer.md)
- [Параллельный](../workflow-designer/parallel-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)