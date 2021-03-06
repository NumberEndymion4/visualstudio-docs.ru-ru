---
title: "Функция String.RAW (JavaScript) | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b1038b73-3944-4645-b075-3a674b313762
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 53df2bf0e455da8b1ccc6de3cbf3f4e3ebee4c09
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="stringraw-function-javascript"></a>Функция String.raw (JavaScript)
Возвращает необработанную строковую форму строки шаблона.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
String.raw`templateStr`;  
String.raw(obj, ...substitutions);  
```  
  
#### <a name="parameters"></a>Параметры  
 `templateStr`  
 Обязательный. Строка шаблона.  
  
 `obj`  
 Обязательный. Правильно отформатированный объект, указанный с помощью нотации объектного литерала, например: { raw: 'value' }.  
  
 `...substitutions`  
 Необязательно. Массив ( [параметр rest](../../javascript/functions-javascript.md)) состоящий из одного или нескольких значений подстановки.  
  
## <a name="remarks"></a>Примечания  
 `String.raw` Функция предназначена для использования с [строки шаблона](../../javascript/advanced/template-strings-javascript.md). Необработанная строка будет содержать все escape-символы и символы обратной косой черты, которые присутствуют в строке.  
  
 Если `obj` не является правильно отформатированным объектом, выводится сообщение об ошибке.  
  
## <a name="example"></a>Пример  
  
```  
function log(arg) {  
    if(console && console.log) {  
        console.log(arg);  
    }  
};  
  
var name = "bob";  
  
log(`hello \t${name}`);  
log(String.raw`hello \t${name}`);  
// The following usage for String.raw is supported but  
// is not typical.  
log(String.raw({ raw: 'fred'}, 'F', 'R', 'E'));  
  
// Output:  
// hello   bob  
// hello \tbob  
// fFrReEd   
```  
  
## <a name="requirements"></a>Требования  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]