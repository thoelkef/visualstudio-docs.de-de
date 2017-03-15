---
title: "Dialogfeld &quot;Vorgang ausw&#228;hlen&quot; (Vorg&#228;ngerversion) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Workflow.Activities.Design.OperationPickerDialog.UI"
ms.assetid: bc3ec902-7797-494e-af48-e70c97eb6779
caps.latest.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Dialogfeld &quot;Vorgang ausw&#228;hlen&quot; (Vorg&#228;ngerversion)
In diesem Thema wird die Verwendung des Dialogfelds **Vorgang auswählen** in der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] beschrieben.Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.  
  
 Mit dem Dialogfeld **Vorgang auswählen** wird ein Vorgang ausgewählt, der einer <xref:System.Workflow.Activities.ReceiveActivity>\-Aktivität oder einer <xref:System.Workflow.Activities.SendActivity>\-Aktivität zugeordnet werden soll.Weitere Informationen zur Verwendung des Dialogfelds mit diesen Aktivitäten finden Sie unter [Vorgehensweise: Implementieren eines WCF\-Vertragsvorgangs \(Vorgängerversion\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) und [Vorgehensweise: Aufrufen eines WCF\-Vertragsvorgangs \(Vorgängerversion\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md).  
  
 In der folgenden Tabelle werden die Benutzeroberflächenelemente des Dialogfelds **Vorgang auswählen** beschrieben.  
  
|Benutzeroberflächenelement|Beschreibung|  
|--------------------------------|------------------|  
|**Vertrag hinzufügen**|Erstellt einen neuen Vertrag.Sie können neue Vorgänge für diesen Vertrag definieren.\(Wird nur mit <xref:System.Workflow.Activities.ReceiveActivity> verwendet.\)|  
|**Vorgang hinzufügen**|Fügt einem neuen Vertrag, den Sie im Dialogfeld **Vorgang auswählen** erstellt haben, neue Vorgänge hinzu. **Note:**  Sie können neue Vorgänge nur Verträgen hinzufügen, die Sie über das Dialogfeld **Vorgang auswählen** erstellt haben. <br /><br /> \(Wird nur mit <xref:System.Workflow.Activities.ReceiveActivity> verwendet.\)|  
|**Importieren...**|Importiert einen zuvor definierten Vertrag und ermöglicht Ihnen die Auswahl eines Vorgangs aus diesem Vertrag.|  
|**Vorgangsname**|Der Name des gerade ausgewählten Vorgangs.Dieses Textfeld steht nur dann zum Bearbeiten zur Verfügung, wenn Sie einen Vorgang über das Dialogfeld **Vorgang auswählen** erstellt haben.|  
|**Parameter**|Registerkarte, die die Parameterdefinitionen für den gerade ausgewählten Vorgang enthält. **Note:**  Parameterdefinitionen können nur dann geändert werden, wenn Sie einen Vorgang über das Dialogfeld **Vorgang auswählen** erstellt haben.|  
|**Eigenschaften**|Registerkarte, die die <xref:System.Net.Security.ProtectionLevel>\-Einstellungen für zwischen dem Client und dem Dienst gesendete Nachrichten enthält. **Note:**  Diese Registerkarte ist nur dann aktiviert, wenn Sie einen Vorgang über das Dialogfeld **Vorgang auswählen** erstellt haben.|  
|**Berechtigungen**|Registerkarte, die die <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionName%2A>\-Eigenschaft und <xref:System.Workflow.Activities.OperationInfoBase.PrincipalPermissionRole%2A>\-Eigenschaft von Benutzern enthält, die berechtigt sind, diesen Vorgang aufzurufen.Wenn z. B. nur Benutzer aus der Gruppe Administratoren berechtigt sind, diesen Vorgang aufzurufen, geben Sie im Textfeld **Rolle** "Administratoren" ein.<br /><br /> Diese Registerkarte ist für über das Dialogfeld **Vorgangauswählen** erstellte Vorgänge und für über die Schaltfläche **Importieren** importierte Vorgänge aktiviert.|  
  
> [!NOTE]
>  Im Dialogfeld **Vorgang auswählen** werden nur Verträge oder Vorgänge angezeigt, die von anderen <xref:System.Workflow.Activities.SendActivity>\-Aktivitäten im Workflow verwendet werden.Entsprechend werden im Dialogfeld **Vorgang auswählen** für <xref:System.Workflow.Activities.ReceiveActivity>\-Aktivitäten nur Verträge oder Vorgänge angezeigt, die von anderen **ReceiveActivity**\-Aktivitäten im Workflow verwendet werden.  
  
## Siehe auch  
 [Vorgehensweise: Implementieren eines WCF\-Vertragsvorgangs \(Vorgängerversion\)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Vorgehensweise: Aufrufen eines WCF\-Vertragsvorgangs \(Vorgängerversion\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Benutzeroberflächenhilfe von Visual Studio Designer für Windows Workflow Foundation \(Vorgängerversion\)](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)