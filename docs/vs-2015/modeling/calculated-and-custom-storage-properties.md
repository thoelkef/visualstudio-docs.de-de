---
title: Berechnete und benutzerdefinierte Speichereigenschaften | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
ms.assetid: 42b785f9-2b0f-4f13-a6b4-246e5e0d477a
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a5aa6edaaba54f9c08921a594b90ca1a7352e4da
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433441"
---
# <a name="calculated-and-custom-storage-properties"></a>Berechnete und benutzerdefinierte Speichereigenschaften
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Alle Domäneneigenschaften in einer domänenspezifischen Sprache (DSL) können für den Benutzer auf das Diagramm und in Ihrer Sprache-Explorer angezeigt werden, und können über Programmcode zugegriffen werden. Unterscheiden sich jedoch die Eigenschaften auf die Weise, dass ihre Werte gespeichert werden.  
  
## <a name="kinds-of-domain-properties"></a>Arten von Domäneneigenschaften  
 Sie können in der DSL-Definition Festlegen der **Art** einer Domäneneigenschaft, wie in der folgenden Tabelle aufgeführt:  
  
|Art der Domäne-Eigenschaft|Beschreibung|  
|--------------------------|-----------------|  
|**Standard** (Standard)|Eine Eigenschaft "Domain", die in gespeichert ist die *speichern* und in der Datei serialisiert.|  
|**Berechnet**|Eine schreibgeschützte-Eigenschaft, die nicht im Speicher gespeichert, sondern aus anderen Werten berechnet.<br /><br /> Z. B. `Person.Age` konnte aus berechnet `Person.BirthDate`.<br /><br /> Sie müssen den Code bereitstellen, der Berechnung ausführt. In der Regel können Sie den Wert von anderen Domäneneigenschaften berechnen. Sie können jedoch auch externe Ressourcen verwenden.|  
|**Benutzerdefinierten Speicher**|Eine Domäneneigenschaft, die nicht direkt im Speicher gespeichert, aber sowohl get- und Set werden kann.<br /><br /> Sie müssen die Methoden bereit, die den Wert abrufen und festlegen.<br /><br /> Z. B. `Person.FullAddress` konnte gespeichert werden, `Person.StreetAddress`, `Person.City`, und `Person.PostalCode`.<br /><br /> Sie können auch externe Ressourcen, z. B. zum Abrufen und Festlegen von Werten aus einer Datenbank zugreifen.<br /><br /> Ihr Code sollte nicht die Werte festgelegt, im Speicher bei `Store.InUndoRedoOrRollback` ist "true". Finden Sie unter [Transaktionen und benutzerdefinierten Setter](#setters).|  
  
## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Den Code bereitstellen für eine Eigenschaft für die berechneten oder benutzerdefinierten Speicher.  
 Wenn Sie die Art der Eigenschaft "Domain" eine berechnete oder benutzerdefinierten Speicher festlegen, müssen Sie Methoden für den Datenzugriff zu bieten. Wenn Sie die Projektmappe erstellen, informiert ein Fehlerbericht Sie was erforderlich ist.  
  
#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Zum Definieren einer berechneten oder benutzerdefinierte Storage-Eigenschaft  
  
1. Wählen Sie in "DslDefinition.DSL", die Eigenschaft "Domain" im Diagramm oder im **DSL-Explorer**.  
  
2. In der **Eigenschaften** legen die **Art** Feld **berechnete** oder **benutzerdefinierten Speicher**.  
  
     Stellen Sie sicher, dass Sie auch festlegen, haben die **Typ** auf die gewünschte.  
  
3. Klicken Sie auf **alle Vorlagen transformieren** auf der Symbolleiste des **Projektmappen-Explorer**.  
  
4. Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.  
  
     Die folgende Fehlermeldung wird angezeigt: "*Ihreklasse* enthält keine Definition für Get*YourProperty*."  
  
5. Doppelklicken Sie auf die Fehlermeldung angezeigt.  
  
     Dsl\GeneratedCode\DomainClasses.cs oder DomainRelationships.cs wird geöffnet. Über den hervorgehobenen Methodenaufruf, ein Kommentar aufgefordert, eine Implementierung für Get bereitstellen*YourProperty*().  
  
    > [!NOTE]
    > Diese Datei wird aus "DslDefinition.DSL" generiert. Wenn Sie diese Datei bearbeiten, Ihre Änderungen verloren das nächste Mal, die Sie klicken **alle Vorlagen transformieren**. Fügen Sie stattdessen die erforderliche Methode in einer separaten Datei hinzu.  
  
6. Erstellen oder öffnen Sie eine Datei in einem separaten Ordner, z. B. CustomCode\\*YourDomainClass*. Cs.  
  
     Stellen Sie sicher, dass der Namespace des generierten Codes identisch ist.  
  
7. Schreiben Sie eine partielle Implementierung der Domänenklasse in der Klassendatei. Schreiben Sie in der Klasse, eine Definition für die fehlende `Get` -Methode, die das folgende Beispiel ähnelt:  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8. Setzen Sie **Art** zu **benutzerdefinierten Speicher**, außerdem müssen Sie zu einer `Set` Methode. Zum Beispiel:  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     Ihr Code sollte nicht die Werte festgelegt, im Speicher bei `Store.InUndoRedoOrRollback` ist "true". Finden Sie unter [Transaktionen und benutzerdefinierten Setter](#setters).  
  
9. Erstellen Sie die Projektmappe, und führen Sie sie aus.  
  
10. Testen Sie die Eigenschaft an. Stellen Sie sicher, dass Sie versuchen **Rückgängig** und **wiederholen**.  
  
## <a name="setters"></a> Transaktionen und benutzerdefinierten Setter  
 In der Set-Methode der Eigenschaft des benutzerdefinierten Speicher müssen Sie keinen zu eine Transaktion zu öffnen, da die Methode in der Regel innerhalb einer aktiven Transaktion aufgerufen wird.  
  
 Die Set-Methode kann jedoch auch aufgerufen werden, wenn der Benutzer zum Rückgängigmachen oder Wiederholen aufruft, oder wenn eine Transaktion ein Rollback ausgeführt wird. Wenn <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> ist "true", die Set-Methode sollte Verhalten sich wie folgt:  
  
- Es sollten keine Änderungen im Speicher, z. B. das Zuweisen von Werten zu einer anderen Domäneneigenschaften vornehmen. Der annullierungsmanager, werden ihre Werte festgelegt.  
  
- Sie sollten jedoch alle externen Ressourcen, z. B. Datenbank bzw. des Dateiinhalts oder Objekten außerhalb des Speichers aktualisieren. Dadurch wird sichergestellt, die sie in Synchronism mit den Werten im Speicher gehalten werden.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Eigenschaften von Domäneneigenschaften](../modeling/properties-of-domain-properties.md)   
 [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)
