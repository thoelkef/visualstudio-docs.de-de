---
title: Dialog Feld "Workflow-Designer-correlationinitializers hinzufügen"
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AddCorrelationInitializers.UI
ms.assetid: c0517467-d54a-4ee6-aef0-c19b96b6f395
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d2a0b0f7c76b392d5d2d0135c3ab6e370f8678e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114295"
---
# <a name="add-correlationinitializers-dialog-box"></a>CorrelationInitializers hinzufügen (Dialogfeld)

Das Dialogfeld **korrelationsinitialisierer hinzufügen** wird in Workflow-Designer verwendet, um die **correlationinitializers** -Eigenschaften der <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Receive> Aktivitäten,, und zu konfigurieren <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.ReceiveReply> . Weitere Informationen zu den Aktivitäts Designern, die dieses Feld verwenden, finden Sie in den Themen [Send](../workflow-designer/send-activity-designer.md), [Receive](../workflow-designer/receive-activity-designer.md), [receiveandsendreply](../workflow-designer/receiveandsendreply-template-designer.md)und [sendandreceivereply](../workflow-designer/sendandreceivereply-template-designer.md) .

Die Korrelations Initialisierer in der Auflistung, die in diesem Dialogfeld angegeben ist, können die folgenden Korrelationen zwischen den Messaging Aktivitäten initialisieren:

- Abfrage basiert
- context
- Rückruf Kontext
- Anforderung-Antwort

In der folgenden Tabelle werden die Benutzeroberflächen Elemente des Dialog Felds **korrelationsinitialisierer hinzufügen** beschrieben:

|Benutzeroberflächenelement|BESCHREIBUNG|
|-|-----------------|
|**Initialisierer hinzufügen**|Klicken Sie auf das Feld **initialisieren hinzufügen** , um der Sammlung einen zusätzlichen Initialisierer hinzuzufügen.|
|**Korrelationstyp**|Gibt den Typ des Korrelationsinitialisierers an. Es stehen vier Typen zur Auswahl:<br /><br /> 1. ein Rückruf korrelationsinitialisierer zum Angeben einer <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer> .<br />2. ein kontexkorrelationsinitialisierer zum Angeben einer <xref:System.ServiceModel.Activities.CorrelationInitializer> .<br />3. ein Anforderungs-/Antwort-korrelationsinitialisierer, um einen anzugeben <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> .<br />4. ein abfragekorrelationsinitialisierer zum Angeben eines-Objekts <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> .<br /><br /> So bearbeiten Sie den **correlationtype**<br /><br /> 1. Tab zur bestimmten Zeile im DataGrid- **Initialisierer hinzufügen** .<br />2. Drücken Sie **STRG**Tab, um den Fokus auf **correlationtypecombobox**festzulegen. + **Tab**<br />3. Drücken Sie alt + nach-unten, um das Kombinations **Feld** aufklappen und bearbeiten.|
|**XPath-Abfragen**|Ein Schlüssel-Wert-Paar, das die Abfragen enthält, mit denen Korrelationsdaten aus eingehenden und ausgehenden Nachrichten extrahiert werden. Diese Liste ist nur bei Verwendung der <xref:System.ServiceModel.Activities.QueryCorrelationInitializer>-Typen gültig.|

## <a name="to-launch-the-add-correlation-initializers-dialog-box"></a>So öffnen Sie das Dialogfeld "Korrelationsinitialisierer hinzufügen"

 Das Dialogfeld **korrelationsinitialisierer hinzufügen** wird von den Designern **Send**, **Receive**, **receiveandsendreply**und **sendandreceivereply** verwendet. Der Zugriff auf Sie ist in jedem Fall ähnlich, und der Fall, in dem der **Empfangs** -Designer verwendet wird, wird hier verwendet, um die Prozedur zu veranschaulichen.

 Der **Receive** -Aktivitäts Designer kann aus der **Toolbox** gezogen und auf der Workflow-Designer-Oberfläche dort abgelegt werden, wo Aktivitäten platziert werden. Beim Löschen des **Empfangs** Aktivitäts Designers wird eine- <xref:System.ServiceModel.Activities.Receive> Aktivität mit dem Standardwert <xref:System.Activities.Activity.DisplayName%2A> Receive erstellt. Wählen Sie den **Receive** -Aktivitäts Designer aus, und klicken Sie auf die Schaltfläche mit den Auslassungs Punkten neben dem Text (Auflistung) für die **correlationinitializers** -Eigenschaft im Eigenschaften Raster, damit das Dialogfeld **Korrelations Initialisierer hinzufügen** angezeigt wird.

## <a name="see-also"></a>Weitere Informationen

- [Korrelation initialisieren (Dialogfeld)](../workflow-designer/initialize-correlation-dialog-box.md)
