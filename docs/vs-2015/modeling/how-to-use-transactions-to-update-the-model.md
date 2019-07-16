---
title: 'Vorgehensweise: Verwenden von Transaktionen zum Aktualisieren des Modells | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bbc09543d0ee0297678d3f205becc55a6b6d7714
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181504"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Vorgehensweise: Verwenden von Transaktionen zum Aktualisieren des Modells
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Transaktionen stellen Sie sicher, dass in den Speicher vorgenommenen Änderungen als Gruppe behandelt werden. Änderungen, die gruppiert werden, können ein Commit oder Rollback als einzelne Einheit sein.  
  
 Jedes Mal, wenn Programmcode ändert, hinzufügt oder löscht ein Element in den Store im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualisierungs- und Modellierungs-SDK, muss sie dies innerhalb einer Transaktion erfolgen. Es muss eine aktive Instanz der <xref:Microsoft.VisualStudio.Modeling.Transaction> der Store zugeordnet wird, wenn die Änderung erfolgt. Dies gilt für alle Modellelementen, Beziehungen, Formen, Diagramme und ihre Eigenschaften.  
  
 Der Transaktionsmechanismus können Sie die inkonsistente Zuständen zu vermeiden. Wenn ein Fehler während einer Transaktion auftritt, werden alle Änderungen ein Rollback ausgeführt. Wenn der Benutzer einen Rückgängig-Befehl ausführt, wird jede aktuelle Transaktion als einem einzigen Schritt behandelt. Benutzer kann nicht Teile einer Änderung, rückgängig machen, es sei denn, Sie ausdrücklich in getrennten Transaktionen eingefügt.  
  
## <a name="opening-a-transaction"></a>Öffnen eine Transaktion  
 Die einfachste Methode der Verwaltung einer Transaktion wird mit einem `using` -Anweisung eingeschlossen werden, einem `try...catch` Anweisung:  
  
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
  
 Wenn eine Ausnahme, die verhindert, die endgültige dass `Commit()` tritt auf, während die Änderungen der Store auf den vorherigen Zustand zurückgesetzt. Dadurch können Sie sicherstellen, dass Fehler nicht das Modell in einem inkonsistenten Zustand verfügbar ist.  
  
 Sie können eine beliebige Anzahl von Änderungen in einer Transaktion vornehmen. Sie können neue Transaktionen innerhalb einer aktiven Transaktion öffnen. Die geschachtelten Transaktionen müssen commit oder Rollback ausgeführt wurde, vor dem Ende des enthaltenden Transaktion. Weitere Informationen finden Sie im Beispiel für die <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> Eigenschaft.  
  
 Um die Änderungen permanent zu machen, sollten Sie `Commit` der Transaktion, bevor es verworfen wird. Wenn eine Ausnahme, die innerhalb der Transaktion nicht abgefangen wird auftritt, wird der Store in dem Zustand vor der Änderungen zurückgesetzt.  
  
## <a name="rolling-back-a-transaction"></a>Rollback einer Transaktion  
 Verwenden Sie eines dieser Taktiken, um sicherzustellen dass der Store in bleibt oder sich auf den Zustand vor der Transaktion zurückgesetzt:  
  
1. Auslösen einer Ausnahme, die innerhalb des Bereichs der Transaktion nicht abgefangen wird.  
  
2. Explizit Rollback der Transaktion:  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## <a name="transactions-do-not-affect-non-store-objects"></a>Transaktionen wirken sich nicht auf die nicht aus dem Store Objekte  
 Transaktionen gesteuert, die nur den Status der Store. Sie können keine teilweise Änderungen rückgängig gemacht werden, die zu externen Elementen wie z. B. Dateien, Datenbanken oder Objekte, die mit normalen Typen außerhalb der DSL-Definition deklariert wurden vorgenommen wurden.  
  
 Wenn eine Ausnahme dieser Änderung nicht mit dem Store lassen kann, sollten Sie diese Möglichkeit im Ausnahmehandler behandeln. Eine Möglichkeit, um sicherzustellen, dass externe Ressourcen mit den Objekten Store synchronisiert bleiben, besteht darin, jedes externes Objekt auf ein Element im Geschäft zu koppeln, mithilfe von Ereignishandlern. Weitere Informationen finden Sie unter [Handler weitergegeben werden Änderungen außerhalb der Ereignismodell](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
## <a name="rules-fire-at-the-end-of-a-transaction"></a>Auslösen von Regeln am Ende einer Transaktion  
 Bevor die Transaktion verworfen wird, werden am Ende einer Transaktion die Regeln, die angefügt werden, um Elemente im Speicher ausgelöst. Jede Regel ist eine Methode, die einem Modellelement angewendet wird, die geändert wurde. Beispielsweise sind "Reparieren" Regeln, die den Zustand einer Form zu aktualisieren, wenn seine Modellelement geändert hat, und das Erstellen einer Form, wenn ein Element des Modells erstellt wird. Es gibt keine Reihenfolge angegebenen ausgelöst. Eine Änderung durch eine Regel kann eine andere Regel ausgelöst werden.  
  
 Sie können Ihre eigenen Regeln definieren. Weitere Informationen zu Regeln finden Sie unter [reagieren auf und propagieren Änderungen](../modeling/responding-to-and-propagating-changes.md).  
  
 Regeln werden nach dem Vorgänge zum Rückgängigmachen, wiederholen oder einen Rollback-Befehl nicht ausgelöst.  
  
## <a name="transaction-context"></a>Transaktionskontext  
 Jede Transaktion besitzt ein Wörterbuch, in dem Sie alle Informationen speichern können Sie die gewünschten:  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 Dies ist besonders nützlich für die Übertragung von Informationen zwischen Regeln.  
  
## <a name="transaction-state"></a>Transaktionsstatus  
 In einigen Fällen, die Sie vermeiden müssen weiter eine Änderung, wenn die Änderung rückgängig machen oder Wiederholen einer Transaktions verursacht wird. Dies kann beispielsweise vorkommen, wenn Sie einen Eigenschaft-Wert-Handler schreiben, der von einem anderen Wert in der Store aktualisiert werden können. Da alle Werte in den Store mit der Rückgängig-Vorgang in ihren vorherigen Zustand zurückgesetzt wird, ist es nicht erforderlich, um die aktualisierten Werte zu berechnen. Verwenden Sie diesen Code:  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 Regeln können immer dann ausgelöst, wenn der Store ursprünglich aus einer Datei geladen wird. Um zu vermeiden, auf Veränderungen reagiert, verwenden Sie:  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```
