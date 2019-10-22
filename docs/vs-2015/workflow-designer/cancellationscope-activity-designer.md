---
title: Cancellationscope-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa41d63fa4f67037a8e98e72abc3e338ad894f70
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659178"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope-Aktivitätsdesigner
Der **cancellationscope** -Aktivitäts Designer wird verwendet, um eine <xref:System.Activities.Statements.CancellationScope>-Aktivität zu erstellen und zu konfigurieren.

## <a name="the-cancellationscope-activity"></a>Die CancellationScope-Aktivität
 Mit der <xref:System.Activities.Statements.CancellationScope>-Aktivität können Sie für eine Aktivität für die Ausführungs- und Abbruchlogik dieser Aktivität angeben.

### <a name="using-the-cancellationscope-activity-designer"></a>Verwenden des CancellationScope-Aktivitätsdesigners
 Der **cancellationscope** -Aktivitäts Designer befindet sich in der Kategorie **Transaktion** der **Toolbox**, auf die Sie zugreifen können, indem Sie im [!INCLUDE[wfd2](../includes/wfd2-md.md)] auf die Registerkarte **Toolbox** klicken (Sie können auch **Symbolleiste** aus der Ansicht auswählen.Menü oder STRG + ALT + X.)

 Der **cancellationscope** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. innerhalb eines <xref:System.Activities.Statements.Sequence>. Dies erstellt eine <xref:System.Activities.Statements.CancellationScope>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert CancellationScope. Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **cancellationscope** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-cancellationscope-properties"></a>Die CancellationScope-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.CancellationScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die <xref:System.Activities.Activity.DisplayName%2A>-Eigenschaften kann im Eigenschaftenraster bearbeitet werden, die anderen Eigenschaften müssen jedoch auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.Activities.Statements.CancellationScope>-Aktivität. Der Standardwert lautet CancellationScope. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|Gibt die Aktivität an, für die Abbruchlogik bereitgestellt wird. Um die <xref:System.Activities.Statements.CancellationScope.Body%2A>-Aktivität hinzuzufügen, legen Sie eine Aktivität aus der **Toolbox** in das Feld **Body** mit dem Hinweis Text "Aktivität hier ablegen" des **cancellationscope** -Aktivitäts Designers ab.|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|Gibt die Aktivität an, die im Fall eines Abbruchs ausgeführt wird. Um die <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>-Aktivität hinzuzufügen, legen Sie eine Aktivität aus der **Toolbox** im Feld **cancellationhandler** mit dem Hinweis Text "Aktivität hier ablegen" des **cancellationscope** -Aktivitäts Designers ab.|

## <a name="see-also"></a>Siehe auch
 [Transaktion](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [Kompensierung](../workflow-designer/compensate-activity-designer.md) [bestätigen](../workflow-designer/confirm-activity-designer.md) [transaktionscope](../workflow-designer/transactionscope-activity-designer.md)