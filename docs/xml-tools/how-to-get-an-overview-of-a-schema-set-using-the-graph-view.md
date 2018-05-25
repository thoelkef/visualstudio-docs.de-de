---
title: 'Vorgehensweise: erhalten Sie einen Überblick über ein Schemaset mithilfe der Diagrammansicht im XML-Schema-Designer'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8be2666316bdc4d64d4f3dd4ec52c5104a1af5cc
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Vorgehensweise: bietet eine Übersicht über ein Schemaset in der Diagrammansicht

Dieses Thema beschreibt, wie die [Diagrammansicht](../xml-tools/graph-view.md) um einen allgemeinen Überblick über die Knoten in einem Schemaset und die Beziehungen zwischen den Knoten anzuzeigen.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>So erstellen Sie eine neue XSD-Datei und zeigen Sie das Stammelement in der Inhaltsmodellansicht an

1.  Erstellen Sie eine neue XML-Schemadatei, und speichern Sie die Datei *Relationships.xsd*.

2.  Klicken Sie auf die **verwenden Sie den XML-Editor, anzeigen und bearbeiten die zugrunde liegende XML-Schemadatei** Link in der Ausgangsansicht auf.

3.  Kopieren Sie die XML-schemabeispielcode aus [Beispiel-XML-Schema: Beziehungen](../xml-tools/sample-xsd-file-relationships.md) und fügen Sie ihn, um den Standardcode zu ersetzen, der die neue XSD-Datei hinzugefügt wurde.

4.  Mit der rechten Maustaste an einer beliebigen Stelle in der XML-Editor, und wählen Sie **Sicht-Designer**.

5.  Wählen Sie aus die Diagrammansicht der **XSD-Symbolleiste**.

6.  Wählen Sie **Schemaset** Knoten in der **XML-Schema-Explorer** , und ziehen Sie den Knoten, um Suface der Diagrammansicht zu entwerfen. Nun sollten alle globalen Knoten und Verbindungspfeile zwischen den Knoten mit Beziehungen angezeigt werden.

     ![Diagrammansicht](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")

7.  Klicken Sie auf der Entwurfsoberfläche auf einen Knoten, und überprüfen Sie in der Breadcrumb-Leiste, wo sich der ausgewählte Knoten im Schemaset befindet.

8.  Rick Klick auf einen Elementknoten, auf die Muster, die Entwurfsoberfläche, und wählen **Beispiel-XML generieren** auf die XML-Instanzdokument anzuzeigen.