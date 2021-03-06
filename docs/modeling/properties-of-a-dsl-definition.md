---
title: Свойства определения доменного языка
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, definition file
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: be119703868316f2335f06174c9f21c2dddd2edc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="properties-of-a-dsl-definition"></a>Свойства определения доменного языка
Определение свойств DslDefinition *доменного языка* определения свойств, таких как нумерация версий. DslDefinition свойства отображаются в **свойства** окна при нажатии кнопки пустую область на диаграмме *конструктора доменного языка*.

 Дополнительные сведения см. в разделе [способ определения доменного языка](../modeling/how-to-define-a-domain-specific-language.md). Дополнительные сведения об использовании этих свойств см. в разделе [настройку и расширение доменного языка](../modeling/customizing-and-extending-a-domain-specific-language.md).

 DslDefinition имеет свойства в таблице ниже.

|Свойство.|Описание|Значение по умолчанию|
|--------------|-----------------|-------------|
|Модификатор доступа|Определяет, является ли модификатор доступа для класса домена public или internal.|public|
|Настраиваемые атрибуты|Пользовательские атрибуты для класса домена.<br /><br /> **Примечание** Чтобы добавить атрибут, нажав кнопку обзора.|\<None >|
|Название организации|Имя текущего имени компании в системном реестре.|Текущее имя компании|
|name|Имя этого класса домена.|Текущее имя|
|Пространство имен|Пространство имен, связано с этим классом домена.|Текущее пространство имен|
|Идентификатор Guid пакета|Идентификатор guid для [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] пакет, созданный для этого DSL.|\<None >|
|Пространство имен пакетов|Пространство имен для [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] пакет, созданный для этого DSL.|\<None >|
|Название продукта|Имя продукта, который будет зарегистрирован для [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] пакет, созданный для этого DSL.|\<None >|
|Примечания|Заметки, связанные с этим классом домена.|\<None >|
|Описание|Описание для этого класса домена.|\<None >|
|Отображаемое имя|Имя, которое будет отображаться в конструкторе, созданный для этого класса домена.|\<None >|
|Ключевое слово Help|Ключевое слово справки, связанное с этим классом домена.|\<None >|
|Построить|Номер инкрементного построения для данного определения доменного языка.|0|
|Основная версия|Добавочное номер основной сборки для данного определения доменного языка.|1|
|Дополнительный номер версии|Добавочное дополнительного номера построения для данного определения доменного языка.|0|
|Номер редакции|Номер для этого определения доменного языка сборки добавочных изменений.|0|

## <a name="see-also"></a>См. также

- [Глоссарий инструменты доменного языка](http://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)