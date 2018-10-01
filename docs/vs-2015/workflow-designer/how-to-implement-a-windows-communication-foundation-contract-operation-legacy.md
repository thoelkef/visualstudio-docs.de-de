---
title: 'Vorgehensweise: implementieren ein Windows Communication Foundation-Vertragsvorgangs (Legacy) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: f4277de8f97951847bf448636fec1b9c652f9359
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514552"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Vorgehensweise: Implementieren eines Windows Communication Foundation-Vertragsvorgangs (Legacy)
In diesem Thema wird die Implementierung eines [!INCLUDE[indigo1](../includes/indigo1-md.md)]-Vertragsvorgangs mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] beschrieben, die auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielt.  
  
 Nach dem Ziehen einer **ReceiveActivity** Aktivität aus der Toolbox auf die Workflow-Entwurfsoberfläche, erstellen Sie entweder eine neue [!INCLUDE[indigo2](../includes/indigo2-md.md)] Vertrag oder einen vorhandenen Vertrag importieren und die Vorgänge zu implementieren. Sie wählen bzw. erstellen Sie den Vertrag und seine Vorgänge über die [Choose Vorgang Dialog Box (Legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### <a name="to-implement-a-wcf-contract-operation"></a>So implementieren Sie einen WCF-Vertragsvorgang  
  
1.  Doppelklicken Sie auf die **ReceiveActivity** Aktivität im Designer oder klicken Sie auf die Auslassungspunkte neben dem **ServiceOperationInfo** -Eigenschaft in der **Eigenschaften** Bereich.  
  
2.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Klicken Sie auf **Vertrag hinzufügen** in der oberen rechten Ecke des Dialogfelds. Dadurch wird für Sie ein neuer [!INCLUDE[indigo2](../includes/indigo2-md.md)]-Vertrag und -Vorgang erstellt.  
  
         - oder -   
  
    -   Klicken Sie auf **Import** in der oberen rechten Ecke des Dialogfelds. Die [navigieren, und wählen Sie eine .NET (Dialogfeld) (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) wird geöffnet. Suchen Sie eine Assembly oder ein Projekt, das den gewünschten Vertrag enthält. Wählen Sie den Vertrag, und klicken Sie auf **OK**.  
  
     Nachdem ein Vertrag erstellt bzw. importiert wurde, können Sie diesem Vertrag neue Vorgänge hinzufügen. Um einen neuen Vorgang hinzuzufügen, wählen Sie den Vertrag aus, und klicken Sie auf **Vorgang hinzufügen** in der oberen rechten Ecke des Dialogfelds. Fahren Sie nach dem Hinzufügen von Vorgängen mit Schritt&#160;3 fort.  
  
3.  Wählen Sie den Vorgang, die Sie zuordnen möchten die **ReceiveActivity** Aktivität. Sie können die Definition des Vorgangs ändern, indem Sie seinen Namen, die Parameter, Eigenschaften und Berechtigungseinstellungen ändern.  
  
     Um den Namen ändern möchten, geben Sie den neuen Namen in der **Vorgangsname** Textfeld.  
  
     Klicken Sie auf die **Parameter** Tab, um die Parameter des Vorgangs zuzugreifen. Sie können den Namen, den Typ oder die Richtung eines Parameters ändern sowie Parameter hinzufügen oder löschen.  
  
     Klicken Sie auf die **Eigenschaften** Tab, um den Vorgang Schutz und unterstützte Nachrichtenaustauschfunktionen des Vorgangs zuzugreifen.  
  
     Klicken Sie auf die **Berechtigungen** um anzugeben, welchen Gruppen zulässig sind, um den Vorgang zu implementieren.  
  
4.  Klicken Sie auf **OK** und **ReceiveActivity** Aktivität zeigt auf den Namen des Vorgangs, der implementiert wird.  
  
5.  Platzieren Sie die Workflowaktivitäten, die Sie dabei sind, verwenden Sie für die Implementierung des Vorgangs innerhalb der **ReceiveActivity** Aktivität.  
  
## <a name="see-also"></a>Siehe auch  
 [Dialogfeld "Vorgang" (Vorgängerversion) auswählen](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Vorgehensweise: Aufrufen ein WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)