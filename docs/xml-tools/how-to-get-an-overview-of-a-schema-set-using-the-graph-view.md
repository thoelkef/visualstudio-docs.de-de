---
title: 'XML-Schema-Designer: Abrufen einer Schemasetübersicht mithilfe der Diagrammansicht'
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592671"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Vorgehensweise: Abrufen einer Übersicht über ein Schemaset in der Diagrammansicht

In diesem Thema wird beschrieben, wie Sie mithilfe der [Diagrammansicht](../xml-tools/graph-view.md) eine allgemeine Ansicht der Knoten in einem Schemaset und der Beziehungen zwischen den Knoten anzeigen.

## <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>So erstellen Sie eine neue XSD-Datei und zeigen Sie das Stammelement in der Inhaltsmodellansicht an

1. Erstellen Sie eine neue XML-Schemadatei, und speichern Sie die Datei unter dem Namen *Relationships.xsd*.

2. Klicken Sie in der Ausgangsansicht auf den Link **Verwenden Sie den XML-Editor, um die zugrunde liegende XML-Schemadatei anzuzeigen und zu bearbeiten**.

3. Kopieren Sie den XML-Schemabeispielcode aus [XML-Beispielschema: Beziehungen](../xml-tools/sample-xsd-file-relationships.md), und fügen Sie ihn ein, um den Standardcode zu ersetzen, der der neuen XSD-Datei hinzugefügt wurde.

4. Klicken Sie mit der rechten Maustaste an einer beliebigen Stelle im XML-Editor, und wählen Sie **Ansichts-Designer** aus.

5. Wählen Sie auf der **XSD-Symbolleiste** die Diagrammansicht aus.

6. Markieren Sie im **XML-Schema-Explorer** den Knoten **Schemaset**, und ziehen Sie den Knoten von der Entwurfsoberfläche in die Diagrammansicht. Nun sollten alle globalen Knoten und Verbindungspfeile zwischen den Knoten mit Beziehungen angezeigt werden.

     ![Diagrammansicht](../xml-tools/media/relationshipingraphview.gif)

7. Klicken Sie auf der Entwurfsoberfläche auf einen Knoten, und überprüfen Sie in der Breadcrumb-Leiste, wo sich der ausgewählte Knoten im Schemaset befindet.

8. Klicken Sie auf der Entwurfsoberfläche mit der rechten Maustaste auf einen Elementknoten, und wählen Sie **Beispiel-XML generieren** aus, um das XML-Instanzdokument anzuzeigen.
