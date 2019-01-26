---
title: Untersuchen des Inhaltsmodells von Knoten in der Inhaltsmodellansicht im XML-Schema-Designer
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a8f1f3a6897e64c58245ac336cb42074db3e262
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54930946"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>Vorgehensweise: Untersuchen des Inhaltsmodells von Knoten in der Inhaltsmodellansicht

In diesem Thema wird beschrieben, wie zum Untersuchen der Knoten in der [Inhaltsmodellansicht](../xml-tools/content-model-view.md).

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>So erstellen Sie eine neue XSD-Datei und zeigen Sie das Stammelement in der Inhaltsmodellansicht an

1.  Erstellen Sie eine neue XML-Schemadatei.

2.  Klicken Sie auf **verwenden Sie den XML-Editor anzeigen und bearbeiten die zugrunde liegende XML-Schemadatei** in der Ausgangsansicht auf.

3.  Kopieren Sie die XML-schemabeispielcode aus [Beispiel-XML-Schema: Bestellungsschema](../xml-tools/sample-xsd-file-purchase-order-schema.md) und fügen Sie ihn, um den Standardcode zu ersetzen, das die neue XSD-Datei standardmäßig hinzugefügt wurde.

4.  Wählen Sie die `purchaseOrder` Element im Schema-Explorer mit der rechten Maustaste die `purchaseOrder` Element in der XML-Editor, und wählen **im XML-Explorer anzeigen**.

5.  Mit der rechten Maustaste die `purchaseOrder` im XML-Explorer, und wählen Sie **in Inhaltsmodellansicht anzeigen**.

     Das `purchaseOrder`-Element wird auf der Entwurfsoberfläche der Inhaltsmodellansicht angezeigt.

6.  Erweitern Sie die Knoten `shipTo`, `billTo` und `items`, indem Sie auf jeden Knoten doppelklicken oder auf den Doppelpfeil rechts neben jedem Knoten klicken.

     Die Knoten des `purchaseOrder`-Elements werden jetzt erweitert, und Sie können das Inhaltsmodell des Elements sehen.

7.  Klicken Sie auf einen Knoten unter dem `purchaseOrder`-Element, und überprüfen Sie in der Breadcrumb-Leiste, wo sich der ausgewählte Knoten im Schemaset befindet.

8.  Klicken Sie auf die **Dokumentation anzeigen** -Schaltfläche in der XSD-Symbolleiste, um die Dokumentation ein-oder auszublenden. Die Dokumentation kann auch über das Kontextmenü der Entwurfsoberfläche ein- und ausgeblendet werden.

9. Rick-klicken Sie auf die `purchaseOrder` Knoten, und wählen **Beispiel-XML generieren** XML-Instanzendokument angezeigt.