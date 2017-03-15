---
title: "Berechnete und benutzerdefinierte Speichereigenschaften | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Domain-Specific Language, Programmieren von Domäneneigenschaften"
ms.assetid: 42b785f9-2b0f-4f13-a6b4-246e5e0d477a
caps.latest.revision: 19
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 19
---
# Berechnete und benutzerdefinierte Speichereigenschaften
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Alle Domäneneigenschaften in eine domänenspezifische Sprache \(DSL\) für den Benutzer auf das Diagramm und in Ihrer Sprache\-Explorer angezeigt werden können und Programmcode zugegriffen werden können. Eigenschaften unterscheiden sich jedoch auf die Weise, dass deren Werte gespeichert werden.  
  
## Arten von Domäneneigenschaften  
 In der DSL\-Definition legen Sie die **Art** einer Domäneneigenschaft, wie in der folgenden Tabelle aufgeführt:  
  
|Art der Domäne\-Eigenschaft|Beschreibung|  
|---------------------------------|------------------|  
|**Standard** \(Standard\)|Eine Domäneneigenschaft, die in gespeichert ist die *Speichern* und in der Datei serialisiert.|  
|**Berechnet**|Eine schreibgeschützte\-Eigenschaft, die nicht im Speicher gespeichert, aber von anderen Werten berechnet wird.<br /><br /> Z. B. `Person.Age` konnte aus berechnet `Person.BirthDate`.<br /><br /> Sie müssen den Code bereitstellen, der die Berechnung ausführt. In der Regel können Sie den Wert von anderen Domäneneigenschaften berechnen. Sie können jedoch auch externe Ressourcen.|  
|**Benutzerdefinierte Speicherung**|Eine Domäneneigenschaft, die nicht direkt im Speicher gespeichert, jedoch kann Get\- und Set.<br /><br /> Sie müssen die Methoden bereit, die den Wert abrufen und festlegen.<br /><br /> Z. B. `Person.FullAddress` in gespeichert werden `Person.StreetAddress`, `Person.City`, und `Person.PostalCode`.<br /><br /> Sie können auch externe Ressourcen, z. B. zum Abrufen und Festlegen von Werten aus einer Datenbank zugreifen.<br /><br /> Der Code sollte nicht Werte im Speicher festgelegt bei `Store.InUndoRedoOrRollback` gilt. Finden Sie unter [Transaktionen und benutzerdefinierte Setter](#setters).|  
  
## Der Code bereitstellen für die berechneten oder benutzerdefinierte Speichereigenschaft  
 Wenn Sie die Art einer Domäneneigenschaft auf berechnete oder einen benutzerdefinierten Speicher festlegen, müssen Sie Methoden für den Datenzugriff bieten. Wenn Sie die Projektmappe erstellen, informiert ein Fehlerbericht Sie erforderlich sind.  
  
#### Zum Definieren einer berechneten oder benutzerdefinierte Storage\-Eigenschaft  
  
1.  Wählen Sie in "DslDefinition.DSL", die Domäneneigenschaft im Diagramm oder im **DSL\-Explorer**.  
  
2.  In der **Eigenschaften** legen die **Art** Feld **berechnete** oder **benutzerdefinierten Speicher**.  
  
     Stellen Sie sicher, dass Sie auch festlegen, haben die **Typ** auf den gewünschten.  
  
3.  Klicken Sie auf **Alle Vorlagen transformieren** in der Symbolleiste der **Projektmappen\-Explorer**.  
  
4.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
     Sie erhalten die folgende Fehlermeldung angezeigt: "*Ihreklasse* enthält keine Definition für Get*YourProperty*."  
  
5.  Doppelklicken Sie auf die Fehlermeldung angezeigt.  
  
     Dsl\\GeneratedCode\\DomainClasses.cs oder DomainRelationships.cs wird geöffnet. Oberhalb der markierten Methodenaufruf, ein Kommentar aufgefordert, eine Implementierung für Get bereitstellen*YourProperty*\(\).  
  
    > [!NOTE]
    >  Diese Datei wird von "DslDefinition.DSL" generiert. Wenn Sie diese Datei bearbeiten, die Änderungen verloren, auf den, nächsten **Alle Vorlagen transformieren**. Fügen Sie stattdessen die gewünschte Methode in einer separaten Datei.  
  
6.  Erstellen oder öffnen Sie eine Datei in einem separaten Ordner, z. B. CustomCode\\*YourDomainClass*. Cs.  
  
     Stellen Sie sicher, dass der Namespace des generierten Codes identisch ist.  
  
7.  Schreiben Sie eine partielle Implementierung der Domänenklasse, in der Klassendatei. In der Klasse schreiben Sie eine Definition für die fehlende `Get` \-Methode, die das folgende Beispiel ähnelt:  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8.  Wenn Sie festlegen, **Artbenutzerdefinierten Speicher**, müssen Sie auch angeben einer `Set` Methode. Zum Beispiel:  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     Der Code sollte nicht Werte im Speicher festgelegt bei `Store.InUndoRedoOrRollback` gilt. Finden Sie unter [Transaktionen und benutzerdefinierte Setter](#setters).  
  
9. Erstellen Sie die Projektmappe, und führen Sie sie aus.  
  
10. Testen Sie die Eigenschaft. Stellen Sie sicher, dass Sie versuchen **Rückgängig** und **Wiederholen**.  
  
##  <a name="setters"></a> Transaktionen und benutzerdefinierte Setter  
 In der Set\-Methode der Eigenschaft benutzerdefinierte Speicher müssen Sie keinen zu eine Transaktion geöffnet werden, da die Methode in der Regel innerhalb einer aktiven Transaktion aufgerufen wird.  
  
 Die Set\-Methode kann jedoch auch aufgerufen werden, wenn der Benutzer zum Rückgängigmachen oder Wiederholen aufruft oder ein Rollback eine Transaktion ausgeführt wird. Wenn <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> true ist, die Set\-Methode sollte Verhalten sich wie folgt:  
  
-   Es sollten keine Änderungen im Speicher, wie z. B. das Zuweisen von Werten zu Eigenschaften von anderen Domänen vornehmen. Rollback\-Manager werden die Werte festlegen.  
  
-   Sie sollten jedoch keine externen Ressourcen, z. B. Datenbank Dateiinhalt oder Objekte außerhalb des Speichers aktualisieren. Dadurch wird sichergestellt, die sie in Synchronism mit den Werten im Speicher gehalten werden.  
  
 Zum Beispiel:  
  
```  
void SetAgeValue(int value)  
{   
  // If we are in Undo, no changes to Store objects:  
  if (!this.Store.InUndoRedoOrRollback)  
  {   
    this.BirthYear = System.DateTime.Today.Year - value;   
  }  
  // But always update external objects:  
  System.IO.File.WriteAllText(AgeFile, value);  
}  
```  
  
 Weitere Informationen über Transaktionen finden Sie unter [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## Siehe auch  
 [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Eigenschaften von Domäneneigenschaften](../modeling/properties-of-domain-properties.md)   
 [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)