---
title: 'Vorgehensweise: Implementieren eines Windows Communication Foundation Vertrags Vorgangs (Legacy) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1f6f54e781dfae15b4b1c1159d73ac3495b35c21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603862"
---
# <a name="how-to-implement-a-windows-communication-foundation-contract-operation-legacy"></a>Vorgehensweise: Implementieren eines Windows Communication Foundation-Vertragsvorgangs (Legacy)
In diesem Thema wird die Implementierung eines [!INCLUDE[indigo1](../includes/indigo1-md.md)]-Vertragsvorgangs mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] beschrieben, die auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielt.

 Nachdem Sie eine **ReceiveActivity** -Aktivität aus der Toolbox auf die Workflow Entwurfs Oberfläche gezogen haben, erstellen Sie entweder einen neuen [!INCLUDE[indigo2](../includes/indigo2-md.md)] Vertrag, oder importieren Sie einen vorhandenen Vertrag, und implementieren Sie die Vorgänge. Sie können den Vertrag und seine Vorgänge im [Dialog Feld "Vorgang auswählen" (](../workflow-designer/choose-operation-dialog-box-legacy.md)Vorgängerversion) auswählen und/oder erstellen.

### <a name="to-implement-a-wcf-contract-operation"></a>So implementieren Sie einen WCF-Vertragsvorgang

1. Doppelklicken Sie im Designer auf die **ReceiveActivity** -Aktivität, oder klicken Sie auf die Auslassungs Punkte neben der **ServiceOperationInfo** -Eigenschaft im Bereich **Eigenschaften** .

2. Führen Sie eines der folgenden Verfahren aus:

   - Klicken Sie in der rechten oberen Ecke des Dialog Felds auf **Vertrag hinzufügen** . Dadurch wird für Sie ein neuer [!INCLUDE[indigo2](../includes/indigo2-md.md)]-Vertrag und -Vorgang erstellt.

      - oder -

   - Klicken Sie rechts oben im Dialogfeld auf **importieren** . Das [Dialog Feld .NET-Typ suchen und auswählen (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) wird geöffnet. Suchen Sie eine Assembly oder ein Projekt, das den gewünschten Vertrag enthält. Wählen Sie den Vertrag aus, und klicken Sie auf **OK**.

     Nachdem ein Vertrag erstellt bzw. importiert wurde, können Sie diesem Vertrag neue Vorgänge hinzufügen. Wenn Sie einen neuen Vorgang hinzufügen möchten, wählen Sie den Vertrag aus, und klicken Sie in der rechten oberen Ecke des Dialog Felds auf **Vorgang hinzufügen** . Fahren Sie nach dem Hinzufügen von Vorgängen mit Schritt&#160;3 fort.

3. Wählen Sie den Vorgang aus, den Sie der **ReceiveActivity** -Aktivität zuordnen möchten. Sie können die Definition des Vorgangs ändern, indem Sie seinen Namen, die Parameter, Eigenschaften und Berechtigungseinstellungen ändern.

    Um den Namen zu ändern, geben Sie im Textfeld **Vorgangs Name** den neuen Namen ein.

    Klicken Sie auf die Registerkarte **Parameter** , um auf die Parameter des Vorgangs zuzugreifen. Sie können den Namen, den Typ oder die Richtung eines Parameters ändern sowie Parameter hinzufügen oder löschen.

    Klicken Sie auf die Registerkarte **Eigenschaften** , um auf die Vorgangs Schutz Ebene und die unterstützte Nachrichtenaustausch Funktion des Vorgangs zuzugreifen.

    Klicken Sie auf die Registerkarte **Berechtigungen** , um anzugeben, welche Gruppe (n) den Vorgang implementieren darf.

4. Klicken Sie auf **OK** , und die **ReceiveActivity** -Aktivität zeigt den Vorgangs Namen für den Vorgang an, der implementiert wird.

5. Platzieren Sie die Workflow Aktivitäten, die für die Implementierung dieses Vorgangs verwendet werden, innerhalb der **ReceiveActivity** -Aktivität.

## <a name="see-also"></a>Weitere Informationen
 [Dialog Feld "Vorgang auswählen" (Legacy)](../workflow-designer/choose-operation-dialog-box-legacy.md) Gewusst [wie: Aufrufen einer WCF-Vertrags Operation (Legacy)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) [Legacy Workflow Aktivitäten](../workflow-designer/legacy-workflow-activities.md)