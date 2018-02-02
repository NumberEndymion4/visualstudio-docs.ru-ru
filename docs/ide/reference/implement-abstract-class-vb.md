---
title: "Реализация абстрактного класса — создание кода (Visual Basic) | Документация Майкрософт"
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 96cfed7f-f090-4369-8a85-2dcd4c7cf12b
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 135c1edc6719c567e21496f047af45b7ce311d13
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2018
---
# <a name="implement-an-abstract-class-in-visual-basic"></a>Реализация абстрактного класса в Visual Basic
**Что?** Вы можете сразу же создать код, необходимый для реализации абстрактного класса. 

**Когда?** Если нужно наследовать абстрактный класс.  

**Зачем?** Вы можете вручную реализовать все абстрактные элементы по одному, но этот компонент позволяет автоматически создать все сигнатуры метода. 

**Как?**

1. Поместите курсор в строку с красной волнистой линией. Она указывает, что вы ссылаетесь на абстрактный класс, но не реализовали все необходимые элементы.

   ![Выделенный код](media/abstract-highlight-vb.png)

1. Затем выполните одно из следующих действий:
   * **Клавиатура**
     * Нажмите клавиши **CTRL+.**, чтобы активировать меню **Быстрые действия и рефакторинг**. Затем во всплывающем окне предварительного просмотра выберите пункт **Реализовать абстрактный класс**.
   * **Мышь**
     * Щелкните правой кнопкой мыши и выберите меню **Быстрые действия и рефакторинг**. Затем во всплывающем окне предварительного просмотра выберите пункт **Реализовать абстрактный класс**.
     * Наведите указатель мыши на красную волнистую линию и щелкните ![значок лампочки,](media/bulb-vb.png) который отображается.
     * Нажмите кнопку ![значок лампочки,](media/bulb-vb.png) который отображается в левом поле, если текстовый курсор уже находится в строке выбора с красной волнистой линией.

   ![Предварительный просмотр реализации класса](media/abstract-preview-vb.png)

   >[!TIP]
   >Щелкните ссылку [**Просмотреть изменения**](../../ide/preview-changes.md) в нижней части окна предварительного просмотра, чтобы просмотреть все изменения перед выбором.
   >
   >Кроме того, вы можете использовать ссылки **Документ**, **Проект** и **Решение** в нижней части окна предварительного просмотра, чтобы создать правильные сигнатуры методов в нескольких классах, которые наследуют абстрактный класс.

1. Сигнатуры методов абстрактного класса создадутся автоматически и будут готовы для реализации.

   ![Результат реализации класса](media/abstract-result-vb.png)

## <a name="see-also"></a>См. также

[Создание кода](../code-generation-in-visual-studio.md)  
[Просмотр изменений](../../ide/preview-changes.md)