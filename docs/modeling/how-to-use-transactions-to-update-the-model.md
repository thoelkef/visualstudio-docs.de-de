---
title: 'Vorgehensweise: Verwenden von Transaktionen zum Aktualisieren des Modells | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: ecd9645bfb202d83bf672d03d3c6903a889677f9
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/10/2018
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Gewusst wie: Verwenden von Transaktionen zum Aktualisieren des Modells
Transaktionen stellen Sie sicher, dass Änderungen an den Store wurden als eine Gruppe behandelt werden. Änderungen, die gruppiert werden können ein Commit oder Rollback als einzelne Einheit.  
  
 Bei jedem Programmcode ändert, hinzufügt oder löscht jedes Element im Speicher [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK muss geschieht dies innerhalb einer Transaktion. Es muss eine aktive Instanz von <xref:Microsoft.VisualStudio.Modeling.Transaction> dem Speicher zugeordnet wird, wenn die Änderung erfolgt. Dies gilt für alle betroffenen Modellelemente, Beziehungen, Formen, Diagramme und ihre Eigenschaften.  
  
 Der Transaktionsmechanismus hilft Ihnen inkonsistente Zustände zu vermeiden. Wenn ein Fehler während einer Transaktion auftritt, werden alle Änderungen rückgängig gemacht. Wenn der Benutzer einen Befehl "Rückgängig" ausführt, wird jede letzte Transaktion als einem einzigen Schritt behandelt. Der Benutzer nicht Bestandteile eine aktuelle Änderung rückgängig machen, es sei denn, Sie explizit in getrennten Transaktionen eingefügt.  
  
## <a name="opening-a-transaction"></a>Öffnen eine Transaktion  
 Die einfachste Methode zur Verwaltung einer Transaktions wird mit einem `using` -Anweisung eingeschlossen werden, eine `try...catch` Anweisung:  
  
```  
Store store; ...  
try  
{  
  using (Transaction transaction =  
    store.TransactionManager.BeginTransaction("update model"))  
    // Outermost transaction must always have a name.  
  {  
    // Make several changes in Store:  
    Person p = new Person(store);  
    p.FamilyTreeModel = familyTree;  
    p.Name = "Edward VI";  
    // end of changes to Store  
  
    transaction.Commit(); // Don't forget this!  
  } // transaction disposed here  
}  
catch (Exception ex)  
{  
  // If an exception occurs, the Store will be   
  // rolled back to its previous state.  
}  
```  
  
 Wenn eine Ausnahme, die verhindert, die endgültige dass `Commit()` tritt auf, während die Änderungen der Speicher auf den ursprünglichen Zustand zurückgesetzt. Dadurch können Sie sicherstellen, dass Fehler nicht das Modell in einem inkonsistenten Zustand verlassen.  
  
 Sie können eine beliebige Anzahl von Änderungen innerhalb einer Transaktion vornehmen. Sie können neue Transaktionen innerhalb einer aktiven Transaktion öffnen. Geschachtelten Transaktionen müssen einen commit oder Rollback vor dem Ende der enthaltenden Transaktion. Weitere Informationen finden Sie im Beispiel für die <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> Eigenschaft.  
  
 Um Ihre Änderungen permanent zu machen, sollten Sie `Commit` der Transaktion, bevor sie freigegeben ist. Wenn eine Ausnahme, die innerhalb der Transaktion nicht aufgefangen werden kann auftritt, wird der Speicher in dem Zustand vor der Änderungen zurückgesetzt.  
  
## <a name="rolling-back-a-transaction"></a>Rollback einer Transaktion  
 Um sicherzustellen, dass der Speicher im verbleibt oder auf den Zustand vor der Transaktion zurückgesetzt, können Sie eine der folgenden Taktiken:  
  
1.  Löst eine Ausnahme, die innerhalb des Bereichs der Transaktion nicht aufgefangen werden kann.  
  
2.  Explizit Rollback der Transaktion:  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## <a name="transactions-do-not-affect-non-store-objects"></a>Transaktionen wirken sich nicht auf die nicht aus dem Store-Objekte  
 Transaktionen Regeln nur den Status des Speichers. Sie können keine partielle Änderungen rückgängig machen, die zu externen Elementen wie Dateien, Datenbanken oder Objekte, die mit normalen Typen außerhalb der DSL-Klassendefinition deklariert wurden vorgenommen wurden.  
  
 Wenn eine Ausnahme eine solche Änderung inkonsistent mit dem Store lassen kann, sollten Sie diese Möglichkeit im Ausnahmehandler behandeln. Eine Möglichkeit, um sicherzustellen, dass externe Ressourcen mit den Speicherobjekten synchronisiert bleiben werden mithilfe von Ereignishandlern jedes externes Objekt auf ein Element im Store zu verknüpfen. Weitere Informationen finden Sie unter [Handler verteilt Änderungen außerhalb der Ereignismodell](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
## <a name="rules-fire-at-the-end-of-a-transaction"></a>Auslösen von Regeln am Ende einer Transaktion  
 Bevor die Transaktion freigegeben wird, werden am Ende einer Transaktion zugeordneten Elemente im Speicher Regeln ausgelöst. Jede Regel ist eine Methode, die mit einem Modellelement angewendet wird, die geändert wurden. Beispielsweise sind "Reparieren" Regeln, die den Zustand einer Form aktualisieren, wenn seine Modellelement geändert hat, und die eine Form "erstellt, wenn ein Modellelement erstellt wird. Es gibt keine angegebenen auslösungsreihenfolge. Eine Änderung durch eine Regel kann eine andere Regel ausgelöst werden.  
  
 Sie können Ihre eigenen Regeln definieren. Weitere Informationen zu Regeln finden Sie unter [Weitergeben von Änderungen und reagieren auf](../modeling/responding-to-and-propagating-changes.md).  
  
 Regeln werden nach einer Rückgängig, wiederholen oder einen Rollbackbefehl nicht ausgelöst.  
  
## <a name="transaction-context"></a>Bereits verwendeten Transaktionskontext  
 Jede Transaktion besitzt ein Wörterbuch, in dem Sie alle Informationen speichern können Sie die gewünschte:  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 Dies ist besonders nützlich für die Übertragung von Informationen zwischen Regeln.  
  
## <a name="transaction-state"></a>Transaktionsstatus  
 In einigen Fällen, die Sie zur Vermeidung müssen weitergeben eine Änderung, wenn die Änderung durch Rückgängigmachen oder Wiederherstellen von einer Transaktions verursacht wird. Dies kann beispielsweise vorkommen, wenn Sie einen Eigenschaft-Wert-Handler schreiben, der einen anderen Wert im Speicher aktualisiert werden können. Da die Rückgängig-Vorgang alle Werte in den Speicher in ihren vorherigen Zustand zurückgesetzt wird, ist es nicht notwendig, die aktualisierten Werte zu berechnen. Verwenden Sie diesen Code ein:  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 Regeln können immer dann ausgelöst, wenn der Speicher ursprünglich aus einer Datei geladen wird. Zur Vermeidung von Antworten auf diese Änderungen zu verwenden:  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```