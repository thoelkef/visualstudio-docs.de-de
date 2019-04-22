---
title: Workflow-Designer - Receive-Aktivitätsdesigner
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Receive.UI
ms.assetid: f58d3c70-944d-4bb4-90a7-e68c103caddc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bcab59a631b1dbf9c85c7bff2454a42e97accff8
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/17/2019
ms.locfileid: "59649214"
---
# <a name="receive-activity-designer"></a>Receive-Aktivitätsdesigner

Die **Receive** Aktivitäts-Designer dient zum Erstellen und Konfigurieren einer <xref:System.ServiceModel.Activities.Receive> Aktivität. Eine <xref:System.ServiceModel.Activities.Receive>-Aktivität ist eine Aktivität, die eine Nachricht empfängt, die entweder ein integrierter Datentyp, etwa ein <xref:System.ServiceModel.Channels.Message>-, <xref:System.IO.Stream>- oder ein <xref:System.Xml.Linq.XElement>-Typ sein kann oder ein anwendungsdefinierter Datenvertrag, ein Nachrichtenvertrag oder eine XML-Klasse, die serialisiert werden kann.

## <a name="the-receive-activity"></a>Die Receive-Aktivität

Die <xref:System.ServiceModel.Activities.Receive>-Aktivität kann abhängig vom Typ des verwendeten Empfangsinhalts ein einzelnes Element oder mehrere Elemente empfangen. Eine <xref:System.ServiceModel.Activities.SendReply>-Aktivität kann an eine <xref:System.ServiceModel.Activities.Receive>-Aktivität gebunden werden, die eine Nachricht als Teil eines Anforderungs-/Antwort-Nachrichtenaustauschmusters des Dienstes empfängt.

### <a name="using-the-receive-activity-designer"></a>Verwenden des Receive-Aktivitätsdesigners

Zugriff die **Receive** Aktivitäts-Designer in der **Messaging** Kategorie der **Toolbox**. Die **Receive** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht werden, wo Aktivitäten normalerweise platziert werden. Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt. Die <xref:System.Activities.Activity.DisplayName%2A> kann im Header des bearbeitet werden die **Receive** Aktivitäts-Designer oder in der **"DisplayName"** Feld des Eigenschaftenrasters.

Zum Erstellen einer <xref:System.ServiceModel.Activities.SendReply> Aktivität und ihn mit dem ausgewählten <xref:System.ServiceModel.Activities.Receive> -Aktivität, mit der rechten Maustaste die **empfangen** Aktivität Designer, klicken Sie auf die **SendReply erstellen** Element im Kontextmenü und die **SendReplyToReceive** -Designer angezeigt wird, unter dem **Receive** Designer. Die <xref:System.ServiceModel.Activities.SendReply>-Aktivität ist eine Aktivität, die die Antwortnachricht als Teil eines Anforderungs-/Antwort-Nachrichtenaustauschmusters des Dienstes sendet. Sie können konfiguriert werden, mit der **SendReplyToReceive** Designer.

Alternativ die **ReceiveAndSendReply** -Vorlagendesigner in der **Messaging** Kategorie der **Toolbox** können verwendet werden, um ein paar vorkonfigurierter <xref:System.ServiceModel.Activities.Receive>und <xref:System.ServiceModel.Activities.SendReply> Aktivität. Weitere Informationen über die Verwendung der **ReceiveAndSendReply** und **SendReplyToReceive** Vorlage finden Sie unter der [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) Thema.

### <a name="the-receive-activity-properties"></a>Die Receive-Aktivitätseigenschaften

In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.Receive>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Oberfläche des Workflow-Designer bearbeitet werden. Die einzige erforderliche Eigenschaft ist die <xref:System.ServiceModel.Activities.Receive.OperationName%2A>-Eigenschaft.

