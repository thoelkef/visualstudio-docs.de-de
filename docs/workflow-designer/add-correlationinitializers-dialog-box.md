---
title: Dialog Feld "Workflow-Designer-correlationinitializers hinzufügen"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5d69b53e21d11cba99a9e897871c6f9e0320352f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650769"
---
# <a name="add-correlationinitializers-dialog-box"></a>CorrelationInitializers hinzufügen (Dialogfeld)

Das Dialogfeld **korrelationsinitialisierer hinzufügen** wird in Workflow-Designer verwendet, um die **correlationinitializers** -Eigenschaften der Aktivitäten <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply> und <xref:System.ServiceModel.Activities.ReceiveReply> zu konfigurieren. Weitere Informationen zu den Aktivitäts Designern, die dieses Feld verwenden, finden Sie in den Themen [Send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [receiveandsendreply](../workflow-designer/receiveandsendreply-template-designer.md)und [sendandreceivereply](../workflow-designer/sendandreceivereply-template-designer.md) .

Die Korrelations Initialisierer in der Auflistung, die in diesem Dialogfeld angegeben ist, können die folgenden Korrelationen zwischen den Messaging Aktivitäten initialisieren:

- Abfrage basiert
- Kontext
- Rückruf Kontext
- Anforderung-Antwort

In der folgenden Tabelle werden die Benutzeroberflächen Elemente des Dialog Felds **korrelationsinitialisierer hinzufügen** beschrieben:

|Benutzeroberflächenelement|Beschreibung|
|-|-----------------|
|**Initialisierer hinzufügen**|Klicken Sie auf das Feld **initialisieren hinzufügen** , um der Sammlung einen zusätzlichen Initialisierer hinzuzufügen.|
|**Korrelationstyp**|Gibt den Typ des Korrelationsinitialisierers an. Es stehen vier Typen zur Auswahl:<br /><br /> 1. ein Rückruf korrelationsinitialisierer, um eine <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> anzugeben.<br />2. ein kontextkorrelations-Initialisierer, um eine <xref:System.ServiceModel.Activities.CorrelationInitializer> anzugeben.<br />3. ein Anforderungs-/Antwort-korrelationsinitialisierer, um eine <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> anzugeben.<br />4. ein abfragekorrelations-Initialisierer, um eine <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> anzugeben.<br /><br /> So bearbeiten Sie den **correlationtype**<br /><br /> 1. Tab zur bestimmten Zeile im DataGrid- **Initialisierer hinzufügen** .<br />2. Drücken Sie **STRG** +**Registerkarte**, um den Fokus auf **correlationtypecombobox**festzulegen.<br />3. Drücken Sie alt + nach-unten, um das Kombinations **Feld** aufklappen und bearbeiten.|
|**XPath-Abfragen**|Ein Schlüssel-Wert-Paar, das die Abfragen enthält, mit denen Korrelationsdaten aus eingehenden und ausgehenden Nachrichten extrahiert werden. Diese Liste ist nur bei Verwendung der <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>-Typen gültig.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>So öffnen Sie das Dialogfeld "Korrelationsinitialisierer hinzufügen"

 Das Dialogfeld **korrelationsinitialisierer hinzufügen** wird von den Designern **Send**, **Receive**, **receiveandsendreply**und **sendandreceivereply** verwendet. Der Zugriff auf Sie ist in jedem Fall ähnlich, und der Fall, in dem der **Empfangs** -Designer verwendet wird, wird hier verwendet, um die Prozedur zu veranschaulichen.

 Der **Receive** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten platziert werden. Beim Löschen des **Receive** -Aktivitäts Designers wird eine <xref:System.ServiceModel.Activities.Receive>-Aktivität mit einem Standard <xref:System.Activities.Activity.DisplayName%2A> empfangen. Wählen Sie den **Receive** -Aktivitäts Designer aus, und klicken Sie auf die Schaltfläche mit den Auslassungs Punkten neben dem Text (Auflistung) für die **correlationinitializers** -Eigenschaft im Eigenschaften Raster, damit das Dialogfeld **Korrelations Initialisierer hinzufügen** angezeigt wird.

## <a name="see-also"></a>Siehe auch

- [Korrelation initialisieren (Dialogfeld)](../workflow-designer/initialize-correlation-dialog-box.md)