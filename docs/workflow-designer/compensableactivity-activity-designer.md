---
title: Workflow-Designer-CompensableActivity-Aktivitäts Designer
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f498c6d025e7527b9767284a77c953e538cef377
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650664"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity-Aktivitätsdesigner

Der **CompensableActivity** -Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.CompensableActivity>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-compensableactivity-activity"></a>Die CompensableActivity-Aktivität
 Die <xref:System.Activities.Statements.CompensableActivity> definiert eine Arbeitseinheit, die nach erfolgreichem Abschluss bestätigt oder kompensiert werden kann.

### <a name="using-the-compensableactivity-activity-designer"></a>Verwenden des CompensableActivity-Aktivitätsdesigners
 Der **CompensableActivity** -Aktivitäts Designer befindet sich in der Kategorie **Transaktion** der **Toolbox**. Um die **Toolbox**zu öffnen, wählen Sie die Registerkarte **Toolbox** auf der linken Seite des Workflow-Designer aus. Sie können auch im Menü **Ansicht** die Option **Toolbox** auswählen oder **STRG** +**alt** +**X**drücken.

 Der **CompensableActivity** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer Oberfläche abgelegt werden. Sie können den Aktivitäts Designer in einem <xref:System.Activities.Statements.Sequence> ablegen. Beim Löschen des Aktivitäts Designers wird eine <xref:System.Activities.Statements.CompensableActivity>-Aktivität mit einem Standard <xref:System.Activities.Activity.DisplayName%2A> von CompensableActivity erstellt. Bearbeiten Sie den <xref:System.Activities.Activity.DisplayName%2A> Wert im Header des **CompensableActivity** -Aktivitäts Designers. Sie kann auch im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-compensableactivity-properties"></a>Die CompensableActivity-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.CompensableActivity>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die Eigenschaften "<xref:System.Activities.Activity.DisplayName%2A>" und "<xref:System.Activities.Activity%601.Result%2A>" können im Eigenschaften Raster bearbeitet werden, die anderen Eigenschaften müssen jedoch auf der Workflow-Designer-Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.Activities.Statements.CompensableActivity>-Aktivität. Der Standardwert lautet CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Gibt den Rückgabewert der <xref:System.Activities.Statements.CompensableActivity> an. Diese Eigenschaft muss im Eigenschaftenraster bearbeitet werden.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Gibt die Aktivität an, für die Kompensations-, Abbruch- und Bestätigungslogik bereitgestellt wurde. Wenn Sie die <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Aktivität hinzufügen möchten, legen Sie eine Aktivität aus der **Toolbox** im Feld **Body** des **CompensableActivity** -Aktivitäts Designers ab. Fügen Sie den Hinweis Text "Aktivität hier ablegen" hinzu.|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Gibt die Aktivität an, die ausgeführt wird, wenn ein Abbruch vorliegt. Um die-Aktivität hinzuzufügen, löschen Sie Ihren Designer aus der **Toolbox** im Feld **cancellationhandler** im **CompensableActivity** -Aktivitäts Designer. Fügen Sie den Hinweis Text "Aktivität hier ablegen" hinzu.|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Gibt die Aktivität an, die beim Kompensieren der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Aktivität ausgeführt werden soll. Dieser Handler kann explizit mithilfe der <xref:System.Activities.Statements.Compensate>-Aktivität aufgerufen werden.<br /><br /> Um die-Aktivität hinzuzufügen, löschen Sie Ihren Aktivitäts Designer aus der **Toolbox** in das Feld **compensationhandler** im **CompensableActivity** -Aktivitäts Designer. Fügen Sie den Hinweis Text "Aktivität hier ablegen" hinzu.|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Gibt die Aktivität an, die beim Bestätigen der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Aktivität ausgeführt werden soll. Dieser Handler kann explizit mithilfe der <xref:System.Activities.Statements.Confirm>-Aktivität aufgerufen werden.<br /><br /> Um die-Aktivität hinzuzufügen, löschen Sie Ihren Aktivitäts Designer aus der **Toolbox** in das Feld **confirmationhandler** im **CompensableActivity** -Aktivitäts Designer. Fügen Sie den Hinweis Text "Aktivität hier ablegen" hinzu.|

## <a name="see-also"></a>Siehe auch

- [Transaktion](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)