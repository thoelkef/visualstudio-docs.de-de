---
title: Workflow-Designer - Compensate-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c7c195c9bfd6bedf0220a989c31936975fb6d70a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54950428"
---
# <a name="compensate-activity-designer"></a>Compensate-Aktivitätsdesigner

Die **kompensieren** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Compensate> Aktivität.

## <a name="the-compensate-activity"></a>Die Compensate-Aktivität

Die <xref:System.Activities.Statements.Compensate>-Aktivität ruft den <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> explizit für eine in einem <xref:System.Activities.Statements.CompensableActivity>-Objekt enthaltene Aktivität auf. Wenn die <xref:System.Activities.Statements.Compensate>-Aktivität nicht innerhalb des <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> oder <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> einer <xref:System.Activities.Statements.CompensableActivity>-Instanz verwendet wird, dann müssen Sie die <xref:System.Activities.Statements.Compensate.Target%2A>-Eigenschaft angeben.

Das vom <xref:System.Activities.Statements.CompensationToken> angegebene <xref:System.Activities.Statements.Compensate.Target%2A>-Token stellt eine Möglichkeit dar, eine <xref:System.Activities.Statements.CompensableActivity>-Instanz explizit zu bestätigen oder zu kompensieren, nachdem der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Teil der <xref:System.Activities.Statements.CompensableActivity>-Instanz erfolgreich beendet wurde.

### <a name="using-the-compensate-activity-designer"></a>Verwenden des Compensate-Aktivitätsdesigners

Die **kompensieren** Aktivitäts-Designer finden Sie in der **Transaktion** Kategorie der **Toolbox**. Zum Öffnen **Toolbox**, wählen die **Toolbox** Registerkarte auf der linken Seite des Workflow-Designers. Wählen Sie alternativ **Toolbox** aus der **Ansicht** Menü, oder drücken Sie **STRG**+**Alt** + **X**.

Die **kompensieren** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht werden, wo Aktivitäten platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Löschen die Aktivitäts-Designer erstellt eine <xref:System.Activities.Statements.Compensate> -Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> -Standardwert Compensate. Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **kompensieren** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.

### <a name="the-compensate-properties"></a>Die Compensate-Eigenschaften

In der folgenden Tabelle werden die <xref:System.Activities.Statements.CancellationScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die <xref:System.Activities.Activity.DisplayName%2A> Eigenschaft im Eigenschaftenraster oder auf die Oberfläche des Workflow-Designer bearbeitet werden kann. Bearbeiten der <xref:System.Activities.Statements.Compensate.Target%2A> Eigenschaft im Eigenschaftenraster.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.Compensate>-Aktivität an. Der Standardwert lautet Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Gibt das <xref:System.Activities.InArgument%601>-Argument an, welches das <xref:System.Activities.Statements.CompensationToken>-Token für diese <xref:System.Activities.Statements.Compensate>-Aktivität enthält.|

## <a name="see-also"></a>Siehe auch

- [Transaktion](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate-Aktivitätsdesigner](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)