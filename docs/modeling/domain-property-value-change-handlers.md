---
title: Обработчики изменений значений домена свойств в Visual Studio
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f1244bed2057de3e9a3dc3ddb7fd61a989e18ded
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="domain-property-value-change-handlers"></a>Обработчики изменений значений свойств домена

Когда в доменном языке [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] меняется свойство домена, в обработчике свойства домена вызываются методы `OnValueChanging()` и `OnValueChanged()`. Чтобы отреагировать на внесенное изменение, можно переопределить эти методы.

## <a name="override-the-property-handler-methods"></a>Переопределите методы обработчика свойства

Каждое свойство домена вашего доменного языка обрабатывается классом, вложенным в родительский класс домена. Его имя имеет формат *PropertyName*PropertyHandler. Вы можете проверить класс обработчика этого свойства в файле **Dsl\Generated Code\DomainClasses.cs**. В этом классе непосредственно перед изменением значения вызывается метод `OnValueChanging()`, а сразу после изменения — метод `OnValueChanged()`.

Например, предположим, имеется класс домена с именем `Comment` , содержащее строковое свойство домена с именем `Text` и целочисленное свойство с именем `TextLengthCount`. Чтобы вызвать `TextLengthCount` всегда должен содержать длина `Text` строки, можно написать следующий код в отдельном файле в проекте Dsl:

```csharp
// Domain Class "Comment":
public partial class Comment
{
  // Domain Property "Text":
  partial class TextPropertyHandler
  {
    protected override void OnValueChanging(CommentBase element, string oldValue, string newValue)
    {
      base.OnValueChanging(element, oldValue, newValue);

      // To update values outside the Store, write code here.

      // Let the transaction manager handle undo:
      Store store = element.Store;
      if (store.InUndoRedoOrRollback || store.InSerializationTransaction) return;

      // Update values in the Store:
      this.TextLengthCount = newValue.Length;
    }
  }
}
```

Об обработчиках свойств необходимо помнить следующее.

-   Методы обработчика свойств вызываются, когда пользователь вносит изменения в свойство домена, а также когда код программы назначает свойству другое значение.

-   Методы вызываются, только когда значение действительно меняется. Обработчик не вызывается, если код программы назначает значение, равное текущему.

-   Вычисляемые и пользовательские свойства доменов хранения не имеют методов OnValueChanged и OnValueChanging.

-   Обработчик изменений нельзя использовать для изменения нового значения. Если это необходимо, например для ограничения значения в определенном диапазоне, определите правило `ChangeRule`.

