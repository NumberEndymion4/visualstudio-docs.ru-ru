---
title: Развертывание ClickOnce в Windows Vista | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c546d7e4287fc47a3770baa306a43a1631be2f06
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="clickonce-deployment-on-windows-vista"></a>Развертывание ClickOnce в Windows Vista
Создание приложений в Visual Studio для управления учетных записей пользователей (UAC) в Windows Vista обычно создается внедренный манифест, закодированы в двоичном XML-данные в исполняемом файле приложения. Поскольку приложения ClickOnce и COM-Взаимодействия без регистрации требуют внешнего манифеста, Visual Studio создает файл для этих типов проектов, содержащий данные UAC вместо внедренного манифеста. По умолчанию Visual Studio использует сведения из файла app.manifest для создания внешнего манифеста UAC (для развертывания ClickOnce и COM-Взаимодействия без регистрации) или для их внедрения в исполняемый файл приложения (для всех других случаев). Visual Studio предоставляет следующие возможности для создания манифеста:  
  
-   Использование внедренного манифеста. Внедрение данных UAC в исполняемый файл приложения и запуск от имени обычного пользователя.  
  
     Это значение по умолчанию (если не используется ClickOnce). Этот параметр будет поддерживать обычным способом, в котором работает Visual Studio в Windows Vista; то есть Создание внутреннего и внешнего манифестов, как с помощью `AsInvoker`.  
  
-   Использование внешнего манифеста. Создание внешнего манифеста с помощью app.manifest.  
  
     Это приводит к возникновению ошибки только внешний манифест с помощью сведений в app.manifest. При публикации приложения с помощью ClickOnce или COM-Взаимодействия без регистрации, Visual Studio добавляет в проект app.manifest и добавляет этот параметр.  
  
-   Работа без использования манифеста. Создайте приложение без манифеста.  
  
     Такой подход называется также *виртуализации*. Используйте этот параметр для обеспечения совместимости с существующими приложениями из более ранних версиях Visual Studio.  
  
 Новые свойства доступны на **приложения** страницы в конструкторе проектов (Visual C# только для проектов) и в формат файла проекта MSBuild.  
  
 Обратите внимание, что метод для настройки создания манифеста контроля учетных Записей в Интегрированной среде разработки Visual Studio отличается в зависимости от типа проекта (Visual C# и Visual Basic).  
  
 Сведения о настройке проектов Visual C# для создания манифеста см. в разделе [страница "приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md).  
  
 Сведения о настройке проектов Visual Basic для создания манифеста см. в разделе [страница "приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md).  
  
## <a name="see-also"></a>См. также  
 [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Разрешения пользователей и Visual Studio](http://msdn.microsoft.com/en-us/d5c55084-1e7b-4b61-b478-137db01c0fc0)   
 [Страница "Приложение" в конструкторе проектов (C#)](../ide/reference/application-page-project-designer-csharp.md)   
 [Страница "Приложение" в конструкторе проектов (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)