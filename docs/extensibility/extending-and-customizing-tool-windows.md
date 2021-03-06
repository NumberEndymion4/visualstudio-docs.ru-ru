---
title: Расширение и настройка окна инструментов | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2ef4f656ed7b7ab7facbcfb470fca98327276cce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="extending-and-customizing-tool-windows"></a>Расширение и настройка окна инструментов
Visual Studio предоставляет различные типы windows, например окна инструментов, окна документов и диалоговых окнах. Другие windows, таких как окна «Свойства», в окне вывода и окне «Список задач» являются типами окон инструментов.  
  
## <a name="tool-windows"></a>Окна инструментов  
 Окна инструментов Visual Studio, windows обычно доступны только для чтения, которые не основаны на файл. В этом они отличаются от окон документов, в которых файлы отображаются в режиме чтения и записи. В качестве примеров окон инструментов можно указать окна **панели элементов**, **обозревателя решений**, **свойств** и **веб-обозревателя** .  
  
 Создание простого окна инструментов, разделе [Добавление окно инструментов](../extensibility/adding-a-tool-window.md).  
  
 Чтобы зарегистрировать окно инструментов в Visual Studio, в разделе [регистрации окно инструментов](../extensibility/registering-a-tool-window.md).  
  
 Окна инструментов по умолчанию существуют в одном экземпляре. Это означает, что в каждый момент времени может быть открыт только один экземпляр окна инструментов. После открытия единственного экземпляра окна инструментов он остается открытым до закрытия IDE. При закрытии окна инструментов одного экземпляра, изменяется только его видимость. Вы также можете создавать многоэкземплярные окна инструментов, так что одновременно можно будет открыть несколько экземпляров окна. В разделе [Создание многоэкземплярные окна инструментов](../extensibility/creating-a-multi-instance-tool-window.md) для получения дополнительной информации.  
  
 Окна инструментов могут быть *динамическое*, то есть они отображаются всякий раз, когда применяется связанный контекстом пользовательского интерфейса. Использование автоматического отображения может сократить число окон в IDE. Дополнительные сведения см. в разделе [Открытие динамические окна инструментов](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Окна инструментов в фрейме документа могут быть закрепленными, плавающими или иметь вкладки. Фрейм окна инструментов предоставляется IDE и используется для управления размером, расположением, состоянием закрепления и другими постоянными свойствами. Область окна инструментов отображает содержимое. Размер и расположение по умолчанию применяются только при первом открытии окна инструментов; после этого состояние окна инструментов сохраняется.  
  
 Области окон инструментов могут размещать пользовательские элементы управления WPF и поддерживать панели инструментов. Можно переопределить <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> свойство, чтобы возвращать дескриптор размещенного элемента управления.  
  
 Можно добавить множество разных функций для окна инструментов. Например, можно добавить панель инструментов: [Добавление панели инструментов в окне инструментов](../extensibility/adding-a-toolbar-to-a-tool-window.md) или контекстное меню: [добавлению контекстного меню в окне инструментов](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Можно добавить элемент управления поиска, которая позволяет выполнять поиск в элементах внутри окна инструментов: [Добавление поиска в окно инструментов](../extensibility/adding-search-to-a-tool-window.md).  
  
 Можно подписаться на события окна инструмента: [подписки на событие](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Расширение существующего окон инструментов  
 Сведения о окна инструментов можно добавить в новую **параметры** страницы и новый параметр на **свойства** страницы, а **список задач** и **выходные данные**  windows. Дополнительные сведения см. в разделе [расширение свойств, список задач, выходные данные и параметры Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) и [расширение свойств, список задач, выходные данные и параметры Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).  
  
## <a name="modal-dialog-boxes"></a>Модальные диалоговые окна  
 В расширение Visual Studio следует создать модальные диалоговые окна, как производные от <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>, который позволяет управлять им и остальная часть пользовательского интерфейса. Для получения дополнительной информации см. . [Создание и управление ими модальные диалоговые окна](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>См. также  
 [Создание расширения с помощью окна инструментов](../extensibility/creating-an-extension-with-a-tool-window.md)