---
title: "Gewusst wie: Untersuchen des Inhaltsmodells von Knoten in der Inhaltsmodellansicht | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Untersuchen des Inhaltsmodells von Knoten in der Inhaltsmodellansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie Sie die Knoten mithilfe der [Inhaltsmodellansicht](../xml-tools/content-model-view.md) untersuchen.  
  
### So erstellen Sie eine neue XSD\-Datei und zeigen Sie das Stammelement in der Inhaltsmodellansicht an  
  
1.  Erstellen Sie eine neue XML\-Schemadatei.  
  
2.  Klicken Sie in der Ausgangsansicht auf **Verwenden Sie den XML\-Editor, um die zugrunde liegende XML\-Schemadatei anzuzeigen und zu bearbeiten**.  
  
3.  Kopieren Sie den XML\-Schemabeispielcode aus [XML\-Beispielschema: Bestellungsschema](../xml-tools/sample-xsd-file-purchase-order-schema.md), und fügen Sie ihn ein, um den Standardcode zu ersetzen, der der neuen XSD\-Datei hinzugefügt wurde.  
  
4.  Wählen Sie im Schema\-Explorer das `purchaseOrder`\-Element aus, indem Sie im XML\-Editor mit der rechten Maustaste auf das `purchaseOrder`\-Element klicken und **In XML\-Schema\-Explorer anzeigen** auswählen.  
  
5.  Klicken Sie im XML\-Explorer mit der rechten Maustaste auf `purchaseOrder`, und wählen Sie **In Inhaltsmodellansicht anzeigen** aus.  
  
     Das `purchaseOrder`\-Element wird auf der Entwurfsoberfläche der Inhaltsmodellansicht angezeigt.  
  
6.  Erweitern Sie die Knoten `shipTo`, `billTo` und `items`, indem Sie auf jeden Knoten doppelklicken oder auf den Doppelpfeil rechts neben jedem Knoten klicken.  
  
     Die Knoten des `purchaseOrder`\-Elements werden jetzt erweitert, und Sie können das Inhaltsmodell des Elements sehen.  
  
7.  Klicken Sie auf einen Knoten unter dem `purchaseOrder`\-Element, und überprüfen Sie in der Breadcrumb\-Leiste, wo sich der ausgewählte Knoten im Schemaset befindet.  
  
8.  Klicken Sie auf der XSD\-Symbolleiste auf die Schaltfläche **Dokumentation anzeigen**, um die Dokumentation ein\- oder auszublenden.Die Dokumentation kann auch über das Kontextmenü der Entwurfsoberfläche ein\- und ausgeblendet werden.  
  
9. Klicken Sie mit der rechten Maustaste auf den `purchaseOrder`\-Knoten, und wählen Sie **Beispiel\-XML generieren** aus, um das XML\-Instanzdokument anzuzeigen.