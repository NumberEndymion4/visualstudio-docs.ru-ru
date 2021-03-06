---
title: Справочные (Разработка решений Office в Visual Studio) | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reference [Office development in Visual Studio], 2007 Microsoft Office system
- Office development in Visual Studio, reference
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5b0b6d7b6fdbb55030088f33fc235429d0b6142e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="managed-reference-office-development-in-visual-studio"></a>Справочные материалы по управляемому коду (разработка решений Office в Visual Studio)
  В этом разделе содержится справочная документация по API для пространств имен и типов, используемых в проектах Office, предназначенных для [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] или [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. API справочную документацию по пространствам имен и типов, используемых в проектах Office, ориентированных на .NET Framework 3.5, см. в следующем справочном разделе документации Visual Studio: [ http://go.microsoft.com/fwlink/?LinkId=160658 ](http://go.microsoft.com/fwlink/?LinkId=160658).  
  
> [!NOTE]  
>  Заинтересованы в разработке решений, расширяющих возможности Office через [нескольких платформ](https://dev.office.com/add-in-availability)? Ознакомьтесь с новой [модель надстроек Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Надстройки Office имеют небольшого размера, по сравнению с надстройками VSTO и решения, и их можно создавать с помощью почти любой технологии веб-программирования, таких как HTML5, JavaScript, CSS3 и XML.  
  
## <a name="in-this-section"></a>В этом разделе  
 <xref:Microsoft.Office.Tools>  
 Содержит классы, общие для программирования решений Office. К ним относятся базовый класс для надстроек VSTO, классы для создания настраиваемых областей задач в настройках VSTO, классы для создания смарт-тегов в решениях Word и Excel и классы для создания панелей действий в настройках уровня документа.  
  
 <xref:Microsoft.Office.Tools.Excel>  
 Содержит элементы управления ведущего приложения и ведущие элементы, которые могут использоваться в решениях для Excel.  
  
 <xref:Microsoft.Office.Tools.Excel.Controls>  
 Содержит элементы управления Excel и элементы управления Windows Forms, которые могут использоваться в решениях для Excel.  
  
 <xref:Microsoft.Office.Tools.Outlook>  
 Содержит классы, используемые надстройками VSTO для Outlook, включая классы, используемые для создания настраиваемых областей формы.  
  
 <xref:Microsoft.Office.Tools.Ribbon>  
 Содержит классы, используемые для программного изменения настроек ленты, созданных с помощью конструктора лент.  
  
 <xref:Microsoft.Office.Tools.Word>  
 Содержит элементы управления ведущего приложения и ведущие элементы, которые могут использоваться в решениях для Word.  
  
 <xref:Microsoft.Office.Tools.Word.Controls>  
 Содержит элементы управления Word и элементы управления Windows Forms, которые могут использоваться в решениях для Word.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications>  
 Содержит класс <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> и набор связанных классов кэшированных данных. Эти классы могут использоваться для изменения некоторых аспектов настроек уровня документа на компьютерах, на которых не установлен Microsoft Office.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Deployment>  
 Содержит интерфейс <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> (который можно реализовать для создания *действий, выполняемых после развертывания* , для решения Office), исключения, которые могут возникать при установке решения Office, и другие API, которые являются частью инфраструктуры Visual Studio.  
  
 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime>  
 Содержит основные исключения, которые могут создаваться [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)], несколько классов, которые могут использоваться для кэширования данных в настройках уровня документа, и другие API, являющиеся частью инфраструктуры Visual Studio.  
  
 <xref:Microsoft.VisualStudio.Tools.Office.BuildTasks>  
 Содержит классы задач MSBuild, которые используются для сборки проектов Office.  
  
## <a name="see-also"></a>См. также  
 [Visual Studio Tools for Office Runtime Overview](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Приступая к работе &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)  
  
  