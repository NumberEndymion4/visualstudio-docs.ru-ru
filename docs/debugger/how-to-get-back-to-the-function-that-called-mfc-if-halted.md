---
title: 'Как: вернуться к функции, вызвавшей MFC, при прерывании работы | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 356e9f4950e62f3ac1399b1e79ee2fe400cec47b
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Практическое руководство. Возврат к функции, вызвавшей MFC, при прерывании работы в MFC
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, в меню "Сервис" выберите команду "Импорт и экспорт параметров". Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 Если вы использовали **прервать** на **отладки** меню для остановки выполнения программы и завершения в MFC и при наличии проблемы в коде, окно стека вызовов можно использовать для перехода к функции. Дополнительные сведения см. в разделе [как: использование окна стека вызова](../debugger/how-to-use-the-call-stack-window.md).  
  
 Иногда код может прерываться в генераторе сообщений. В таком случае в стеке вызовов нет пользовательского кода. Чтобы избежать этой проблемы, можно использовать точки останова (с условиями и числами попаданий) вместо **прервать** команды. Дополнительные сведения см. в разделе [точек останова и точек отслеживания](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583)).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>Переход к функции, из которой был вызван MFC  
  
-   Используйте **стек вызовов** окна.  
  
## <a name="see-also"></a>См. также  
 [Часто задаваемые вопросы по отладке машинного кода](../debugger/debugging-native-code-faqs.md)   
 [Отладка машинного кода](../debugger/debugging-native-code.md)