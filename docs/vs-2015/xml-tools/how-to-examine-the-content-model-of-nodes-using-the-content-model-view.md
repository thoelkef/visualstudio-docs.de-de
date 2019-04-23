---
title: 'Vorgehensweise: Untersuchen des Inhaltsmodells von Knoten in der Inhaltsmodellansicht | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 24ceb80c0ffd03e7c796b7a5d5abdc93f4c1c78d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099064"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Vorgehensweise: Untersuchen des Inhaltsmodells von Knoten in der Inhaltsmodellansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie zum Untersuchen der Knoten in der [Inhaltsmodellansicht](../xml-tools/content-model-view.md).  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>So erstellen Sie eine neue XSD-Datei und zeigen Sie das Stammelement in der Inhaltsmodellansicht an  
  
1. Erstellen Sie eine neue XML-Schemadatei.  
  
2. Klicken Sie auf **verwenden Sie den XML-Editor anzeigen und bearbeiten die zugrunde liegende XML-Schemadatei** in der Ausgangsansicht auf.  
  
3. Kopieren Sie die XML-schemabeispielcode aus [XML-Beispielschema: Bestellungsschema](../xml-tools/sample-xsd-file-purchase-order-schema.md) und fügen Sie ihn, um den Standardcode zu ersetzen, das die neue XSD-Datei standardmäßig hinzugefügt wurde.  
  
4. Wählen Sie die `purchaseOrder` Element im Schema-Explorer mit der rechten Maustaste die `purchaseOrder` Element in der XML-Editor, und wählen **im XML-Explorer anzeigen**.  
  
5. Mit der rechten Maustaste die `purchaseOrder` im XML-Explorer, und wählen Sie **in Inhaltsmodellansicht anzeigen**.  
  
     Das `purchaseOrder`-Element wird auf der Entwurfsoberfläche der Inhaltsmodellansicht angezeigt.  
  
6. Erweitern Sie die Knoten `shipTo`, `billTo` und `items`, indem Sie auf jeden Knoten doppelklicken oder auf den Doppelpfeil rechts neben jedem Knoten klicken.  
  
     Die Knoten des `purchaseOrder`-Elements werden jetzt erweitert, und Sie können das Inhaltsmodell des Elements sehen.  
  
7. Klicken Sie auf einen Knoten unter dem `purchaseOrder`-Element, und überprüfen Sie in der Breadcrumb-Leiste, wo sich der ausgewählte Knoten im Schemaset befindet.  
  
8. Klicken Sie auf die **Dokumentation anzeigen** -Schaltfläche in der XSD-Symbolleiste, um die Dokumentation ein-oder auszublenden. Die Dokumentation kann auch über das Kontextmenü der Entwurfsoberfläche ein- und ausgeblendet werden.  
  
9. Rick-klicken Sie auf die `purchaseOrder` Knoten, und wählen **Beispiel-XML generieren** XML-Instanzendokument angezeigt.
