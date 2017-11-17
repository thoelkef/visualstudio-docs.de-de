---
title: "TransactedReceiveScope-Aktivitätsdesigner | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: System.ServiceModel.Activities.TransactedReceiveScope.UI
ms.assetid: 7ca93aad-4e83-4d81-90f4-998ee114d9b6
caps.latest.revision: "4"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77f7b4e0131eb5afc4585a68097c8d419145096b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="transactedreceivescope-activity-designer"></a>TransactedReceiveScope-Aktivitätsdesigner
Die **TransactedReceiveScope** -Designer dient zum Erstellen und Konfigurieren einer <xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivität.  
  
## <a name="the-transactedreceivescope-activity"></a>Die TransactedReceiveScope-Aktivität  
 Die <xref:System.ServiceModel.Activities.TransactedReceiveScope>-Aktivität ermöglicht es Ihnen, eine Transaktion in Servertransaktionen einzubinden, die von einem Workflow oder einem Verteiler erstellt werden.  
  
### <a name="using-the-transactedreceivescope-activity-designer"></a>Verwenden des TransactedReceiveScope-Aktivitätsdesigners  
 Die **TransactedReceiveScope** Aktivitäts-Designer finden Sie in der **Messaging** Kategorie der **Toolbox**, die erfolgt durch Klicken auf die **Toolbox**  Registerkarte [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] (Wählen Sie alternativ **Symbolleiste** aus der **Ansicht** Menüs oder STRG + ALT + X drücken.)  
  
 Die **TransactedReceiveScope** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden. Dies erstellt eine <xref:System.ServiceModel.Activities.TransactedReceiveScope> -Aktivität mit dem standardmäßigen **DisplayName** des TransactedReceiveScope. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **TransactedReceiveScope** Aktivitäts-Designer oder in der **DisplayName** Feld des Eigenschaftenrasters.  
  
 Die **TransactedReceiveScope** -Designer enthält **anfordern** und **Text** Felder. Diese werden verwendet, um die <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>-Eigenschaft, die eine <xref:System.ServiceModel.Activities.Receive>-Aktivität angibt, und die <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>-Eigenschaft zu konfigurieren, die eine andere <xref:System.Activities.Activity>-Instanz angibt. <xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A> erstellt eine Transaktion. Die Transaktion wird dann dem Geltungsbereich der <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>-Instanz zugeordnet, damit jede Aktivität in diesem Bereich in dieser Transaktion ausgeführt wird.  
  
### <a name="the-transactedreceivescope-properties"></a>Die TransactedReceiveScope-Eigenschaften  
 In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.TransactedReceiveScope>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese <xref:System.Activities.Activity.DisplayName%2A>-Eigenschaft kann im Eigenschaftenraster oder in der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]-Oberfläche bearbeitet werden, die anderen Eigenschaften müssen jedoch in der Entwurfsoberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der optionale Anzeigename der <xref:System.ServiceModel.Activities.TransactedReceiveScope>-Aktivität. Der Standardwert lautet TransactedReceiveScope.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A>-Name nicht unbedingt erforderlich ist, wird als Best Practice empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Request%2A>|True|Löscht eine <xref:System.ServiceModel.Activities.Receive> Aktivität in der **anfordern** -Block auf der aktivitätsdesigneroberfläche.|  
|<xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A>|False|Löscht eine <xref:System.Activities.Activity> in der **Text** -Block auf der aktivitätsdesigneroberfläche.|  
  
## <a name="see-also"></a>Siehe auch  
 [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)   
 [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)   
 [Empfangen](../workflow-designer/receive-activity-designer.md)   
 [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)   
 [Senden](../workflow-designer/send-activity-designer.md)   
 [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)