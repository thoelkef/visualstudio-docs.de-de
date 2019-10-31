---
title: Dialog Feld "Workflow-Designer-Inhalts Definition"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MessageContent.UI
ms.assetid: 7e4237c3-90a1-4149-bd8a-3643d1dde0df
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4925d6f6321cd039daca469844ebac6627b08f81
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189791"
---
# <a name="content-definition-dialog-box"></a>Inhaltsdefinition (Dialogfeld)

Das Dialogfeld **Inhalts Definition** wird in Workflow-Designer verwendet, um die **Inhalts** Eigenschaften der Aktivitäten <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> und <xref:System.ServiceModel.Activities.ReceiveReply> zu konfigurieren. Weitere Informationen zu den Aktivitäts Designern, die dieses Feld verwenden, finden Sie in den Themen [Send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [receiveandsendreply](../workflow-designer/receiveandsendreply-template-designer.md)und [sendandreceivereply](../workflow-designer/sendandreceivereply-template-designer.md) .

In der folgenden Tabelle werden die Benutzeroberflächen Elemente des Dialog Felds " **Korrelation initialisieren** " beschrieben:

|Benutzeroberflächenelement|Beschreibung|
|-|-----------------|
|**Meldung**|Gibt den Nachrichten Inhalt mit dem Textfeld für den **Nachrichten Daten** Ausdruck und den Typ im Dropdown-Listenfeld **Nachrichtentyp** an. Standardmäßig verwendet die **Inhalts Definition** das <xref:System.ServiceModel.Activities.ReceiveMessageContent>, das eine <xref:System.ServiceModel.Channels.Message> oder einen Nachrichten Vertragstyp in der Workflow Dienst Definition erwartet.|
|**Parameter**|Klicken Sie auf das Optionsfeld **Parameter** , um <xref:System.ServiceModel.Activities.ReceiveParametersContent> zu verwenden, das einen Datenvertrag erwartet. Legen Sie mithilfe des Datenrasters eine generische Auflistung von <xref:System.Activities.OutArgument>-Schlüssel-Wert-Paaren fest, deren Werte variablen Parametern im aktuellen Workflow zugewiesen werden.|

Das Dialogfeld **Inhalts Definition** wird von den Designern **Send**, **Receive**, **receiveandsendreply**und **sendandreceivereply** verwendet. Auf diese Designer wird auf ähnliche Weise zugegriffen. Zur Veranschaulichung des Verfahrens wird hier der Receive-Fall verwendet.

Der **Receive** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden. Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt. Wählen Sie den **Receive** -Aktivitäts Designer aus, und klicken Sie im Eigenschaften Raster auf die Schaltfläche mit den Auslassungs Zeichen, **damit das Dialog** Feld **Inhalts Definition** angezeigt wird.

Der Inhalt kann im **Nachrichten** Abschnitt für eine <xref:System.ServiceModel.Activities.ReceiveMessageContent> Aktivität oder innerhalb des **Parameter** Abschnitts für eine <xref:System.ServiceModel.Activities.ReceiveParametersContent> Aktivität angegeben werden.

## <a name="see-also"></a>Siehe auch

- [Workflow-Designer-Benutzeroberflächenhilfe](browse-and-select-a-dotnet-type-dialog-box.md)