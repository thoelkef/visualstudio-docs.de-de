---
title: Berechnete und benutzerdefinierte Speichereigenschaften
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1bdf6d413287f75fa57ef80525a43f86cd55c74d
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="calculated-and-custom-storage-properties"></a>Berechnete und benutzerdefinierte Speichereigenschaften
Alle Domäneneigenschaften in eine domänenspezifische Sprache (DSL) für den Benutzer auf das Diagramm und in Ihrer Sprache-Explorer angezeigt werden können und Programmcode zugegriffen werden können. Eigenschaften unterscheiden sich jedoch auf die Weise, dass ihre Werte gespeichert werden.

## <a name="kinds-of-domain-properties"></a>Arten von Domäneneigenschaften
 In der DSL-Definition, legen Sie die **Art** von einer Eigenschaft "Domain", wie in der folgenden Tabelle aufgeführt:

|Art der Domäne-Eigenschaft|Beschreibung|
|--------------------------|-----------------|
|**Standard** (Standard)|Eine Eigenschaft "Domain", die in gespeichert ist die *speichern* und in der Datei serialisiert.|
|**Berechnet**|Eine nur-Lese Domäneneigenschaft, die nicht im Speicher gespeichert ist, jedoch aus anderen Werten berechnet wird.<br /><br /> Beispielsweise `Person.Age` konnte aus berechnet werden `Person.BirthDate`.<br /><br /> Sie müssen den Code angeben, der die Berechnung ausführt. In der Regel können Sie den Wert von anderen Domäneneigenschaften berechnen. Sie können jedoch auch externe Ressourcen.|
|**Benutzerdefinierte Speicherung**|Eine Eigenschaft "Domain", die nicht direkt im Speicher gespeichert ist, aber die Get- und Set werden kann.<br /><br /> Sie müssen die Methoden bereit, die den Wert abrufen und festlegen.<br /><br /> Beispielsweise `Person.FullAddress` konnte gespeichert werden, `Person.StreetAddress`, `Person.City`, und `Person.PostalCode`.<br /><br /> Sie können auch externe Ressourcen, z. B. zum Abrufen und Festlegen von Werten aus einer Datenbank zugreifen.<br /><br /> Codes Werte im Speicher sollte nicht festgelegt werden Wenn `Store.InUndoRedoOrRollback` ist "true". Finden Sie unter [Transaktionen und benutzerdefinierte Setter](#setters).|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Der Code bereitstellen für eine berechnete oder benutzerdefinierte Speichereigenschaft
 Wenn Sie die Art der Eigenschaft "Domain" eine berechnete oder einen benutzerdefinierten Speicher festlegen, müssen Sie über Zugriffsmethoden angeben. Wenn Sie die Projektmappe erstellen, wird ein Fehlerbericht Aufschluss darüber, was erforderlich ist.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Zum Definieren einer berechneten oder benutzerdefinierte "Storage"-Eigenschaft

1.  Wählen Sie im DslDefinition.dsl, die Eigenschaft "Domain" im Diagramm oder im **Explorer für DSL**.

2.  In der **Eigenschaften** legen die **Art** Feld **berechnete** oder **benutzerdefinierten Speicher**.

     Stellen Sie sicher, dass Sie auch festlegen, haben die **Typ** auf den gewünschten.

3.  Klicken Sie auf **alle Vorlagen transformieren** auf der Symbolleiste des **Projektmappen-Explorer**.

4.  Klicken Sie im Menü **Erstellen** auf **Projektmappe erstellen**.

     Sie erhalten die folgende Fehlermeldung angezeigt: "*YourClass* enthält keine Definition für Get*YourProperty*."

5.  Doppelklicken Sie auf die Fehlermeldung angezeigt.

     Dsl\GeneratedCode\DomainClasses.cs oder DomainRelationships.cs wird geöffnet. Oberhalb der markierten-Methodenaufruf, ein Kommentar aufgefordert, eine Implementierung für Get bereitstellen*YourProperty*().

    > [!NOTE]
    >  Diese Datei wird aus DslDefinition.dsl generiert. Wenn Sie diese Datei bearbeiten, Ihre Änderungen verloren das nächste Mal, die Sie klicken Sie auf **alle Vorlagen transformieren**. Fügen Sie stattdessen die erforderliche Methode in einer separaten Datei hinzu.

6.  Erstellen oder öffnen Sie eine Klassendatei in einem separaten Ordner, z. B. CustomCode\\*YourDomainClass*. Cs.

     Stellen Sie sicher, dass der Namespace in den generierten Code identisch ist.

7.  Schreiben Sie in der Klassendatei partielle Implementierung des Domain-Klasse. Schreiben Sie in der Klasse ist eine Definition für die fehlende `Get` -Methode, die das folgende Beispiel ähnelt:

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8.  Wenn Sie festlegen, **Art** zu **benutzerdefinierten Speicher**, Sie müssen auch angeben einer `Set` Methode. Zum Beispiel:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     Codes Werte im Speicher sollte nicht festgelegt werden Wenn `Store.InUndoRedoOrRollback` ist "true". Finden Sie unter [Transaktionen und benutzerdefinierte Setter](#setters).

9. Erstellen Sie die Projektmappe, und führen Sie sie aus.

10. Testen Sie die Eigenschaft an. Stellen Sie sicher, dass Sie versuchen **Rückgängig** und **wiederholen**.

##  <a name="setters"></a> Transaktionen und benutzerdefinierte Setter
 In der Set-Methode des benutzerdefinierten Speichereigenschaft müssen Sie keine Transaktion zu öffnen, da die Methode in der Regel innerhalb einer aktiven Transaktion aufgerufen wird.

 Die Set-Methode kann jedoch auch aufgerufen werden, wenn der Benutzer zum Rückgängigmachen oder Wiederholen aufruft oder ein Rollback eine Transaktion ausgeführt wird. Wenn <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> ist "true", die Set-Methode, verhalten sich wie folgt:

-   Es sollten keine Änderungen im Speicher, z. B. das Zuweisen von Werten zu anderen Domäneneigenschaften vornehmen. Rollback-Manager werden ihre Werte festgelegt.

-   Allerdings sollten sie keine externen Ressourcen, z. B. Datenbank Dateiinhalte oder Objekte außerhalb des Informationsspeichers aktualisieren. Dadurch wird sichergestellt, die sie in Synchronism mit den Werten im Speicher gehalten werden.

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

 Weitere Informationen über Transaktionen finden Sie unter [Navigieren in und Aktualisieren eines Modells im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Siehe auch

- [Navigieren in und Aktualisieren von Modellen im Programmcode](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Eigenschaften von Domäneneigenschaften](../modeling/properties-of-domain-properties.md)
- [So definieren Sie eine domänenspezifische Sprache](../modeling/how-to-define-a-domain-specific-language.md)