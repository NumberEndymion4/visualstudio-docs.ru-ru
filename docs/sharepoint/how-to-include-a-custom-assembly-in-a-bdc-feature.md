---
title: "Практическое руководство. Добавление пользовательской сборки в функцию BDC"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.BDC.Add_Assemblies_Dialog"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], добавление ссылки"
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], пользовательская сборка"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], добавление ссылки"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], пользовательская сборка"
ms.assetid: 2ddf44b9-5f51-4bca-b8bb-94c4bbd1c5f3
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Практическое руководство. Добавление пользовательской сборки в функцию BDC
  Проект может содержать ссылки на сборки из других проектов того же решения.  Однако эти сборки нужно добавить в список функций проекта, воспользовавшись диалоговым окном **Назначение указанных сборок бизнес\-системам**.  
  
### Включение пользовательской сборки в функцию подключения к бизнес\-данным \(BDC\)  
  
1.  В **обозревателе решений** выберите папку, содержащую модель подключения к бизнес\-данным.  
  
2.  В меню **Вид** выберите пункт **Окно свойств**.  
  
3.  В окне **Свойства** выберите свойство **Сборки** и нажмите кнопку многоточия \(![Эллипс конструктора ASP.NET для мобильных устройств](~/sharepoint/media/mwellipsis.gif "Эллипс конструктора ASP.NET для мобильных устройств")\).  
  
     Откроется диалоговое окно **Назначение указанных сборок бизнес\-системам**.  
  
4.  В списке **Выберите сборку** выберите пользовательскую сборку.  
  
    > [!NOTE]  
    >  Сборки отображаются в диалоговом окне **Назначение указанных сборок бизнес\-системам**, если добавлена ссылка на проект, содержащий сборку.  Для получения дополнительной информации см. [Практическое руководство. Добавление и удаление ссылок с помощью диалогового окна "Добавление ссылок"](http://msdn.microsoft.com/ru-ru/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
5.  В группе **Свойства ссылки** откройте список, отображаемый для свойства **Область бизнес\-системы**, выберите бизнес\-систему методов, которые используют пользовательскую сборку, и нажмите кнопку **OK**.  
  
    > [!NOTE]  
    >  Однако для отладки кода в пользовательской сборке необходимо добавить сборку к пакету решения.  Для получения дополнительной информации см. [Практическое руководство. Добавление и удаление дополнительных сборок](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
## См. также  
 [Практическое руководство. Использование файла ресурсов для задания локализованных имен, свойств и разрешений](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Практическое руководство. Добавление существующего файла модели подключения к бизнес-данным в проект SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)   
 [Создание модели подключения к бизнес-данным](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Практическое руководство. Создание модели подключения к бизнес-данным](../sharepoint/how-to-create-a-bdc-model.md)   
 [Интеграция бизнес-данных в SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  