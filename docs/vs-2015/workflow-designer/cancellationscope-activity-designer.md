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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659178"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope-Aktivitätsdesigner
Der **cancellationscope** -Aktivitäts Designer wird verwendet, um eine-Aktivität zu erstellen und zu konfigurieren <xref:System.Activities.Statements.CancellationScope> .

## <a name="the-cancellationscope-activity"></a>Die CancellationScope-Aktivität
 Mit der <xref:System.Activities.Statements.CancellationScope>-Aktivität können Sie für eine Aktivität für die Ausführungs- und Abbruchlogik dieser Aktivität angeben.

### <a name="using-the-cancellationscope-activity-designer"></a>Verwenden des CancellationScope-Aktivitätsdesigners
 Der **cancellationscope** -Aktivitäts Designer befindet sich in der Kategorie **Transaktion** der **Toolbox**, auf die Sie zugreifen können, indem Sie in auf die Registerkarte **Toolbox** klicken (Sie können auch im [!INCLUDE[wfd2](../includes/wfd2-md.md)] Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG + ALT + X drücken).

 Der **cancellationscope** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der- [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, z. b. in einer <xref:System.Activities.Statements.Sequence> . Dies erstellt eine <xref:System.Activities.Statements.CancellationScope>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert CancellationScope. Der <xref:System.Activities.Activity.DisplayName%2A> Wert kann im Header des **cancellationscope** -Aktivitäts Designers oder im Feld **Display Name** des Eigenschaften Rasters bearbeitet werden.

### <a name="the-cancellationscope-properties"></a>Die CancellationScope-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.CancellationScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Die <xref:System.Activities.Activity.DisplayName%2A>-Eigenschaften kann im Eigenschaftenraster bearbeitet werden, die anderen Eigenschaften müssen jedoch auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verbrauch|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Falsch|Der optionale Anzeigename der <xref:System.Activities.Statements.CancellationScope>-Aktivität. Der Standardwert lautet CancellationScope. Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|Richtig|Gibt die Aktivität an, für die Abbruchlogik bereitgestellt wird. Um die-Aktivität hinzuzufügen, legen Sie <xref:System.Activities.Statements.CancellationScope.Body%2A> eine Aktivität aus der **Toolbox** in das Feld **Body** mit dem Hinweis Text "Aktivität hier ablegen" des **cancellationscope** -Aktivitäts Designers ab.|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|Richtig|Gibt die Aktivität an, die im Fall eines Abbruchs ausgeführt wird. Um die- <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> Aktivität hinzuzufügen, löschen Sie eine Aktivität aus der **Toolbox** im Feld **cancellationhandler** mit dem Hinweis Text "Aktivität hier ablegen" des **cancellationscope** -Aktivitäts Designers.|

## <a name="see-also"></a>Weitere Informationen
 [Transaktion](../workflow-designer/transaction-activity-designers.md) [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md) [Kompensierung](../workflow-designer/compensate-activity-designer.md) [bestätigen](../workflow-designer/confirm-activity-designer.md) [transaktionscope](../workflow-designer/transactionscope-activity-designer.md)