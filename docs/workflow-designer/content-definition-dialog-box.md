---
title: Inhalts-Definition (Dialogfeld) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: abbdf64494386b0c5dc61d4cfc1a37940c29f9a8
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="content-definition-dialog-box"></a>Inhaltsdefinition (Dialogfeld)
Die **Inhaltsdefinition** Dialogfeld dient in Windows Workflow-Designer zum Konfigurieren der **Content** Eigenschaften der <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, und <xref:System.ServiceModel.Activities.ReceiveReply> Aktivitäten. Weitere Informationen zu den Aktivitäts-Designer, die diesem Feld verwenden, finden Sie unter der [senden](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), und [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) Themen.

 Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **Korrelation initialisieren** (Dialogfeld).

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Meldung**|Gibt den Nachrichteninhalt mit dem **Nachrichtendaten** Ausdruckstextfeld und den Typ mit der **Nachrichtentyp** Dropdown Listenfeld aus. Wird standardmäßig die **Inhaltsdefinition** verwendet die <xref:System.ServiceModel.Activities.ReceiveMessageContent>, der erwartet, dass eine <xref:System.ServiceModel.Channels.Message> oder einen Nachrichtenvertragstyp innerhalb der workflowdienstdefinition.|
|**Parameter**|Klicken Sie auf die **Parameter** Optionsfeld verwenden <xref:System.ServiceModel.Activities.ReceiveParametersContent>, der einen Datenvertrag erwartet. Legen Sie mithilfe des Datenrasters eine generische Auflistung von <xref:System.Activities.OutArgument>-Schlüssel-Wert-Paaren fest, deren Werte variablen Parametern im aktuellen Workflow zugewiesen werden.|

 Die **Inhaltsdefinition** Dialogfeld wird verwendet, durch die **senden**, **Receive**, **ReceiveAndSendReply**, und  **SendAndReceiveReply** Designer. Auf diese Designer wird auf ähnliche Weise zugegriffen. Zur Veranschaulichung des Verfahrens wird hier der Receive-Fall verwendet.

 Die **Receive** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden. Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt. Wählen Sie die **Receive** Aktivitäts-Designer, und klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben dem (Inhalt) Text für die **Content** Eigenschaft im Eigenschaftenraster für die **Inhaltsdefinition**Dialogfeld angezeigt.

 Der Inhalt kann angegeben werden, in der **Nachricht** im Abschnitt für eine <xref:System.ServiceModel.Activities.ReceiveMessageContent> Aktivität oder innerhalb der **Parameter** im Abschnitt für eine <xref:System.ServiceModel.Activities.ReceiveParametersContent> Aktivität.

## <a name="see-also"></a>Siehe auch

- [Workflow-Designer-Benutzeroberflächenhilfe](../workflow-designer/workflow-designer-ui-help.md)