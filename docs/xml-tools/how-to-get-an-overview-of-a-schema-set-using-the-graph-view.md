---
title: 'Vorgehensweise: Erhalten Sie einen Überblick über ein Schemaset, das mit der Diagrammansicht im XML-Schema Designer'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1a161e2b354559eed220914842eaba73f20654b1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917093"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Vorgehensweise: Bietet einen Überblick über ein Schemaset in der Diagrammansicht

In diesem Thema wird beschrieben, wie Sie mit der [Diagrammansicht](../xml-tools/graph-view.md) um einen allgemeinen Überblick über die Knoten in einem Schemaset und die Beziehungen zwischen den Knoten anzuzeigen.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>So erstellen Sie eine neue XSD-Datei und zeigen Sie das Stammelement in der Inhaltsmodellansicht an

1.  Erstellen Sie eine neue XML-Schema-Datei, und speichern Sie die Datei *Relationships.xsd*.

2.  Klicken Sie auf die **verwenden Sie den XML-Editor anzeigen und bearbeiten die zugrunde liegende XML-Schemadatei** Link in der Ausgangsansicht auf.

3.  Kopieren Sie die XML-schemabeispielcode aus [Beispiel-XML-Schema: Beziehungen](../xml-tools/sample-xsd-file-relationships.md) und fügen Sie ihn, um den Standardcode zu ersetzen, das die neue XSD-Datei standardmäßig hinzugefügt wurde.

4.  Mit der rechten Maustaste in der XML-Editor, und wählen Sie **Ansicht-Designer**.

5.  Wählen Sie die Diagrammansicht aus der **XSD-Symbolleiste**.

6.  Wählen Sie **Schemaset** Knoten in der **XML-Schema-Explorer** und ziehen Sie den Knoten auf der Entwurfsoberfläche der Diagrammansicht angezeigt. Nun sollten alle globalen Knoten und Verbindungspfeile zwischen den Knoten mit Beziehungen angezeigt werden.

     ![Diagrammansicht](../xml-tools/media/relationshipingraphview.gif)

7.  Klicken Sie auf der Entwurfsoberfläche auf einen Knoten, und überprüfen Sie in der Breadcrumb-Leiste, wo sich der ausgewählte Knoten im Schemaset befindet.

8.  Rick, klicken Sie auf einen Elementknoten, auf die Entwurfsoberfläche, und wählen **Beispiel-XML generieren** XML-Instanzendokument angezeigt.