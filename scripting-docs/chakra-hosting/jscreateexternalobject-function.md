---
title: "Функция JsCreateExternalObject | Документы Майкрософт"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- jsrt/JsCreateExternalObject
helpviewer_keywords:
- JsCreateExternalObject function
ms.assetid: 6bcef506-93fb-429b-b06a-a971ff0b71f3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f2b7b3d0f7cb4004d06de4b9b9258750e5d6f75b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="jscreateexternalobject-function"></a>Функция JsCreateExternalObject
Создает новый объект, который хранит некие внешние данные.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalObject(  
   _In_opt_ void *data,  
   _In_opt_ JsFinalizeCallback finalizeCallback,  
   _Out_ JsValueRef *object  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `data`  
 Внешние данные, которые будет представлять объект. Может принимать значение NULL.  
  
 `finalizeCallback`  
 Обратный вызов для времени после завершения объекта. Может принимать значение NULL.  
  
 `object`  
 Новый объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Код `JsNoError` , если операция завершилась успешно, если нет, то код сбоя.  
  
## <a name="remarks"></a>Примечания  
 Требуется контекст активного скрипта.  
  
## <a name="requirements"></a>Требования  
 **Заголовок:** jsrt.h  
  
## <a name="see-also"></a>См. также  
 [Справочник (среда выполнения JavaScript)](../chakra-hosting/reference-javascript-runtime.md)