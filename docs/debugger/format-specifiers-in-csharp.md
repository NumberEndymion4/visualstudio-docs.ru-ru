---
title: Описателях в отладчике (C#) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- expressions [C#], formatting values
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- specifiers, watch variable format
- QuickWatch dialog box, format specifiers in C#
- specifiers
- watch variable symbols
- Watch window, format specifiers in C#
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 345c8589-5f36-4d34-a58c-e56271687dd6
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 447d1c1d9a60e1ff2a360790abe2c3c89f174fa6
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="format-specifiers-in-c-in-the-visual-studio-debugger"></a>Описатели формата в C# в отладчике Visual Studio
С помощью описателей формата можно изменить формат, в котором значение отображается в окне **Контрольные значения** . Можно также использовать описатели формата в **Интерпретация** окне **команда** окна в [точки трассировки](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)и даже в окнах исходного кода. Если вы приостановите выполнение на выражении в одном из этих окон, результат отобразится в подсказке по данным. Отображение результата в подсказке по данным будет соответствовать спецификатору формата.  
  
 Чтобы применить спецификатор формата, введите выражение и запятую. После запятой добавьте соответствующий спецификатор.  
  
## <a name="using-format-specifiers"></a>Использование спецификаторов формата  
 Предположим, что имеется следующий код:  
  
```csharp  
{  
        int my_var1 = 0x0065;  
        int my_var2 = 0x0066;  
        int my_var3 = 0x0067;  
}  
```  
  
 Добавить `my_var1` переменной в окно контрольных значений (во время отладки, **Отладка > Windows > Контрольные значения > Контрольные значения 1**) и задайте Шестнадцатеричный вывод (в **Контрольные значения** окно, щелкните правой кнопкой мыши переменную и Выберите **Шестнадцатеричный вывод**). Теперь в окне **Контрольные значения** показано значение 0x0065. Чтобы представить это значение в виде десятичного, а не шестнадцатеричного целого числа, в столбце «Имя» после имени переменной добавьте спецификатор десятичного формата: **, d**. В столбце «Значение» теперь отображается десятичное значение 101.  
  
 ![WatchFormatCSharp](../debugger/media/watchformatcsharp.png "WatchFormatCSharp")  
  
## <a name="format-specifiers"></a>Спецификаторы формата  
 В следующей таблице показаны спецификаторы формата C#, распознаваемые отладчиком.  
  
|Описатель|Формат|Исходное контрольное значение|Отображение|  
|---------------|------------|--------------------------|--------------|  
|ac|Принудительное вычисление выражения. Это может быть полезно в том случае, когда неявное вычисление свойств и неявные вызовы функций отключены.|Сообщение «неявное вычисление функций отключена пользователем»|\<Значение >|  
|d|Десятичное целое число|0x0065|101|  
|dynamic|Отображает указанный объект с помощью динамического представления.|Отображает все члены объекта, включая динамическое представление|Отображает только динамическое представление|  
|h|шестнадцатеричное целое число|61541|0x0000F065|  
|nq|строка без кавычек|"Моя строка"|Моя строка|  
|hidden|Отображает все открытые и не являющиеся открытыми члены.|Отображение открытых членов|Отображение всех членов|  
|raw|Отображает элемент в том виде, в котором он отображается в узле необработанного элемента. Допустимо только для прокси-объектов.|Словарь\<T >|Базовое представление Dictionary\<T >|  
|results|Используется с переменной типа, реализующего интерфейс IEnumerable или IEnumerable\<T >, обычно это результат выражения запроса. Отображает только члены, которые содержат результат запроса.|Отображение всех членов.|Отображение членов, соответствующих условиям запроса.|  
  
## <a name="see-also"></a>См. также  
 [Контрольное значение и окна "Быстрая проверка"](../debugger/watch-and-quickwatch-windows.md)   
 [Окна "Видимые" и "Локальные"](../debugger/autos-and-locals-windows.md)
