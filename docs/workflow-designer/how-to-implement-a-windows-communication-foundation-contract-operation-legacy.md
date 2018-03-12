---
title: "Vorgehensweise: implementieren ein Windows Communication Foundation-Vertragsvorgangs (Vorgängerversion) | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: a8ea31cf143c572e42f1250f3a16cf73148a53fd
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Vorgehensweise: Implementieren eines Windows Communication Foundation-Vertragsvorgangs (Legacy)
In diesem Thema wird beschrieben, wie zum Implementieren einer [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)] -vertragsvorgangs mithilfe der älteren Windows-Workflow-Designer, die als Ziel verwendet die [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

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

- [Dialogfeld "Vorgang auswählen" (Vorgängerversion)](../workflow-designer/choose-operation-dialog-box-legacy.md)
- [Vorgehensweise: Aufrufen ein WCF-Vertragsvorgangs (Vorgängerversion)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)
- [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)