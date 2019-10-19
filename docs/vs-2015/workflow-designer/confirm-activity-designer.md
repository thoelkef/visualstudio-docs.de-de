---
title: Confirm-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Confirm.UI
ms.assetid: c753b67b-b0e7-462a-bb4e-ba8db04a078d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b3835c6cb537e7ac74862ac4a6794dd7b0bd5003
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656962"
---
# <a name="confirm-activity-designer"></a>Confirm-Aktivitätsdesigner
Der **Confirm** -Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.Confirm>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-confirm-activity"></a>Die Confirm-Aktivität
 Die <xref:System.Activities.Statements.Confirm>-Aktivität ruft den <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> explizit für eine in einem <xref:System.Activities.Statements.CompensableActivity>-Objekt enthaltene Aktivität auf. Wenn die <xref:System.Activities.Statements.Confirm>-Aktivität nicht innerhalb des <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> oder <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> einer <xref:System.Activities.Statements.CompensableActivity>-Instanz verwendet wird, dann müssen Sie die <xref:System.Activities.Statements.Confirm.Target%2A>-Eigenschaft angeben.

 Das vom <xref:System.Activities.Statements.CompensationToken> angegebene <xref:System.Activities.Statements.Compensate.Target%2A>-Token stellt eine Möglichkeit dar, eine <xref:System.Activities.Statements.CompensableActivity>-Instanz explizit zu bestätigen oder zu kompensieren, nachdem der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Teil der <xref:System.Activities.Statements.CompensableActivity>-Instanz erfolgreich beendet wurde.

### <a name="using-the-confirm-activity-designer"></a>Verwenden des Confirm-Aktivitätsdesigners
 Der **Confirm** -Aktivitäts Designer befindet sich in der Kategorie **Transaktion** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite der [!INCLUDE[wfd2](../includes/wfd2-md.md)] auf die Registerkarte **Toolbox** klicken (Sie können auch in der Ansicht **Toolbar** auswählen).Menü oder STRG + ALT + X.)

 Der **Confirm** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Dadurch wird eine <xref:System.Activities.Statements.Confirm>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert Confirm erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann entweder im Header des **Confirm** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-confirm-properties"></a>Die Confirm-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Confirm>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die <xref:System.Activities.Activity.DisplayName%2A>-Eigenschaften kann im Eigenschaftenraster und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche bearbeitet werden, die <xref:System.Activities.Statements.Confirm.Target%2A>- Eigenschaften muss jedoch im Eigenschaftenraster bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.CancellationScope>-Aktivität an. Der Standardwert lautet Confirm.|
|<xref:System.Activities.Statements.Confirm.Target%2A>|True|Gibt das <xref:System.Activities.InArgument%601>-Argument an, welches das <xref:System.Activities.Statements.CompensationToken>-Token für diese <xref:System.Activities.Statements.Confirm>-Aktivität enthält.|

## <a name="see-also"></a>Siehe auch
 [Transaktion](../workflow-designer/transaction-activity-designers.md) [cancellationscope](../workflow-designer/cancellationscope-activity-designer.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [kompensiert](../workflow-designer/compensate-activity-designer.md) [transaktionscope](../workflow-designer/transactionscope-activity-designer.md)