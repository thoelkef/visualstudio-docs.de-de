---
title: "Compensate-Aktivitätsdesigner | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4aee48f5fa8b8452b5e80bd53002fe3c6f7f2fe7
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="compensate-activity-designer"></a>Compensate-Aktivitätsdesigner
Die **kompensieren** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.Activities.Statements.Compensate> Aktivität.

## <a name="the-compensate-activity"></a>Die Compensate-Aktivität
 Die <xref:System.Activities.Statements.Compensate>-Aktivität ruft den <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> explizit für eine in einem <xref:System.Activities.Statements.CompensableActivity>-Objekt enthaltene Aktivität auf. Wenn die <xref:System.Activities.Statements.Compensate>-Aktivität nicht innerhalb des <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> oder <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> einer <xref:System.Activities.Statements.CompensableActivity>-Instanz verwendet wird, dann müssen Sie die <xref:System.Activities.Statements.Compensate.Target%2A>-Eigenschaft angeben.

 Das vom <xref:System.Activities.Statements.CompensationToken> angegebene <xref:System.Activities.Statements.Compensate.Target%2A>-Token stellt eine Möglichkeit dar, eine <xref:System.Activities.Statements.CompensableActivity>-Instanz explizit zu bestätigen oder zu kompensieren, nachdem der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Teil der <xref:System.Activities.Statements.CompensableActivity>-Instanz erfolgreich beendet wurde.

### <a name="using-the-compensate-activity-designer"></a>Verwenden des Compensate-Aktivitätsdesigners
 Die **kompensieren** Aktivitäts-Designer finden Sie in der **Transaktion** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox** auf der linken Seite der Registerkarte die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)

 Die **kompensieren** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden, z. B. in einem <xref:System.Activities.Statements.Sequence>. Daraufhin wird eine <xref:System.Activities.Statements.Compensate>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert Compensate erstellt. Die <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des bearbeitet werden die **kompensieren** Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters.

### <a name="the-compensate-properties"></a>Die Compensate-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.CancellationScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die <xref:System.Activities.Activity.DisplayName%2A>-Eigenschaften kann im Eigenschaftenraster und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]-Oberfläche bearbeitet werden, die <xref:System.Activities.Statements.Compensate.Target%2A>- Eigenschaften muss jedoch im Eigenschaftenraster bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.Compensate>-Aktivität an. Der Standardwert lautet Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Gibt das <xref:System.Activities.InArgument%601>-Argument an, welches das <xref:System.Activities.Statements.CompensationToken>-Token für diese <xref:System.Activities.Statements.Compensate>-Aktivität enthält.|

## <a name="see-also"></a>Siehe auch

- [Transaktion](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate-Aktivitätsdesigner](../workflow-designer/compensate-activity-designer.md)
- [Vergewissern Sie sich](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)