---
title: BPREQI_FIELDS90 | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ef4363b210fff059a88f80bd7377d91971ef2bce
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="bpreqifields90"></a>BPREQI_FIELDS90
Перечисляет допустимые значения, указывающие получаемых сведений о запросе на точку останова. Это перечисление расширяет [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
enum enum_BPREQI_FIELDS90  
{  
   // VS 8.0 values  
   BPREQI90_BPLOCATION                = 0x0001,  
   BPREQI90_LANGUAGE                  = 0x0002,  
   BPREQI90_PROGRAM                   = 0x0004,  
   BPREQI90_PROGRAMNAME               = 0x0008,  
   BPREQI90_THREAD                    = 0x0010,  
   BPREQI90_THREADNAME                = 0x0020,  
   BPREQI90_PASSCOUNT                 = 0x0040,  
   BPREQI90_CONDITION                 = 0x0080,  
   BPREQI90_FLAGS                     = 0x0100,  
   BPREQI90_ALLOLDFIELDS              = 0x01ff,  
   BPREQI90_VENDOR                    = 0x0200,  
   BPREQI90_CONSTRAINT                = 0x0400,  
   BPREQI90_TRACEPOINT                = 0x0800,  
  
   // Values added in VS 9.0  
   BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
   BPREQI90_ALLFIELDS                 = 0xffff  
};  
typedef DWORD BPREQI_FIELDS90;  
```  
  
```csharp  
public enum enum_BPREQI_FIELDS90  
{  
    // VS 8.0 values  
    BPREQI90_BPLOCATION                = 0x0001,  
    BPREQI90_LANGUAGE                  = 0x0002,  
    BPREQI90_PROGRAM                   = 0x0004,  
    BPREQI90_PROGRAMNAME               = 0x0008,  
    BPREQI90_THREAD                    = 0x0010,  
    BPREQI90_THREADNAME                = 0x0020,  
    BPREQI90_PASSCOUNT                 = 0x0040,  
    BPREQI90_CONDITION                 = 0x0080,  
    BPREQI90_FLAGS                     = 0x0100,  
    BPREQI90_ALLOLDFIELDS              = 0x01ff,  
    BPREQI90_VENDOR                    = 0x0200,  
    BPREQI90_CONSTRAINT                = 0x0400,  
    BPREQI90_TRACEPOINT                = 0x0800,  
  
    // Values added in VS 9.0  
    BPREQI90_MACROTRACEPOINT           = 0x1000,  
  
    BPREQI90_ALLFIELDS                 = 0xffff  
};  
```  
  
#### <a name="parameters"></a>Параметры  
 BPREQI90_BPLOCATION  
 Инициализировать или использовать `bpLocation` поле (точки останова) [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) или [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры.  
  
 BPREQI90_LANGUAGE  
 Инициализировать или использовать `guidLanguage` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_PROGRAM  
 Инициализировать или использовать `pProgram` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_PROGRAMNAME  
 Инициализировать или использовать `bstrProgramName` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_THREAD  
 Инициализировать или использовать `pThread` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_THREADNAME  
 Инициализировать или использовать `bstrThreadName` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_PASSCOUNT  
 Инициализировать или использовать `bpPassCount` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_CONDITION  
 Инициализировать или использовать `bpCondition` поле (условие точки останова) `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_FLAGS  
 Инициализировать или использовать `dwFlags` поле `BP_REQUEST_INFO` или `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_ALLOLDFIELDS  
 Инициализировать или использовать все поля для объекта `BP_REQUEST_INFO` структуры.  
  
 BPREQI90_VENDOR  
 Инициализировать или использовать `guidVendor` поле `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_CONSTRAINT  
 Инициализировать или использовать `bstrConstraint` поле `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_TRACEPOINT  
 Инициализировать или использовать `bstrTracepoint` поле `BP_REQUEST_INFO2` структуры.  
  
 BPREQI90_MACROTRACEPOINT  
 Инициализировать или использовать `bstrMacroTracepoint` поле `BP_REQUEST_INFO2` структуры. BPREQI_ALLFIELDS не содержит это поле.  
  
 BPREQI90_ALLFIELDS  
 Указывает, все поля для `BP_REQUEST_INFO2` структуры.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg90.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)