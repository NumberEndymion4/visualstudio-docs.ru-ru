---
title: Конструктор рабочих процессов - варианты пошаговой отладки отладки (для прежних версий)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- branch stepping
- stepping, options in workflow debugging
- debugging, stepping options
- debugging workflows, stepping options
- instance stepping
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f46c0ab382a0e189c595e6e0f8aeb69c71814faf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="debug-stepping-options-legacy"></a>Варианты пошаговой отладки (для прежних версий)

В этом разделе описываются способы отладки приложений Windows Workflow Foundation (WF), содержащих параллельно выполняемые действия в конструкторе рабочих процессов прежних версий Windows. Используйте конструктор рабочих процессов прежних версий, для целевой платформы .NET Framework 3.5 или WinFX.

При отладке действий прежних версий, которые выполняются одновременно, таких как **ParallelActivity** или **ConditionedActivityGroup**, можно использовать один из следующих двух вариантов для пошаговой проверки кода .

-   **Пошаговое выполнение ветви.** Этот режим проверки позволяет выполнить проверку и отладку определенной ветви сложного действия, такие как **ParallelActivity** или **ConditionalActivityGroup** действия. При использовании этого параметра для отладки будет заметно возникновение изменения в элементе управления из-за параллельного выполнения других действий в рабочем процессе. Отладчик выполняет проверку по шагам действий выбранной в данный момент ветви, тогда как другие действия в рабочем процессе могут выполняться параллельно. Например, по умолчанию, крайняя слева ветвь в **ParallelActivity** действия и первое дочернее действие **ConditionedActivityGroup** действия используются для проверки. Если нужно получить сведения об отладке любой другой ветви или дочернего действия, явная точка останова должна быть размещена в этой ветви или в дочернем действии. Проверка продолжается в этой ветви после запуска точки останова.

-   **Пошаговое выполнение экземпляра.** Этот режим проверки позволяет выполнить проверку и отладку параллельно выполняемых действий в рабочем процессе. С этим параметром будет заметно возникновение изменения в элементе управления при параллельно выполняемых действиях, запущенных в рабочем процессе.

По умолчанию выбран вариант с пошаговым выполнением ветви. Пользователи могут переключаться между двумя этими вариантами при отладке рабочего процесса более ранней версии.

При отладке рабочих процессов конечного автомата более ранней версии необходимо выбрать режим проверки пошагового выполнения экземпляра.

## <a name="see-also"></a>См. также

- [Отладка рабочих процессов прежних версий](../workflow-designer/debugging-legacy-workflows.md)
- [Как изменить вариант пошаговой отладки (для прежних версий)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)