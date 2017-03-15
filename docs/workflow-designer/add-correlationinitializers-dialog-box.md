---
title: "CorrelationInitializers hinzuf&#252;gen (Dialogfeld) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "AddCorrelationInitializers.UI"
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# CorrelationInitializers hinzuf&#252;gen (Dialogfeld)
Das Dialogfeld **Korrelationsinitialisierer hinzufügen** wird in [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] verwendet, um die **CorrelationInitializers**\-Eigenschaften der Aktivitäten <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> und <xref:System.ServiceModel.Activities.ReceiveReply> zu konfigurieren.[!INCLUDE[crabout](../test/includes/crabout_md.md)] zu den Aktivitätsdesignern, die dieses Dialogfeld verwenden, finden Sie in den Themen [Senden](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md) und [SendAndReceiveReply](../workflow-designer/sendandreceivereply-template-designer.md).  
  
 Die Korrelationsinitialisierer der in diesem Dialogfeld angegebenen Auflistung können abfragebasierte, Kontext\-, Rückrufkontext\- oder Anforderung\-Antwort\-Korrelationen zwischen den Messagingaktivitäten initialisieren.  
  
 In der folgenden Tabelle werden die Benutzeroberflächenelemente des Dialogfelds **Korrelationsinitialisierer hinzufügen** beschrieben.  
  
|Benutzeroberflächenelement|Beschreibung|  
|--------------------------------|------------------|  
|**Initialisierer hinzufügen**|Klicken Sie auf das Feld **Initialisierer hinzufügen**, um der Auflistung einen zusätzlichen Initialisierer hinzuzufügen.|  
|**Korrelationstyp**|Gibt den Typ des Korrelationsinitialisierers an.Es stehen vier Typen zur Auswahl:<br /><br /> 1.  Ein Rückrufkorrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>\-Objekt anzugeben.<br />2.  Ein Kontextkorrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.CorrelationInitializer>\-Objekt anzugeben.<br />3.  Ein Anforderung\-Antwort\-Korrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>\-Objekt anzugeben.<br />4.  Ein Abfragekorrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>\-Objekt anzugeben.<br /><br /> So bearbeiten Sie den **CorrelationType**<br /><br /> 1.  Gehen Sie mit der Tabulatortaste zu der entsprechenden Zeile im Datenraster **Initialisierer hinzufügen**.<br />2.  Tastenkombination STRG\+TAB Festlegen des Fokus auf **CorrelationTypeComboBox**<br />3.  Tastenkombination ALT\+NACH\-UNTEN Öffnen und Bearbeiten von **ComboBox**.|  
|**XPath\-Abfragen**|Ein Schlüssel\-Wert\-Paar, das die Abfragen enthält, mit denen Korrelationsdaten aus eingehenden und ausgehenden Nachrichten extrahiert werden.Diese Liste ist nur bei Verwendung der <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>\-Typen gültig.|  
  
## So öffnen Sie das Dialogfeld "Korrelationsinitialisierer hinzufügen"  
 Das Dialogfeld **Korrelationsinitialisierer hinzufügen** wird von den **Send**\-, **Receive**\-, **ReceiveAndSendReply**\- und **SendAndReceiveReply**\-Designern verwendet.Auf jeden Designer wird auf ähnliche Weise zugegriffen Fall, und dieses Verfahren wird hier anhand des **Receive**\-Designers veranschaulicht.  
  
 Der **Receive**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden.Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>\-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt.Wählen Sie den **Receive**\-Aktivitätsdesigner aus, und klicken Sie neben dem Text \(Auflistung\) für die **CorrelationInitializers**\-Eigenschaft im Eigenschaftenraster auf die Schaltfläche mit den Auslassungspunkten, um das Dialogfeld **Korrelationsinitialisierer hinzufügen** anzuzeigen.  
  
## Siehe auch  
 [Add Correlation Dialog Box](http://msdn.microsoft.com/de-de/9e41a149-e8ab-41b1-8886-ea06a63041b6)   
 [ Korrelation initialisieren \(Dialogfeld\)](../workflow-designer/initialize-correlation-dialog-box.md)