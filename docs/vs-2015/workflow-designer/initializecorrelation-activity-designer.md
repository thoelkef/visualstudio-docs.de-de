---
title: InitializeCorrelation-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 145b67574169696771f4102b29e9dc8f6a9d1575
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659021"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation-Aktivitätsdesigner
Der **InitializeCorrelation** -Aktivitäts Designer wird verwendet, um eine <xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivität zu erstellen und zu konfigurieren, die verwendet wird, um eine Korrelation zwischen Nachrichten vor dem Senden oder empfangen herzustellen.

## <a name="the-initializecorrelation-activity"></a>Die InitializeCorrelation-Aktivität
 Eine <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität wird verwendet, um Korrelationen zu initialisieren, ohne eine Nachricht zu senden oder zu empfangen. In der Regel wird die Korrelation durch das Senden oder Empfangen einer Nachricht initialisiert. Wenn eine Korrelation festgelegt werden muss, bevor eine Nachricht gesendet oder empfangen wird, verwenden Sie <xref:System.ServiceModel.Activities.InitializeCorrelation>, um die Korrelation zu initialisieren.

### <a name="using-the-initializecorrelation-activity-designer"></a>Verwenden des InitializeCorrelation-Aktivitätsdesigners
 Der **InitializeCorrelation** -Aktivitäts Designer befindet sich in der Kategorie **Messaging** der **Toolbox**, auf die Sie zugreifen können, indem Sie im [!INCLUDE[wfd2](../includes/wfd2-md.md)] auf die Registerkarte **Toolbox** klicken (Sie können auch **Symbolleiste** aus der Ansicht auswählen.Menü oder STRG + ALT + X.)

 Der **InitializeCorrelation** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche abgelegt werden. Dadurch wird eine <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität mit einem Standard <xref:System.Activities.Activity.DisplayName%2A> von InitializeCorrelation erstellt. der <xref:System.Activities.Activity.DisplayName%2A> kann im Header des **InitializeCorrelation** -Aktivitäts Designers oder im Feld **Display Name** des **Eigenschaften** Fensters bearbeitet werden.

 Der <xref:System.ServiceModel.Activities.CorrelationHandle> kann im Feld **Korrelation** im Fenster **Eigenschaften** auf der **InitializeCorrelation** -Aktivitäts Designer Oberfläche angegeben werden.

 Klicken Sie im **Eigenschaften** Fenster auf die Schaltfläche mit den Auslassungs Punkten neben dem Feld **correlationdata** oder der Ansicht "Ansicht...". der Hinweis Text auf der **InitializeCorrelation** -Aktivitäts Designer Oberfläche zeigt das Dialogfeld **Korrelation initialisieren** an, in dem Sie das Korrelations Handle und die Schlüssel-Wert-Paare angeben können, die zum Initialisieren verwendet werden. [!INCLUDE[crabout](../includes/crabout-md.md)] in diesem Dialogfeld finden Sie im Thema typauflistungs- [Editor](../workflow-designer/type-collection-editor-dialog-box.md) .

### <a name="the-initializecorrelation-properties"></a>Die InitializeCorrelation-Eigenschaften
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.InitializeCorrelation>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im **Eigenschaften** Fenster oder auf [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche bearbeitet werden.

|Eigenschaftenname|Erforderlich|Verwendung|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität. Der Standardwert lautet InitializeCorrelation.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den benutzerfreundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen solchen Wert zu verwenden.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|Das <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekt, das verwendet wurde, um Workflowaktivitäten in der Korrelation zuzuordnen.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Ein Wörterbuch von Korrelationsdaten, die Nachrichten mit der Workflowinstanz verknüpft.<br /><br /> Verwenden Sie das Dialogfeld **Korrelation initialisieren** , um die <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A> zu konfigurieren. [!INCLUDE[crabout](../includes/crabout-md.md)] das Dialogfeld dieses Dialogfeld verwenden finden Sie im Thema typauflistungs- [Editor](../workflow-designer/type-collection-editor-dialog-box.md) .|

## <a name="see-also"></a>Siehe auch
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md) [Receive](../workflow-designer/receive-activity-designer.md) [receiveandsendreply](../workflow-designer/receiveandsendreply-template-designer.md) [Send](../workflow-designer/send-activity-designer.md) [sendandreceivereply](../workflow-designer/sendandreceivereply-template-designer.md) [transactedreceivescope](../workflow-designer/transactedreceivescope-activity-designer.md)