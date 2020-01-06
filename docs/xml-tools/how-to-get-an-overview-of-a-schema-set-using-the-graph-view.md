---
title: 'XML Schema Designer: Get schema set overview using Graph View'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f066bc96cd5acf314150def2e40ec3064d154b8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592671"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>How to: Get an overview of a schema set using the Graph View

This topic describes how to use the [Graph View](../xml-tools/graph-view.md) to see a high-level view of the nodes in a schema set and the relationships between the nodes.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>So erstellen Sie eine neue XSD-Datei und zeigen Sie das Stammelement in der Inhaltsmodellansicht an

1. Create a new XML Schema file and save the file as *Relationships.xsd*.

2. Click the **Use XML editor to view and edit the underlying XML Schema file** link on the Start View.

3. Kopieren Sie den XML-Schema Beispielcode aus XML- [Beispiel Schema: Beziehungen](../xml-tools/sample-xsd-file-relationships.md) , und fügen Sie ihn ein, um den Code zu ersetzen, der standardmäßig der neuen XSD-Datei hinzugefügt wurde.

4. Klicken Sie mit der rechten Maustaste in den XML-Editor, und wählen Sie **Ansicht-Designer**

5. Wählen Sie die Diagramm Ansicht von der **XSD-Symbolleiste**aus.

6. Wählen Sie im **XML-Schema-Explorer** den Knoten **Schema Satz** aus, und ziehen Sie den Knoten auf die Entwurfs Oberfläche der Diagramm Ansicht. Nun sollten alle globalen Knoten und Verbindungspfeile zwischen den Knoten mit Beziehungen angezeigt werden.

     ![Diagrammansicht](../xml-tools/media/relationshipingraphview.gif)

7. Klicken Sie auf der Entwurfsoberfläche auf einen Knoten, und überprüfen Sie in der Breadcrumb-Leiste, wo sich der ausgewählte Knoten im Schemaset befindet.

8. Klicken Sie auf der Entwurfs Oberfläche auf einen beliebigen Elementknoten, und wählen Sie **Beispiel-XML generieren** aus, um das XML-Instanzdokument anzuzeigen.
