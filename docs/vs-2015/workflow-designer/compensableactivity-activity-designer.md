---
title: CompensableActivity-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e2bc28c4586912d7c253c9629c2af0eefd30e47e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656995"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity-Aktivitätsdesigner
Der **CompensableActivity** -Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.CompensableActivity>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-compensableactivity-activity"></a>Die CompensableActivity-Aktivität
 Die <xref:System.Activities.Statements.CompensableActivity> definiert eine Arbeitseinheit, die nach erfolgreichem Abschluss bestätigt oder kompensiert werden kann.

### <a name="using-the-compensableactivity-activity-designer"></a>Verwenden des CompensableActivity-Aktivitätsdesigners
 Der **CompensableActivity** -Aktivitäts Designer befindet sich in der Kategorie **Transaktion** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite der [!INCLUDE[wfd2](../includes/wfd2-md.md)] auf die Registerkarte **Toolbox** klicken (Sie können auch **Toolbar** auswählen). über das Menü **Ansicht** oder STRG + ALT + X.)

 Der **CompensableActivity** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Dadurch wird eine <xref:System.Activities.Statements.CompensableActivity>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> CompensableActivity erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **CompensableActivity** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-compensableactivity-properties"></a>Die CompensableActivity-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.CompensableActivity>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die Eigenschaften <xref:System.Activities.Activity.DisplayName%2A> und <xref:System.Activities.Activity%601.Result%2A> können im Eigenschaftenraster bearbeitet werden, die anderen Eigenschaften müssen jedoch auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.Activities.Statements.CompensableActivity>-Aktivität. Der Standardwert lautet CompensableActivity.|
|<xref:System.Activities.Activity%601.Result%2A>|False|Gibt den Rückgabewert der <xref:System.Activities.Statements.CompensableActivity> an. Diese Eigenschaft muss im Eigenschaftenraster bearbeitet werden.|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|Gibt die Aktivität an, für die Kompensations-, Abbruch- und Bestätigungslogik bereitgestellt wurde. Um die <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Aktivität hinzuzufügen, legen Sie eine Aktivität aus der **Toolbox** in das Feld **Body** mit dem Hinweis Text "Aktivität hier ablegen" des **CompensableActivity** -Aktivitäts Designers ab.|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|Gibt die Aktivität an, die im Fall eines Abbruchs ausgeführt wird. Um die-Aktivität hinzuzufügen, löschen Sie Ihren Designer aus der **Toolbox** in das Feld **cancellationhandler** mit dem Hinweis Text "Aktivität hier ablegen" des **CompensableActivity** -Aktivitäts Designers.|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|Gibt die Aktivität an, die beim Kompensieren der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Aktivität ausgeführt werden soll. Dieser Handler kann explizit mithilfe der <xref:System.Activities.Statements.Compensate>-Aktivität aufgerufen werden.<br /><br /> Um die-Aktivität hinzuzufügen, löschen Sie Ihren Aktivitäts Designer aus der **Toolbox** in das Feld **compensationhandler** mit dem Hinweis Text "Aktivität hier ablegen" des **CompensableActivity** -Aktivitäts Designers.|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|Gibt die Aktivität an, die beim Bestätigen der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Aktivität ausgeführt werden soll. Dieser Handler kann explizit mithilfe der <xref:System.Activities.Statements.Confirm>-Aktivität aufgerufen werden.<br /><br /> Um die-Aktivität hinzuzufügen, löschen Sie Ihren Aktivitäts Designer aus der **Toolbox** in das Feld **confirmationhandler** mit dem Hinweis Text "Aktivität hier ablegen" des **CompensableActivity** -Aktivitäts Designers.|

## <a name="see-also"></a>Siehe auch
 [Transaktion](../workflow-designer/transaction-activity-designers.md) [cancellationscope](../workflow-designer/cancellationscope-activity-designer.md) [Kompensierung](../workflow-designer/compensate-activity-designer.md) [bestätigen](../workflow-designer/confirm-activity-designer.md) [transaktionscope](../workflow-designer/transactionscope-activity-designer.md)