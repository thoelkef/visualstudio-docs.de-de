---
title: Workflow-Designer - InitializeCorrelation-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
f1_keywords:
- System.ServiceModel.Activities.InitializeCorrelation.UI
ms.assetid: 4c54f34c-ee84-42a6-abb0-ec260c1ccb76
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 693c0304a8204832c3d3f06eb5587d7274d7d260
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53858616"
---
# <a name="initializecorrelation-activity-designer"></a>InitializeCorrelation-Aktivitätsdesigner

Die **InitializeCorrelation** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivität. Die <xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivität richtet eine Korrelation zwischen Nachrichten vor dem Senden oder empfangen werden.

## <a name="the-initializecorrelation-activity"></a>Die InitializeCorrelation-Aktivität

Eine <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität wird verwendet, um Korrelationen zu initialisieren, ohne eine Nachricht zu senden oder zu empfangen. In der Regel wird die Korrelation durch das Senden oder Empfangen einer Nachricht initialisiert. Wenn eine Korrelation festgelegt werden muss, bevor eine Nachricht gesendet oder empfangen wird, verwenden Sie <xref:System.ServiceModel.Activities.InitializeCorrelation>, um die Korrelation zu initialisieren.

### <a name="using-the-initializecorrelation-activity-designer"></a>Verwenden des InitializeCorrelation-Aktivitätsdesigners

Zugriff die **InitializeCorrelation** Aktivitäts-Designer in der **Messaging** Kategorie der **Toolbox**.

Die **InitializeCorrelation** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht. Löschen die Aktivitäts-Designer erstellt eine <xref:System.ServiceModel.Activities.InitializeCorrelation> -Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> -Standardwert InitializeCorrelation. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **InitializeCorrelation** Aktivitäts-Designer oder in der **"DisplayName"** im Feld der **Eigenschaften** Fenster.

Die <xref:System.ServiceModel.Activities.CorrelationHandle> kann gibt an, der **Korrelation** Feld **Eigenschaften** -Fenster auf die **InitializeCorrelation** aktivitätsdesigneroberfläche.

Zum Anzeigen der **Korrelation initialisieren** Dialogfeld, in dem Sie angeben können, das Korrelationshandle und die Schlüssel-Wert-Paare verwendet, um Sie zu initialisieren wählen Sie die Schaltfläche mit den Auslassungspunkten neben, der **CorrelationData** im Feld **Eigenschaften** Fenster. Oder wählen Sie den Hinweistext "View …" auf die **InitializeCorrelation** aktivitätsdesigneroberfläche. Weitere Informationen zur Verwendung dieses Dialogfelds finden Sie unter den [Auflistung-Editor-Dialogfeld](../workflow-designer/type-collection-editor-dialog-box.md) Artikel.

### <a name="the-initializecorrelation-properties"></a>Die InitializeCorrelation-Eigenschaften

Die folgende Tabelle zeigt die <xref:System.ServiceModel.Activities.InitializeCorrelation> Eigenschaften und beschreibt, wie sie im Designer verwendet werden. Diese Eigenschaften können bearbeitet werden, **Eigenschaften** Fenster oder Workflow-Designer-Oberfläche.

|Eigenschaftenname|Erforderlich|Verwendung|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität. Der Standardwert lautet InitializeCorrelation.<br /><br /> Obwohl die Verwendung von einem nicht standardmäßigen Wert für den Anzeigenamen <xref:System.Activities.Activity.DisplayName%2A> ist nicht zwingend erforderlich, es wird empfohlen.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.Correlation%2A>|False|Das <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekt, das verwendet wurde, um Workflowaktivitäten in der Korrelation zuzuordnen.|
|<xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>|False|Ein Wörterbuch von Korrelationsdaten, die Nachrichten mit der Workflowinstanz verknüpft.<br /><br /> Verwenden der **Korrelation initialisieren** Dialogfeld zum Konfigurieren der <xref:System.ServiceModel.Activities.InitializeCorrelation.CorrelationData%2A>. Weitere Informationen zur Verwendung dieses Dialogfelds finden Sie unter den [Auflistung-Editor (Dialogfeld)](../workflow-designer/type-collection-editor-dialog-box.md) Artikel.|

## <a name="see-also"></a>Siehe auch

- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [Receive](../workflow-designer/receive-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)