-   Обработчик изменений нельзя добавить в свойство, представляющее роль отношения. Вместо этого настройте правила `AddRule` и `DeleteRule` в классе отношения. Они запускаются, когда связи создаются или изменяются. Дополнительные сведения см. в разделе [распространение изменений в модели правил](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="changes-in-and-out-of-the-store"></a>Изменения внутри хранилища и за его пределами

Методы обработчика свойств вызываются внутри транзакции, запустившей изменение. Это значит, что можно внести и другие изменения в хранилище, не открывая новую транзакцию. Изменения могут привести к дополнительным вызовам обработчика.

Когда транзакция отменяется, выполняется заново или откатывается, вносить изменения в хранилище, то есть в элементы модели, отношения, фигуры, схемы соединителей или их свойства, не нужно.

Более того, обновлять значения не нужно и тогда, когда модель загружается из файла.

Изменения в модели следует защищать тестом следующего вида:

```csharp
if (!store.InUndoRedoOrRollback && !store. InSerializationTransaction)
{
   this.TextLength = ...; // in-store changes
}
```

Если же обработчик свойств распространяет изменения за пределы хранилища, например в файл, базу данных или переменные вне хранилища, эти изменения обязательно необходимо внести и обеспечить обновление внешних значений при выполнении операций отмены или повторного выполнения.

### <a name="cancel-a-change"></a>Отмена изменений

Если изменение необходимо предотвратить, можно откатить текущую транзакцию. Это позволит, например, гарантировать, что свойство остается в определенном диапазоне.

```csharp
if (newValue > 10)
{
   store.TransactionManager.CurrentTransaction.Rollback();
   System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}
```

### <a name="alternative-technique-calculated-properties"></a>Альтернативный способ: вычисляемые свойства

В предыдущем примере показано, как использовать метод OnValueChanged() для распространения значений из одного свойства домена в другое. Каждое свойство имеет свое сохраненное значение.

Вместо этого можно определить в качестве вычисляемого производное свойство. В этом случае свойство не имеет собственного хранилища, а определяющая функция оценивается там, где это значение требуется. Дополнительные сведения см. в разделе [вычисляемые и пользовательские свойства хранилища](../modeling/calculated-and-custom-storage-properties.md).

Вместо предыдущего примера можно задать **вид** поле `TextLengthCount` быть **вычисляемое** в определении DSL. Бы предоставить свой собственный **получить** метода для этого свойства домена. **Получить** метод вернет текущей длины `Text` строки.

Потенциальный недостаток вычисляемых свойств заключается в том, что выражение оценивается при каждом использовании значения, что может снижать производительность. Также к вычисляемым свойствам не применяются методы OnValueChanging() и OnValueChanged().

### <a name="alternative-technique-change-rules"></a>Альтернативный способ: изменение правила

Если вы определили ChangeRule, он выполняется в конце транзакции, в которой изменяется значение свойства.  Дополнительные сведения см. в разделе [распространение изменений в модели правил](../modeling/rules-propagate-changes-within-the-model.md).

Если в одной транзакции вносятся сразу несколько изменений, метод ChangeRule выполняется после их завершения. В отличие от этого, OnValue... методы выполняются в том случае, когда некоторые изменения не были выполнены. В зависимости от целей метод ChangeRule может оказаться более подходящим.

ChangeRule также можно использовать для настройки нового значения свойства их хранения в пределах определенного диапазона.

> [!WARNING]
> Если правило вносит изменения в содержимое хранилища, могут запускаться другие правила и обработчики свойства. Если правило изменяет свойство, которое его запустило, оно будет вызвано вновь. Обязательно следите за тем, чтобы определения правил не приводили к бесконечному запуску.

```csharp
using Microsoft.VisualStudio.Modeling;
...
// Change rule on the domain class Comment:
[RuleOn(typeof(Comment), FireTime = TimeToFire.TopLevelCommit)]
class MyCommentTrimRule : ChangeRule
{
  public override void
    ElementPropertyChanged(ElementPropertyChangedEventArgs e)
  {
    base.ElementPropertyChanged(e);
    Comment comment = e.ModelElement as Comment;

    if (comment.Text.StartsWith(" ") || comment.Text.EndsWith(" "))
      comment.Text = comment.Text.Trim();
    // If changed, rule will trigger again.
  }
}

// Register the rule:
public partial class MyDomainModel
{
 protected override Type[] GetCustomDomainModelTypes()
 { return new Type[] { typeof(MyCommentTrimRule) };
 }
}
```

## <a name="example"></a>Пример

### <a name="description"></a>Описание

Код в приведенном ниже примере переопределяет обработчик свойств домена и уведомляет пользователя об изменении свойства класса домена `ExampleElement`.

### <a name="code"></a>Код

```csharp
using DslModeling = global::Microsoft.VisualStudio.Modeling;
using DslDesign = global::Microsoft.VisualStudio.Modeling.Design;

namespace msft.FieldChangeSample
{
  public partial class ExampleElement
  {
    internal sealed partial class NamePropertyHandler
    {
      protected override void OnValueChanged(ExampleElement element,
         string oldValue, string newValue)
      {
        if (!this.Store.InUndoRedoOrRollback)
        {
           // make in-store changes here...
        }
        // This part is called even in undo:
        System.Windows.Forms.MessageBox.Show("Value Has Changed");
        base.OnValueChanged(element, oldValue, newValue);
      }
    }
  }
}
```