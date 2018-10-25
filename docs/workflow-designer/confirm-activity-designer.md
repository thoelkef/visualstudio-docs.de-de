---
title: Workflow-Designer - Confirm-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f6823b564b7ec3da1585810c27db2f97c1b16ae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49906532"
---
# <a name="confirm-activity-designer"></a>Confirm-Aktivitätsdesigner

Die **bestätigen** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Confirm> Aktivität.

## <a name="the-confirm-activity"></a>Die Confirm-Aktivität
 Die <xref:System.Activities.Statements.Confirm>-Aktivität ruft den <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> explizit für eine in einem <xref:System.Activities.Statements.CompensableActivity>-Objekt enthaltene Aktivität auf. Wenn die <xref:System.Activities.Statements.Confirm>-Aktivität nicht innerhalb des <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> oder <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> einer <xref:System.Activities.Statements.CompensableActivity>-Instanz verwendet wird, dann müssen Sie die <xref:System.Activities.Statements.Confirm.Target%2A>-Eigenschaft angeben.

 Das vom <xref:System.Activities.Statements.CompensationToken> angegebene <xref:System.Activities.Statements.Compensate.Target%2A>-Token stellt eine Möglichkeit dar, eine <xref:System.Activities.Statements.CompensableActivity>-Instanz explizit zu bestätigen oder zu kompensieren, nachdem der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Teil der <xref:System.Activities.Statements.CompensableActivity>-Instanz erfolgreich beendet wurde.

### <a name="using-the-confirm-activity-designer"></a>Verwenden des Confirm-Aktivitätsdesigners
 Die **bestätigen** Aktivitäts-Designer finden Sie in der **Transaktion** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**Registerkarte auf der linken Seite des Workflow-Designers. Wählen Sie alternativ **Toolbox** aus der **Ansicht** Menü, oder drücken Sie **STRG**+**Alt** + **X**.

 Die **bestätigen** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht werden, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Dadurch wird eine <xref:System.Activities.Statements.Confirm>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert Confirm erstellt. Die <xref:System.Activities.Activity.DisplayName%2A> Werte sind möglich im Header des bearbeitet die **bestätigen** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.

### <a name="the-confirm-properties"></a>Die Confirm-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Confirm>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die <xref:System.Activities.Activity.DisplayName%2A> -Eigenschaft bearbeitet werden können, im Eigenschaftenraster oder Workflow-Designer-Oberfläche, aber die <xref:System.Activities.Statements.Confirm.Target%2A> Eigenschaft muss im Eigenschaftenraster bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.CancellationScope>-Aktivität an. Der Standardwert lautet Confirm.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|Gibt das <xref:System.Activities.InArgument%601>-Argument an, welches das <xref:System.Activities.Statements.CompensationToken>-Token für diese <xref:System.Activities.Statements.Confirm>-Aktivität enthält.|

## <a name="see-also"></a>Siehe auch

- [Transaktion](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)