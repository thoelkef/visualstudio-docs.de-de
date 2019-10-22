---
title: 'XML-Schema-Designer: Get Schema Set Overview using Graph View'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8acc2ff6a41f7057818c4a7659f2aa9d07c8bac
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651176"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Gewusst wie: Anzeigen einer Übersicht über ein Schemaset mithilfe der Diagramm Ansicht

In diesem Thema wird beschrieben, wie die [Diagramm Ansicht](../xml-tools/graph-view.md) verwendet wird, um eine allgemeine Ansicht der Knoten in einem Schemaset und die Beziehungen zwischen den Knoten anzuzeigen.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>So erstellen Sie eine neue XSD-Datei und zeigen Sie das Stammelement in der Inhaltsmodellansicht an

1. Erstellen Sie eine neue XML-Schema Datei, und speichern Sie die Datei als " *Beziehungen. xsd*".

2. Klicken Sie auf den **XML-Editor verwenden, um den zugrunde liegenden XML-Schema Datei** Link in der Start Ansicht anzuzeigen und zu bearbeiten.

3. Kopieren Sie den XML-Schema Beispielcode aus XML- [Beispiel Schema: Beziehungen](../xml-tools/sample-xsd-file-relationships.md) , und fügen Sie ihn ein, um den Code zu ersetzen, der standardmäßig der neuen XSD-Datei hinzugefügt wurde.

4. Klicken Sie mit der rechten Maustaste in den XML-Editor, und wählen Sie **Ansicht-Designer**

5. Wählen Sie die Diagramm Ansicht von der **XSD-Symbolleiste**aus.

6. Wählen Sie im **XML-Schema-Explorer** den Knoten **Schema Satz** aus, und ziehen Sie den Knoten auf die Entwurfs Oberfläche der Diagramm Ansicht. Nun sollten alle globalen Knoten und Verbindungspfeile zwischen den Knoten mit Beziehungen angezeigt werden.

     ![Diagrammansicht](../xml-tools/media/relationshipingraphview.gif)

7. Klicken Sie auf der Entwurfsoberfläche auf einen Knoten, und überprüfen Sie in der Breadcrumb-Leiste, wo sich der ausgewählte Knoten im Schemaset befindet.

8. Klicken Sie auf der Entwurfs Oberfläche auf einen beliebigen Elementknoten, und wählen Sie **Beispiel-XML generieren** aus, um das XML-Instanzdokument anzuzeigen.