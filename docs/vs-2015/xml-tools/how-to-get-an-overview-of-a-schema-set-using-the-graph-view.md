---
title: 'Gewusst wie: Anzeigen einer Übersicht über ein Schemaset mithilfe der Diagramm Ansicht | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: c0df4b0d-52ef-4a6c-9676-1d8311aad7c7
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7009e5772b4f4c6977d58d2c52d733999a0d9369
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670894"
---
# <a name="how-to-get-an-overview-of-a-schema-set-using-the-graph-view"></a>Gewusst wie: Anzeigen einer Übersicht über ein Schemaset in der Diagrammansicht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie Sie mithilfe der [Diagrammansicht](../xml-tools/graph-view.md) eine allgemeine Ansicht der Knoten in einem Schemaset und der Beziehungen zwischen den Knoten anzeigen.

### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>So erstellen Sie eine neue XSD-Datei und zeigen Sie das Stammelement in der Inhaltsmodellansicht an

1. Erstellen Sie eine neue XML-Schemadatei, und speichern Sie die Datei unter dem Namen "Relationships.xsd".

2. Klicken Sie auf den **XML-Editor verwenden, um den zugrunde liegenden XML-Schema Datei** Link in der Start Ansicht anzuzeigen und zu bearbeiten.

3. Kopieren Sie den XML-Schema Beispielcode aus XML- [Beispiel Schema: Beziehungen](../xml-tools/sample-xsd-file-relationships.md) , und fügen Sie ihn ein, um den Code zu ersetzen, der standardmäßig der neuen XSD-Datei hinzugefügt wurde.

4. Klicken Sie mit der rechten Maustaste in den XML-Editor, und wählen Sie **Ansicht-Designer**

5. Wählen Sie auf der XSD-Symbolleiste die Diagrammansicht aus.

6. Wählen Sie im XML-Schema-Explorer den Knoten **Schema Satz** aus, und ziehen Sie den Knoten zur Entwurfs Unterseite der Diagramm Ansicht. Nun sollten alle globalen Knoten und Verbindungspfeile zwischen den Knoten mit Beziehungen angezeigt werden.

     ![Diagrammansicht](../xml-tools/media/relationshipingraphview.gif "RelationshipInGraphView")

7. Klicken Sie auf der Entwurfsoberfläche auf einen Knoten, und überprüfen Sie in der Breadcrumb-Leiste, wo sich der ausgewählte Knoten im Schemaset befindet.

8. Klicken Sie mit der rechten Maustaste auf einen beliebigen Elementknoten auf der Oberfläche, und wählen Sie **Beispiel-XML generieren** , um das XML-Instanzdokument anzuzeigen.
