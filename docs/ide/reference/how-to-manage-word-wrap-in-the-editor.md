---
title: Практическое руководство. Управление переносом слов в редакторе
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- word wrap
- editors, text viewing
- Code Editor, word wrap
ms.assetid: 442f33ef-9f52-4515-b55f-fb816d664645
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 08fe7ac16eff2c7ebf398b0483034a324eb02d91
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-manage-word-wrap-in-the-editor"></a>Практическое руководство. Управление переносом слов в редакторе

Флажок **Перенос по словам** можно устанавливать и снимать. Если этот флажок установлен, часть длинной строки, выступающая за пределы текущей ширины окна редактора кода, отображается на следующей строке. Если этот флажок снят, например для упрощения использования нумерации строк, окно можно прокрутить вправо, чтобы увидеть окончание длинной строки.

> [!NOTE]
> Отображаемые диалоговые окна и команды меню могут отличаться от описанных в **справке** в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="procedure"></a>Процедура

### <a name="to-set-word-wrap-preferences"></a>Задание настроек переноса по словам

1.  В меню **Сервис** выберите пункт **Параметры**.

2.  В папке **Текстовый редактор** в подпапке **Все языки** выберите **общие** параметры, чтобы задать этот параметр глобально.

     Или...

     Выберите **общие** параметры в подпапке языка программирования.

3.  В разделе **Параметры**установите или снимите флажок **Перенос по словам**.

     Если установлен флажок **Перенос по словам**, включается параметр **Показывать графические метки в местах переноса слов**.

4.  Установите флажок **Показывать графические метки в местах переноса слов**, если требуется отображать стрелку переноса каретки там, где длинная строка переносится на следующую строку. Снимите этот флажок, если не требуется отображать эти стрелки.

    > [!NOTE]
    >  Эти стрелки-напоминания не добавляются в код: они отображаются просто для удобства.

## <a name="see-also"></a>См. также

- [Настройка редактора](../../ide/customizing-the-editor.md)
- [Диалоговое окно "Параметры текстового редактора"](../../ide/reference/text-editor-options-dialog-box.md)
- [Создание кода](../../ide/writing-code-in-the-code-and-text-editor.md)