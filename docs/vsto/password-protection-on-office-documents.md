---
title: Защита паролем в документах Office | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio]
- workbooks [Office development in Visual Studio], restricted permissions
- passwords [Office development in Visual Studio], document protections
- documents [Office development in Visual Studio], restricted permissions
- Office documents [Office development in Visual Studio, restricted permissions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5d85f1dc0aa54da22b02259aea372f2ad6dd42ac
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="password-protection-on-office-documents"></a>Защита паролей в документах Office
  Можно задать пароль документы Microsoft Office Word и книг Microsoft Office Excel, чтобы они не может быть открыта тем, кто знает пароль. Этот параметр называется **пароль для открытия**.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Вы можете создавать проекты уровня документа с помощью существующих документов и книг, которые имеют **пароль для открытия** включена. Поведение в Visual Studio отличается в документах Word и Excel, содержащих **пароль для открытия** включена.  
  
 Сведения о включении **пароль для открытия**, см. в справке в Word или Excel.  
  
## <a name="behavior-of-excel-and-word"></a>Поведение Excel и Word  
 Каждый раз при открытии книги Excel в Visual Studio, **пароль для открытия** включен, Excel запрашивает пароль. При построении решения вы предложит ввести пароль еще раз, так как документ открыт во время сборки.  
  
 Первый раз при открытии документа Word в Visual Studio, **пароль для открытия** включен, для Excel запрашивает пароль. После указания пароля, **пароль для открытия** удалены из документа, открыть документ больше не требует пароля. Если документ в решении требуется пароль, прежде чем он может быть открыт, необходимо включить **пароль для открытия** после завершения последнего построения и перед развертыванием решения.  
  
## <a name="see-also"></a>См. также  
 [Защита документов в решениях уровня документа](../vsto/document-protection-in-document-level-solutions.md)   
 [Управление правами и Обзор расширений управляемого кода](../vsto/information-rights-management-and-managed-code-extensions-overview.md)   
 [Как: код разрешено выполнение с выделенным документов с ограниченными разрешениями](../vsto/how-to-permit-code-to-run-behind-documents-with-restricted-permissions.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)  
  
  