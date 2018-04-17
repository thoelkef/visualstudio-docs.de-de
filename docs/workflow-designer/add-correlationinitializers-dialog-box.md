---
title: CorrelationInitializers Dialogfeld "hinzufügen" | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1dda343758925e1cece9d796bee8f0d225729c36
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="add-correlationinitializers-dialog-box"></a>CorrelationInitializers hinzufügen (Dialogfeld)
Die **Korrelationsinitialisierer hinzufügen** Dialogfeld dient in Windows Workflow-Designer zum Konfigurieren der **CorrelationInitializers** Eigenschaften der <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, und <xref:System.ServiceModel.Activities.ReceiveReply> Aktivitäten. Weitere Informationen zu den Aktivitäts-Designer, die diesem Feld verwenden, finden Sie unter der [senden](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), und [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) Themen.

 Die Korrelationsinitialisierer der in diesem Dialogfeld angegebenen Auflistung können abfragebasierte, Kontext-, Rückrufkontext- oder Anforderung-Antwort-Korrelationen zwischen den Messagingaktivitäten initialisieren.

 Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **Korrelationsinitialisierer hinzufügen** (Dialogfeld).

|Benutzeroberflächenelement|Beschreibung|
|----------------|-----------------|
|**Initialisierer hinzufügen**|Klicken Sie auf die **Add Initialize** Feld, um der Auflistung einen zusätzlichen Initialisierer hinzuzufügen.|
|**Korrelationstyp**|Gibt den Typ des Korrelationsinitialisierers an. Es stehen vier Typen zur Auswahl:<br /><br /> 1.  Ein Rückrufkorrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>-Objekt anzugeben.<br />2.  Ein Kontextkorrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekt anzugeben.<br />3.  Ein Anforderung-Antwort-Korrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>-Objekt anzugeben.<br />4.  Ein Abfragekorrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>-Objekt anzugeben.<br /><br /> So bearbeiten Sie die **CorrelationType**<br /><br /> 1.  Registerkarte ", zu der entsprechenden Zeile in der **Initialisierer hinzufügen** DataGrid.<br />2.  Drücken Sie Strg + Tab, um den Fokus **CorrelationTypeComboBox**<br />3.  Drücken Sie Alt + nach-unten, um Popup-die **ComboBox** und bearbeiten.|
|**XPath-Abfragen**|Ein Schlüssel-Wert-Paar, das die Abfragen enthält, mit denen Korrelationsdaten aus eingehenden und ausgehenden Nachrichten extrahiert werden. Diese Liste ist nur bei Verwendung der <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>-Typen gültig.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>So öffnen Sie das Dialogfeld "Korrelationsinitialisierer hinzufügen"
 Die **Korrelationsinitialisierer hinzufügen** Dialogfeld wird verwendet, durch die **senden**, **Receive**, **ReceiveAndSendReply**, und  **SendAndReceiveReply** Designer. Auf diese zuzugreifen ähnelt in jedem Fall und die Groß-/Kleinschreibung, die umfasst die **Receive** -Designer ist die Verwendung hier zur Veranschaulichung des Verfahrens.

 Die **Receive** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** gezogen und auf die [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] -Oberfläche ablegen, wo Aktivitäten normalerweise platziert werden. Dadurch wird eine <xref:System.ServiceModel.Activities.Receive>-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt. Wählen Sie die **Receive** Aktivitäts-Designer, und klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben dem (Collection) Text für die **CorrelationInitializers** Eigenschaft im Eigenschaftenraster für die **hinzufügen Korrelationsinitialisierer** Dialogfeld angezeigt.

## <a name="see-also"></a>Siehe auch

- [Korrelation Dialogfeld "hinzufügen"](http://msdn.microsoft.com/en-us/9e41a149-e8ab-41b1-8886-ea06a63041b6)
- [Korrelation initialisieren (Dialogfeld)](../workflow-designer/initialize-correlation-dialog-box.md)