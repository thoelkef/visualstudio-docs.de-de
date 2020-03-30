---
title: Workflow-Designer - Aktivitäts-Designer senden
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.ServiceModel.Activities.Send.UI
ms.assetid: b514f2e4-767c-4b94-ac61-dd3a54d4b96d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8690d5ccf18c752aacb37a71243d9f591fb9ee30
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395223"
---
# <a name="send-activity-designer"></a>Send-Aktivitätsdesigner

Der Aktivitäts-Designer **Senden** wird <xref:System.ServiceModel.Activities.Send> zum Erstellen und Konfigurieren einer Aktivität verwendet.

## <a name="the-send-activity"></a>Die Send-Aktivität

 Eine <xref:System.ServiceModel.Activities.Send>-Aktivität wird verwendet, um eine Nachricht an einen Dienst zu senden. Eine <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität kann an eine <xref:System.ServiceModel.Activities.Send>-Aktivität gebunden werden, die eine Nachricht als Teil eines Anforderungs-/Antwort-Nachrichtenaustauschmusters auf dem Client empfängt.

### <a name="using-the-send-activity-designer"></a>Verwenden des Send-Aktivitätsdesigners

Greifen Sie auf den **Aktivitäts-Designer Senden** in der Kategorie **Messaging** der **Toolbox**zu. Der Aktivitäts-Designer **senden** kann aus der **Toolbox** gezogen und überall dort, wo Aktivitäten normalerweise platziert werden, auf die Workflow-Designer-Oberfläche abgelegt werden. Daraufhin wird eine <xref:System.ServiceModel.Activities.Send>-Aktivität mit dem <xref:System.Activities.Activity.DisplayName%2A>-Standardwert Send erstellt. Der <xref:System.Activities.Activity.DisplayName%2A> kann in der Kopfzeile des **Aktivitäts-Designers Senden** oder im **Feld DisplayName** des Eigenschaftenrasters bearbeitet werden.

Um eine <xref:System.ServiceModel.Activities.ReceiveReply> Aktivität zu erstellen <xref:System.ServiceModel.Activities.Send> und an die ausgewählte Aktivität zu binden, klicken Sie mit der rechten Maustaste auf den Aktivitäts-Designer **Senden,** klicken Sie im Kontextmenü auf das Element **ReceiveReply erstellen,** und der **ReceiveReplyForSend-Designer** wird unter dem **Sende-Designer** angezeigt. Die <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität ist eine Aktivität, die eine Nachricht als Teil eines Anforderungs-/Antwort-Nachrichtenaustauschmusters auf dem Client empfängt. Sie kann mit dem **ReceiveReplyForSend-Designer** konfiguriert werden.

Alternativ kann der **SendAndReceiveReply-Vorlagen-Designer** in der **Messaging-Kategorie** der **Toolbox** verwendet <xref:System.ServiceModel.Activities.Send> werden, um ein Paar vorkonfigurierter und <xref:System.ServiceModel.Activities.ReceiveReply> Aktivitäten zu erstellen. Weitere Informationen zur Verwendung der **Vorlagen SendAndReceiveReply** und **ReceiveReplyForSend** finden Sie im Thema [SendAndReceiveReply.](../workflow-designer/sendandreceivereply-template-designer.md)

### <a name="the-send-activity-properties"></a>Die Eigenschaften der Send-Aktivität

In der folgenden Tabelle werden die <xref:System.ServiceModel.Activities.Send>-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden. Diese Eigenschaften können im Eigenschaftenraster oder auf der Workflow-Designer-Oberfläche bearbeitet werden.

