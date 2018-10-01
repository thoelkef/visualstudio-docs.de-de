---
title: Dialogfeld "CorrelationInitializers" hinzufügen "| Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 8543ebd784af13251663155327c2bfb9097b4904
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520378"
---
# <a name="add-correlationinitializers-dialog-box"></a>CorrelationInitializers hinzufügen (Dialogfeld)
Die **Korrelationsinitialisierer hinzufügen** Dialogfeld wird verwendet, [!INCLUDE[wfd1](../includes/wfd1-md.md)] so konfigurieren Sie die **CorrelationInitializers** Eigenschaften der <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, und <xref:System.ServiceModel.Activities.ReceiveReply> Aktivitäten. [!INCLUDE[crabout](../includes/crabout-md.md)] die Aktivitäts-Designer, die dieses Dialogfeld verwenden, finden Sie unter den [senden](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), und [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md) Themen.  
  
 Die Korrelationsinitialisierer der in diesem Dialogfeld angegebenen Auflistung können abfragebasierte, Kontext-, Rückrufkontext- oder Anforderung-Antwort-Korrelationen zwischen den Messagingaktivitäten initialisieren.  
  
 Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **Add Correlation Initializers** Dialogfeld.  
  
|Benutzeroberflächenelement|Beschreibung|  
|----------------|-----------------|  
|**Initialisierer hinzufügen**|Klicken Sie auf die **hinzufügen Initialize** Feld, um der Auflistung einen zusätzlichen Initialisierer hinzuzufügen.|  
|**Korrelationstyp**|Gibt den Typ des Korrelationsinitialisierers an. Es stehen vier Typen zur Auswahl:<br /><br /> 1.  Ein Rückrufkorrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>-Objekt anzugeben.<br />2.  Ein Kontextkorrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekt anzugeben.<br />3.  Ein Anforderung-Antwort-Korrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>-Objekt anzugeben.<br />4.  Ein Abfragekorrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>-Objekt anzugeben.<br /><br /> So bearbeiten Sie die **CorrelationType**<br /><br /> 1.  Registerkarte ", zu der entsprechenden Zeile in der **Initialisierer hinzufügen** DataGrid.<br />2.  Drücken Sie Strg + Tab, um den Fokus zu setzen, um **CorrelationTypeComboBox**<br />3.  Drücken Sie Alt + nach-unten für das Anzeigen der **"ComboBox"** und bearbeiten Sie sie.|  
|**XPath-Abfragen**|Ein Schlüssel-Wert-Paar, das die Abfragen enthält, mit denen Korrelationsdaten aus eingehenden und ausgehenden Nachrichten extrahiert werden. Diese Liste ist nur bei Verwendung der <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>-Typen gültig.|  
  
## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>So öffnen Sie das Dialogfeld "Korrelationsinitialisierer hinzufügen"  
 Die **Korrelationsinitialisierer hinzufügen** Dialogfeld wird verwendet, durch die **senden**, **Receive**, **ReceiveAndSendReply**, und  **SendAndReceiveReply** Designer. Zugriff darauf ist ähnlich wie in jedem Fall und der Fall, bei der, die **Receive** Designer verwendet wird, zur Veranschaulichung des Verfahrens.  
  
 Die **Receive** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und auf die [!INCLUDE[wfd2](../includes/wfd2-md.md)] -Oberfläche ganz egal, wo Aktivitäten normalerweise platziert werden. Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt. Wählen Sie die **Receive** Aktivitäts-Designer, und klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben dem (Collection) Text für die **CorrelationInitializers** Eigenschaft im Eigenschaftenraster für das **hinzufügen Korrelationsinitialisierer** Dialogfeld angezeigt.  
  
## <a name="see-also"></a>Siehe auch  
 [Korrelations-Dialogfeld hinzufügen](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [Korrelation initialisieren (Dialogfeld)](../workflow-designer/initialize-correlation-dialog-box.md)