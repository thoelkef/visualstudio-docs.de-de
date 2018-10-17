---
title: InitializeCorrelation-Aktivitätsdesigner | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 9dd9d622785fbfebd8560daf9bf459716381ddbf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49234025"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation-Aktivitätsdesigner
Die **InitializeCorrelation** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivität, die zum Herstellen einer Korrelations zwischen Nachrichten vor dem Senden oder empfangen verwendet wird.  
  
## <a name="the-initializecorrelation-activity"></a>Die InitializeCorrelation-Aktivität  
 Eine <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität wird verwendet, um Korrelationen zu initialisieren, ohne eine Nachricht zu senden oder zu empfangen. In der Regel wird die Korrelation durch das Senden oder Empfangen einer Nachricht initialisiert. Wenn eine Korrelation festgelegt werden muss, bevor eine Nachricht gesendet oder empfangen wird, verwenden Sie <xref:System.ServiceModel.Activities.InitializeCorrelation>, um die Korrelation zu initialisieren.  
  
### <a name="using-the-initializecorrelation-activity-designer"></a>Verwenden des InitializeCorrelation-Aktivitätsdesigners  
 Die **InitializeCorrelation** Aktivitäts-Designer finden Sie in der **Messaging** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**  Registerkarte die [!INCLUDE[wfd2](../includes/wfd2-md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menü- oder STRG + ALT + X.)  
  
 Die **InitializeCorrelation** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche. Erstellt eine <xref:System.ServiceModel.Activities.InitializeCorrelation> -Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A> von InitializeCorrelation.The <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **InitializeCorrelation** Aktivitäts-Designer oder in der  **"DisplayName"** im Feld der **Eigenschaften** Fenster.  
  
 Die <xref:System.ServiceModel.Activities.CorrelationHandle> kann gibt an, der **Korrelation** Feld **Eigenschaften** -Fenster auf die **InitializeCorrelation** aktivitätsdesigneroberfläche.  
  
 Klicken auf die Schaltfläche mit den Auslassungspunkten neben der **CorrelationData** Feld **Eigenschaften** Fenster oder die "View …" Hinweise für Text auf **InitializeCorrelation** aktivitätsdesigneroberfläche zeigt die **Korrelation initialisieren** Dialogfeld, in dem Sie das Korrelationshandle und verwendet, um Schlüssel-Wert-Paare angeben können, Initialisieren Sie es aus. [!INCLUDE[crabout](../includes/crabout-md.md)] mit diesem Dialogfeld finden Sie unter den [Auflistung-Editor-Dialogfeld](../workflow-designer/type-collection-editor-dialog-box.md) Thema.  
  
### <a name="the-initializecorrelation-properties"></a>Die InitializeCorrelation-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.InitializeCorrelation>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können bearbeitet werden, **Eigenschaften** Fenster oder auf [!INCLUDE[wfd2](../includes/wfd2-md.md)] Oberfläche.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität. Der Standardwert lautet InitializeCorrelation.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den benutzerfreundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen solchen Wert zu verwenden.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|Das <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekt, das verwendet wurde, um Workflowaktivitäten in der Korrelation zuzuordnen.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Ein Wörterbuch von Korrelationsdaten, die Nachrichten mit der Workflowinstanz verknüpft.<br /><br /> Verwenden der **Korrelation initialisieren** Dialogfeld zum Konfigurieren der <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. [!INCLUDE[crabout](../includes/crabout-md.md)] die Verwendung dieses Dialogfelds finden Sie unter der [Auflistung-Editor-Dialogfeld](../workflow-designer/type-collection-editor-dialog-box.md) Thema.|  
  
## <a name="see-also"></a>Siehe auch  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Empfangen](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Senden](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)