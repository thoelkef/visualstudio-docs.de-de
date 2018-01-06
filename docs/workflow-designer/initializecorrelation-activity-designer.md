---
title: "InitializeCorrelation-Aktivitätsdesigner | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 83abd9f76f68ec4131840fb0ea58e9aeb93f30d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation-Aktivitätsdesigner
Die **InitializeCorrelation** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivität, die zum Herstellen einer Korrelations zwischen Nachrichten vor dem Senden oder empfangen verwendet wird.  
  
## <a name="the-initializecorrelation-activity"></a>Die InitializeCorrelation-Aktivität  
 Eine <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität wird verwendet, um Korrelationen zu initialisieren, ohne eine Nachricht zu senden oder zu empfangen. In der Regel wird die Korrelation durch das Senden oder Empfangen einer Nachricht initialisiert. Wenn eine Korrelation festgelegt werden muss, bevor eine Nachricht gesendet oder empfangen wird, verwenden Sie <xref:System.ServiceModel.Activities.InitializeCorrelation>, um die Korrelation zu initialisieren.  
  
### <a name="using-the-initializecorrelation-activity-designer"></a>Verwenden des InitializeCorrelation-Aktivitätsdesigners  
 Die **InitializeCorrelation** Aktivitäts-Designer finden Sie in der **Messaging** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**  Registerkarte auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X.)  
  
 Die **InitializeCorrelation** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] Oberfläche. Dies erstellt eine <xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivität hat den Standardwert <xref:System.Activities.Activity.DisplayName%2A> von InitializeCorrelation.The <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **InitializeCorrelation** Aktivitäts-Designer oder in der  **DisplayName** im Feld der **Eigenschaften** Fenster.  
  
 Die <xref:System.ServiceModel.Activities.CorrelationHandle> kann gibt an, der **Korrelation** Feld **Eigenschaften** -Fenster auf die **InitializeCorrelation** aktivitätsdesigneroberfläche.  
  
 Klicken auf die Schaltfläche mit den Auslassungspunkten neben der **CorrelationData** Feld **Eigenschaften** Fenster oder den Hinweistext "Anzeigen …" auf **InitializeCorrelation** Aktivitäts-Designer Oberfläche zeigt die **Korrelation initialisieren** (Dialogfeld), in dem Sie das Korrelationshandle und verwendet, um es zu initialisieren Schlüssel-Wert-Paare angeben können. [!INCLUDE[crabout](../test/includes/crabout_md.md)]Mithilfe dieses Dialogfelds finden Sie unter der [Auflistung-Editor (Dialogfeld)](../workflow-designer/type-collection-editor-dialog-box.md) Thema.  
  
### <a name="the-initializecorrelation-properties"></a>Die InitializeCorrelation-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.InitializeCorrelation>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können bearbeitet werden, **Eigenschaften** Fenster oder auf [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] Oberfläche.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität. Der Standardwert lautet InitializeCorrelation.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den benutzerfreundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen solchen Wert zu verwenden.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|Das <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekt, das verwendet wurde, um Workflowaktivitäten in der Korrelation zuzuordnen.|  
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Ein Wörterbuch von Korrelationsdaten, die Nachrichten mit der Workflowinstanz verknüpft.<br /><br /> Verwenden der **Korrelation initialisieren** Dialogfeld zum Konfigurieren der <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. [!INCLUDE[crabout](../test/includes/crabout_md.md)]die Verwendung dieses Dialogfeld finden Sie unter der [Auflistung-Editor (Dialogfeld)](../workflow-designer/type-collection-editor-dialog-box.md) Thema.|  
  
## <a name="see-also"></a>Siehe auch  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [Empfangen](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Senden](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)   
 [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)