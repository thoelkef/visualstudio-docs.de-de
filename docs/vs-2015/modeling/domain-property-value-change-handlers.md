---
title: Ändern von Handlern für Domänen Eigenschafts Wert | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, overriding event handlers
ms.assetid: 96d8f392-045e-4bc5-b165-fbaa470a3e16
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 69ebcc264eb3caa68fa0dfd2998613a7c9037b2e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669772"
---
# <a name="domain-property-value-change-handlers"></a>Handler für Wertänderungen von Domäneneigenschaften
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn in einer domänenspezifischen Sprache von [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] der Wert einer Domäneneigenschaft geändert wird, werden die Methoden `OnValueChanging()` und `OnValueChanged()` im Domäneneigenschaftenhandler aufgerufen. Als Reaktion auf diese Änderung können Sie diese Methoden überschreiben.

## <a name="overriding-the-property-handler-methods"></a>Überschreiben der Eigenschaftenhandlermethoden
 Jede Domäneneigenschaft Ihrer domänenspezifischen Sprache wird von einer Klasse verarbeitet, die in der übergeordneten Domänenklasse geschachtelt ist. Der Name folgt dem Format *propertyName*propertyhandler. Sie können diese eigenschaftenhandlerklasse in der Datei **dsl\generated code\domainclasses.cs**überprüfen. In der Klasse wird `OnValueChanging()` unmittelbar vor der Wertänderung aufgerufen, und `OnValueChanged()` wird unmittelbar nach der Wertänderung aufgerufen.

 Angenommen, Sie verfügen über eine Domänen Klasse mit dem Namen `Comment`, die eine Zeichen folgen-Domänen Eigenschaft namens `Text` und eine ganzzahlige Eigenschaft mit dem Namen `TextLengthCount` aufweist Damit `TextLengthCount` immer die Länge der `Text` Zeichenfolge enthält, können Sie den folgenden Code in eine separate Datei im DSL-Projekt schreiben:

```
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

 Beachten Sie die folgenden Punkte zu Eigenschaftenhandlern:

- Die Eigenschaftenhandlermethoden werden aufgerufen, wenn der Benutzer Änderungen an einer Domäneneigenschaft vornimmt und wenn der Programmcode der Eigenschaft einen anderen Wert zuweist.

- Die Methoden werden nur aufgerufen, wenn der Wert tatsächlich geändert wird. Der Handler wird nicht aufgerufen, wenn der Programmcode einen Wert zuweist, der dem aktuellen Wert entspricht.

- Berechnete und benutzerdefinierte Speicherdomäneneigenschaften enthalten die Methoden "OnValueChanged" und "OnValueChanging" nicht.

- Sie können einen Änderungshandler nicht verwenden, um den neuen Wert zu ändern. Wenn Sie dies tun möchten, um beispielsweise den Wert auf einen bestimmten Bereich zu beschränken, definieren Sie `ChangeRule`.

- Sie können einen Änderungshandler keiner Eigenschaft hinzufügen, die für eine Rolle einer Beziehung steht. Definieren Sie stattdessen `AddRule` und `DeleteRule` für die Beziehungsklasse. Diese Regeln werden ausgelöst, wenn die Links erstellt oder geändert werden. Weitere Informationen finden Sie unter [Regeln verbreiten Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="changes-in-and-out-of-the-store"></a>Änderungen innerhalb und außerhalb des Speichers
 Eigenschaftenhandlermethoden werden innerhalb der Transaktion aufgerufen, die die Änderung initiiert hat. Daher können Sie weitere Änderungen im Speicher vornehmen, ohne eine neue Transaktion zu öffnen. Ihre Änderungen können zu weiteren Handleraufrufen führen.

 Wenn eine Transaktion rückgängig gemacht, wiederholt oder zurückgesetzt wird, sollten Sie keine Änderungen im Speicher vornehmen, d. h. Änderungen an Modellelementen, Beziehungen, Formen, Konnektoren Diagrammen oder deren Eigenschaften.

 Des Weiteren würden Sie normalerweise Werte nicht aktualisieren, wenn das Modell aus der Datei geladen wird.

 Änderungen am Modell könnten also mit einem Test wie dem folgenden geschützt werden:

```
if (!store.InUndoRedoOrRollback
         && !store. InSerializationTransaction)
{ this.TextLength = ...; // in-store changes
}
```

 Wenn der Eigenschafts Handler dagegen Änderungen außerhalb des Geschäfts, z. b. an eine Datei, eine Datenbank oder nicht-Speicher Variablen weitergibt, sollten Sie diese Änderungen immer vornehmen, damit die externen Werte aktualisiert werden, wenn der Benutzer rückgängig oder wiederholen aufruft.

### <a name="canceling-a-change"></a>Abbrechen einer Änderung
 Wenn Sie eine Änderung verhindern möchten, können Sie die aktuelle Transaktion zurücksetzen. Sie könnten beispielsweise sicherstellen, dass eine Eigenschaft in einem bestimmten Bereich bleibt.

```
if (newValue > 10)
{ store.TransactionManager.CurrentTransaction.Rollback();
  System.Windows.Forms.MessageBox.Show("Value must be less than 10");
}

