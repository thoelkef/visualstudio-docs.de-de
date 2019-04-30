---
title: Workflow-Designer - CorrelationInitializers Dialogfeld "hinzufügen"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21c030295d325ea1ee4d546356f8cda5ef6ffd3f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946650"
---
# <a name="add-correlationinitializers-dialog-box"></a>CorrelationInitializers hinzufügen (Dialogfeld)

Die **Korrelationsinitialisierer hinzufügen** Dialogfeld wird im Workflow-Designer verwendet, so konfigurieren Sie die **CorrelationInitializers** Eigenschaften der <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, und <xref:System.ServiceModel.Activities.ReceiveReply> Aktivitäten. Weitere Informationen zu den Aktivitätsdesignern, die dieses Feld verwenden, finden Sie unter den [senden](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [ReceiveAndSendReply](../workflow-designer/receiveandsendreply-template-designer.md), und [SendAndReceiveReply ](../workflow-designer/sendandreceivereply-template-designer.md) Themen.

Die korrelationsinitialisierer der in diesem Dialogfeld angegebenen Auflistung können die folgenden Korrelationen zwischen den messagingaktivitäten initialisieren:

- abfragebasierte
- Kontext
- rückrufkontext
- request-reply

Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **Add Correlation Initializers** Dialogfeld:

|Benutzeroberflächenelement|Beschreibung|
|-|-----------------|
|**Initialisierer hinzufügen**|Klicken Sie auf die **hinzufügen Initialize** Feld, um der Auflistung einen zusätzlichen Initialisierer hinzuzufügen.|
|**Korrelationstyp**|Gibt den Typ des Korrelationsinitialisierers an. Es stehen vier Typen zur Auswahl:<br /><br /> 1. Ein Rückrufkorrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>-Objekt anzugeben.<br />2. Ein Kontextkorrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.CorrelationInitializer>-Objekt anzugeben.<br />3. Ein Anforderung-Antwort-Korrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>-Objekt anzugeben.<br />4. Ein Abfragekorrelationsinitialisierer, um ein <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>-Objekt anzugeben.<br /><br /> So bearbeiten Sie die **CorrelationType**<br /><br /> 1. Registerkarte ", zu der entsprechenden Zeile in der **Initialisierer hinzufügen** DataGrid.<br />2. Um den Fokus zu setzen, um **CorrelationTypeComboBox**, drücken Sie die **STRG**+**Registerkarte**.<br />3. Drücken Sie Alt + nach-unten für das Anzeigen der **"ComboBox"** und bearbeiten Sie sie.|
|**XPath-Abfragen**|Ein Schlüssel-Wert-Paar, das die Abfragen enthält, mit denen Korrelationsdaten aus eingehenden und ausgehenden Nachrichten extrahiert werden. Diese Liste ist nur bei Verwendung der <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>-Typen gültig.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>So öffnen Sie das Dialogfeld "Korrelationsinitialisierer hinzufügen"

 Die **Korrelationsinitialisierer hinzufügen** Dialogfeld wird verwendet, durch die **senden**, **Receive**, **ReceiveAndSendReply**, und  **SendAndReceiveReply** Designer. Zugriff darauf ist ähnlich wie in jedem Fall und der Fall, bei der, die **Receive** -Designer dient hier zur Veranschaulichung des Verfahrens.

 Die **Receive** Aktivitäts-Designer gezogen werden kann, aus der **Toolbox** und sich der Workflow-Designer-Oberfläche gelöscht werden, wo Aktivitäten platziert werden. Löschen der **Receive** Aktivitäts-Designer erstellt eine <xref:System.ServiceModel.Activities.Receive> -Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Receive. Wählen Sie die **Receive** Aktivitäts-Designer, und klicken Sie auf die Schaltfläche mit den Auslassungspunkten neben dem (Collection) Text für die **CorrelationInitializers** Eigenschaft im Eigenschaftenraster für das **hinzufügen Korrelationsinitialisierer** Dialogfeld angezeigt.

## <a name="see-also"></a>Siehe auch

- [Korrelation initialisieren (Dialogfeld)](../workflow-designer/initialize-correlation-dialog-box.md)