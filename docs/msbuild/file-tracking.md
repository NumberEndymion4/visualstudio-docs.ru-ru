---
title: Отслеживание файлов | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, file tracking
ms.assetid: e6c66ac0-3464-451f-9192-3b98dca21b4a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 51d17894025800acd9c8ab0736ebe92d7f790fc7
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="file-tracking"></a>Отслеживание файлов
Журналы отслеживания файлов отправляют в файловую систему Windows вызов процесса и его дочерних процессов. Вызывая указанные ниже функции, программы управляют включением и отключением ведения журнала, а также задают нужный файл журнала.  
  
## <a name="in-this-section"></a>В этом разделе  
 [EndTrackingContext](../msbuild/endtrackingcontext.md)  
 Останавливает отслеживание в текущем контексте.  
  
 [ResumeTracking](../msbuild/resumetracking.md)  
 Возобновляет отслеживания после вызова [SuspendTracking](../msbuild/suspendtracking.md).  
  
 [SetThreadCount](../msbuild/setthreadcount.md)  
 Задает количество потоков, используемых для отслеживания.  
  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)  
 Запускает новый контекст отслеживания.  
  
 [StartTrackingContextWithRoot](../msbuild/starttrackingcontextwithroot.md)  
 Запускает новый контекст отслеживания с указанным корнем.  
  
 [StopTrackingAndCleanup](../msbuild/stoptrackingandcleanup.md)  
 Завершает отслеживание и освобождает использованные ресурсы.  
  
 [SuspendTracking](../msbuild/suspendtracking.md)  
 Временно приостанавливает отслеживание.  
  
 [WriteAllTLogs](../msbuild/writealltlogs.md)  
 Записывает журналы отслеживания для всех контекстов.  
  
 [WriteContextTLogs](../msbuild/writecontexttlogs.md)  
 Записывает журнал отслеживания для текущего контекста.