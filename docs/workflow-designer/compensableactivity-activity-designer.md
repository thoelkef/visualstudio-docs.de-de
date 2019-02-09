---
title: Workflow-Designer - CompensableActivity-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cfe5a207136b44e61beff77bec8c8c7b869568b6
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942361"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity-Aktivitätsdesigner

Die **CompensableActivity** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.CompensableActivity> Aktivität.

## <a name="the-compensableactivity-activity"></a>Die CompensableActivity-Aktivität
 Die <xref:System.Activities.Statements.CompensableActivity> definiert eine Arbeitseinheit, die nach erfolgreichem Abschluss bestätigt oder kompensiert werden kann.

### <a name="using-the-compensableactivity-activity-designer"></a>Verwenden des CompensableActivity-Aktivitätsdesigners
 Die **CompensableActivity** Aktivitäts-Designer finden Sie in der **Transaktion** Kategorie **Toolbox**. Zum Öffnen **Toolbox**, wählen die **Toolbox** Registerkarte auf der linken Seite des Workflow-Designers. Wählen Sie alternativ **Toolbox** aus der **Ansicht** Menü, oder drücken Sie **STRG**+**Alt** + **X**.

 Die **CompensableActivity** Aktivitäts-Designer gezogen werden kann, von **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht. Sie konnte innerhalb der Aktivitäts-Designer Ablegen einer <xref:System.Activities.Statements.Sequence>. Löschen die Aktivitäts-Designer erstellt eine <xref:System.Activities.Statements.CompensableActivity> -Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> compensableactivity. Bearbeiten der <xref:System.Activities.Activity.DisplayName%2A> Wert im Header der **CompensableActivity** Aktivitäts-Designer. Sie können auch im bearbeitet werden die **"DisplayName"** Feld des Eigenschaftenrasters.

### <a name="the-compensableactivity-properties"></a>Die CompensableActivity-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.CompensableActivity>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die <xref:System.Activities.Activity.DisplayName%2A> und <xref:System.Activities.Activity%601.Result%2A> Eigenschaft kann im Eigenschaftenraster bearbeitet werden, aber die anderen Eigenschaften müssen auf der Oberfläche des Workflow-Designer bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.Activities.Statements.CompensableActivity>-Aktivität. Der Standardwert lautet CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Gibt den Rückgabewert der <xref:System.Activities.Statements.CompensableActivity> an. Diese Eigenschaft muss im Eigenschaftenraster bearbeitet werden.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Gibt die Aktivität an, für die Kompensations-, Abbruch- und Bestätigungslogik bereitgestellt wurde. Hinzufügen der <xref:System.Activities.Statements.CompensableActivity.Body%2A> -Aktivität, indem Sie eine Aktivität aus **Toolbox** in die **Text** Feld der **CompensableActivity** Aktivitäts-Designer. Fügen Sie den Hinweistext "Aktivität hier ablegen" hinzu.|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Gibt die Aktivität, die ausgeführt wird, wenn ein Abbruch vorhanden ist. Fügen Sie die Aktivität hinzu, legen Sie ihren Designer aus **Toolbox** in die **CancellationHandler** Feld der **CompensableActivity** Aktivitäts-Designer. Fügen Sie Hinweistext "Aktivität hier ablegen" hinzu.|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Gibt die Aktivität an, die beim Kompensieren der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Aktivität ausgeführt werden soll. Dieser Handler kann explizit mithilfe der <xref:System.Activities.Statements.Compensate>-Aktivität aufgerufen werden.<br /><br /> Fügen Sie die Aktivität hinzu, legen Sie ihren Aktivitätsdesigner aus **Toolbox** in die **CompensationHandler** Feld der **CompensableActivity** Aktivitäts-Designer. Fügen Sie Hinweistext "Aktivität hier ablegen" hinzu.|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Gibt die Aktivität an, die beim Bestätigen der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Aktivität ausgeführt werden soll. Dieser Handler kann explizit mithilfe der <xref:System.Activities.Statements.Confirm>-Aktivität aufgerufen werden.<br /><br /> Fügen Sie die Aktivität hinzu, legen Sie ihren Aktivitätsdesigner aus **Toolbox** in die **ConfirmationHandler** Feld der **CompensableActivity** Aktivitäts-Designer. Fügen Sie Hinweistext "Aktivität hier ablegen" hinzu.|

## <a name="see-also"></a>Siehe auch

- [Transaktion](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)