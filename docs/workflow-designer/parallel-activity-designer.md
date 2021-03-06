---
title: Конструктор рабочих процессов - конструктор действия Parallel
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Parallel.UI
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2315c27bc0a35ac1dc839b5fd98003105d92bd4
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="parallel-activity-designer"></a>Конструктор действия Parallel

Действие <xref:System.Activities.Statements.Parallel> выполняет коллекцию дочерних действий параллельно.

## <a name="the-parallel-activity"></a>Действие Parallel

Действие <xref:System.Activities.Statements.Parallel> хранит свои дочерние действия в коллекции <xref:System.Activities.Statements.Parallel.Branches%2A>. Используйте действие <xref:System.Activities.Statements.Parallel> вместо действия <xref:System.Activities.Statements.Sequence>, если некоторые дочерние действия могут перейти в состояние бездействия.

<xref:System.Activities.Statements.Parallel> Действие имеет <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> свойство имеет значение, указанное выражение Visual Basic. Действие <xref:System.Activities.Statements.Parallel> вычисляет это свойство после завершения каждого участка кода. Если значение равно **True**, то <xref:System.Activities.Statements.Parallel> действие завершается без выполнения других участков кода. Если <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> не вычисляется **True**, то <xref:System.Activities.Statements.Parallel> завершается после того, все его дочерние действия будут завершены.

### <a name="using-the-parallel-activity-designer"></a>Использование конструктора действия Parallel

**Параллельных** конструктора действий можно найти в **поток управления** категории **элементов**, который нажав **элементов**вкладка в левой части конструктора рабочих процессов (либо выберите **инструментов** из **представление** меню или сочетание клавиш CTRL + ALT + X.)

**Параллельных** конструктора можно перетащить из **элементов** и удалена на поверхности конструктора рабочих процессов, везде, где обычно помещаются конструкторы, например, внутри **Последовательность** конструктора действий. После помещения его в конструкторе рабочих процессов, он создает <xref:System.Activities.Statements.Parallel> действия, которое по умолчанию содержит <xref:System.Activities.Activity.DisplayName%2A> из **параллельных**

Чтобы добавить действие <xref:System.Activities.Statements.Parallel.Branches%2A> коллекцию действия parallel, перетащите какой-либо другой конструктор действия из **элементов** и поместите его на треугольник внутри **параллельных** конструктора действий. Треугольники обрамляют действия, которые содержатся в ветвях. Дополнительные действия можно добавить, применяя эту процедуру повторно. Порядок действия можно изменять с помощью перетаскивания их в **параллельных** конструктора действий.

### <a name="parallel-activity-properties-in-the-workflow-designer"></a>Свойства действия Parallel в конструкторе рабочих процессов

В следующей таблице показаны свойства действия Parallel, а также приводится описание их использования в конструкторе.

|Имя свойства|Обязательно|Использование|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Указывает понятное отображаемое имя действия конструктора в заголовке. Значение по умолчанию — **параллельных**. Значение можно дополнительно изменить в **свойства** сетки или напрямую в заголовке конструктора действий.|
|<xref:System.Activities.Statements.Parallel.Branches%2A>|Да|Содержит коллекцию дочерних действий, которые должны быть выполнены.|
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Вычисляется после завершения какой-либо ветви. Если значение равно **True**, то запланированные ожидающие выполнения ветви отменяются. Если это свойство не задано или равно **False**, действие завершается, если все его дочерние действия будут завершены. Значение по умолчанию — **null**.|

## <a name="see-also"></a>См. также

- [последовательности](../workflow-designer/sequence-activity-designer.md)
- [ParallelForEach\<T >](../workflow-designer/parallelforeach-t-activity-designer.md)
- [Поток управления](../workflow-designer/control-flow-activity-designers.md)