---
title: Workflow-Designer - Inhaltsdefinition (Dialogfeld)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cc434e35755b04054d1e24da97e8a4699af7df0e
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2018
ms.locfileid: "36757950"
---
# <a name="content-definition-dialog-box"></a>Inhaltsdefinition (Dialogfeld)

Die **Inhaltsdefinition** Dialogfeld wird im Workflow-Designer verwendet, so konfigurieren Sie die **Content** Eigenschaften der <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, und <xref:System.ServiceModel.Activities.ReceiveReply> Aktivitäten. Weitere Informationen zu den Aktivitätsdesignern, die dieses Feld verwenden, finden Sie unter den [senden](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), und [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) Themen.

Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **Korrelation initialisieren** Dialogfeld:

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Meldung**|Gibt an, den Nachrichteninhalt mit dem **Message Data** Ausdruckstextfeld und den Typ mit der **Nachrichtentyp** im Dropdown Listenfeld. Standardmäßig die **Inhaltsdefinition** verwendet die <xref:System.ServiceModel.Activities.ReceiveMessageContent>, der erwartet, dass eine <xref:System.ServiceModel.Channels.Message> oder einen Nachrichtenvertragstyp innerhalb der workflowdienstdefinition.|
|**Parameter**|Klicken Sie auf die **Parameter** Optionsfeld mit <xref:System.ServiceModel.Activities.ReceiveParametersContent>, der einen Datenvertrag erwartet. Legen Sie mithilfe des Datenrasters eine generische Auflistung von <xref:System.Activities.OutArgument>-Schlüssel-Wert-Paaren fest, deren Werte variablen Parametern im aktuellen Workflow zugewiesen werden.|

Die **Inhaltsdefinition** Dialogfeld wird verwendet, durch die **senden**, **Receive**, **ReceiveAndSendReply**, und  **SendAndReceiveReply** Designer. Auf diese Designer wird auf ähnliche Weise zugegriffen. Zur Veranschaulichung des Verfahrens wird hier der Receive-Fall verwendet.

Die **Receive** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht werden, wo Aktivitäten normalerweise platziert werden. Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt. Wählen Sie die **Receive** Aktivitäts-Designer, und klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben dem (Inhalt) Text für die **Inhalt** Eigenschaft im Eigenschaftenraster für das **Inhaltsdefinition**Dialogfeld angezeigt.

Der Inhalt kann angegeben werden, in der **Nachricht** im Abschnitt für eine <xref:System.ServiceModel.Activities.ReceiveMessageContent> Aktivität oder innerhalb der **Parameter** im Abschnitt für eine <xref:System.ServiceModel.Activities.ReceiveParametersContent> Aktivität.

## <a name="see-also"></a>Siehe auch

- [Workflow-Designer-Benutzeroberflächenhilfe](../workflow-designer/workflow-designer-ui-help.md)