```

### <a name="alternative-technique-calculated-properties"></a>Alternative Technik: Berechnete Eigenschaften
 Das vorherige Beispiel veranschaulicht, wie mit "OnValueChanged()" Werte von einer Domäneneigenschaft an eine andere übertragen werden können. Jede Eigenschaft verfügt über einen eigenen gespeicherten Wert.

 Sie könnten stattdessen die abgeleitete Eigenschaft als berechnete Eigenschaft definieren. In diesem Fall hat die Eigenschaft keinen eigenen Speicher und die definierende Funktion wird ausgewertet, wenn der Wert erforderlich ist. Weitere Informationen finden Sie unter [berechnete und benutzerdefinierte Speicher Eigenschaften](../modeling/calculated-and-custom-storage-properties.md).

 Anstelle des vorherigen Beispiels können Sie das **Kind** -Feld von `TextLengthCount` festlegen, das in der DSL-Definition **berechnet** werden soll. Sie würden ihre eigene **Get** -Methode für diese Domänen Eigenschaft bereitstellen. Die **Get** -Methode gibt die aktuelle Länge der `Text` Zeichenfolge zurück.

 Ein möglicher Nachteil berechneter Eigenschaften ist jedoch, dass der Ausdruck bei jeder Verwendung des Werts ausgewertet wird. Dies kann ein Leistungsproblem darstellen. Auch gibt es "OnValueChanging()" und "OnValueChanged()" nicht für eine berechnete Eigenschaft.

### <a name="alternative-technique-change-rules"></a>Alternative Technik: Änderungsregeln
 Wenn Sie eine ChangeRule definieren, wird sie am Ende einer Transaktion ausgeführt, in der der Wert einer Eigenschaft geändert wurde.  Weitere Informationen finden Sie unter [Regeln verbreiten Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).

 Wenn in einer Transaktion mehrere Änderungen vorgenommen werden, wird die ChangeRule ausgeführt, wenn alle Änderungen abgeschlossen sind. Im Gegensatz dazu ist die onvalue... Methoden werden ausgeführt, wenn einige der Änderungen nicht durchgeführt wurden. Abhängig von Ihren Zielen kann eine ChangeRule daher für Sie vorteilhaft sein.

 Darüber hinaus können Sie mit einer ChangeRule den neuen Wert der Eigenschaft anpassen, damit er im angegebenen Bereich bleibt.

> [!WARNING]
> Wenn eine Regel Änderungen am Speicherinhalt vornimmt, können andere Regeln und Eigenschaftenhandler ausgelöst werden. Wenn eine Regel die Eigenschaft ändert, von der die Regeln ausgelöst wurde, wird die Regel erneut aufgerufen. Sie müssen darauf achten, dass Ihre Regeldefinitionen nicht zu endlosem Auslösen führen.

```
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

## <a name="example"></a>Beispiel

### <a name="description"></a>Beschreibung
 Mit dem folgenden Beispiel wird der Eigenschaftenhandler einer Domäneneigenschaft überschrieben und der Benutzer informiert, wenn eine Eigenschaft der `ExampleElement`-Domänenklasse geändert wurde.

### <a name="code"></a>Code

```
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
