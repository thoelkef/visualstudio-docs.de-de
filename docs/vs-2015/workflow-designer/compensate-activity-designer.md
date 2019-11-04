---
title: Kompensierungs Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 706cd446e931d6a3a065a3e8abfb58b5a90e9152
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656974"
---
# <a name="compensate-activity-designer"></a>Compensate-Aktivitätsdesigner
Der **Kompensierungs** Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.Compensate>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-compensate-activity"></a>Die Compensate-Aktivität
 Die <xref:System.Activities.Statements.Compensate>-Aktivität ruft den <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> explizit für eine in einem <xref:System.Activities.Statements.CompensableActivity>-Objekt enthaltene Aktivität auf. Wenn die <xref:System.Activities.Statements.Compensate>-Aktivität nicht innerhalb des <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>, <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> oder <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A> einer <xref:System.Activities.Statements.CompensableActivity>-Instanz verwendet wird, dann müssen Sie die <xref:System.Activities.Statements.Compensate.Target%2A>-Eigenschaft angeben.

 Das vom <xref:System.Activities.Statements.CompensationToken> angegebene <xref:System.Activities.Statements.Compensate.Target%2A>-Token stellt eine Möglichkeit dar, eine <xref:System.Activities.Statements.CompensableActivity>-Instanz explizit zu bestätigen oder zu kompensieren, nachdem der <xref:System.Activities.Statements.CompensableActivity.Body%2A>-Teil der <xref:System.Activities.Statements.CompensableActivity>-Instanz erfolgreich beendet wurde.

### <a name="using-the-compensate-activity-designer"></a>Verwenden des Compensate-Aktivitätsdesigners
 Der **Kompensierungs** Aktivitäts Designer befindet sich in der Kategorie **Transaktion** der **Toolbox**, auf **die Sie zugreifen** können, indem Sie auf der linken Seite der [!INCLUDE[wfd2](../includes/wfd2-md.md)] auf die Registerkarte **Toolbox** klicken (Sie **können auch im Feld Menü anzeigen** oder STRG + ALT + X.)

 Der **Kompensierungs** Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Daraufhin wird eine <xref:System.Activities.Statements.Compensate>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert Compensate erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **Kompensierungs** Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-compensate-properties"></a>Die Compensate-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.CancellationScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die <xref:System.Activities.Activity.DisplayName%2A>-Eigenschaften kann im Eigenschaftenraster und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche bearbeitet werden, die <xref:System.Activities.Statements.Compensate.Target%2A>- Eigenschaften muss jedoch im Eigenschaftenraster bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den optionalen Anzeigenamen der <xref:System.Activities.Statements.Compensate>-Aktivität an. Der Standardwert lautet Compensate.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|Gibt das <xref:System.Activities.InArgument%601>-Argument an, welches das <xref:System.Activities.Statements.CompensationToken>-Token für diese <xref:System.Activities.Statements.Compensate>-Aktivität enthält.|

## <a name="see-also"></a>Siehe auch
 [Transaktions](../workflow-designer/transaction-activity-designers.md) [compensableactivity](../workflow-designer/compensableactivity-activity-designer.md) [Kompensierungs - Designer](../workflow-designer/compensate-activity-designer.md) [bestätigen](../workflow-designer/confirm-activity-designer.md) [transaktionscope](../workflow-designer/transactionscope-activity-designer.md)