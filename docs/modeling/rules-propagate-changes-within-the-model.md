---
title: Regeln Weitergeben von Änderungen innerhalb des Modells | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: af086275f641e3237f8d22308c960ad30240b647
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2018
---
# <a name="rules-propagate-changes-within-the-model"></a>Regeln propagieren Änderungen im Modell
Erstellen Sie eine Store-Regel, um eine Änderung von einem Element zu einem anderen in Visualization and Modeling SDK (VMSDK) weitergegeben werden. Wenn eine Änderung auf jedes Element im Speicher erfolgt, sind Regeln ausgeführt werden, in der Regel auf, wenn die äußerste Transaktion ein Commit ausgeführt wird, geplant. Es gibt verschiedene Typen von Regeln für verschiedene Arten von Ereignissen, z. B. ein Element hinzufügen oder löschen. Sie können Regeln für bestimmte Typen von Elementen, Formen oder Diagramme anfügen. Viele integrierte Funktionen werden durch Regeln definiert: beispielsweise Regeln dafür sorgen, dass ein Diagramm aktualisiert wird, wenn das Modell ändert. Sie können Ihre einer domänenspezifischen Sprache anpassen, indem Sie eigene Regeln hinzufügen.  
  
 Store-Regeln sind besonders nützlich für die Weitergabe von Änderungen in den Speicher - d. h. Änderungen Modellelemente, Beziehungen, Formen oder Verbindungen und ihrer Domäne Eigenschaften. Regeln werden nicht ausgeführt, wenn der Benutzer die Befehle rückgängig machen oder Wiederholen aufruft. Stattdessen stellt der Transaktions-Manager sicher, dass es sich bei den Store-Inhalt auf den richtigen Zustand wiederhergestellt werden. Wenn Sie Änderungen an Ressourcen außerhalb des Informationsspeichers weitergeben möchten, verwenden Sie Ereignisse speichern. Weitere Informationen finden Sie unter [Handler verteilt Änderungen außerhalb der Ereignismodell](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
 Nehmen wir beispielsweise an, um anzugeben, dass ein weiteres Element eines anderen Typs in einen anderen Teil des Modells, wenn der Benutzer (oder Code) ein neues Element vom Typ ExampleDomainClass erstellt erstellt wird, werden sollen. Sie könnten eine AddRule schreiben und ExampleDomainClass zuordnen. Schreiben Sie Code in der Regel auf das zusätzliche Element zu erstellen.  
  
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
  
    // Code here propagates change as required - for example:  
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
>  Der Code einer Regel sollte den Status nur Elemente innerhalb der Store ändern; die Regel sollte also nur Modellelemente, Beziehungen, Formen, Connectors, Diagramme oder ihre Eigenschaften ändern. Wenn Sie Änderungen an Ressourcen außerhalb des Informationsspeichers weitergeben möchten, definieren Sie Ereignisse speichern. Weitere Informationen finden Sie unter [Handler verteilt Änderungen außerhalb der Ereignismodell](../modeling/event-handlers-propagate-changes-outside-the-model.md)  
  
### <a name="to-define-a-rule"></a>Um eine Regel zu definieren.  
  
1.  Die Regel definieren, wie eine Klasse mit dem Präfix der `RuleOn` Attribut. Das Attribut ordnet die Regel zu Ihrer Domänenklassen, die Beziehungen oder die Diagrammelemente. Die Regel wird auf jede Instanz dieser Klasse, die abstrakte möglicherweise, angewendet werden.  
  
2.  Registrieren Sie die Regel, indem Sie den Satz von zurückgegebenen hinzugefügt `GetCustomDomainModelTypes()` in Ihrer Modellklasse Domäne.  
  
3.  Leiten Sie die Regelklasse von einer abstrakten Klassen für die Regel, und Schreiben Sie den Code, der die excecution-Methode.  
  
 In den folgenden Abschnitten werden diese Schritte ausführlicher beschrieben.  
  
### <a name="to-define-a-rule-on-a-domain-class"></a>So definieren Sie eine Regel auf eine Domänenklasse  
  
-   Klicken Sie in einer Datei mit benutzerdefiniertem Code eine Klasse definieren, und mit Präfix der <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> Attribut:  
  
    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value - but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  
  
    ```  
  
-   Der Typ des Antragstellers im ersten Parameter möglich einer Domänenklasse, domänenbeziehung, Form, Connector oder Diagramm. In der Regel ist, wenden Sie Regeln auf Domänenklassen und Beziehungen.  
  
     Die `FireTime` ist in der Regel `TopLevelCommit`. Dadurch wird sichergestellt, dass die Regel ausgeführt wird, nur, nachdem alle primären Änderungen der Transaktion vorgenommen wurden. Die alternativen sind Inline, das die Regel bald nach der Änderung ausführt. und LocalCommit, die die Regel am Ende der aktuellen Transaktion ausgeführt wird (was bewirkt die äußerste möglicherweise nicht). Sie können auch die Priorität einer Regel, um zu beeinflussen, Reihenfolge in der Warteschlange festlegen, aber dies ist eine unzuverlässigen Methode das erforderliche Ergebnis zu erreichen.  
  
-   Sie können eine abstrakte Klasse als Typ des Antragstellers angeben.  
  
-   Die Regel gilt für alle Instanzen der Subject-Klasse.  
  
-   Der Standardwert für `FireTime` TimeToFire.TopLevelCommit ist. Dies bewirkt, dass die Regel ausgeführt werden, wenn die äußerste Transaktion ein Commit ausgeführt wird. Eine Alternative besteht TimeToFire.Inline. Dies bewirkt, dass die Regel so kurz nach dem auslösenden Ereignis ausgeführt werden.  
  
### <a name="to-register-the-rule"></a>Um die Regel zu registrieren.  
  
-   Fügen Sie Ihre Regelklasse zur Liste der Typen von zurückgegebenen `GetCustomDomainModelTypes` in Ihrem Domänenmodell:  
  
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
  
-   Wenn Sie nicht genau wissen, den Namen Ihrer Domäne Skriptobjektmodell-Klasse sind, suchen Sie in der Datei **Dsl\GeneratedCode\DomainModel.cs**  
  
-   Fügen Sie diesen Code in einer benutzerdefinierten Codedatei im Projekt DSL.  
  
### <a name="to-write-the-code-of-the-rule"></a>So schreiben Sie den Code der Regel  
  
-   Werden die Regelklasse von einer der folgenden Basisklassen abgeleitet:  
  
    |Basisklasse|Trigger|  
    |----------------|-------------|  
    |<xref:Microsoft.VisualStudio.Modeling.AddRule>|Ein Element, verknüpfen oder Form hinzugefügt wird.<br /><br /> Hiermit können Sie um neue Beziehungen, zusätzlich zu den neuen Elemente zu erkennen.|  
    |<xref:Microsoft.VisualStudio.Modeling.ChangeRule>|Ein Eigenschaftswert für die Domäne geändert wird. Das Methodenargument bietet die alten und neuen Werte.<br /><br /> Bei Formen mit dieser Regel wird ausgelöst, wenn die integrierte `AbsoluteBounds` Eigenschaft ändert, wenn die Form bewegt wird.<br /><br /> In vielen Fällen ist es praktischer sein, außer Kraft setzen `OnValueChanged` oder `OnValueChanging` in der Eigenschaft Handler. Diese Methoden werden aufgerufen, unmittelbar vor und nach der Änderung. Im Gegensatz dazu wird die Regel in der Regel am Ende der Transaktion ausgeführt werden. Weitere Informationen finden Sie unter [Domäne Eigenschaft Wert ändern Handler](../modeling/domain-property-value-change-handlers.md). **Hinweis:** mit dieser Regel wird nicht ausgelöst, wenn ein Link erstellt oder gelöscht wird. Schreiben Sie stattdessen eine `AddRule` und ein `DeleteRule` für die domänenbeziehung.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeletingRule>|Wird ausgelöst, wenn ein Element oder ein Link gelöscht werden sollen. Die Eigenschaft ModelElement.IsDeleting ist "true", bis zum Ende der Transaktion.|  
    |<xref:Microsoft.VisualStudio.Modeling.DeleteRule>|Ausgeführt, wenn ein Element oder ein Link gelöscht wurde. Die Regel wird ausgeführt, nachdem alle anderen Regeln einschließlich DeletingRules ausgeführt wurden. ModelElement.IsDeleting ist "false", und ModelElement.IsDeleted ist "true". Um eine nachfolgende rückgängig zu ermöglichen, wird das Element nicht tatsächlich aus dem Arbeitsspeicher entfernt wird aus den Store.ElementDirectory entfernt.|  
    |<xref:Microsoft.VisualStudio.Modeling.MoveRule>|Ein Element wird aus einem Store Partition verschoben.<br /><br /> (Beachten Sie, dass dies nicht mit einer Form die grafische Position verknüpft ist.)|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>|Diese Regel gilt nur für zwischen Domänen. Es wird ausgelöst, wenn Sie ein Modellelement an beiden Enden einer Verknüpfung explizit zuweisen.|  
    |<xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule>|Ausgelöst, wenn die Reihenfolge von Links zu oder von einem Element mit der MoveBefore oder MoveToIndex auf einen Link geändert wird.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>|Ausgeführt, wenn eine Transaktion erstellt wird.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>|Ausgeführt, wenn die Transaktion wird ein Commit ausgeführt werden.|  
    |<xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>|Ausgeführt, wenn die Transaktion wird ein Rollback ausgeführt werden.|  
  
-   Jede Klasse verfügt über eine Methode, die Sie außer Kraft setzen. Typ `override` in Ihrer Klasse, um ihn zu ermitteln. Die Parameter dieser Methode identifiziert das Element, das geändert wird.  
  
 Beachten Sie die folgenden Punkte bezüglich der Regeln aus:  
  
1.  Der Satz von Änderungen in einer Transaktion kann viele Regeln ausgelöst werden. In der Regel werden die Regeln ausgeführt, wenn die äußerste Transaktion ein Commit ausgeführt wird. Sie werden in einer nicht angegebenen Reihenfolge ausgeführt.  
  
2.  Eine Regel ist immer innerhalb einer Transaktion ausgeführt. Aus diesem Grund müssen Sie keinen erstellen Sie eine neue Transaktion, um Änderungen vorzunehmen.  
  
3.  Regeln werden nicht ausgeführt, wenn eine Transaktion ein Rollback ausgeführt wird oder die Vorgänge rückgängig gemacht bzw. wiederholt ausgeführt werden. Diese Vorgänge werden alle Inhalte des Speichers den ursprünglichen Zustand zurücksetzen. Aus diesem Grund, wenn die Regel den Zustand von anderem außerhalb des Informationsspeichers ändert, kann nicht in Synchronism mit dem Store Content gewährleisten. Um außerhalb der Speicher zu aktualisieren, ist es besser, Ereignisse zu verwenden. Weitere Informationen finden Sie unter [Handler verteilt Änderungen außerhalb der Ereignismodell](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
4.  Einige Regeln werden ausgeführt, wenn ein Modell aus der Datei geladen wird. Um zu bestimmen, ob beim Laden oder Speichern von ausgeführt wird, verwenden Sie `store.TransactionManager.CurrentTransaction.IsSerializing`.  
  
5.  Wenn der Code der Regel Weitere Regel Trigger erstellt, sie werden am Ende der Liste Auslösen von Ereignissen hinzugefügt werden und werden ausgeführt, bevor die Transaktion abgeschlossen ist. DeletedRules werden nach allen anderen Regeln ausgeführt. Eine Regel kann mehrere Male in einer Transaktion, einmal für jede Änderung ausgeführt.  
  
6.  Um Informationen zu und von Regeln zu übergeben, speichern Sie Informationen in den `TransactionContext`. Dies ist nur ein Wörterbuch, das während der Transaktion beibehalten wird. Es wird am Ende die Transaktion verworfen. In jeder Regel die Ereignisargumente bieten Zugriff auf sie. Denken Sie daran, dass Regeln nicht in einer vorhersagbaren Reihenfolge ausgeführt werden.  
  
7.  Verwenden Sie andere alternativen Berücksichtigung Regeln. Wenn Sie eine Eigenschaft, wenn sich ein ändert aktualisieren möchten, betrachten Sie beispielsweise eine berechnete Eigenschaft verwenden. Wenn Sie die Größe oder Position einer Form einschränken möchten, verwenden Sie eine `BoundsRule`. Wenn auf eine Änderung eines Eigenschaftswerts reagieren sollen, fügen Sie eine `OnValueChanged` Handler für die Eigenschaft. Weitere Informationen finden Sie unter [Weitergeben von Änderungen und reagieren auf](../modeling/responding-to-and-propagating-changes.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel aktualisiert eine Eigenschaft, wenn eine domänenbeziehung zum Verknüpfen von zwei Elementen instanziiert wird. Die Regel wird ausgelöst werden, nicht nur, wenn der Benutzer einen Link in einem Diagramm, sondern auch erstellt, wenn Programmcode eine Verknüpfung erstellt.  
  
 Zum Testen dieses Beispiels erstellen Sie eine DSL mit der Projektmappe (Vorlage) Datenflusstask, und fügen Sie folgenden Code in einer Datei in der Dsl-Projekt. Erstellen Sie und führen Sie die Projektmappe, und öffnen Sie die Beispieldatei im Projekt debuggen. Ziehen Sie eine Comment-Verknüpfung zwischen einer Form "Kommentar" und ein Element für fortlaufenden. Der Text im Bericht auf das letzte Element, dem Sie damit eine Verbindung hergestellt haben Kommentar geändert.  
  
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
 [Ereignishandler Weitergeben von Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [BoundsRules schränken Position und Größe von Formen ein](../modeling/boundsrules-constrain-shape-location-and-size.md)