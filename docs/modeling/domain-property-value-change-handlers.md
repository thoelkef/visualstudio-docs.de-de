---
title: "Handler f&#252;r Wert&#228;nderungen von Dom&#228;neneigenschaften | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domänenspezifische Sprache, Überschreiben von Ereignishandlern"
ms.assetid: 96d8f392-045e-4bc5-b165-fbaa470a3e16
caps.latest.revision: 24
caps.handback.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Handler f&#252;r Wert&#228;nderungen von Dom&#228;neneigenschaften
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn in einer domänenspezifischen Sprache von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] der Wert einer Domäneneigenschaft geändert wird, werden die Methoden `OnValueChanging()` und `OnValueChanged()` im Domäneneigenschaftenhandler aufgerufen. Als Reaktion auf diese Änderung können Sie diese Methoden überschreiben.  
  
## Überschreiben der Eigenschaftenhandlermethoden  
 Jede Domäneneigenschaft Ihrer domänenspezifischen Sprache wird von einer Klasse verarbeitet, die in der übergeordneten Domänenklasse geschachtelt ist. Der Name weist das Format *Eigenschaftenname*PropertyHandler auf. Sie können diese Eigenschaftenhandlerklasse in der Datei **Dsl\\Generated Code\\DomainClasses.cs** untersuchen. In der Klasse wird `OnValueChanging()` unmittelbar vor der Wertänderung aufgerufen, und `OnValueChanged()` wird unmittelbar nach der Wertänderung aufgerufen.  
  
 Nehmen Sie beispielsweise an, Ihre Domänenklasse `Comment` weist eine Zeichenfolgen\-Domäneneigenschaft namens `Text` und eine Integer\-Eigenschaft namens `TextLengthCount` auf. Damit `TextLengthCount` immer die Länge der Zeichenfolge `Text` enthält, könnten Sie den folgenden Code in einer separaten Datei im Dsl\-Projekt schreiben:  
  
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
  
-   Die Eigenschaftenhandlermethoden werden aufgerufen, wenn der Benutzer Änderungen an einer Domäneneigenschaft vornimmt und wenn der Programmcode der Eigenschaft einen anderen Wert zuweist.  
  
-   Die Methoden werden nur aufgerufen, wenn der Wert tatsächlich geändert wird. Der Handler wird nicht aufgerufen, wenn der Programmcode einen Wert zuweist, der dem aktuellen Wert entspricht.  
  
-   Berechnete und benutzerdefinierte Speicherdomäneneigenschaften enthalten die Methoden "OnValueChanged" und "OnValueChanging" nicht.  
  
-   Sie können einen Änderungshandler nicht verwenden, um den neuen Wert zu ändern. Wenn Sie dies tun möchten, um beispielsweise den Wert auf einen bestimmten Bereich zu beschränken, definieren Sie `ChangeRule`.  
  
-   Sie können einen Änderungshandler keiner Eigenschaft hinzufügen, die für eine Rolle einer Beziehung steht. Definieren Sie stattdessen `AddRule` und `DeleteRule` für die Beziehungsklasse. Diese Regeln werden ausgelöst, wenn die Links erstellt oder geändert werden. Weitere Informationen finden Sie unter [Regeln propagieren Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).  
  
### Änderungen innerhalb und außerhalb des Speichers  
 Eigenschaftenhandlermethoden werden innerhalb der Transaktion aufgerufen, die die Änderung initiiert hat. Daher können Sie weitere Änderungen im Speicher vornehmen, ohne eine neue Transaktion zu öffnen. Ihre Änderungen können zu weiteren Handleraufrufen führen.  
  
 Wenn eine Transaktion rückgängig gemacht, wiederholt oder zurückgesetzt wird, sollten Sie keine Änderungen im Speicher, an Modellelementen, Beziehungen, Formen, Konnektoren, Diagrammen oder deren Eigenschaften vornehmen.  
  
 Des Weiteren würden Sie normalerweise Werte nicht aktualisieren, wenn das Modell aus der Datei geladen wird.  
  
 Änderungen am Modell könnten also mit einem Test wie dem folgenden geschützt werden:  
  
