---
title: 'Workflow-Designer - Vorgehensweise: Aufrufen ein Windows Communication Foundation-Vertragsvorgangs (Vorgängerversion)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b39d2132b29ec1f8fbfd8339bdb8f81e6f752a0
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Vorgehensweise: Aufrufen eines Windows Communication Foundation-Vertragsvorgangs (Vorgängerversion)

In diesem Thema wird beschrieben, wie aufzurufenden einem Windows Communication Foundation (WCF)-vertragsvorgangs mit älteren Windows Workflow-Designer mit der Zielversion .NET Framework, Version 3.5 oder die WinFX.

Nach dem Ziehen einer **SendActivity** Aktivität aus der Toolbox auf die Entwurfsoberfläche des Workflows einen vorhandenen Vertrag importieren. Bestimmen, welcher Vorgang aufgerufen wird, von dem **SendActivity** Aktivität. Wählen Sie den Vertrag und seine Vorgänge über die [wählen Vorgang (Dialogfeld) (Legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md).

Wenn Sie eine Konfigurationsdatei mit dem Dienst verwenden, müssen Sie auch angeben einer <xref:System.Workflow.Activities.ChannelToken>. Das <xref:System.Workflow.Activities.ChannelToken> identifiziert die Endpunktkonfiguration, die die Sendeaktivität für die Verbindung zum Workflowdienst verwendet.

## <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>So rufen Sie einen WCF-Vertragsvorgang aus einer SendActivity-Aktivität auf

1.  Doppelklicken Sie auf die **SendActivity** Aktivität im Designer oder klicken Sie auf die Auslassungszeichen neben der **ServiceOperationInfo** Eigenschaft in der **Eigenschaften** Bereich.

2.  Wenn die **Vorgang auswählen** Dialogfeld geöffnet ist, klicken Sie auf **Import** in der oberen rechten Ecke des Dialogfelds.

     Die [navigieren, und wählen Sie eine .NET (Dialogfeld) (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) wird geöffnet.

3.  Suchen Sie eine Assembly oder ein Projekt, das den gewünschten Vertrag enthält.

4.  Wählen Sie den Vertrag aus, und klicken Sie auf **OK**.

5.  Klicken Sie unter **verfügbaren Vorgänge**, wählen Sie den Vorgang, die Sie verwenden möchten, aufzurufen, und klicken Sie auf **OK**.

## <a name="to-specify-a-channel-token"></a>So geben Sie ein Kanaltoken an

1.  Wählen Sie die <xref:System.Workflow.Activities.SendActivity>-Aktivität im Designer aus.

2.  In der **Eigenschaften** Bereich, geben Sie einen Namen für die <xref:System.Workflow.Activities.ChannelToken>. Dieser Name identifiziert das Kanaltoken eindeutig.

3.  Erweitern Sie den Kanaltokenknoten, und geben Sie einen Namen für den Clientendpunkt an, den Sie im <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>-Feld verwenden. Die Endpunktkonfiguration mit dem gleichen Namen in der Konfigurationsdatei wird verwendet, um den Kanal zu konfigurieren.

4.  Erstellen Sie die Endpunktkonfiguration in der Konfigurationsdatei, wenn noch nicht vorhanden. Weitere Informationen zum Konfigurieren Ihrer Clients finden Sie unter [Überblick über WCF-Client](/dotnet/framework/wcf/wcf-client-overview).

## <a name="see-also"></a>Siehe auch

- [Dialogfeld "Vorgang auswählen" (Vorgängerversion)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [Vorgehensweise: implementieren ein WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)
- [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)