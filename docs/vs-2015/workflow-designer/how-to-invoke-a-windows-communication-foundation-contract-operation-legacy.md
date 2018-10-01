---
title: 'Vorgehensweise: Aufrufen ein Windows Communication Foundation-Vertragsvorgangs (Legacy) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 70f96176cb40fd531ddb41f58126ea310091d3fe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515415"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Vorgehensweise: Aufrufen eines Windows Communication Foundation-Vertragsvorgangs (Vorgängerversion)
In diesem Thema wird der Aufruf eines [!INCLUDE[indigo1](../includes/indigo1-md.md)]-Vertragsvorgangs mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] beschrieben, die auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielt.  
  
 Nach dem Ziehen einer **SendActivity** Aktivität aus der Toolbox auf die Entwurfsoberfläche des Workflows müssen Sie einen vorhandenen Vertrag importieren und zu bestimmen, welcher Vorgang aus, die aufgerufen wird, **SendActivity** Aktivität. Wählen Sie den Vertrag und seine Vorgänge über die [Choose Vorgang Dialog Box (Legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
 Beim Verwenden einer Konfigurationsdatei mit dem Dienst müssen Sie auch ein <xref:System.Workflow.Activities.ChannelToken> angeben. Das <xref:System.Workflow.Activities.ChannelToken> identifiziert die Endpunktkonfiguration, die die Sendeaktivität für die Verbindung zum Workflowdienst verwendet.  
  
### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>So rufen Sie einen WCF-Vertragsvorgang aus einer SendActivity-Aktivität auf  
  
1.  Doppelklicken Sie auf die **SendActivity** Aktivität im Designer oder klicken Sie auf die Auslassungspunkte neben dem **ServiceOperationInfo** -Eigenschaft in der **Eigenschaften** Bereich.  
  
2.  Wenn die **Vorgang auswählen** -Dialogfeld geöffnet wird, klicken Sie auf **Import** in der oberen rechten Ecke des Dialogfelds.  
  
     Die [navigieren, und wählen Sie eine .NET (Dialogfeld) (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) wird geöffnet.  
  
3.  Suchen Sie eine Assembly oder ein Projekt, das den gewünschten Vertrag enthält.  
  
4.  Wählen Sie den Vertrag, und klicken Sie auf **OK**.  
  
5.  Klicken Sie unter **verfügbaren Vorgänge**, wählen Sie den Vorgang, die Sie verwenden möchten, rufen Sie aus, und klicken Sie auf **OK**.  
  
### <a name="to-specify-a-channel-token"></a>So geben Sie ein Kanaltoken an  
  
1.  Wählen Sie die <xref:System.Workflow.Activities.SendActivity>-Aktivität im Designer aus.  
  
2.  In der **Eigenschaften** Bereich, geben Sie einen Namen für die <xref:System.Workflow.Activities.ChannelToken>. Dieser Name identifiziert das Kanaltoken eindeutig.  
  
3.  Erweitern Sie den Kanaltokenknoten, und geben Sie einen Namen für den Clientendpunkt an, den Sie im <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>-Feld verwenden. Die Endpunktkonfiguration mit dem gleichen Namen in der Konfigurationsdatei wird zum Konfigurieren des Kanals verwendet.  
  
4.  Erstellen Sie die Endpunktkonfiguration in der Konfigurationsdatei, wenn noch nicht vorhanden. Weitere Informationen zum Konfigurieren des Clients finden Sie unter [WCF Client Overview](http://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d).  
  
## <a name="see-also"></a>Siehe auch  
 [Dialogfeld "Vorgang" (Vorgängerversion) auswählen](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Vorgehensweise: implementieren ein WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)