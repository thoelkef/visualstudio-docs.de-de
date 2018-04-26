---
title: Workflow-Designer - CancellationScope-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a0f9a40434821294384154ddcbbfebbd0a7885eb
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope-Aktivitätsdesigner

Die **CancellationScope** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.CancellationScope> Aktivität.

## <a name="the-cancellationscope-activity"></a>Die CancellationScope-Aktivität
 Mit der <xref:System.Activities.Statements.CancellationScope>-Aktivität können Sie für eine Aktivität für die Ausführungs- und Abbruchlogik dieser Aktivität angeben.

### <a name="using-the-cancellationscope-activity-designer"></a>Verwenden des CancellationScope-Aktivitätsdesigners
 Die **CancellationScope** Aktivitäts-Designer finden Sie in der **Transaktion** Kategorie **Toolbox**. So öffnen **Toolbox**, wählen die **Toolbox** Registerkarte im Workflow-Designer. Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menü, oder drücken Sie STRG + ALT + X.

 Die **CancellationScope** Aktivitäts-Designer gezogen werden kann, von **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht wird, wo Aktivitäten platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Löschen der **CancellationScope** Aktivitäts-Designer erstellt eine <xref:System.Activities.Statements.CancellationScope> -Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> des CancellationScope. Bearbeiten der <xref:System.Activities.Activity.DisplayName%2A> im Header der Wert der **CancellationScope** Aktivitäts-Designer. Sie können auch bearbeiten Sie sie in der **DisplayName** Feld des Eigenschaftenrasters.

### <a name="the-cancellationscope-properties"></a>Die CancellationScope-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.CancellationScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die <xref:System.Activities.Activity.DisplayName%2A> Eigenschaft kann im Eigenschaftenraster bearbeitet werden, aber die anderen Eigenschaften müssen auf die Oberfläche des Workflow-Designer bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.Activities.Statements.CancellationScope>-Aktivität. Der Standardwert lautet CancellationScope. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Gibt die Aktivität an, für die Abbruchlogik bereitgestellt wird. Hinzufügen der <xref:System.Activities.Statements.CancellationScope.Body%2A> Aktivität, indem Sie eine Aktivität aus **Toolbox** in der **Text** Feld der **CancellationScope** Aktivitäts-Designer. Fügen Sie dem Hinweistext "Aktivität hier ablegen" hinzu.|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Gibt die Aktivität, die ausgeführt wird, wenn ein Abbruch vorhanden ist. Hinzufügen der <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> Aktivität, indem Sie eine Aktivität aus **Toolbox** in der **CancellationHandler** Feld der **CancellationScope** Aktivitäts-Designer. Fügen Sie dem Hinweistext "Aktivität hier ablegen" hinzu.|

## <a name="see-also"></a>Siehe auch

- [Transaktion](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Kompensieren](../workflow-designer/compensate-activity-designer.md)
- [Vergewissern Sie sich](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)