| Eigenschaftenname | Erforderlich | Verwendung |
|-|----------|-|
| <xref:System.Activities.Activity.DisplayName%2A> | False | Der Anzeigename der <xref:System.ServiceModel.Activities.Send>-Aktivität. Der Standardwert lautet Send. Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden. |
| <xref:System.ServiceModel.Activities.Send.OperationName%2A> | True | Der Name des Dienstvorgangs, der von dieser <xref:System.ServiceModel.Activities.Send>-Aktivität aufgerufen wurde. Diese Eigenschaft wird verwendet, um den Standardwert für die **Action-Eigenschaft** zu erstellen, wenn die **Action-Eigenschaft** nicht explizit festgelegt ist. |
| <xref:System.ServiceModel.Activities.Send.ServiceContractName%2A> | True | Der Name des Dienstvertrags, der von dem aufzurufenden Dienst implementiert wird. |
| <xref:System.ServiceModel.Activities.Send.Content%2A> | False | Gibt die zu empfangende Nachricht oder den zu empfangenden Parameterinhalt an. Dies kann entweder eine <xref:System.ServiceModel.Activities.ReceiveMessageContent>-Aktivität oder eine <xref:System.ServiceModel.Activities.ReceiveParametersContent>-Aktivität sein. Bearbeiten Sie diese Eigenschaft, indem Sie die Schaltfläche "Auslassung" neben dem Feld **Inhalt** im Eigenschaftenraster auswählen oder auf die Schaltfläche **Definieren...** neben der **Inhaltsbeschriftung** auf der Designeroberfläche **"Aktivität empfangen"** klicken. Beide zeigen das Dialogfeld **Inhaltsdefinition** an. Weitere Informationen zur Verwendung dieses Felds finden Sie im Thema [Dialogfeld Inhaltsdefinition.](../workflow-designer/content-definition-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> | False | Gibt den <xref:System.ServiceModel.Activities.CorrelationHandle> an, der verwendet wurde, um die Nachricht an die entsprechende Workflowinstanz weiterzuleiten.<br /><br /> Klicken Sie auf die Schaltfläche <xref:System.ServiceModel.Activities.Send.CorrelatesWith%2A> Auslassung neben der Eigenschaft im Eigenschaftenraster, um das Dialogfeld **Ausdrucks-Editor** zu öffnen. Weitere Informationen zur Verwendung dieses Dialogfelds finden Sie im Thema [Gewusst wie: Verwenden des Ausdrucks-Editors.](../workflow-designer/how-to-use-the-expression-editor.md) |
| <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> | False | Gibt die Auflistung von <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekten an, die mehrere <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekte initialisiert, die diese <xref:System.ServiceModel.Activities.Send>-Aktivität im Workflow konfigurieren. Klicken Sie auf die Schaltfläche <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> Auslassung neben der Eigenschaft im Eigenschaftenraster, um das Dialogfeld **Korrelationsinitialisierer hinzufügen** zu öffnen. Weitere Informationen zur Verwendung dieses Felds finden Sie im Thema [Dialogfeld "Korrelationinitialisierer hinzufügen".](../workflow-designer/add-correlationinitializers-dialog-box.md) |
| <xref:System.ServiceModel.Activities.Send.KnownTypes%2A> | False | Eine Auflistung bekannter Typen für den von dieser <xref:System.ServiceModel.Activities.Send>-Aktivität aufzurufenden Dienstvorgang. Diese Eigenschaft muss in Verbindung mit der <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>-Eigenschaft verwendet werden, die auf <xref:System.Runtime.Serialization.DataContractSerializer> festgelegt wurde. Sie wird ignoriert, wenn der <xref:System.Xml.Serialization.XmlSerializer> verwendet wird.<br /><br /> Wählen Sie die Schaltfläche Auslassung neben dem Feld **KnownTypes** im Eigenschaftenraster aus, um das Dialogfeld **Typsammlungs-Editor** anzuzeigen, mit dem Sie relevante Typen hinzufügen können.<br /><br /> Wählen Sie die Schaltfläche Auslassungneben eignern Sie das Feld **KnownTypes** im Eigenschaftenraster aus, um das Dialogfeld **Typsammlungs-Editor** anzuzeigen, mit dem Sie relevante Typen hinzufügen können. Weitere Informationen zur Verwendung dieses Felds finden Sie im [Dialogfeld Typsammlungs-Editor.For](../workflow-designer/type-collection-editor-dialog-box.md) more information about using this box, see the Type Collection Editor Dialog Box topic. |
| <xref:System.ServiceModel.Activities.Send.ProtectionLevel%2A> | True | Gibt die <xref:System.Net.Security.ProtectionLevel>-Einstellung für die Nachricht an.<br /><br /> 1. <xref:System.Net.Security.ProtectionLevel> bedeutet nur Authentifizierung.<br />2. <xref:System.Net.Security.ProtectionLevel> Zeichendaten, um die Integrität der übertragenen Daten zu gewährleisten.<br />3. <xref:System.Net.Security.ProtectionLevel> Daten zu verschlüsseln und zu signieren, um die Vertraulichkeit und Integrität der übertragenen Daten zu gewährleisten. |
| <xref:System.ServiceModel.Activities.Send.SerializerOption%2A> | True | Das Serialisierungsprogramm, das für den Dienstvorgang verwendet werden soll, der von der <xref:System.ServiceModel.Activities.Send>-Aktivität aufgerufen werden soll. Der Standardwert lautet <xref:System.Runtime.Serialization.DataContractSerializer>, der unter Verwendung eines angegebenen Datenvertrags eine Instanz eines Typs in einen XML-Datenstrom oder ein Dokument serialisiert und daraus deserialisiert. |
| <xref:System.ServiceModel.Activities.Send.Action%2A> | False | Gibt den Aktionsheader der Nachricht an. Wenn er nicht explizit festgelegt ist, `https://tempuri.org/{service contract namespace}/{service contract name}/{operation name}`wird der Wert standardmäßig auf: gesetzt. Bei Festlegung für eine <xref:System.ServiceModel.Activities.Send>-Aktivität muss die <xref:System.ServiceModel.Activities.Receive>-Aktivität, die die Nachricht empfängt, über den gleichen Wert verfügen, damit die Nachricht ordnungsgemäß übermittelt werden kann. |
| <xref:System.ServiceModel.Activities.Send.TokenImpersonationLevel%2A> | | Die für den Empfänger der Nachricht zulässige <xref:System.Security.Principal.TokenImpersonationLevel>-Instanz. Es definiert Sicherheitsidentitätswechselebenen, die den Grad bestimmen, in dem ein Serverprozess im Namen eines Clientprozesses handeln kann.<xref:System.Security.Principal.TokenImpersonationLevel>  gibt an, dass keine Identitätswechselebene zugeordnet ist. <xref:System.Security.Principal.TokenImpersonationLevel>gibt an, dass der Serverprozess keine Identifikationsinformationen über den Client abrufen und die Identität des Clients nicht haben kann. <xref:System.Security.Principal.TokenImpersonationLevel>gibt an, dass der Serverprozess Informationen über den Client abrufen kann, z. B. Sicherheitskennungen und -berechtigungen, aber nicht die Identität des Clients. Dies ist nützlich für Server, die eigene Objekte exportieren (z. B. Datenbankprodukte, von denen Tabellen und Ansichten exportiert werden). Mit den abgerufenen Informationen zur Clientsicherheit können vom Server Entscheidungen im Rahmen der Zugriffsvalidierung getroffen werden, ohne dass andere Dienste verwendet werden können, die den Sicherheitskontext des Clients verwenden. <xref:System.Security.Principal.TokenImpersonationLevel>gibt an, dass der Serverprozess die Identität des Sicherheitskontexts des Clients auf seinem lokalen System haben kann. Der Server kann den Client auf Remotesystemen nicht imitieren. <xref:System.Security.Principal.TokenImpersonationLevel>gibt an, dass der Serverprozess die Identität des Sicherheitskontexts des Clients auf Remotesystemen haben kann. |
| <xref:System.ServiceModel.Activities.Send.Endpoint%2A> | | Das <xref:System.ServiceModel.Endpoint>-Objekt, an das die <xref:System.ServiceModel.Activities.Send>-Aktivität eine Nachricht sendet. Wenn diese Eigenschaft <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> festgelegt ist, sollte die Eigenschaft **null**sein. |
| <xref:System.ServiceModel.Activities.Send.EndpointAddress%2A> | | Das <xref:System.ServiceModel.EndpointAddress>-Objekt, an das die Meldung gesendet wird. |
| <xref:System.ServiceModel.Activities.Send.EndpointConfigurationName%2A> | | Der Name der Endpunktkonfiguration. Diese Eigenschaft wird beim Konfigurieren eines Endpunkts in einer Konfigurationsdatei festgelegt. Diese Eigenschaft sollte auf den Namen ** \<** festgelegt werden, der im Endpunkt>-Element in der Konfigurationsdatei angegeben ist. Wenn diese Eigenschaft festgelegt <xref:System.ServiceModel.Activities.Send.Endpoint%2A> ist, sollte die Eigenschaft **null**sein. |

## <a name="see-also"></a>Siehe auch

- [InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)
- [CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)
- [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)
- [Empfangen](../workflow-designer/receive-activity-designer.md)
- [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)
- [TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)