---
title: Inhalts Definition (Dialog Feld) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d989f5a0c57e381041e8fe9c200aae1a76316ad8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656957"
---
# <a name="content-definition-dialog-box"></a>Inhaltsdefinition (Dialogfeld)
Das Dialogfeld **Inhalts Definition** wird in [!INCLUDE[wfd1](../includes/wfd1-md.md)] verwendet, um die **Inhalts** Eigenschaften der Aktivitäten <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> und <xref:System.ServiceModel.Activities.ReceiveReply> zu konfigurieren. [!INCLUDE[crabout](../includes/crabout-md.md)] den Aktivitäts Designern, die dieses Feld verwenden, finden [Sie](../workflow-designer/send-activity-designer.md)in den Themen Send, [Receive](../workflow-designer/receive-activity-designer.md), [receiveandsendreply](../workflow-designer/receiveandsendreply-template-designer.md)und [sendandreceivereply](../workflow-designer/sendandreceivereply-template-designer.md) .

 In der folgenden Tabelle werden die Benutzeroberflächen Elemente des Dialog Felds **Korrelation initialisieren** beschrieben.

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Meldung**|Gibt den Nachrichten Inhalt mit dem Textfeld für den **Nachrichten Daten** Ausdruck und den Typ im Dropdown-Listenfeld **Nachrichtentyp** an. Standardmäßig verwendet die **Inhalts Definition** das <xref:System.ServiceModel.Activities.ReceiveMessageContent>, das eine <xref:System.ServiceModel.Channels.Message> oder einen Nachrichten Vertragstyp in der Workflow Dienst Definition erwartet.|
|**Parameter**|Klicken Sie auf das Optionsfeld **Parameter** , um <xref:System.ServiceModel.Activities.ReceiveParametersContent> zu verwenden, das einen Datenvertrag erwartet. Legen Sie mithilfe des Datenrasters eine generische Auflistung von <xref:System.Activities.OutArgument>-Schlüssel-Wert-Paaren fest, deren Werte variablen Parametern im aktuellen Workflow zugewiesen werden.|

 Das Dialogfeld **Inhalts Definition** wird von den Designern **Send**, **Receive**, **receiveandsendreply**und **sendandreceivereply** verwendet. Auf diese Designer wird auf ähnliche Weise zugegriffen. Zur Veranschaulichung des Verfahrens wird hier der Receive-Fall verwendet.

 Der **Receive** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden. Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt. Wählen Sie den **Receive** -Aktivitäts Designer aus, und klicken Sie im Eigenschaften Raster auf die Schaltfläche mit den Auslassungs Zeichen, **damit das Dialog** Feld **Inhalts Definition** angezeigt wird.

 Der Inhalt kann im **Nachrichten** Abschnitt für eine <xref:System.ServiceModel.Activities.ReceiveMessageContent> Aktivität oder innerhalb des **Parameter** Abschnitts für eine <xref:System.ServiceModel.Activities.ReceiveParametersContent> Aktivität angegeben werden.

## <a name="see-also"></a>Siehe auch
 [Workflow-Designer-Benutzeroberflächenhilfe](../workflow-designer/workflow-designer-ui-help.md)