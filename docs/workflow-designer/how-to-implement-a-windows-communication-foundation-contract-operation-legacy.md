---
title: "Vorgehensweise: implementieren ein Windows Communication Foundation-Vertragsvorgangs (Vorgängerversion) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: "7"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 02d6a544b660a110c618bdcb7d3b778fd82ceaaa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Vorgehensweise: Implementieren eines Windows Communication Foundation-Vertragsvorgangs (Legacy)
In diesem Thema wird die Implementierung eines [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)]-Vertragsvorgangs mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] beschrieben, die auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielt.  
  
 Nach dem Ziehen einer **ReceiveActivity** Aktivität aus der Toolbox auf die Entwurfsoberfläche des Workflows, erstellen Sie entweder ein neues [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] Vertrag oder einen vorhandenen Vertrag importieren und die Vorgänge implementieren. Wählen Sie und/oder den Vertrag und die Vorgänge durch Erstellen der [wählen Vorgang (Dialogfeld) (Legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### <a name="to-implement-a-wcf-contract-operation"></a>So implementieren Sie einen WCF-Vertragsvorgang  
  
1.  Doppelklicken Sie auf die **ReceiveActivity** Aktivität im Designer oder klicken Sie auf die Auslassungszeichen neben der **ServiceOperationInfo** Eigenschaft in der **Eigenschaften** Bereich.  
  
2.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Klicken Sie auf **Vertrag hinzufügen** in der oberen rechten Ecke des Dialogfelds. Dadurch wird für Sie ein neuer [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]-Vertrag und -Vorgang erstellt.  
  
         - oder -   
  
    -   Klicken Sie auf **Import** in der oberen rechten Ecke des Dialogfelds. Die [navigieren, und wählen Sie eine .NET (Dialogfeld) (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) wird geöffnet. Suchen Sie eine Assembly oder ein Projekt, das den gewünschten Vertrag enthält. Wählen Sie den Vertrag aus, und klicken Sie auf **OK**.  
  
     Nachdem ein Vertrag erstellt bzw. importiert wurde, können Sie diesem Vertrag neue Vorgänge hinzufügen. Um einen neuen Vorgang hinzuzufügen, wählen Sie den Vertrag aus, und klicken Sie auf **Vorgang hinzufügen** in der oberen rechten Ecke des Dialogfelds. Fahren Sie nach dem Hinzufügen von Vorgängen mit Schritt&#160;3 fort.  
  
3.  Wählen Sie den Vorgang, die Sie zuordnen möchten die **ReceiveActivity** Aktivität. Sie können die Definition des Vorgangs ändern, indem Sie seinen Namen, die Parameter, Eigenschaften und Berechtigungseinstellungen ändern.  
  
     Um den Namen zu ändern, geben Sie den neuen Namen in der **Vorgangsnamen** Textfeld.  
  
     Klicken Sie auf die **Parameter** Tab, um die Parameter des Vorgangs zuzugreifen. Sie können den Namen, den Typ oder die Richtung eines Parameters ändern sowie Parameter hinzufügen oder löschen.  
  
     Klicken Sie auf die **Eigenschaften** Tab, um den Vorgang Schutz vorgangsschutzgrad und unterstützte Nachrichtenaustauschfunktionen des Vorgangs zuzugreifen.  
  
     Klicken Sie auf die **Berechtigungen** Registerkarte, um anzugeben, welchen Gruppen zulässig sind, um den Vorgang zu implementieren.  
  
4.  Klicken Sie auf **OK** und **ReceiveActivity** Aktivität wird zeigt den Namen für den Vorgang, der implementiert wird.  
  
5.  Platzieren Sie die Workflowaktivitäten, die Sie sind im Begriff, verwenden Sie für die Durchführung dieses Vorgangs innerhalb der **ReceiveActivity** Aktivität.  
  
## <a name="see-also"></a>Siehe auch  
 [Wählen Sie Vorgang Dialogfeld "aus" (Vorgängerversion)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Vorgehensweise: Aufrufen ein WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)