---
title: Правила производительности для отслеживания ресурсов | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f0f77faf-0a05-4718-a2c5-47934be40868
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 433a89ae2a7cf8c9e20ec3711dcebe1514ae021b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="resource-monitoring-performance-rules"></a>Правила производительности отслеживания ресурсов
Сообщения о производительности в категории "Наблюдение за ресурсами" предоставляют дополнительные сведения о производительности приложения. Эти данные позволяют анализировать проблемы производительности. Эти правила являются информационными, и их данные выводятся для каждого сеанса профилирования.  
  
|||  
|-|-|  
|[DA0501: среднее использование ЦП профилируемым процессом](../profiling/da0501-average-cpu-consumption-by-the-process-being-profiled.md)|Это сообщение указывает долю времени, когда процессор был занят выполнением инструкций, поступающих из приложения. Содержащееся в отчете значение является средним по всем интервалам измерения, в которых профилируемый процесс был активным.|  
|[DA0502. Максимальное использование ЦП профилируемым процессом](../profiling/da0502-maximum-cpu-consumption-by-the-process-being-profiled.md)|Это сообщение указывает максимальную долю времени, когда процессор был занят выполнением инструкций, поступающих из приложения. Содержащееся в отчете значение является максимальным значением по всем интервалам измерения, в которых профилируемый процесс был активным.|  
|[DA0503. Средний рабочий набор в байтах для профилируемого процесса](../profiling/da0503-average-working-set-in-bytes-for-the-process-being-profiled.md)|Это сообщение указывает средний объем физической памяти (в байтах), использованной процессом, пока профилирование было активно. Эта мера физической памяти называется рабочим набором.|  
|[DA0504. Максимальный рабочий набор в байтах для профилируемого процесса](../profiling/da0504-maximum-working-set-in-bytes-for-the-process-being-profiled.md)|Это сообщение указывает максимальный объем физической памяти (в байтах), использованной процессом, пока профилирование было активно.|  
|[DA0505. Среднее число байт исключительного пользования, распределенное для профилируемого процесса](../profiling/da0505-average-private-bytes-allocated-for-the-process-being-profiled.md)|Это сообщение указывает средний объем виртуальной памяти (в байтах), выделенной процессом, пока профилирование было активно. Эта мера виртуальной памяти называется *байтами исключительного пользования*. Байты исключительного пользования представляют области виртуальной памяти, которые были выделены процессом и доступ к которым могут получить только потоки, выполняющиеся внутри процесса.|  
|[DA0506: максимальное число байт исключительного пользования, распределенное для профилируемого процесса](../profiling/da0506-maximum-private-bytes-allocated-for-the-process-being-profiled.md)|Это сообщение указывает максимальный объем виртуальной памяти (в байтах исключительного пользования), выделенной процессом, пока профилирование было активно.|