---
title: "Vorgehensweise: Aufrufen ein Windows Communication Foundation-Vertragsvorgangs (Vorgängerversion) | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 522db4f46486470333393ca99f384f258898e09a
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Vorgehensweise: Aufrufen eines Windows Communication Foundation-Vertragsvorgangs (Vorgängerversion)
In diesem Thema wird beschrieben, wie zum Aufrufen einer [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] -vertragsvorgangs mithilfe der älteren Windows-Workflow-Designer, die als Ziel verwendet die [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Nach dem Ziehen einer **SendActivity** Aktivität aus der Toolbox auf die Entwurfsoberfläche des Workflows müssen Sie einen vorhandenen Vertrag importieren und zu bestimmen, welcher Vorgang aus, die aufgerufen wird, **SendActivity** Aktivität. Wählen Sie den Vertrag und seine Vorgänge über die [wählen Vorgang (Dialogfeld) (Legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md).

 Beim Verwenden einer Konfigurationsdatei mit dem Dienst müssen Sie auch ein <xref:System.Workflow.Activities.ChannelToken> angeben. Das <xref:System.Workflow.Activities.ChannelToken> identifiziert die Endpunktkonfiguration, die die Sendeaktivität für die Verbindung zum Workflowdienst verwendet.

### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>So rufen Sie einen WCF-Vertragsvorgang aus einer SendActivity-Aktivität auf

1.  Doppelklicken Sie auf die **SendActivity** Aktivität im Designer oder klicken Sie auf die Auslassungszeichen neben der **ServiceOperationInfo** Eigenschaft in der **Eigenschaften** Bereich.

2.  Wenn die **Vorgang auswählen** Dialogfeld geöffnet ist, klicken Sie auf **Import** in der oberen rechten Ecke des Dialogfelds.

     Die [navigieren, und wählen Sie eine .NET (Dialogfeld) (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) wird geöffnet.

3.  Suchen Sie eine Assembly oder ein Projekt, das den gewünschten Vertrag enthält.

4.  Wählen Sie den Vertrag aus, und klicken Sie auf **OK**.

5.  Klicken Sie unter **verfügbaren Vorgänge**, wählen Sie den Vorgang, die Sie verwenden möchten, aufzurufen, und klicken Sie auf **OK**.

### <a name="to-specify-a-channel-token"></a>So geben Sie ein Kanaltoken an

1.  Wählen Sie die <xref:System.Workflow.Activities.SendActivity>-Aktivität im Designer aus.

2.  In der **Eigenschaften** Bereich, geben Sie einen Namen für die <xref:System.Workflow.Activities.ChannelToken>. Dieser Name identifiziert das Kanaltoken eindeutig.

3.  Erweitern Sie den Kanaltokenknoten, und geben Sie einen Namen für den Clientendpunkt an, den Sie im <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>-Feld verwenden. Die Endpunktkonfiguration mit dem gleichen Namen in der Konfigurationsdatei wird zum Konfigurieren des Kanals verwendet.

4.  Erstellen Sie die Endpunktkonfiguration in der Konfigurationsdatei, wenn noch nicht vorhanden. Weitere Informationen zum Konfigurieren Ihrer Clients finden Sie unter [Überblick über WCF-Client](/dotnet/framework/wcf/wcf-client-overview).

## <a name="see-also"></a>Siehe auch

- [Dialogfeld "Vorgang auswählen" (Vorgängerversion)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [Vorgehensweise: implementieren ein WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)