```  
if (!store.InUndoRedoOrRollback   
         && !store. InSerializationTransaction)  
{ this.TextLength = ...; // in-store changes   
}  
```  
  
 Wenn der Eigenschaftenhandler dagegen Änderungen außerhalb des Speichers überträgt, beispielsweise an eine Datei, eine Datenbank oder Variablen außerhalb des Speichers, sollten Sie diese Änderungen immer vornehmen, damit die externen Werte aktualisiert werden, wenn der Benutzer Vorgänge zum Rückgängigmachen oder Wiederholen aufruft.  
  
### Abbrechen einer Änderung  
 Wenn Sie eine Änderung verhindern möchten, können Sie die aktuelle Transaktion zurücksetzen. Sie könnten beispielsweise sicherstellen, dass eine Eigenschaft in einem bestimmten Bereich bleibt.  
  
```  
if (newValue > 10)   
{ store.TransactionManager.CurrentTransaction.Rollback();  
  System.Windows.Forms.MessageBox.Show("Value must be less than 10");  
}  
  
```  
  
### Alternative Technik: Berechnete Eigenschaften  
 Das vorherige Beispiel veranschaulicht, wie mit "OnValueChanged\(\)" Werte von einer Domäneneigenschaft an eine andere übertragen werden können. Jede Eigenschaft verfügt über einen eigenen gespeicherten Wert.  
  
 Sie könnten stattdessen die abgeleitete Eigenschaft als berechnete Eigenschaft definieren. In diesem Fall hat die Eigenschaft keinen eigenen Speicher und die definierende Funktion wird ausgewertet, wenn der Wert erforderlich ist. Weitere Informationen finden Sie unter [Berechnete und benutzerdefinierte Speichereigenschaften](../modeling/calculated-and-custom-storage-properties.md).  
  
 Statt des vorherigen Beispiels könnten Sie das Feld **Art** von `TextLengthCount` in der DSL\-Definition als **Berechnet** festlegen. Sie würden für diese Domäneneigenschaft eine eigene **Get**\-Methode bereitstellen. Die **Get**\-Methode würde die aktuelle Länge der Zeichenfolge `Text` zurückgeben.  
  
 Ein möglicher Nachteil berechneter Eigenschaften ist jedoch, dass der Ausdruck bei jeder Verwendung des Werts ausgewertet wird. Dies kann ein Leistungsproblem darstellen. Auch gibt es "OnValueChanging\(\)" und "OnValueChanged\(\)" nicht für eine berechnete Eigenschaft.  
  
### Alternative Technik: Änderungsregeln  
 Wenn Sie eine ChangeRule definieren, wird sie am Ende einer Transaktion ausgeführt, in der der Wert einer Eigenschaft geändert wurde. Weitere Informationen finden Sie unter [Regeln propagieren Änderungen innerhalb des Modells](../modeling/rules-propagate-changes-within-the-model.md).  
  
 Wenn in einer Transaktion mehrere Änderungen vorgenommen werden, wird die ChangeRule ausgeführt, wenn alle Änderungen abgeschlossen sind. Dagegen werden die OnValue...\-Methoden ausgeführt, wenn einige Änderungen noch nicht vorgenommen wurden. Abhängig von Ihren Zielen kann eine ChangeRule daher für Sie vorteilhaft sein.  
  
 Darüber hinaus können Sie mit einer ChangeRule den neuen Wert der Eigenschaft anpassen, damit er im angegebenen Bereich bleibt.  
  
> [!WARNING]
>  Wenn eine Regel Änderungen am Speicherinhalt vornimmt, können andere Regeln und Eigenschaftenhandler ausgelöst werden. Wenn eine Regel die Eigenschaft ändert, von der die Regeln ausgelöst wurde, wird die Regel erneut aufgerufen. Sie müssen darauf achten, dass Ihre Regeldefinitionen nicht zu endlosem Auslösen führen.  
  
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
  
## Beispiel  
  
### Beschreibung  
 Mit dem folgenden Beispiel wird der Eigenschaftenhandler einer Domäneneigenschaft überschrieben und der Benutzer informiert, wenn eine Eigenschaft der `ExampleElement`\-Domänenklasse geändert wurde.  
  
### Code  
  
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
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Modeling.DomainPropertyValueHandler%602.OnValueChanged%2A>   
 <xref:Microsoft.VisualStudio.Modeling.DomainPropertyValueHandler%602.OnValueChanging%2A>