---
title: 'Как: с помощью файла ресурсов для указания локализованные имена, свойства и разрешения | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58c8d74e29144a525eb33031fb98e25051d0305f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Практическое руководство. Использование файла ресурсов для задания локализованных имен, свойств и разрешений
  С помощью файла ресурсов можно предоставлять локализованные имена, определять свойства и применять разрешения к объектам, определенным в модели подключения к бизнес-данным (BDC). Чтобы задать эти сведения, добавьте **ресурса подключения к бизнес-данным** элемента в проект, содержащий **модель подключения к бизнес-данным** элемента. Затем задайте имена, свойства и разрешения, редактируя XML-код для файла ресурсов.  
  
### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Чтобы добавить файл ресурсов BDC в проект SharePoint  
  
1.  В **обозревателе решений**, разверните папку проекта SharePoint и выберите папку, содержащую модель BDC.  
  
2.  В строке меню выберите **проекта**, **Добавление нового элемента**.  
  
3.  Разверните **SharePoint** узел, а затем выберите **2010** узла.  
  
4.  В **Добавление нового элемента** диалогового окна выберите **элемент ресурса подключения к бизнес-данным**.  
  
5.  В **имя** , укажите имя файла ресурсов и выберите **добавить** кнопки.  
  
     Файл ресурсов с расширением .bdcr добавляется в проект и открывается для редактирования.  
  
6.  Добавьте XML-код, чтобы определить локализованные имена, свойства и разрешения, которые необходимо применить к модели подключения к бизнес-данным.  
  
     Сведения об определении этих элементов см. в разделе [модель и файлы ресурсов](http://go.microsoft.com/fwlink/?LinkID=169283).  
  
## <a name="see-also"></a>См. также  
 [Как: Добавление существующего файла модели BDC в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Как: создать модель BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Как: Добавление пользовательской сборки в функцию BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  