| Eigenschaftenname | Erforderlich | Verwendung |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Gibt den benutzerfreundlichen Namen der <xref:System.ServiceModel.Activities.Receive>-Aktivität an. Der Standardwert lautet Receive.<br /><br /> Obwohl die Verwendung eines nicht standardmäßigen Werts für den benutzerfreundlichen <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen solchen Wert zu verwenden. |
| <xref:System.ServiceModel.Activities.Receive.OperationName%2A> | True | Gibt den Namen des von dieser <xref:System.ServiceModel.Activities.Receive>-Aktivität implementierten Dienstvorgangs an. Diese Eigenschaft wird verwendet, um den Standardwert für die **Aktion** Eigenschaft Wenn die **Aktion** -Eigenschaft nicht explizit festgelegt. |
| <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> | False | Gibt den Namen des Dienstvertrags an. Diese Eigenschaft wird verwendet, um Dienstvorgänge in einzelne Dienstverträge zu gruppieren. Alle <xref:System.ServiceModel.Activities.Receive>-Aktivitäten, die über den gleichen <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A> verfügen, werden in den gleichen Dienstvertrag (WSDL-Anschlusstyp) gruppiert. Der Standardwert ist der vollqualifizierte CLR-Name der Aktivität der obersten Ebene (Stamm). |
| <xref:System.ServiceModel.Activities.Receive.Content%2A> | False | Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Bearbeiten Sie diese Eigenschaft durch Auswählen der Schaltfläche mit den Auslassungspunkten neben der **Content** Feld im Eigenschaftenraster oder indem Sie auf die **definieren...**  neben der **Content** Bezeichnung auf die **Receive** aktivitätsdesigneroberfläche. Anzeigen der **Inhaltsdefinition** Dialogfeld. Weitere Informationen dazu, wie Sie dieses Feld verwenden, finden Sie unter den [Content Definition (Dialogfeld)](../workflow-designer/content-definition-dialog-box.md) Thema. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> | False | Gibt die Korrelationen zwischen <xref:System.ServiceModel.Activities.Receive>-Aktivitäten in Dienstvorgängen eines Workflows mit einem <xref:System.ServiceModel.MessageQuerySet>-Objekt an. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> Eigenschaft im Eigenschaftenraster, öffnen Sie die **CorrelatesOn-Definition** im Dialogfeld. Weitere Informationen zur Verwendung dieses Dialogfelds finden Sie unter den [Content Definition (Dialogfeld)](../workflow-designer/content-definition-dialog-box.md) Thema. |
| <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> | False | Gibt den <xref:System.ServiceModel.Activities.CorrelationHandle> an, der verwendet wurde, um die Nachricht an die entsprechende Workflowinstanz weiterzuleiten.<br /><br /> Klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der <xref:System.ServiceModel.Activities.Receive.CorrelatesWith%2A> Eigenschaft im Eigenschaftenraster, öffnen Sie die **Ausdrucks-Editor** im Dialogfeld. Weitere Informationen zur Verwendung dieses Dialogfelds finden Sie unter den [Vorgehensweise: Verwenden Sie den Ausdrucks-Editor](../workflow-designer/how-to-use-the-expression-editor.md) Thema. |
| <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> | False | Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Receive>-Aktivität im Workflow konfigurieren. Klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben der <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> Eigenschaft im Eigenschaftenraster, öffnen Sie die **Korrelationsinitialisierer hinzufügen** im Dialogfeld. Weitere Informationen zur Verwendung dieses Dialogfelds finden Sie unter den [CorrelationInitializers-Dialogfeld hinzufügen](../workflow-designer/add-correlationinitializers-dialog-box.md) Thema. |
| <xref:System.ServiceModel.Activities.Receive.CanCreateInstance%2A> | False | Gibt einen Wert an, der bestimmt, ob eine neue Workflowinstanz zur Verarbeitung der Nachricht erstellt wird, wenn die Nachricht keiner vorhandenen Workflowinstanz entspricht. Wenn der Wert, um festgelegt ist **"true"**, eine neue Workflowinstanz wird erstellt, um die Nachricht zu verarbeiten, wenn die Nachricht mit einer vorhandenen Workflowinstanz nicht korreliert werden. |
| <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> | False | Gibt eine Auflistung bekannter Typen für den von dieser <xref:System.ServiceModel.Activities.Receive>-Aktivität implementierten Dienstvorgang an. Diese Eigenschaft muss in Verbindung mit der <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>-Eigenschaft verwendet werden, die auf <xref:System.Runtime.Serialization.DataContractSerializer> festgelegt wurde. Sie wird ignoriert, wenn der <xref:System.Xml.Serialization.XmlSerializer> verwendet wird.<br /><br /> Wählen Sie die Schaltfläche mit den Auslassungspunkten neben der **KnownTypes** Feld im Eigenschaftenraster zum Anzeigen der **Typauflistungs-Editor** Dialogfeld, in dem Sie relevante Typen hinzufügen können. Weitere Informationen zur Verwendung dieses Dialogfelds finden Sie unter den [Auflistung-Editor-Dialogfeld](../workflow-designer/type-collection-editor-dialog-box.md) Thema. |
| <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> | False | Gibt die <xref:System.Net.Security.ProtectionLevel>-Einstellung für die Nachricht an.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> bedeutet, dass nur die Authentifizierung.<br />2. <xref:System.Net.Security.ProtectionLevel> bedeutet, dass signiert Daten, die Integrität übertragener Daten sicherzustellen.<br />3. <xref:System.Net.Security.ProtectionLevel> bedeutet, dass Daten verschlüsselt und signiert, um die Vertraulichkeit und Integrität übertragener Daten sicherzustellen. |
| <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A> | False | Gibt den Typ des Serialisierungsprogramms an, das für den von der <xref:System.ServiceModel.Activities.Receive>-Aktivität implementierten Dienstvorgang verwendet werden soll. Der Standardwert ist <xref:System.Runtime.Serialization.DataContractSerializer>, der eine Instanz eines Typs, der einen angegebenen Datenvertrag verwendet, in einen XML-Datenstrom oder ein Dokument serialisiert und deserialisiert. Der <xref:System.Xml.Serialization.XmlSerializer> kann auch verwendet werden, wenn eine genauere Kontrolle des XML-Codes erforderlich ist. |
| <xref:System.ServiceModel.Activities.Receive.Action%2A> | False | Gibt den Aktionsheader der Nachricht an. Wenn sie nicht explizit festgelegt wird, sein Standardwert: `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`. |

## <a name="see-also"></a>Siehe auch

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Send](../workflow-designer/send-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)
