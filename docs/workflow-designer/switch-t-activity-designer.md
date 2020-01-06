---
title: Workflow-Designer<T> Aktivitäts Designer wechseln
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a39e8c1e789c1c448e30962789d1a9ab7f3e65c5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593121"
---
# <a name="switcht-activity-designer"></a>\<t-> Aktivitäts Designer wechseln

Die <xref:System.Activities.Statements.Switch%601>-Aktivität wertet einen angegebenen Ausdruck aus und führt diejenige Aktivität aus einer Auflistung von Aktivitäten aus, deren zugeordneter Schlüssel dem Wert entspricht, der aus der Auswertung hervorging.

Der **Switch < T-\>** Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.Switch%601> Aktivität in der Workflow-Designer zu erstellen und zu konfigurieren.

## <a name="the-switchtactivity"></a>Der Switch\<t-> Aktivität

Eine <xref:System.Activities.Statements.Switch%601>-Aktivität enthält einen <xref:System.Activities.Statements.Switch%601.Expression%2A>-Ausdruck und ein Wörterbuch von <xref:System.Activities.Statements.Switch%601.Cases%2A>-Fällen. Jeder Fall im Wörterbuch besteht aus einem Paar, das einen *Schlüssel* und eine Aktivität enthält, die als entsprechender *Wert*fungiert. Die <xref:System.Activities.Statements.Switch%601>-Aktivität wertet den <xref:System.Activities.Statements.Switch%601.Expression%2A>-Ausdruck aus und vergleicht ihn mit jedem Schlüssel. Wenn eine Übereinstimmung gefunden wird, wird die entsprechende Aktivität ausgeführt. Nur eine Übereinstimmung ist möglich, da die Wörterbuchschlüssel entsprechend der vom Gleichheitsvergleich des Wörterbuchs definierten Gleichheit eindeutig sein müssen. Wenn keine Übereinstimmung gefunden wird, wird die <xref:System.Activities.Statements.Switch%601.Default%2A>-Aktivität ausgeführt.

## <a name="how-to-use-the-switcht-activity-designer"></a>Verwenden des Switch\<t-> Aktivitäts Designers

Greifen Sie **\<t >** Aktivitäts Designer in der Kategorie **Ablauf Steuerung** der **Toolbox**auf den Switch zu. Nachdem Sie Sie im Workflow-Designer abgelegt haben, wird das Dialogfeld **Typen auswählen** angezeigt, mit dem der Benutzer den in <xref:System.Activities.Statements.Switch%601> Aktivität verwendeten generischen Typ *T* angeben kann. Der Standardwert ist **Int32**. Sobald der generische Typ *T* ausgewählt wurde, wird dem Workflow-Designer ein **Switch < T-\>** -Designer hinzugefügt.

Im folgenden finden Sie die Eigenschaften von **Switch < T\>** Designer. Alle diese Eigenschaften können im Eigenschaftenraster bearbeitet werden. Einige von ihnen können auch in der Designeroberfläche bearbeitet werden.

In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.Switch%601>-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.

|Eigenschaftsname|Erforderlich|Verwendungs-|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Gibt den optionalen Anzeigenamen des <xref:System.Activities.Statements.Switch%601>-Aktivitätsdesigners an. Der Standardwert ist Switch < Int32\>. Der Wert kann im **Eigenschaften** Fenster oder direkt im Designer Header bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|Gibt den Ausdruck an, mit dem die Schlüssel in der Auflistung der Fälle verglichen wurden, um zu bestimmen, welcher Fall auszuführen ist.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Gibt die Aktivität an, die ausgeführt werden soll, wenn keine Übereinstimmung gefunden wird. Klicken Sie im Designer auf die Schaltfläche **Aktivität hinzufügen** , um das **Standard** Feld zu öffnen, in dem die Aktivität abgelegt werden kann.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Gibt die Fälle an, die ausgewertet werden sollen. Um einen Fall hinzuzufügen, klicken Sie auf die Schaltfläche **neuen Fall hinzufügen** am unteren Rand der **Switch-\<t >** -Designers. Die Schaltfläche ändert sich in ein Textfeld (Kombinations Feld, wenn der generische Typ, der beim Hinzufügen des Schalters ausgewählt wurde\<t > ist String oder Enum ist). Nach dem Hinzufügen eines Schlüssels im Feld **Fall Wert** wird der Case-Bereich erweitert, und es kann eine Aktivität mit dem Hinweis Text "Aktivität hier ablegen" abgelegt werden, um die Ausführungs Logik für die Groß-/Kleinschreibung zu definieren.|

Solange keine doppelten Fallschlüssel vorkommen, können mehrere Fälle hinzugefügt werden. Andernfalls wird ein Fehlerdialogfeld mit der Meldung angezeigt, dass der angegebene Fallschlüssel bereits vorhanden ist und dass Sie einen anderen Schlüssel auswählen müssen. Im **Switch\<t >** Designer kann jeweils nur ein Fall Bereich in der erweiterten Ansicht angezeigt werden. Wenn ein case-Bereich reduziert angezeigt wird, klicken Sie auf den case-Bereich, um ihn zu erweitern. Beachten Sie, dass der Designer bei einem reduzierten case-Bereich den Anzeigenamen der Aktivität rechts neben dem Bereich anzeigt, sofern eine Aktivität vorhanden ist. Andernfalls wird die Schaltfläche **Aktivität hinzufügen** angezeigt, mit der der Fall erweitert wird, wenn Sie darauf klicken, und Sie können eine Aktivität hinzufügen.

Wenn Sie auf den Schlüssel eines vorhandenen Falls klicken, wird der Schlüssel von einer Bezeichnung in ein Textfeld geändert, damit Sie den Fallschlüssel bearbeiten können.

Es gibt zwei Möglichkeiten, einen Fall zu löschen:

- Wählen Sie den Fall aus, und löschen Sie ihn.

- Wählen Sie den Fall aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Löschen**aus.

Beachten Sie, dass Sie den Fall selbst markieren müssen, um ihn zu löschen. Wenn Sie die Aktivität in einem Fall markieren und löschen, wird nur Aktivität, nicht der Fall gelöscht.

## <a name="see-also"></a>Siehe auch

- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
