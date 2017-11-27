---
title: "Синхронизировать тип и имя файла - рефакторинг (C#) | Документы Microsoft"
ms.custom: 
ms.date: 02/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48172dd7-24a5-4884-8a73-f92497ad6a0d
author: gewarren
ms.author: gewarren
manager: ghogen
dev_langs: CSharp
ms.openlocfilehash: ee37983575aa82abb764d57006cdabd094ea6497
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="sync-a-type-to-a-filename-or-a-filename-to-a-type-in-c"></a>Синхронизировать тип имени файла или имя файла для типа в C# #

<!-- VERSIONLESS -->
**Эта функция доступна в Visual Studio 2017 г. и более поздней версии.  Кроме того Стандартная .NET проекты пока не поддерживаются для этой оптимизации кода.**

**Что:** позволяет переименовать тип для сопоставления имени файла или имя файла в соответствии с типом, он содержит.

**Когда:** был переименован файл или тип и еще не обновлены, соответствующий файл или тип для сопоставления. 

**Почему:** помещается в файл с другим именем или наоборот, трудно найти то, что вы ищете его тип.  Переименование типа или имя файла, код становится более читаемым и простым для перехода.

**Как:**

1. Выделите или наведите курсор текста внутри имя типа для синхронизации:

   ![Выделенный код](media/synctype_highlight.png)

1. Затем выполните одно из следующих действий.
   * **Клавиатура**
     * Нажмите клавишу **Ctrl +.** для запуска **Быстрые действия и рефакторинг** и выбрать пункт **переименования файла *TypeName*.cs** из контекстного меню окна предварительного просмотра, где *TypeName* — имя выбранного типа.
     * Нажмите клавишу **Ctrl +.** для запуска **Быстрые действия и рефакторинг** и выбрать пункт **переименовать тип _Filename_**  из контекстного меню окна предварительного просмотра, где *Filename* — имя текущего файла.
   * **Мышь**
     * Щелкните его правой кнопкой мыши, выберите **Быстрые действия и рефакторинг** и выбрать пункт **переименования файла *TypeName*.cs** из контекстного меню окна предварительного просмотра, где *TypeName* — имя выбранного типа.
     * Щелкните его правой кнопкой мыши, выберите **Быстрые действия и рефакторинг** и выбрать пункт **переименовать тип _Filename_**  из контекстного меню окна предварительного просмотра, где  *Имя файла* имя текущего файла.

   Тип или файл мгновенно быть переименован.  В примере ниже файл **MyClass.cs** был переименован в **MyNewClass.cs** должно совпадать с именем типа.

   ![Встроенная результат](media/synctype_result.png)

## <a name="see-also"></a>См. также  
[Рефакторинг (C#)](../refactoring-csharp.md)