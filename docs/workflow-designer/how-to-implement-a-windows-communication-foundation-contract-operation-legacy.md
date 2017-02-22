---
title: "Vorgehensweise: Implementieren eines Windows Communication Foundation-Vertragsvorgangs (Legacy) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: d6aeb20e-fac8-4a9d-bd26-ae78bef96b41
caps.latest.revision: 7
caps.handback.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Vorgehensweise: Implementieren eines Windows Communication Foundation-Vertragsvorgangs (Legacy)
In diesem Thema wird die Implementierung eines [!INCLUDE[indigo1](../workflow-designer/includes/indigo1_md.md)]\-Vertragsvorgangs mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] beschrieben, die auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielt.  
  
 Nach dem Ziehen einer **ReceiveActivity**\-Aktivität aus der Toolbox zur Workflowentwurfsoberfläche erstellen Sie entweder einen neuen [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]\-Vertrag, oder Sie importieren einen vorhandenen Vertrag und implementieren die Vorgänge.Sie wählen den Vertrag und seine Vorgänge aus und\/oder erstellen sie über das [Dialogfeld "Vorgang auswählen" \(Vorgängerversion\)](../workflow-designer/choose-operation-dialog-box-legacy.md).  
  
### So implementieren Sie einen WCF\-Vertragsvorgang  
  
1.  Doppelklicken Sie auf die **ReceiveActivity**\-Aktivität im Designer oder klicken Sie auf die Ellipse neben der **ServiceOperationInfo**\-Eigenschaft im Bereich **Eigenschaften**.  
  
2.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Klicken Sie rechts oben im Dialogfeld auf **Vertrag hinzufügen**.Dadurch wird für Sie ein neuer [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]\-Vertrag und \-Vorgang erstellt.  
  
         \-oder\-  
  
    -   Klicken Sie rechts oben im Dialogfeld auf **Importieren**.Daraufhin wird das [Dialogfeld '.NET\-Typ suchen und auswählen' \(Vorgängerversion\)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md) geöffnet.Suchen Sie eine Assembly oder ein Projekt, das den gewünschten Vertrag enthält.Wählen Sie den Vertrag aus, und klicken Sie auf **OK**.  
  
     Nachdem ein Vertrag erstellt bzw. importiert wurde, können Sie diesem Vertrag neue Vorgänge hinzufügen.Wählen Sie zum Hinzufügen eines neuen Vorgangs den Vertrag aus, und klicken Sie oben rechts im Dialogfeld auf **Vorgang hinzufügen**.Fahren Sie nach dem Hinzufügen von Vorgängen mit Schritt 3 fort.  
  
3.  Wählen Sie den Vorgang aus, den Sie der **ReceiveActivity**\-Aktivität zuordnen möchten.Sie können die Definition des Vorgangs ändern, indem Sie seinen Namen, die Parameter, Eigenschaften und Berechtigungseinstellungen ändern.  
  
     Geben Sie zum Ändern des Namens den neuen Namen im Textfeld **Vorgangsname** ein.  
  
     Klicken Sie auf die Registerkarte **Parameter**, um auf die Parameter des Vorgangs zuzugreifen.Sie können den Namen, den Typ oder die Richtung eines Parameters ändern sowie Parameter hinzufügen oder löschen.  
  
     Klicken Sie auf die Registerkarte **Eigenschaften**, um auf den Vorgangsschutzgrad und unterstützte Nachrichtenaustauschfunktionen des Vorgangs zuzugreifen.  
  
     Klicken Sie auf die Registerkarte **Berechtigungen**, um anzugeben, welche Gruppe oder Gruppen den Vorgang implementieren dürfen.  
  
4.  Klicken Sie auf **OK**, und die **ReceiveActivity**\-Aktivität zeigt den Namen des Vorgangs an, der implementiert wird.  
  
5.  Legen Sie die Workflowaktivitäten, die Sie für die Implementierung dieses Vorgangs verwenden werden, innerhalb der **ReceiveActivity**\-Aktivität ab.  
  
## Siehe auch  
 [Dialogfeld "Vorgang auswählen" \(Vorgängerversion\)](../workflow-designer/choose-operation-dialog-box-legacy.md)   
 [Vorgehensweise: Aufrufen eines WCF\-Vertragsvorgangs \(Vorgängerversion\)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md)   
 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)