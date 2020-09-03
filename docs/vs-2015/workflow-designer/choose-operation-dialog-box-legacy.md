---
title: Dialog Feld "Vorgang auswählen" (Legacy) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f2736db7e18733a9477238cafad21088eb135e89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659160"
---
# <a name="choose-operation-dialog-box-legacy"></a>Dialogfeld "Vorgang auswählen" (Vorgängerversion)
In diesem Thema wird beschrieben, wie das Dialogfeld **Vorgang auswählen** in der Vorgängerversion von verwendet wird [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.

 Das Dialogfeld **Vorgang auswählen** wird verwendet, um einen Vorgang auszuwählen, der einer- <xref:System.Workflow.Activities.ReceiveActivity> Aktivität oder einer-Aktivität zugeordnet werden soll <xref:System.Workflow.Activities.SendActivity> . Weitere Informationen zur Verwendung dieses Dialog Felds mit diesen Aktivitäten finden Sie unter Gewusst [wie: Implementieren eines WCF-Vertrags Vorgangs (Legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) und Gewusst [wie: Aufrufen eines WCF-Vertrags Vorgangs (](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)Vorgängerversion).

 In der folgenden Tabelle werden die Benutzeroberflächen Elemente des Dialog Felds **Vorgang auswählen** beschrieben.

|Benutzeroberflächenelement|BESCHREIBUNG|
|----------------|-----------------|
|**Vertrag hinzufügen**|Erstellt einen neuen Vertrag. Sie können neue Vorgänge für diesen Vertrag definieren. (Wird nur mit <xref:System.Workflow.Activities.ReceiveActivity> verwendet.)|
|**Vorgang hinzufügen**|Fügt einem neuen Vertrag, den Sie im Dialogfeld **Vorgang auswählen** erstellt haben, neue Vorgänge hinzu. **Hinweis:**  Sie können neue Vorgänge nur zu Verträgen hinzufügen, die Sie über das Dialogfeld **Vorgang auswählen** erstellt haben. <br /><br /> (Wird nur mit <xref:System.Workflow.Activities.ReceiveActivity> verwendet.)|
|**Importieren...**|Importiert einen zuvor definierten Vertrag und ermöglicht Ihnen die Auswahl eines Vorgangs aus diesem Vertrag.|
|**Vorgangsname**|Der Name des gerade ausgewählten Vorgangs. Dieses Textfeld ist nur zur Bearbeitung verfügbar, wenn Sie einen Vorgang über das Dialogfeld **Vorgang auswählen** erstellt haben.|
|**Parameter**|Registerkarte, die die Parameterdefinitionen für den gerade ausgewählten Vorgang enthält. **Hinweis:**  Parameter Definitionen können nur geändert werden, wenn Sie einen Vorgang über das Dialogfeld **Vorgang auswählen** erstellt haben.|
|**Eigenschaften**|Registerkarte, die die <xref:System.Net.Security.ProtectionLevel>-Einstellungen für zwischen dem Client und dem Dienst gesendete Nachrichten enthält. **Hinweis:**  Diese Registerkarte ist nur aktiviert, wenn Sie einen Vorgang über das Dialogfeld **Vorgang auswählen** erstellt haben.|
|**Berechtigungen**|Registerkarte, die die <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A>-Eigenschaft und <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A>-Eigenschaft von Benutzern enthält, die berechtigt sind, diesen Vorgang aufzurufen. Wenn z. b. nur Benutzer der Gruppe "Administratoren" diesen Vorgang anrufen dürfen, würden Sie im Textfeld **Rolle** "Administratoren" schreiben.<br /><br /> Diese Registerkarte ist für beide Vorgänge aktiviert, die über das Dialogfeld **Auswahl Vorgang** erstellt wurden, sowie durch Vorgänge, die über die Schaltfläche **importieren** importiert wurden.|

> [!NOTE]
> Im Dialogfeld **Vorgang auswählen** werden nur Verträge oder Vorgänge angezeigt, die von anderen <xref:System.Workflow.Activities.SendActivity> Aktivitäten im Workflow verwendet werden. Entsprechend werden im Dialogfeld **Vorgang auswählen** für <xref:System.Workflow.Activities.ReceiveActivity> Aktivitäten nur Verträge oder Vorgänge angezeigt, die von anderen **ReceiveActivity** -Aktivitäten im Workflow verwendet werden.

## <a name="see-also"></a>Weitere Informationen
 Vorgehens [Weise: Implementieren eines WCF-Vertrags Vorgangs (Legacy)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) Gewusst [wie: Aufrufen eines WCF-Vertrags Vorgangs (Legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [Legacy-Designer für die Windows Workflow Foundation UI-Hilfe](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)