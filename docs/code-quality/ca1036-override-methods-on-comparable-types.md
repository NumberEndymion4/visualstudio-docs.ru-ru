---
title: 'CA1036: переопределяйте методы в сравнимых типах'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: acd90414e101c03bae1d3d74f1be4f538cacfce2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: переопределяйте методы в сравнимых типах
|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Открытый или защищенный тип реализует <xref:System.IComparable?displayProperty=fullName> интерфейсов и не переопределяет <xref:System.Object.Equals%2A?displayProperty=fullName> или не перегружает языковой оператор равенства, неравенства, меньше или больше. Правило сообщает о нарушениях, если тип наследует только реализацию интерфейса.

## <a name="rule-description"></a>Описание правила
 Типы, определяющие пользовательский порядок сортировки, реализуют <xref:System.IComparable> интерфейса. <xref:System.IComparable.CompareTo%2A> Метод возвращает целочисленное значение, указывающее правильный порядок сортировки для двух экземпляров типа. Это правило определяет типы, задающие порядка сортировки. Это означает, что порядковое значение равенства, неравенства, меньше и больше не применяются. Если предоставить реализацию <xref:System.IComparable>, обычно необходимо также переопределить <xref:System.Object.Equals%2A> , возвращающий значения, которые соответствуют <xref:System.IComparable.CompareTo%2A>. При переопределении <xref:System.Object.Equals%2A> и написания кода на языке, поддерживающем перегрузки операторов, также должен предоставить операторы, которые соответствуют <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 Чтобы устранить нарушение данного правила, переопределите <xref:System.Object.Equals%2A>. Если язык программирования поддерживает перегрузку операторов, предоставьте следующие операторы:

-   op_Equality

-   op_Inequality

-   op_LessThan

-   op_GreaterThan

 В C#, токены, которые используются для представления этих операторов используются: ==,! =, \<, и >.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Это безопасно подавить предупреждение из этого правила, если причиной нарушения является отсутствие операторов и язык программирования не поддерживает перегрузку операторов, как в случае с Visual Basic. Также можно отключить предупреждения для данного правила, при его активации на операторы равенства, отличного от op_Equality Если выяснится, что реализация операторы не имеет смысла в контексте вашего приложения. Тем не менее, вы должны всегда через op_Equality и оператора ==, если переопределяет Object.Equals.

## <a name="example"></a>Пример
 В следующем примере содержится тип, реализующий правильно <xref:System.IComparable>. Комментарии к коду определяют методы, которые удовлетворяют различные правила, которые относятся к <xref:System.Object.Equals%2A> и <xref:System.IComparable> интерфейса.

 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

## <a name="example"></a>Пример
 В следующем приложении тестируется поведение <xref:System.IComparable> реализацию, показанном выше.

 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>См. также
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName> [Операторы равенства](/dotnet/standard/design-guidelines/equality-operators)