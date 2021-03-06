---
title: Задача VCMessage | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa8ef67a4fa19bd715e73e50fcc268aee7a4df5d
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="vcmessage-task"></a>Задача VCMessage
Заносит в журнал предупреждения и сообщения об ошибках, возникшие при сборке.  
  
## <a name="remarks"></a>Примечания  
 Эта задача помогает реализовать MSBuild для Visual C++ и не предназначена для вызова пользователем. Дополнительные сведения см. в разделе <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры задачи **VCMessage**.  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|**Аргументы**|Необязательный параметр типа **String**.<br /><br /> Разделенный точками с запятой список отображаемых сообщений.|  
|**Код**|Обязательный параметр **string**.<br /><br /> Номер ошибки, определяющий сообщение.|  
|**Type**|Необязательный параметр типа **String**.<br /><br /> Задает тип выдаваемого сообщения. Укажите `"Warning"`, чтобы выдать предупреждающее сообщение, или `"Error"`, чтобы выдать сообщение об ошибке.|  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)