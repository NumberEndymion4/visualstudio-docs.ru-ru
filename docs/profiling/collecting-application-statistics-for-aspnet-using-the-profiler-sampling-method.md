---
title: Сбор статистики для веб-приложений ASP.NET | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, sampling method
- sampling profling method
ms.assetid: f8383ab1-eb49-4d3f-8608-d8b4d51a81be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 9be304398fcefaf6a38ca7e1d557f2c9146b4872
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/11/2018
---
# <a name="collect-statistics-for-aspnet-web-apps"></a>Сбор статистики для веб-приложений ASP.NET

В этом разделе описаны процедуры и параметры для сбора статистики производительности веб-приложения ASP.NET с использованием средств командной строки **VSPerfASPNETCmd** и **VSPerfCmd** и метода профилирования выборки.  
  
> [!NOTE]
>  Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Для приложений универсальной платформы Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
> [!NOTE]
>  Несмотря на то, что средство **VSPerfCmd** предоставляет полый доступ к функциональности средств профилирования, включая приостановку и возобновление профилирования, сбор дополнительных данных от процессора и счетчиков производительности Windows, следует использовать средство командной строки **VSPerfASPNETCmd**, если эта функциональность не требуется. Средство командной строки **VSPerfASPNETCmd** является предпочтительным при выполнении профилирования веб-сайтов ASP.NET с помощью отдельного профилировщика. В отличие от средства [VSPerfCmd](../profiling/vsperfcmd.md), нет необходимости устанавливать переменные среды и перезагружать компьютер. Дополнительные сведения см.в статье [Rapid Web Site Profiling with VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) (Быстрое профилирование веб-сайтов с помощью средства VSPerfASPNETCmd).  
  
## <a name="common-tasks"></a>Общие задачи  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Присоединение профилировщика к приложению ASP.NET**|-   [Практическое руководство. Присоединение профилировщика к веб-приложению ASP.NET для сбора статистики приложения](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line.md)|  
  
## <a name="related-tasks"></a>Связанные задачи  
  
### <a name="profiling-aspnet-web-applications"></a>Профилирование веб-приложений ASP.NET  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Профилирование с помощью метода инструментирования**|-   [Сбор подробных сведений о времени с помощью инструментирования](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|  
|**Профилирование выделения памяти и сбора мусора**|-   [Сбор данных об использовании памяти](../profiling/collecting-memory-data-from-an-aspnet-web-application.md)|  
|**Профилирование конфликтов ресурсов и действий потока**|-   [Сбор данных параллелизма](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|  
  
### <a name="sampling-method"></a>Способ выборки  
  
|Задача|Связанное содержимое|  
|----------|---------------------|  
|**Профилирование автономных (клиентских) приложений**|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|  
|-   **Профилирование служб**|-   [Использование метода выборки для сбора статистики приложения](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|  
  
### <a name="analyzing-sampling-data-views-and-reports"></a>Анализ представлений и отчетов данных выборки  
 [Представления данных метода выборки](../profiling/profiler-sampling-method-data-views.md)