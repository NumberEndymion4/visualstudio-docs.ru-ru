---
title: Ошибки и предупреждения XAML
ms.date: 03/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: karann
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea8bf298f5847c779d2dc13154ddb27b2efeb214
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="xaml-errors-and-warnings"></a>Ошибки и предупреждения XAML

В Visual Studio создаваемый код XAML анализируется при вводе. При обнаружении ошибки в строке кода появляется волнистая линия. Если навести на нее указатель мыши, отобразятся дополнительные сведения об ошибке или предупреждении. Для некоторых ошибок и предупреждений отображается значок лампочки быстрого действия. А если нажать клавиши **Ctrl**+**.**, появятся варианты устранения проблемы.

## <a name="error-types"></a>Типы ошибок

По сути, при помощи многих средств код XAML анализируется в параллельном режиме. В зависимости от средства, с помощью которого обнаружена ошибка, ошибки XAML делятся на следующие три типа:

|**Средство, с помощью которого обнаружена ошибка**|**Формат кода ошибки**|
|--------------------------------|-----------------|
|Языковая служба XAML (редактор XAML)|XLSxxxx|
|Конструктор XAML|XDGxxxx|
|Функция XAML "Изменить и продолжить"|XECxxxx|

> [!Note]
> Некоторые ошибки или предупреждения не имеют соответствующего кода. Как правило, это ошибки, обнаруженные при помощи конструктора XAML.


## <a name="suppress-xaml-designer-errors"></a>Скрытие ошибок конструктора XAML

Щелкните **Сервис > Параметры** и последовательно выберите **Текстовый редактор > XAML > Разное**, чтоб открыть диалоговое окно **Параметры**.

Снимите флажок **Show errors detected by the XAML designer** (Показывать ошибки, обнаруженные при помощи конструктора XAML).

![Скрытие ошибок конструктора XAML](../designers/media/suppress_xaml_designer_errors.PNG "SuppressXAMLDesignerErrors")


