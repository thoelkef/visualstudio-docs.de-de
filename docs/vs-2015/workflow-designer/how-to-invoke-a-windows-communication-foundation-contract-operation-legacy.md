---
title: 'Vorgehensweise: Aufrufen eines Windows Communication Foundation Vertrags Vorgangs (Legacy) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: a9058345-708f-4fcf-8739-2a43e5285b7a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6f42600a739561a27a6dd8f6caa237027bac4554
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603706"
---
# <a name="how-to-invoke-a-windows-communication-foundation-contract-operation-legacy"></a>Vorgehensweise: Aufrufen eines Windows Communication Foundation-Vertragsvorgangs (Vorgängerversion)
In diesem Thema wird der Aufruf eines [!INCLUDE[indigo1](../includes/indigo1-md.md)]-Vertragsvorgangs mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] beschrieben, die auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielt.

 Nach dem Ziehen einer **SendActivity** -Aktivität aus der Toolbox auf die Workflow Entwurfs Oberfläche müssen Sie einen vorhandenen Vertrag importieren und ermitteln, welcher Vorgang von der **SendActivity** -Aktivität aufgerufen wird. Sie wählen den Vertrag und seine Vorgänge im [Dialog Feld "Vorgang auswählen" (](../workflow-designer/choose-operation-dialog-box-legacy.md)Vorgängerversion) aus.

 Beim Verwenden einer Konfigurationsdatei mit dem Dienst müssen Sie auch ein <xref:System.Workflow.Activities.ChannelToken> angeben. Das <xref:System.Workflow.Activities.ChannelToken> identifiziert die Endpunktkonfiguration, die die Sendeaktivität für die Verbindung zum Workflowdienst verwendet.

### <a name="to-invoke-a-wcf-contract-operation-from-a-sendactivity-activity"></a>So rufen Sie einen WCF-Vertragsvorgang aus einer SendActivity-Aktivität auf

1. Doppelklicken Sie im Designer auf die **SendActivity** -Aktivität, oder klicken Sie auf die Auslassungs Punkte neben der **ServiceOperationInfo** -Eigenschaft im Bereich **Eigenschaften** .

2. Wenn das Dialogfeld **Vorgang auswählen** geöffnet wird, klicken Sie rechts oben im Dialogfeld auf **importieren** .

     Das [Dialog Feld .NET-Typ suchen und auswählen (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) wird geöffnet.

3. Suchen Sie eine Assembly oder ein Projekt, das den gewünschten Vertrag enthält.

4. Wählen Sie den Vertrag aus, und klicken Sie auf **OK**.

5. Wählen Sie unter **Verfügbare Vorgänge**den Vorgang aus, den Sie aufrufen möchten, und klicken Sie auf **OK**.

### <a name="to-specify-a-channel-token"></a>So geben Sie ein Kanaltoken an

1. Wählen Sie die <xref:System.Workflow.Activities.SendActivity>-Aktivität im Designer aus.

2. Geben Sie im Bereich **Eigenschaften** einen Namen für das an <xref:System.Workflow.Activities.ChannelToken> . Dieser Name identifiziert das Kanaltoken eindeutig.

3. Erweitern Sie den Kanaltokenknoten, und geben Sie einen Namen für den Clientendpunkt an, den Sie im <xref:System.Workflow.Activities.ChannelToken.EndpointName%2A>-Feld verwenden. Die Endpunktkonfiguration mit dem gleichen Namen in der Konfigurationsdatei wird zum Konfigurieren des Kanals verwendet.

4. Erstellen Sie die Endpunktkonfiguration in der Konfigurationsdatei, wenn noch nicht vorhanden. Weitere Informationen zum Konfigurieren des Clients finden Sie unter [Übersicht](https://msdn.microsoft.com/library/f60d9bc5-8ade-4471-8ecf-5a07a936c82d)über den WCF-Client.

## <a name="see-also"></a>Weitere Informationen
 [Dialog Feld "Vorgang auswählen" (Legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md) Gewusst [wie: Implementieren einer WCF-Vertrags Operation (Legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) [Legacy Workflow Aktivitäten](../workflow-designer/legacy-workflow-activities.md)