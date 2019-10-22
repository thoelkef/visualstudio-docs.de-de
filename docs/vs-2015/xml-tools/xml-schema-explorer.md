---
title: XML-Schema-Explorer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5e9f61c56dd7ff2a9c6c19afc20ed279a7fdf855
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669375"
---
# <a name="xml-schema-explorer"></a>XML-Schema-Explorer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der XML-Schema-Explorer ist in Microsoft Visual Studio und den XML-Editor integriert, um die Arbeit mit XSD-Schemas (XML-Schemadefinitionssprache) zu ermöglichen. Wenn Sie eine XML-Schema Datei öffnen, wird der Knoten **Schemaset** im XML-Schema-Explorer angezeigt. Alle enthaltenen, importierten oder neu definierten Schemas für die Zieldatei und alle Dateien, auf die durch eine `include`- oder `import`-Anweisung verwiesen wird, werden auch im XML-Schema-Explorer angezeigt.

 Der XML-Schema-Explorer ermöglicht folgende Tätigkeiten:

- Abrufen einer kurzen Übersicht über das Schemaset.

- Durchsuchen und Navigieren in der Struktur.

- Durchführen von schlüsselwort- und schemaspezifischen Suchvorgängen. Weitere Informationen finden Sie unter durch [Suchen des Schema Satzes](../xml-tools/searching-the-schema-set.md).

- Hinzufügen der Suchergebnisse zur Diagramm- oder Inhaltsmodellansicht.

- Sortieren der Struktur nach Dokumentreihenfolge, Typ oder Namen. Weitere Informationen finden Sie unter [Sortieren, Filtern und Gruppieren](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

- Öffnen des XML-Editors und Springen zu Codepositionen in der XSD-Datei. Weitere Informationen finden Sie unter [Integration in den XML-Editor](../xml-tools/integration-with-xml-editor.md).

- Generieren von Beispiel-XML für globale Elemente.

  Der XML-Schema-Explorer stellt mit einer Strukturansicht eine hierarchische Ansicht des Schemasets bereit. Der XML-Schema-Explorer stellt auch Funktionen zu Suche, Filterung, Navigation und Sortierung bereit. Führen Sie einen der folgenden Schritte aus, um auf den XML-Schema-Explorer zuzugreifen:

- Wenn Sie sich in der [Start Ansicht](../xml-tools/start-view.md)befinden, klicken Sie auf den Link **XML-Schema-Explorer** .

- Wenn Sie sich in der [Diagramm Ansicht](../xml-tools/graph-view.md) oder in der [Inhalts Modell Ansicht](../xml-tools/content-model-view.md) befinden und über Knoten im Arbeitsbereich verfügen, wählen Sie im Kontextmenü den XML-Schema-Explorer aus.

- Sie können auch das XML-Schema exploreraus dem Menü **Ansicht** auswählen.

- Sie können auf das XML-Schema exploreraus einer VB-Datei zugreifen, die über ein Visual Basic XML-Literale verfügt, das einer XSD-Datei zugeordnet ist. Um das im XML-Schema-Explorer festgelegte Schema anzuzeigen, klicken Sie mit der rechten Maustaste auf einen XML-Knoten in einem XML-Literaltyp oder einem XML-Namespace Import, und wählen Sie den Befehl **in Schema** Weitere Informationen finden Sie unter [Integration von XML-Literalen in den XML-Schema-Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Strukturansicht
 Der XML-Schema-Explorer zeigt vorkompilierte Schemasetinformationen in einer Struktur an. Die Struktur ist wie folgt aufgebaut:

- Auf oberster Ebene befindet sich der Schemasetknoten.

- Die zweite Ebene enthält die Namespaces.

- Die dritte Ebene enthält die Dateien.

- Die vierte Ebene enthält die globalen Knoten. Dazu können Elemente, Gruppen, komplexe Typen, einfache Typen, Attribute, Attributgruppen und `include`-, `import`- und `redefine`-Anweisungen gehören.

  Im Folgenden Sie ein Beispiel für eine Struktur:

  ![XML-Schema-Explorer](../xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")

## <a name="selection-and-activation"></a>Auswahl und Aktivierung
 Klicken Sie im Schema-Explorer einmal auf einen Knoten, um ihn hervorzuheben und auszuwählen.

 Um einen Knoten zu aktivieren, doppelklicken Sie darauf, oder drücken Sie die **Eingabe** Taste, wenn der Knoten ausgewählt ist.

- Durch das Aktivieren eines Knotens wird die Datei, in der dieser Knoten definiert ist, geöffnet (wenn sie nicht bereits geöffnet ist), und der Knoten wird in der Datei ausgewählt.

- Durch das Aktivieren eines Dateiknotens wird die ausgewählte Datei geöffnet (wenn sie nicht bereits geöffnet ist), und der Knoten `<schema>` wird hervorgehoben.

- Beim Aktivieren eines Schemaset- oder Namespaceknotens geschieht nichts.

## <a name="draging-and-dropping-nodes"></a>Drag &amp; Drop von Knoten
 Sie können globale Knoten, Dateiknoten und Namespaceknoten per Drag &amp; Drop in einer XSD-Designer-Ansicht ablegen. Wenn es sich bei der aktuellen Ansicht um die [Start Ansicht](../xml-tools/start-view.md)handelt, wird die [Diagramm Ansicht](../xml-tools/graph-view.md)geöffnet, wenn Sie einen Knoten auf die Ansicht ziehen. Wenn es sich bei der aktuellen Ansicht um die [Inhalts Modell Ansicht](../xml-tools/content-model-view.md) oder die Diagramm Ansicht handelt, wird die Ansicht beim Ablegen eines Knotens nicht geändert.

 Wenn Sie Dateien in der Ansicht ablegen, werden alle globalen Knoten in der Datei dem [Arbeitsbereich des XSD-Designers](../xml-tools/xml-schema-designer-workspace.md)hinzugefügt. Wenn Sie Namespaces in der Ansicht ablegen, werden dem Arbeitsbereich alle globalen Knoten im Namespace hinzugefügt. Der Arbeitsbereich wird für alle Ansichten verwendet.

 Lokale Knoten oder Importe können nicht per Drag &amp; Drop verschoben werden.

## <a name="in-this-section"></a>In diesem Abschnitt

- [Durchsuchen des Schemasets](../xml-tools/searching-the-schema-set.md)

- [Sortieren, Filtern und Gruppieren](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)

- [Kontextmenüs](../xml-tools/context-menus-xml-schema-explorer.md)

- [Integration von XML-Literalen in den XML-Schema-Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)

## <a name="see-also"></a>Siehe auch
 [Gewusst wie: Hinzufügen von Knoten aus dem XML-Schema-Explorer zum Arbeitsbereich](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
