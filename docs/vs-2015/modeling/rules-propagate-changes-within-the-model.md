---
title: Regeln propagieren Änderungen im Modell | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ab05923a02176f4c0d8aa30ac9d26b0e41868396
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49222715"
---
# <a name="rules-propagate-changes-within-the-model"></a>Regeln propagieren Änderungen im Modell
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können eine Store-Regel, um eine Änderung von einem Element zu einem anderen im Visualisierungs- und Modellierungs-SDK (VMSDK) weitergegeben werden erstellen. Wenn eine Änderung auf ein Element in der Store erfolgt, werden Regeln ausgeführt werden, in der Regel, wenn die äußerste Transaktion ein Commit ausgeführt wird, geplant. Es gibt verschiedene Typen von Regeln für verschiedene Arten von Ereignissen, z. B. ein Element hinzugefügt oder gelöscht wird. Sie können Regeln auf bestimmte Typen von Elementen, Formen und Diagrammen anfügen. Viele integrierte Features durch Regeln definiert werden: z. B. Regeln stellen sicher, dass ein Diagramm aktualisiert wird, wenn das Modell geändert wird. Sie können Ihrer domänenspezifischen Sprache anpassen, indem Sie eigene Regeln hinzufügen.  
  
 Store-Regeln sind besonders nützlich, für die Weitergabe von Änderungen in den Speicher – d. h. an Modellelementen, Beziehungen, Formen oder Konnektoren und ihrer Domäne Eigenschaften. Regeln werden nicht ausgeführt werden, wenn der Benutzer die Befehle zum Rückgängigmachen oder Wiederholen aufruft. Stattdessen stellt der Transaktions-Manager sicher, dass es sich bei den Store-Inhalt auf den richtigen Zustand wiederhergestellt werden. Wenn Sie Änderungen an Ressourcen außerhalb des Speichers weitergeben möchten, verwenden Sie die Store-Ereignisse. Weitere Informationen finden Sie unter [Handler weitergegeben werden Änderungen außerhalb der Ereignismodell](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
 Nehmen wir beispielsweise an, dass Sie angeben möchten, dass, wenn der Benutzer (oder in Ihrem Code) ein neues Element vom Typ ExampleDomainClass erstellt, ein weiteres Element eines anderen Typs in einen anderen Teil des Modells erstellt wird. Sie können eine AddRule schreiben und ExampleDomainClass zuzuordnen. Sie würden Code schreiben, in der Regel auf das zusätzliche Element zu erstellen.  
  
```csharp  
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
>  Der Code eine Regel muss den Zustand nur der Elemente in der Store ändern; die Regel sollte, also nur Modellelementen, Beziehungen, Formen, Konnektoren, Diagramme oder deren Eigenschaften ändern. Wenn Sie Änderungen an Ressourcen außerhalb des Speichers weitergeben möchten, definieren Sie Store-Ereignisse. Weitere Informationen finden Sie unter [Handler weitergegeben werden Änderungen außerhalb der Ereignismodell](../modeling/event-handlers-propagate-changes-outside-the-model.md)  
  
### <a name="to-define-a-rule"></a>Definieren eine Regel  
  
1.  Die Regel definieren, wie eine Klasse mit dem Präfix die `RuleOn` Attribut. Das Attribut ordnet die Regel mit einem Ihrer Domänenklassen, Beziehungen oder Diagrammelemente. Die Regel wird auf jede Instanz dieser Klasse angewendet werden, der möglicherweise abstrakt.  
  
2.  Registrieren Sie die Regel, indem Sie auf den Satz von zurückgegebenen hinzufügen `GetCustomDomainModelTypes()` in Ihrer Domain-Model-Klasse.  
  
3.  Die Regelklasse Ableiten von der abstrakten Klassen für die Regel, und schreiben den Code für die Execution-Methode.  
  
 In den folgenden Abschnitten werden diese Schritte ausführlicher beschrieben.  
  
### <a name="to-define-a-rule-on-a-domain-class"></a>Definieren eine Regel für eine Domänenklasse  
  
-   Klicken Sie in einer benutzerdefinierten Codedatei zu verlassen, definieren Sie eine Klasse, und stellen sie mit der <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> Attribut:  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value – but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   Im ersten Parameter der Betreff-Typ kann es sich um eine Domänenklasse, domänenbeziehung, Form, Connectors, oder ein Diagramm sein. In der Regel können Sie Regeln anwenden, um Domänenklassen und Beziehungen.  
  
     Die `FireTime` ist in der Regel `TopLevelCommit`. Dadurch wird sichergestellt, dass die Regel ausgeführt wird, nur, nachdem die wichtigsten Änderungen der Transaktion vorgenommen wurden. Die alternativen sind Inline, die die Regel ausgeführt, kurz nach der Umstellung wird; und LocalCommit, die die Regel am Ende der aktuellen Transaktion ausgeführt wird (was die äußerste möglicherweise nicht). Sie können auch festlegen, die Priorität einer Regel, um die Reihenfolge, in der Warteschlange zu beeinflussen, aber dies ist eine unzuverlässigen Methode das benötigte Ergebnis zu erreichen.  
  
-   Sie können eine abstrakte Klasse angeben, wie der Antragstellertyp.  
  
-   Die Regel gilt für alle Instanzen der Subject-Klasse.  
  
-   Der Standardwert für `FireTime` TimeToFire.TopLevelCommit ist. Dies bewirkt, dass die Regel ausgeführt werden, wenn die äußerste Transaktion ein Commit ausgeführt wird. Alternativ kann es sich um TimeToFire.Inline. Dies bewirkt, dass die Regel, die kurz nach dem auslösenden Ereignis ausgeführt werden.  
  
### <a name="to-register-the-rule"></a>Um die Regel zu registrieren.  
  
-   Fügen Sie Ihrer Klasse zur Liste der Typen, die vom `GetCustomDomainModelTypes` in Ihrem Domänenmodell:  
  
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
  
-   Wenn Sie nicht mit dem Namen Ihrer Domäne Modellklasse sicher sind, suchen Sie in der Datei **Dsl\GeneratedCode\DomainModel.cs**  
  
-   Schreiben Sie diesen Code in einer benutzerdefinierten Codedatei in das DSL-Projekt.  
  
### <a name="to-write-the-code-of-the-rule"></a>Den Code der Regel schreiben  
  
-   Leiten Sie die Regelklasse, von einem der folgenden Basisklassen:  
  
    |Basisklasse|Trigger|  
    |----------------|-------------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|Ein Element, eine Verknüpfung oder eine Form wird hinzugefügt.<br /><br /> Verwenden Sie diese Option, um neue Beziehungen, zusätzlich zu neuen Elementen zu erkennen.|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|Ein Domäne-Eigenschaftswert geändert wird. Das Methodenargument enthält die alten und neuen Werte.<br /><br /> Für Formen die, mit dieser Regel wird ausgelöst, wenn die integrierte `AbsoluteBounds` eigenschaftsänderungen, wenn die Form bewegt wird.<br /><br /> In vielen Fällen ist es einfacher, außer Kraft setzen `OnValueChanged` oder `OnValueChanging` in der Handler. Diese Methoden werden unmittelbar vor und nach der Änderung aufgerufen. Im Gegensatz dazu wird die Regel in der Regel am Ende der Transaktion ausgeführt werden. Weitere Informationen finden Sie unter [Handler für Wertänderungen von Domäne](../modeling/domain-property-value-change-handlers.md). **Hinweis:** mit dieser Regel wird nicht ausgelöst, wenn ein Link erstellt oder gelöscht wird. Schreiben Sie stattdessen eine `AddRule` und `DeleteRule` für die domänenbeziehung.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|Wird ausgelöst, wenn ein Element oder ein Link gelöscht werden soll. Die Eigenschaft ModelElement.IsDeleting gilt bis zum Ende der Transaktion.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|Ausgeführt, wenn ein Element oder ein Link gelöscht wurde. Die Regel ausgeführt wird, nachdem alle anderen Regeln einschließlich DeletingRules ausgeführt wurden. ModelElement.IsDeleting ist "false", und ModelElement.IsDeleted ist "true". Um für eine nachfolgende Rollback zu ermöglichen, wird das Element nicht tatsächlich aus dem Arbeitsspeicher entfernt wird er aus Store.ElementDirectory entfernt.|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|Ein Element wird aus einem Speicher-Partition in eine andere verschoben.<br /><br /> (Beachten Sie, dass dies nicht mit der grafischen Position einer Form verknüpft ist.)|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|Diese Regel gilt nur für Beziehungen. Es wird ausgelöst, wenn Sie ein Modellelement an beiden Enden einer Verknüpfung explizit zuweisen.|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|Ausgelöst, wenn die Reihenfolge von Links zu oder von einem Element mit den Methoden MoveBefore oder MoveToIndex einen Link geändert wird.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|Ausgeführt, wenn eine Transaktion erstellt wird.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|Ausgeführt, wenn die Transaktion ein Commit ausgeführt wird.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|Ausgeführt, wenn die Transaktion wird ein Rollback ausgeführt werden.|  
  
-   Jede Klasse verfügt über eine Methode, die Sie außer Kraft setzen. Typ `override` in der Klasse ermittelt. Die Parameter dieser Methode gibt das Element, das geändert wird.  
  
 Beachten Sie die folgenden Punkte bezüglich der Regeln aus:  
  
1.  Der Satz von Änderungen in einer Transaktion möglicherweise viele Regeln ausgelöst. In der Regel werden die Regeln ausgeführt, wenn die äußerste Transaktion ein Commit ausgeführt wird. Sie werden in einer nicht vorgegebenen Reihenfolge ausgeführt.  
  
2.  Eine Regel wird immer innerhalb einer Transaktion ausgeführt. Aus diesem Grund müssen Sie keinen, erstellen Sie eine neue Transaktion, um Änderungen vorzunehmen.  
  
3.  Regeln werden nicht ausgeführt werden, wenn eine Transaktion ein Rollback ausgeführt wird, oder die Vorgänge zum Rückgängigmachen oder Wiederholen-Vorgang ausgeführt werden. Diese Vorgänge werden alle Inhalte von den Store den ursprünglichen Zustand zurückgesetzt. Aus diesem Grund, wenn Ihre Regel den Zustand des irgendetwas außerhalb der Store geändert wird, kann nicht an Synchronism mit dem Store Content aufbewahren. Um den Store Zustand zu aktualisieren, ist es besser, Ereignisse zu verwenden. Weitere Informationen finden Sie unter [Handler weitergegeben werden Änderungen außerhalb der Ereignismodell](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
4.  Einige Regeln werden ausgeführt, wenn ein Modell aus der Datei geladen wird. Um zu bestimmen, ob beim Laden oder das Speichern von ausgeführt wird, verwenden Sie `store.TransactionManager.CurrentTransaction.IsSerializing`.  
  
5.  Wenn der Code der Regel Weitere Regel wird erstellt, sie werden am Ende der Liste der Auslösung hinzugefügt werden, und werden ausgeführt werden, bevor die Transaktion abgeschlossen ist. DeletedRules werden nach allen anderen Regeln ausgeführt. Eine Regel kann oft in einer Transaktion, die einmal für jede Änderung ausgeführt werden.  
  
6.  Um Informationen zu und von Regeln zu übergeben, können Sie die Informationen im Speichern der `TransactionContext`. Dies ist nur ein Wörterbuch, das während der Transaktion beibehalten wird. Es wird verworfen, wenn am Ende der Transaktion. Die Ereignisargumente, die in jeder Regel geben Sie den Zugriff darauf. Denken Sie daran, dass die Regeln nicht in einer vorhersagbaren Reihenfolge ausgeführt werden.  
  
7.  Verwenden Sie Regeln nach Berücksichtigung andere Alternativen. Wenn Sie eine Eigenschaft, wenn ein Wert ändert aktualisieren möchten, betrachten Sie beispielsweise eine berechnete Eigenschaft verwenden. Wenn Sie die Größe oder Position einer Form einschränken möchten, verwenden Sie eine `BoundsRule`. Wenn Sie auf eine Änderung eines Eigenschaftswerts zu reagieren möchten, Hinzufügen einer `OnValueChanged` Handler, der die Eigenschaft. Weitere Informationen finden Sie unter [reagieren auf und propagieren Änderungen](../modeling/responding-to-and-propagating-changes.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird eine Eigenschaft aktualisiert, wenn eine domänenbeziehung instanziiert wird, um zwei Elemente zu verknüpfen. Die Regel wird ausgelöst, nicht nur, wenn der Benutzer einen Link in einem Diagramm, sondern auch erstellt, wenn Programmcode eine Verknüpfung erstellt.  
  
 Klicken Sie zum Testen dieses Beispiels erstellen Sie eine DSL mithilfe der Lösungsvorlage Aufgabenfluss, und fügen Sie den folgenden Code in einer Datei im Dsl-Projekt. Erstellen Sie und führen Sie die Projektmappe, und öffnen Sie die Beispieldatei im Projekt debuggen. Zeichnen Sie einen Kommentar-Link zwischen einem Kommentar-Form und ein Element für fortlaufenden. Der Text in die Kommentar-Änderungen auf den Bericht auf das letzte Element, dem Sie damit eine Verbindung hergestellt haben.  
  
 In der Praxis würden Sie in der Regel eine DeleteRule für jede AddRule schreiben.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Ereignishandler propagieren Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [BoundsRules schränken Position und Größe von Formen ein](../modeling/boundsrules-constrain-shape-location-and-size.md)



