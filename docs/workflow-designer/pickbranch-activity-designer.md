---
title: Workflow-Designer - PickBranch-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6c452cb4fd5b8a343473204c2b2bee614383ebb
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922055"
---
# <a name="pickbranch-activity-designer"></a>PickBranch-Aktivitätsdesigner

Der <xref:System.Activities.Statements.PickBranch> stellt einen ereignisbasierten Ausführungspfad innerhalb einer <xref:System.Activities.Statements.Pick>-Aktivität bereit, der von einem eingehenden Ereignis ausgelöst werden kann.

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch>-Objekte sind in der <xref:System.Activities.Statements.Pick.Branches%2A>-Auflistung einer <xref:System.Activities.Statements.Pick>-Aktivität enthalten. Jede <xref:System.Activities.Statements.PickBranch> ist in einem Branch der <xref:System.Activities.Statements.Pick>-Aktivität enthalten und wird aufgrund eines eingehenden Ereignisses ausgeführt, das als Trigger dient. Auf diese Weise stellt das Workflow-Designer das ereignisbasierte ablaufsteuerungsmodellierung bereit. Jede <xref:System.Activities.Statements.PickBranch> enthält einen <xref:System.Activities.Statements.PickBranch.Trigger%2A> und eine <xref:System.Activities.Statements.PickBranch.Action%2A>.

### <a name="how-to-use-the-pick-activity-designer"></a>So verwenden Sie den Pick-Aktivitätsdesigner

Zugriff die **PickBranch** im Designer die **Ablaufsteuerung** Kategorie der **Toolbox**.

Zwei leere <xref:System.Activities.Statements.PickBranch> Objekte mit den Anzeigenamen **Branch1** und **Branch2** werden als Elemente standardmäßig erstellt eine <xref:System.Activities.Statements.Pick> Aktivität bei der **auswählen** Aktivitäts-Designer wird zunächst an den Workflow-Designer gelöscht werden. Die jeweiligen <xref:System.Activities.Statements.PickBranch.DisplayName%2A> Eigenschaftswerte können bearbeitet werden, der **PickBranch** Designer-Header oder in der **Eigenschaften** für jeden Branch.

Es gibt zwei Möglichkeiten zum Hinzufügen von <xref:System.Activities.Statements.PickBranch> Objekte auf die Auflistung von einer <xref:System.Activities.Statements.Pick> Objekt: Ziehen und Ablegen der **PickBranch** -Designer aus der **Toolbox**, oder mithilfe von mit der rechten Maustaste in der **auswählen** Entwurfsoberfläche:

- Die **PickBranch** -Designer erstellt eine <xref:System.Activities.Statements.PickBranch> Wenn es gezogen wird von der **Toolbox** und in einer der Verzweigungen einer **auswählen** Aktivitäts-Designer auf der Workflow-Designer-Oberfläche. Die neuen <xref:System.Activities.Statements.PickBranch>-Objekte können im <xref:System.Activities.Statements.Pick>-Designer auf der linken oder rechten Seite jedes <xref:System.Activities.Statements.PickBranch>-Elements platziert werden, das bereits in der Auflistung enthalten ist. Beim Ziehen einer **PickBranch** Designer auf die **auswählen** mit der Maus, die **auswählen** Designer mithilfe ein vertikales blaugrauen Bands an, wo entsprechend der <xref:System.Activities.Statements.PickBranch> wird für den gegebenen Mausposition hinzugefügt.

- Mit der rechten Maustaste **auswählen** -Aktivitätsdesigner (jedoch nicht im **PickBranch** Designer) ein Kontextmenü und wählen Sie **Verzweigung erstellen** zum Hinzufügen einer neuen <xref:System.Activities.Statements.PickBranch>. Beachten Sie, dass die neue <xref:System.Activities.Statements.PickBranch> wird hinzugefügt, die rechts neben den vorhandenen <xref:System.Activities.Statements.PickBranch> Objekte in der **auswählen** Designer.

Die **PickBranch** Designer kann erweitert werden, damit die **Trigger** und **Aktion** Dialogfelder oder durch Klicken auf die doppelten Caretzeichen auf der rechten Seite ihrer Header reduziert. Bearbeiten der <xref:System.Activities.Statements.PickBranch.Trigger%2A> und <xref:System.Activities.Statements.PickBranch.Action%2A> aller <xref:System.Activities.Statements.PickBranch> durch Ablegen von Aktivitäten in der **Trigger** und **Aktion** Felder ihrer Designer.

Der <xref:System.Activities.Statements.PickBranch> Objekte in der <xref:System.Activities.Statements.Pick.Branches%2A> Auflistung von einer <xref:System.Activities.Statements.Pick> Objekt, das neu angeordnet werden können, durch Ziehen und Ablegen in einem neuen Speicherort innerhalb der **auswählen** Designer. Die **auswählen** Designer mithilfe ein vertikales blaugrauen Bands an, wo entsprechend der <xref:System.Activities.Statements.PickBranch> gegebenen Mausposition hinzugefügt wird.

Es gibt zwei Möglichkeiten, ein <xref:System.Activities.Statements.PickBranch>-Objekt zu löschen:

- Wählen Sie die **PickBranch** Designer und löschen Sie sie.
- Wählen Sie die **PickBranch** Designer, mit der rechten Maustaste das Kontextmenü, und wählen Sie **löschen**.

Wählen Sie die **PickBranch** Designer, wie die Auswahl einer der Aktivitäten in dessen **Trigger** oder **Aktion** Felder versehentlich löscht diese Aktivitäten und nicht die <xref:System.Activities.Statements.PickBranch> Objekt.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>PickBranch-Eigenschaften im Workflow-Designer

In der folgende Tabelle werden die nützlichsten <xref:System.Activities.Statements.PickBranch> Eigenschaften und beschreibt, wie sie im Workflow-Designer.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Der Anzeigename für den Header von den **PickBranch** Designer. Der Standardwert lautet Branch.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Jedes <xref:System.Activities.Statements.PickBranch>-Objekt enthält eine <xref:System.Activities.Statements.PickBranch.Trigger%2A>-Aktion, die <xref:System.Activities.Statements.PickBranch.Action%2A> aufrufen kann.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Jede <xref:System.Activities.Statements.PickBranch>-Objekt enthält eine <xref:System.Activities.Statements.PickBranch.Action%2A>, die ausgeführt wird, sobald sie ausgelöst wird.|

## <a name="see-also"></a>Siehe auch

- [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)
- [Auswahlaktivität](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Verwenden der Pick-Aktivität](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)