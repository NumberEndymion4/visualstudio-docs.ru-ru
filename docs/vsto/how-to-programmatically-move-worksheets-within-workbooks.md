---
title: 'Как: программное перемещение листов в книгах | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5b34374b7795422aef83c7f79fe49931b1b69acc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Практическое руководство. Программное перемещение листов в книгах
  Вы можете программными средствами изменять положение листов относительно других листов в книге. Если не указать расположение для перемещаемого листа, Excel создает для него новую книгу.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Перемещение листа в настройке уровня документа  
  
1.  Назначьте переменной общее число листов в книге и затем переместите первый лист, чтобы он стал последним.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]  
  
### <a name="to-move-a-worksheet-in-an-vsto-add-in"></a>Перемещение листа в надстройке VSTO  
  
1.  Назначьте переменной общее число листов в книге и затем переместите первый лист, чтобы он стал последним.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Как: программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Как: программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Как: программная Защита листов Excel](../vsto/how-to-programmatically-protect-worksheets.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  