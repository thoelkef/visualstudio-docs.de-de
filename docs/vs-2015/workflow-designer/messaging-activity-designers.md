---
title: Messaging-Aktivitäts Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 897e63cf-a42f-4edd-876f-c4ccfffaf6d6
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a6fb06bea4cebf2558990d23f7ece5b4f8db5b95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658936"
---
# <a name="messaging-activity-designers"></a>Messaging-Aktivitätsdesigner
Messaging-Aktivitätsdesigner werden verwendet, um Messaging-Aktivitäten zu erstellen und zu konfigurieren, die [!INCLUDE[indigo1](../includes/indigo1-md.md)]-Nachrichten in einer [!INCLUDE[wf](../includes/wf-md.md)]-Anwendung senden und empfangen. Der [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] führt fünf Messaging-Aktivitäten ein, und der [!INCLUDE[wfd1](../includes/wfd1-md.md)] stellt zwei neue Vorlagen-Designer bereit, die Ihnen ermöglichen, das Messaging innerhalb eines Workflows zu verwalten. Die Themen, die in diesem Abschnitt enthalten und in der folgenden Tabelle aufgeführt sind, enthalten Anleitungen dazu, wie die [!INCLUDE[wfd2](../includes/wfd2-md.md)]-Aktivitäts- und Vorlagen-Designer verwendet werden.

## <a name="in-this-section"></a>In diesem Abschnitt

|Messagingaktivität|BESCHREIBUNG|
|----------------------|-----------------|
|[CorrelationScope](../workflow-designer/correlationscope-activity-designer.md)|Erstellt und konfiguriert eine <xref:System.ServiceModel.Activities.CorrelationScope>-Aktivität, die die implizite Verwaltung von untergeordneten Messagingaktivitäten mit einem <xref:System.ServiceModel.Activities.CorrelationHandle>-Objekt bereitstellt.|
|[InitializeCorrelation](../workflow-designer/initializecorrelation-activity-designer.md)|Erstellt und konfiguriert eine <xref:System.ServiceModel.Activities.InitializeCorrelation>-Aktivität, die verwendet wird, um eine Korrelation zu initialisieren, ohne eine Nachricht zu senden oder zu empfangen.|
|[Medizinisch](../workflow-designer/receive-activity-designer.md)|Erstellt und konfiguriert eine <xref:System.ServiceModel.Activities.Receive>-Aktivität, die eine Nachricht von einem Dienst empfängt.|
|[ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md)|Erstellt innerhalb einer <xref:System.ServiceModel.Activities.Send>-Aktivität ein vorkonfiguriertes Paar von <xref:System.ServiceModel.Activities.ReceiveReply>-Aktivität und <xref:System.Activities.Statements.Sequence>-Aktivität.|
|[Senden](../workflow-designer/send-activity-designer.md)|Erstellt und konfiguriert eine <xref:System.ServiceModel.Activities.Send>-Aktivität, die eine Nachricht an einen Dienst sendet.|
|[SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md)|Erstellt innerhalb einer <xref:System.ServiceModel.Activities.Receive>-Aktivität ein vorkonfiguriertes Paar von <xref:System.ServiceModel.Activities.SendReply>-Aktivität und <xref:System.Activities.Statements.Sequence>-Aktivität.|
|[TransactedReceiveScope](../workflow-designer/transactedreceivescope-activity-designer.md)|Erstellt und konfiguriert eine <xref:System.ServiceModel.Activities.TransactedReceiveScope>-Aktivität, welche den Transaktionsfluss in einen Workflow ermöglicht.|

## <a name="reference"></a>Referenz
 <xref:System.Activities.Activity>

 <xref:System.ServiceModel.Activities.CorrelationScope>

 <xref:System.ServiceModel.Activities.Receive>

 <xref:System.ServiceModel.Activities.Send>

 <xref:System.ServiceModel.Activities.ReceiveReply>

 <xref:System.ServiceModel.Activities.SendReply>

 <xref:System.ServiceModel.Activities.TransactedReceiveScope>

## <a name="related-sections"></a>Verwandte Abschnitte
 Andere Typen von Aktivitätsdesignern werden in den folgenden Themen behandelt.

 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)

 [Verwenden der Aktivitätsdesigner](../workflow-designer/using-the-activity-designers.md)

 [Flussdiagramm](../workflow-designer/flowchart-activity-designers.md)

 [Laufzeit](../workflow-designer/runtime-activity-designers.md)

 [Grundtypen](../workflow-designer/primitives-activity-designers.md)

 [Transaktion](../workflow-designer/transaction-activity-designers.md)

 [Sammlung](../workflow-designer/collection-activity-designers.md)

 [Fehlerbehandlung](../workflow-designer/error-handling-activity-designers.md)

## <a name="external-resources"></a>Externe Ressourcen
 [Verwenden der Aktivitätsdesigner](../workflow-designer/using-the-activity-designers.md)