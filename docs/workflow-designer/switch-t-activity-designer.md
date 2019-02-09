---
title: Workflow-Designer - Switch<T> Aktivitäts-Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7eb83567a7d59dc02779839a5305b9c1c0329912
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55920938"
---
# <a name="switcht-activity-designer"></a>Switch\<T >-Aktivitätsdesigner

Die <xref:System.Activities.Statements.Switch%601>-Aktivität wertet einen angegebenen Ausdruck aus und führt diejenige Aktivität aus einer Auflistung von Aktivitäten aus, deren zugeordneter Schlüssel dem Wert entspricht, der aus der Auswertung hervorging.

Die **Switch < T\>**  Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Switch%601> Aktivität im Workflow-Designer.

## <a name="the-switchtactivity"></a>Der Schalter\<T >-Aktivität

Eine <xref:System.Activities.Statements.Switch%601>-Aktivität enthält einen <xref:System.Activities.Statements.Switch%601.Expression%2A>-Ausdruck und ein Wörterbuch von <xref:System.Activities.Statements.Switch%601.Cases%2A>-Fällen. Jeder Fall im Wörterbuch besteht aus einem Paar, das enthält eine *Schlüssel* und eine Aktivität, die als das entsprechende dient *Wert*. Die <xref:System.Activities.Statements.Switch%601>-Aktivität wertet den <xref:System.Activities.Statements.Switch%601.Expression%2A>-Ausdruck aus und vergleicht ihn mit jedem Schlüssel. Wenn eine Übereinstimmung gefunden wird, wird die entsprechende Aktivität ausgeführt. Nur eine Übereinstimmung ist möglich, da die Wörterbuchschlüssel entsprechend der vom Gleichheitsvergleich des Wörterbuchs definierten Gleichheit eindeutig sein müssen. Wenn keine Übereinstimmung gefunden wird, wird die <xref:System.Activities.Statements.Switch%601.Default%2A>-Aktivität ausgeführt.

## <a name="how-to-use-the-switcht-activity-designer"></a>Gewusst wie: Verwenden Sie den Switch\<T >-Aktivitätsdesigner

Zugriff die **Switch\<T >** Aktivitäts-Designer in der **Ablaufsteuerung** Kategorie der **Toolbox**. Nach dem Workflow-Designer ablegen, wird die **Typen auswählen** Dialogfeld ermöglichen den Benutzer aus, geben Sie den generischen Typ *T* verwendet <xref:System.Activities.Statements.Switch%601> Aktivität. Der Standardwert ist **Int32**. Sobald der generische Typ *T* ausgewählt wurde, eine **Switch < T\>**  -Designer zum Workflow-Designer hinzugefügt.

Nachfolgend werden die Eigenschaften des **Switch < T\>**  Designer. Alle diese Eigenschaften können im Eigenschaftenraster bearbeitet werden. Einige von ihnen können auch in der Designeroberfläche bearbeitet werden.

In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.Switch%601>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen des <xref:System.Activities.Statements.Switch%601>-Aktivitätsdesigners an. Der Standardwert ist Switch < Int32\>. Der Wert kann bearbeitet werden, der **Eigenschaften** Fenster oder direkt im Header.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|Gibt den Ausdruck an, mit dem die Schlüssel in der Auflistung der Fälle verglichen wurden, um zu bestimmen, welcher Fall auszuführen ist.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Gibt die Aktivität an, die ausgeführt werden soll, wenn keine Übereinstimmung gefunden wird. Klicken Sie auf die **Hinzufügen einer Aktivität** Designer auf die Schaltfläche zum Öffnen der **Standard** Feld, in dem die Aktivität abgelegt werden kann.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Gibt die Fälle an, die ausgewertet werden sollen. Um einen Fall hinzuzufügen, klicken Sie auf die **neuen Fall hinzufügen** Schaltfläche am unteren Rand **Switch\<T >** Designer. Die Schaltfläche ändert sich in einem Textfeld (Kombinationsfeld, wenn der generische Typ ausgewählt wird, beim Hinzufügen der Switch\<T > ist, String oder Enum). Nach dem Hinzufügen eines Schlüssels in der **Case-Wert** Box der Case-Bereich wird erweitert und eine Aktivität kann gelöscht werden, in dem der Hinweistext "Aktivität hier ablegen", um die Ausführungslogik für den Fall zu definieren.|

Solange keine doppelten Fallschlüssel vorkommen, können mehrere Fälle hinzugefügt werden. Andernfalls wird ein Fehlerdialogfeld mit der Meldung angezeigt, dass der angegebene Fallschlüssel bereits vorhanden ist und dass Sie einen anderen Schlüssel auswählen müssen. In der **Switch\<T >** -Designer mehrere Case-Bereiche kann in der erweiterten Ansicht zu einem Zeitpunkt werden. Wenn ein case-Bereich reduziert angezeigt wird, klicken Sie auf den case-Bereich, um ihn zu erweitern. Beachten Sie, dass der Designer bei einem reduzierten case-Bereich den Anzeigenamen der Aktivität rechts neben dem Bereich anzeigt, sofern eine Aktivität vorhanden ist. Andernfalls werden die **Hinzufügen einer Aktivität** Schaltfläche, die die Groß-/Kleinschreibung wird erweitert, wenn Sie darauf klicken und Sie können eine Aktivität hinzuzufügen.

Wenn Sie auf den Schlüssel eines vorhandenen Falls klicken, wird der Schlüssel von einer Bezeichnung in ein Textfeld geändert, damit Sie den Fallschlüssel bearbeiten können.

Es gibt zwei Möglichkeiten, einen Fall zu löschen:

- Wählen Sie den Fall aus, und löschen Sie ihn.

- Wählen Sie die Groß-/Kleinschreibung, mit der rechten Maustaste das Kontextmenü anzuzeigen, und wählen Sie **löschen**.

Beachten Sie, dass Sie den Fall selbst markieren müssen, um ihn zu löschen. Wenn Sie die Aktivität in einem Fall markieren und löschen, wird nur Aktivität, nicht der Fall gelöscht.

## <a name="see-also"></a>Siehe auch

- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)