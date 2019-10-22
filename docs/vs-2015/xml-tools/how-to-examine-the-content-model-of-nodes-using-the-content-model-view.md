---
title: 'Vorgehensweise: Untersuchen des Inhalts Modells von Knoten mithilfe der Inhalts Modell Ansicht | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ddadcb0fbd772a5638bf6023b8cf6c18fbd270d7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670855"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Gewusst wie: Untersuchen des Inhaltsmodells von Knoten in der Inhaltsmodellansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie Sie Ihre Knoten mithilfe der [Inhalts Modell Ansicht](../xml-tools/content-model-view.md)untersuchen.

### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>So erstellen Sie eine neue XSD-Datei und zeigen Sie das Stammelement in der Inhaltsmodellansicht an

1. Erstellen Sie eine neue XML-Schemadatei.

2. Klicken Sie auf **XML-Editor verwenden, um die zugrunde liegende XML-Schema Datei in der Start Ansicht anzuzeigen und zu bearbeiten** .

3. Kopieren Sie den XML-Schema Beispielcode aus dem [Beispiel-XML-Schema: Bestell Schema](../xml-tools/sample-xsd-file-purchase-order-schema.md) , und fügen Sie ihn ein, um den Code zu ersetzen, der standardmäßig der neuen XSD-Datei hinzugefügt wurde.

4. Wählen Sie im Schema-Explorer das `purchaseOrder` Element aus, indem Sie im XML-Editor mit der rechten Maustaste auf das Element `purchaseOrder` klicken und **im XML-Explorer anzeigen**auswählen.

5. Klicken Sie mit der rechten Maustaste auf die `purchaseOrder` im XML-Explorer, und wählen Sie **in Inhalts Modell Ansicht anzeigen aus**.

     Das `purchaseOrder`-Element wird auf der Entwurfsoberfläche der Inhaltsmodellansicht angezeigt.

6. Erweitern Sie die Knoten `shipTo`, `billTo` und `items`, indem Sie auf jeden Knoten doppelklicken oder auf den Doppelpfeil rechts neben jedem Knoten klicken.

     Die Knoten des `purchaseOrder`-Elements werden jetzt erweitert, und Sie können das Inhaltsmodell des Elements sehen.

7. Klicken Sie auf einen Knoten unter dem `purchaseOrder`-Element, und überprüfen Sie in der Breadcrumb-Leiste, wo sich der ausgewählte Knoten im Schemaset befindet.

8. Klicken Sie auf der XSD-Symbolleiste auf die Schaltfläche **Dokumentation anzeigen** , um die Dokumentation zu wechseln. Die Dokumentation kann auch über das Kontextmenü der Entwurfsoberfläche ein- und ausgeblendet werden.

9. Klicken Sie auf den Knoten `purchaseOrder`, und wählen Sie **Beispiel-XML generieren** aus, um das XML-Instanzdokument anzuzeigen.
