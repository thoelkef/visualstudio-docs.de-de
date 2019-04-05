---
title: Dialogfeld "Vorgang" (Vorgängerversion) auswählen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Design.OperationPickerDialog.UI
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7b9d40f3627cd24aa7758a0d599eb6e5d770c9f8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946909"
---
# <a name="choose-operation-dialog-box-legacy"></a>Dialogfeld "Vorgang auswählen" (Vorgängerversion)
In diesem Thema wird beschrieben, wie die **Vorgang auswählen** Dialogfeld in der Vorgängerversion [!INCLUDE[wfd1](../includes/wfd1-md.md)]. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../includes/wfd2-md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielen möchten.  
  
 Die **Vorgang auswählen** Dialogfeld wird verwendet, um das Auswählen eines Vorgangs zugeordnet werden soll eine <xref:System.Workflow.Activities.ReceiveActivity> Aktivität oder eine <xref:System.Workflow.Activities.SendActivity> Aktivität. Weitere Informationen zum Verwenden dieses Dialogfeld können Sie mit diesen Aktivitäten finden Sie unter [Vorgehensweise: Implementieren ein WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) und [Vorgehensweise: Aufrufen ein WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).  
  
 Die folgende Tabelle beschreibt die Elemente der Benutzeroberfläche (UI) von der **Vorgang auswählen** Dialogfeld.  
  
|Benutzeroberflächenelement|Beschreibung|  
|----------------|-----------------|  
|**Vertrag hinzufügen**|Erstellt einen neuen Vertrag. Sie können neue Vorgänge für diesen Vertrag definieren. (Wird nur mit <xref:System.Workflow.Activities.ReceiveActivity> verwendet.)|  
|**Vorgang hinzufügen**|Fügt neue Vorgänge auf einen neuen Vertrag, die Sie in erstellt die **Vorgang auswählen** Dialogfeld. **Hinweis**:  Sie können neue Vorgänge nur Verträgen, die Sie, durch erstellt haben Hinzufügen der **Vorgang auswählen** Dialogfeld. <br /><br /> (Wird nur mit <xref:System.Workflow.Activities.ReceiveActivity> verwendet.)|  
|**Importieren...**|Importiert einen zuvor definierten Vertrag und ermöglicht Ihnen die Auswahl eines Vorgangs aus diesem Vertrag.|  
|**Vorgangsname**|Der Name des gerade ausgewählten Vorgangs. Dieses Textfeld steht für die Bearbeitung nur dann, wenn Sie einen Vorgang über erstellt haben die **Vorgang auswählen** Dialogfeld.|  
|**Parameter**|Registerkarte, die die Parameterdefinitionen für den gerade ausgewählten Vorgang enthält. **Hinweis**:  Parameterdefinitionen können geändert werden, nur dann, wenn Sie einen Vorgang über erstellt haben, haben die **Vorgang auswählen** Dialogfeld.|  
|**Eigenschaften**|Registerkarte, die die <xref:System.Net.Security.ProtectionLevel>-Einstellungen für zwischen dem Client und dem Dienst gesendete Nachrichten enthält. **Hinweis**:  Auf dieser Registerkarte wird nur aktiviert, wenn Sie einen Vorgang über erstellt haben die **Vorgang auswählen** Dialogfeld.|  
|**Berechtigungen**|Registerkarte, die die <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A>-Eigenschaft und <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A>-Eigenschaft von Benutzern enthält, die berechtigt sind, diesen Vorgang aufzurufen. Z. B. nur Benutzer aus Gruppe "Administratoren" zugelassen wird, diesen Vorgang aufzurufen, klicken Sie dann Sie würden schreiben "Administratoren" in der **Rolle** Textfeld.<br /><br /> Diese Registerkarte ist aktiviert, für beide Vorgänge erstellt werden, über die **ChooseOperation** Dialogfeld und Vorgänge, die über importiert wurden die **Import** Schaltfläche.|  
  
> [!NOTE]
>  Die **Vorgang auswählen** Dialogfeld zeigt nur Verträge oder Vorgänge, die von anderen verwendet werden <xref:System.Workflow.Activities.SendActivity> Aktivitäten im Workflow. Auf ähnliche Weise die **Vorgang auswählen** Dialogfeld <xref:System.Workflow.Activities.ReceiveActivity> -Aktivitäten nur Verträge oder Vorgänge, die von anderen verwendet werden **ReceiveActivity** Aktivitäten im Workflow.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Implementieren eines WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Vorgehensweise: Aufrufen eines WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Benutzeroberflächenhilfe von Visual Studio Designer für Windows Workflow Foundation (Vorgängerversion)](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)