---
title: 'Как: программное копирование листов Excel | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying
- Excel [Office development in Visual Studio], copying worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8fc3252c314a2f9529c5372b1388639057b3c019
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-copy-worksheets"></a>Практическое руководство. Программное копирование листов Excel
  Можно создать копию листа и вставить данный лист перед существующим листом в книге или после него. Если место вставки листа не указано, Excel создает новую книгу, которая будет содержать новый лист.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  Независимо от того, копируете ли вы лист программно или конечный пользователь копирует его вручную, код под новым листом отсутствует, а элементы управления на новом листе не работают. Это происходит потому, что новый скопированный лист является объектом <xref:Microsoft.Office.Interop.Excel.Worksheet>, а не ведущим элементом <xref:Microsoft.Office.Tools.Excel.Worksheet>. Элементы управления Windows Forms и элементы управления ведущего приложения можно добавлять только к ведущим элементам. Для получения дополнительной информации см. [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
### <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-document-level-customization"></a>Добавление скопированного листа в книгу в настройке на уровне документа  
  
1.  Для копирования первого листа в текущей книге и размещения копии после третьего листа используйте метод <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomation#16](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#16)]  
  
### <a name="to-add-a-copied-worksheet-to-a-workbook-in-a-vsto-add-in"></a>Добавление скопированного листа к книге в надстройке VSTO  
  
1.  Для копирования первого листа в текущей книге и размещения копии после третьего листа используйте метод <xref:Microsoft.Office.Interop.Excel.Worksheets.Copy%2A>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#12)]  
  
## <a name="see-also"></a>См. также  
 [Работа с листами](../vsto/working-with-worksheets.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Как: программное добавление новых листов в книги Excel](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Как: программное удаление листов из книг](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [Как: программный Выбор листов Excel](../vsto/how-to-programmatically-select-worksheets.md)   
 [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)   
 [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  