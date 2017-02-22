---
title: "Regeln propagieren &#196;nderungen innerhalb des Modells | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domain-Specific Language, programmierdomänenmodelle"
  - "Domain-Specific Language, Regeln"
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 30
caps.handback.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Regeln propagieren &#196;nderungen innerhalb des Modells
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können eine Regel Store zum Weitergeben einer Änderung von einem Element zu einem anderen in Visualization and Modeling SDK \(VMSDK\) erstellen. Bei eine Änderung auf jedes Element im Speicher, werden Regeln ausgeführt werden, in der Regel auf, wenn die äußerste Transaktion ein Commit ausgeführt wird, soll. Es gibt verschiedene Typen von Regeln für verschiedene Arten von Ereignissen, z. B. ein Element hinzufügen oder löschen. Sie können Regeln auf bestimmte Typen von Elementen, Formen oder Diagramme anfügen. Viele integrierte Features werden durch Regeln definiert: Regeln zum Beispiel stellen Sie sicher, dass ein Diagramm aktualisiert wird, wenn das Modell ändert. Sie können Ihrer domänenspezifischen Sprache anpassen, indem Sie eigene Regeln hinzufügen.  
  
 Store\-Regeln sind besonders nützlich für die Weitergabe von Änderungen in den Speicher – d. h. an Modellelementen, Beziehungen, Formen oder Konnektoren und ihrer Domäne Eigenschaften. Regeln werden nicht ausgeführt, wenn der Benutzer die Befehle zum Rückgängigmachen oder Wiederholen aufruft. Stattdessen stellt der Transaktions\-Manager sicher, dass der Speicher\-Inhalt in den richtigen Status wiederhergestellt werden. Wenn Sie auf Ressourcen außerhalb des Speichers weiterleiten möchten, verwenden Sie Ereignisse speichern. Weitere Informationen finden Sie unter [Ereignishandler propagieren Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
 Nehmen wir beispielsweise an, dass Sie angeben möchten, dass, wenn der Benutzer \(oder Code\) ein neues Element vom Typ ExampleDomainClass erstellt, ein weiteres Element eines anderen Typs in einen anderen Teil des Modells erstellt wird. Sie konnte ein AddRule schreiben und ExampleDomainClass zuordnen. Sie möchten Code schreiben, in der Regel auf das zusätzliche Element zu erstellen.  
  
```c#  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
  
namespace ExampleNamespace  
{  
 // Attribute associates the rule with a domain class:  
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]  
 // The rule is a class derived from one of the abstract rules:  
 class MyAddRule : AddRule  
 {  
  // Override the abstract method:  
  public override void ElementAdded(ElementAddedEventArgs e)  
  {  
    base.ElementAdded(e);  
    ExampleDomainClass element = e.ModelElement;  
    Store store = element.Store;  
    // Ignore this call if we're currently loading a model:  
    if (store.TransactionManager.CurrentTransaction.IsSerializing)   
       return;  
  
    // Code here propagates change as required – for example:  
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);  
      echo.Name = element.Name;  
      echo.Parent = element.Parent;    
    }  
  }  
 // The rule must be registered:  
 public partial class ExampleDomainModel  
 {  
   protected override Type[] GetCustomDomainModelTypes()  
   {  
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
     types.Add(typeof(MyAddRule));  
     // If you add more rules, list them here.   
     return types.ToArray();  
   }  
 }  
}  
  
```  
  
> [!NOTE]
>  Der Code einer Regel sollte den Status der Elemente in den Speicher nur ändern. die Regel sollte also nur Modellelementen, Beziehungen, Formen, Konnektoren, Diagrammen oder ihre Eigenschaften ändern. Wenn Sie Änderungen an Ressourcen außerhalb des Speichers weitergeben möchten, definieren Sie Ereignisse speichern. Weitere Informationen finden Sie unter [Ereignishandler propagieren Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md)  
  
### Definieren eine Regel  
  
1.  Die Regel definieren, wie eine Klasse mit dem Präfix der `RuleOn` Attribut. Das Attribut ordnet die Regel mit einem Ihrer Domänenklassen, Beziehungen oder Diagrammelemente. Die Regel wird für jede Instanz dieser Klasse angewendet werden, der möglicherweise abstrakt.  
  
2.  Registrieren Sie die Regel durch Hinzufügen zum festgelegten zurückgegebene `GetCustomDomainModelTypes()` in Ihrer Domäne Modell\-Klasse.  
  
3.  Leiten Sie die Regelklasse von einer der abstrakten Klassen ab und Schreiben Sie den Code für die Execution\-Methode.  
  
 In den folgenden Abschnitten werden diese Schritte ausführlicher beschrieben.  
  
### So definieren Sie eine Regel auf eine Domänenklasse  
  
-   In einer Datei benutzerdefinierten Code eine Klasse definieren und zwischen den <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> Attribut:  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value – but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   Der Typ des Antragstellers im ersten Parameter kann eine Domänenklasse, Domäne, Form, Connectors oder Diagramm. In der Regel wenden Sie Regeln, um Domänenklassen und Beziehungen.  
  
     Die `FireTime` ist in der Regel `TopLevelCommit`. Dadurch wird sichergestellt, dass die Regel ausgeführt wird, nur, nachdem die wichtigsten Änderungen der Transaktion vorgenommen wurden. Die alternativen sind Inline bald nach der Änderung der Regel ausgeführt wird. und LocalCommit, der die Regel am Ende der aktuellen Transaktion ausgeführt wird \(die nicht das äußerste sein kann\). Sie können auch die Priorität einer Regel beeinflussen die Reihenfolge in der Warteschlange festlegen, aber dies ist eine unzuverlässigen Methode das gewünschte Ergebnis zu erreichen.  
  
-   Sie können eine abstrakte Klasse als Typ des Antragstellers angeben.  
  
-   Die Regel gilt für alle Instanzen der Klasse Betreff.  
  
-   Der Standardwert für `FireTime` TimeToFire.TopLevelCommit ist. Dies bewirkt, dass die Regel ausgeführt werden, wenn die äußerste Transaktion ein Commit ausgeführt wird. Eine Alternative ist TimeToFire.Inline. Dies bewirkt, dass die Regel bald nach dem auslösenden Ereignis ausgeführt wird.  
  
### Um die Regel zu registrieren.  
  
-   Fügen Sie Ihre Regelklasse zur Liste der von zurückgegebenen Typen `GetCustomDomainModelTypes` im Domänenmodell:  
  
    ```  
    public partial class ExampleDomainModel  
     {  
       protected override Type[] GetCustomDomainModelTypes()  
       {  
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
         types.Add(typeof(MyAddRule));  
         // If you add more rules, list them here.   
         return types.ToArray();  
       }  
     }  
  
    ```  
  
-   Wenn Sie nicht den Namen der Domäne Modellklasse sicher sind, suchen Sie in der Datei **Dsl\\GeneratedCode\\DomainModel.cs**  
  
-   Fügen Sie diesen Code in einer benutzerdefinierten Codedatei im DSL\-Projekt.  
  
### Schreiben Sie den Code für die Regel  
  
-   Leiten Sie die Regelklasse aus einem der folgenden Basisklassen:  
  
    |Basisklasse|Trigger|  
    |-----------------|-------------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|Ein Element, eine Verknüpfung oder eine Form wird hinzugefügt.<br /><br /> Verwenden Sie diese Option, um neue Beziehungen, zusätzlich zu neuen Elementen zu erkennen.|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|Ein Wert einer Domäne geändert wird. Das Methodenargument enthält die alten und neuen Werte.<br /><br /> Bei Formen mit dieser Regel wird ausgelöst, wenn die integrierte `AbsoluteBounds` Eigenschaft ändert, wenn die Form bewegt wird.<br /><br /> In vielen Fällen ist es einfacher, überschreiben `OnValueChanged` oder `OnValueChanging` in der Handler. Diese Methoden werden unmittelbar vor und nach der Änderung aufgerufen. Im Gegensatz dazu wird die Regel in der Regel am Ende der Transaktion ausgeführt werden. Weitere Informationen finden Sie unter [Handler für Wertänderungen von Domäneneigenschaften](../modeling/domain-property-value-change-handlers.md). **Note:**  Diese Regel wird nicht ausgelöst, wenn eine Verknüpfung erstellt oder gelöscht wird. Schreiben Sie stattdessen, ein `AddRule` und ein `DeleteRule` für die domänenbeziehung.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|Wird ausgelöst, wenn ein Element oder ein Link gelöscht werden soll. Die Eigenschaft ModelElement.IsDeleting gilt bis zum Ende der Transaktion.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|Ausgeführt, wenn ein Element oder ein Link gelöscht wurde. Die Regel wird ausgeführt, nachdem alle anderen Regeln einschließlich DeletingRules ausgeführt wurden. ModelElement.IsDeleting ist "false", und ModelElement.IsDeleted ist true. Um eine nachfolgende rückgängig zu ermöglichen, wird das Element nicht tatsächlich aus dem Arbeitsspeicher entfernt wird aus Store.ElementDirectory entfernt.|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|Ein Element wird aus einem Speicher\-Partition in eine andere verschoben.<br /><br /> \(Beachten Sie, dass dies nicht der grafisch Position einer Form verknüpft ist.\)|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|Diese Regel gilt nur für zwischen Domänen. Es wird ausgelöst, wenn Sie explizit ein Modellelement an beiden Enden einer Verbindung zuweisen.|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|Ausgelöst, wenn die Reihenfolge von Links zu oder von einem Element mit der MoveBefore oder MoveToIndex auf einen Link geändert wird.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|Ausgeführt, wenn eine Transaktion erstellt wird.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|Ausgeführt, wenn die Transaktion ein Commit ausgeführt wird.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|Ausgeführt, wenn die Transaktion wird ein Rollback ausgeführt werden.|  
  
-   Jede Klasse verfügt über eine Methode, die Sie außer Kraft setzen. Typ `override` in Ihrer Klasse, um ihn zu ermitteln. Die Parameter dieser Methode identifiziert das Element, das geändert wird.  
  
 Beachten Sie die folgenden Punkte zu Regeln:  
  
1.  Der Satz von Änderungen in einer Transaktion kann viele Regeln ausgelöst werden. In der Regel werden die Regeln ausgeführt, wenn die äußerste Transaktion ein Commit ausgeführt wird. Sie werden in einer nicht vorgegebenen Reihenfolge ausgeführt.  
  
2.  Eine Regel wird immer innerhalb einer Transaktion ausgeführt. Daher müssen Sie keinen erstellen Sie eine neue Transaktion zu ändern.  
  
3.  Regeln werden nicht ausgeführt, wenn eine Transaktion ein Rollback ausgeführt wird, oder wenn der Vorgänge zum Rückgängigmachen oder wiederholen. Diese Vorgänge werden alle Inhalte des Speichers in den vorherigen Zustand zurücksetzen. Daher, wenn die Regel den Zustand eines Elements außerhalb des Speichers ändert, möglicherweise nicht an Synchronism mit dem Informationsspeicher Inhalt aufbewahren. Um außerhalb des Speichers zu aktualisieren, ist es besser, Ereignisse zu verwenden. Weitere Informationen finden Sie unter [Ereignishandler propagieren Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
4.  Einige Regeln werden ausgeführt, wenn ein Modell aus der Datei geladen wird. Um zu bestimmen, ob beim Laden oder Speichern ausgeführt wird, verwenden Sie `store.TransactionManager.CurrentTransaction.IsSerializing`.  
  
5.  Wenn der Code der Regel Weitere Regel Trigger erstellt, sie werden am Ende der Liste der auslösenden hinzugefügt und ausgeführt, bevor die Transaktion abgeschlossen ist. DeletedRules werden nach allen anderen Regeln ausgeführt. Eine Regel kann oft in einer Transaktion, die einmal für jede Änderung ausgeführt werden.  
  
6.  Um Informationen zu und von Regeln zu übergeben, können Sie die Informationen im Speichern der `TransactionContext`. Dies ist nur ein Wörterbuch, das während der Transaktion beibehalten wird. Es wird verworfen, wenn die Transaktion endet. In jeder Regel die Ereignisargumente bieten Zugriff auf sie. Denken Sie daran, dass die Regeln nicht in einer vorhersagbaren Reihenfolge ausgeführt werden.  
  
7.  Verwenden Sie Regeln, nachdem Sie andere alternativen geprüft. Z. B. Wenn Sie eine Eigenschaft, die bei Änderung eines aktualisieren möchten, sollten Sie verwenden eine berechnete Eigenschaft. Wenn Sie die Größe oder Position einer Form einschränken möchten, verwenden Sie eine `BoundsRule`. Wenn auf eine Änderung eines Eigenschaftswerts reagieren soll, fügen Sie ein `OnValueChanged` Handler der Eigenschaft. Weitere Informationen finden Sie unter [Reagieren auf und Propagieren von Änderungen](../modeling/responding-to-and-propagating-changes.md).  
  
## Beispiel  
 Im folgenden Beispiel wird eine Eigenschaft aktualisiert, bei der Instanziierung einer domänenbeziehung zum Verknüpfen von zwei Elementen. Die Regel wird ausgelöst, nicht nur, wenn der Benutzer einen Link in einem Diagramm, sondern auch erstellt Programmcode eine Verknüpfung erstellt.  
  
 Um dieses Beispiel zu testen, erstellen Sie eine DSL mithilfe der Projektmappenvorlage "Aufgabenfluss", und fügen Sie den folgenden Code in eine Datei im Dsl\-Projekt. Erstellen Sie und führen Sie die Projektmappe, und öffnen Sie die Beispieldatei im Projekt debuggen. Zeichnen Sie einen Kommentar\-Link zwischen einem Kommentar\-Form und ein Element für fortlaufenden. Der Text im Kommentar ändert, Berichte für das aktuelle Element, dem Sie damit eine Verbindung hergestellt haben.  
  
 In der Praxis würden Sie normalerweise eine DeleteRule für jede AddRule schreiben.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  
  
namespace Company.TaskRuleExample  
{  
  
  [RuleOn(typeof(CommentReferencesSubjects))]  
  public class RoleRule : AddRule  
  {  
  
    public override void ElementAdded(ElementAddedEventArgs e)  
    {  
      base.ElementAdded(e);  
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;  
      Comment comment = link.Comment;  
      FlowElement subject = link.Subject;  
      Transaction current = link.Store.TransactionManager.CurrentTransaction;  
      // Don't want to run when we're just loading from file:  
      if (current.IsSerializing) return;  
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";  
    }  
  
  }  
  
  public partial class TaskRuleExampleDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(RoleRule));  
      return types.ToArray();  
    }  
  }  
  
}  
  
```  
  
## Siehe auch  
 [Ereignishandler propagieren Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [BoundsRules schränken Position und Größe von Formen ein](../modeling/boundsrules-constrain-shape-location-and-size.md)