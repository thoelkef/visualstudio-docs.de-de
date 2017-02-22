---
title: "Gewusst wie: Verwenden von Transaktionen zum Aktualisieren des Modells | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 7
caps.handback.revision: 7
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Gewusst wie: Verwenden von Transaktionen zum Aktualisieren des Modells
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Transaktionen sicherzustellen, dass Änderungen, die im Speicher vorgenommen wurden, als Gruppe behandelt werden.  Änderungen, die als Einheit ein Commit oder Rollback gruppiert sind.  
  
 Sobald der Programmcode hinzufügt, ändert oder löscht jedes Element im Speicher in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualisierung und Modellieren SDK, muss er innerhalb einer Transaktion.  Es muss eine aktive Instanz von <xref:Microsoft.VisualStudio.Modeling.Transaction> geben den Speicher zugeordnet sind, wenn die Änderung ausgeführt wird.  Dies gilt für alle Modellelemente, Beziehungen, Formen, Diagramme und ihre Eigenschaften zu.  
  
 Der Mechanismus für Transaktionen hilft Ihnen, zu inkonsistenten Zustand zu vermeiden.  Wenn ein Fehler während einer Transaktion auftritt, stellen alle Änderungen zurück.  Wenn der Benutzer einen Befehl Rückgängig ausführt, wird jede neue Transaktion als Schritt behandelt.  Der Benutzer kann Teile einer neuen Änderung nicht rückgängig gemacht werden, es sei denn, Sie sie in separaten Transaktionen explizit einfügen.  
  
## Eine Transaktion öffnen  
 Die bequemste Methode für die Verwaltung einer Transaktion mit einer `using`\-Anweisung, die in einer `try...catch`\-Anweisung eingeschlossen werden:  
  
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
  
 Wenn eine Ausnahme, die während der letzten `Commit()`verhindert Änderungen auftritt, wird der Speicher auf ihren vorherigen Zustand zurückgesetzt.  Dies hilft Ihnen, um sicherzustellen, dass keine Fehler in einem inkonsistenten Zustand des Modells lassen.  
  
 Sie können eine beliebige Anzahl von Änderungen innerhalb einer Transaktion erstellen.  Sie können neue Transaktionen innerhalb einer aktiven Transaktion öffnen.  Die geschachtelten Transaktionen müssen sich vor den enthaltenden Beenden Transaktionen einen Commit bzw. Rollback.  Weitere Informationen finden Sie im Beispiel für die <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A>\-Eigenschaft.  
  
 Um die permanente Änderung vorzunehmen, sollten Sie `Commit` die Transaktion bevor sie wieder zugänglich gemacht wird.  Wenn eine Ausnahme auftritt, die nicht innerhalb der Transaktion abgefangen wird, wird der Speicher auf seinen Zustand vor den Änderungen zurückgesetzt.  
  
## Eine Transaktion zurücksetzen  
 Um sicherzustellen, dass der Speicher in verbleibt oder in den Zustand vor der Transaktion wiederhergestellt werden kann, können Sie eine dieser Taktiken verwenden:  
  
1.  Lösen Sie eine Ausnahme aus, die sich nicht im Gültigkeitsbereich der Transaktion abgefangen wird.  
  
2.  Setzen Sie explizit die Transaktion zurück:  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## Transaktionen wirken sich nicht auf Objekte Nicht\-Speicher  
 Regeln für Transaktionen nur den Zustand des Speichers.  Sie können partielle Änderungen nicht rückgängig machen, die zu externen Elementen wie Dateien, Datenbanken oder Objekten vorgenommen wurden, die Sie mit gewöhnlichen Typen außerhalb der DSL\-Definition deklariert wurden.  
  
 Wenn eine Ausnahme möglicherweise eine solche Änderung im Speicher inkonsistent. h., sollten Sie diese Möglichkeit im Ausnahmehandler verarbeiten.  Eine Möglichkeit, zu überprüfen, ob externe Ressourcen mit den Speicherobjekten synchronisiert bleiben, ist jedes externe Objekt auf einen speicherinternen Element zu verknüpfen, indem Sie Ereignishandler verwendet.  Weitere Informationen finden Sie unter [Ereignishandler propagieren Änderungen außerhalb des Modells](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
## Regeln lösen beim Ende einer Transaktion aus  
 Am Ende einer Transaktion, bevor die Transaktion freigegeben wird, werden die Regeln, die für die Elemente im Speicher verbunden sind, ausgelöst.  Jede Regel ist eine Methode, die zu einem Modellelement angewendet wird, das geändert wurde.  Es gibt z. B. „korrigieren oben“ Regeln, die den Zustand einer Form zu aktualisieren, wenn das Modellelement geändert hat, und eine Form erstellen, wenn ein Modellelement erstellt wird.  Es gibt keine bestimmte Zündfolge.  Eine Regel, die durch eine Änderung vorgenommen wurde, kann eine andere Regel auslösen.  
  
 Sie können definieren Regeln besitzen.  Weitere Informationen zu Regeln finden Sie unter [Reagieren auf und Propagieren von Änderungen](../modeling/responding-to-and-propagating-changes.md).  
  
 Regeln lösen keine nachdem ein Rückgängig\- oder ein Rollback für eine wiederholte Befehl aus.  
  
## Transaktions\-Kontext  
 Jede Transaktion ist ein Wörterbuch, in dem Sie alle Informationen können, die Sie speichern möchten:  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 Dies ist zum Übertragen von Informationen zwischen Regeln hilfreich.  
  
## Zustand der Transaktion  
 In einigen Fällen müssen Sie eine Änderung weitergegeben werden vermeiden, wenn die Änderung verursacht wird, indem eine Transaktion rückgängig gemacht bzw. wiederholt.  Dies kann der Fall sein, z. B. wenn Sie einen Eigenschaftswert Handler schreiben, der einen anderen Wert im Speicher aktualisieren kann.  Da der Rückgängig\-Vorgang alle Werte im Speicher zu ihren vorherigen Zustand zurückgesetzt wird, ist es nicht erforderlich, aktualisierte Werte zu berechnen.  Verwenden Sie den folgenden Code:  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 Regeln können ausgelöst werden, wenn der Speicher zunächst aus einer Datei geladen wird.  So reagieren Sie auf diese Änderungen zu vermeiden, verwenden Sie:  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```