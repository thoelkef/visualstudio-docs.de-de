---
title: XML-Schema-Explorer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 717a5d85a9d3a3251739b62728be572bee1487f6
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926782"
---
# <a name="xml-schema-explorer"></a>XML-Schema-Explorer

Der **XML-Schema-Explorer** ist in Microsoft Visual Studio und den XML-Editor integriert, damit Sie mit XSD-Schemas (XML Schema Definition Language) arbeiten können. Wenn Sie eine XML-Schema Datei öffnen, wird der Knoten Schemaset im **XML-Schema-Explorer**angezeigt. Alle enthaltenen, importierten oder neu definierten Schemas für die Zieldatei sowie alle Dateien, auf die über eine `include` -oder `import` -Anweisung verwiesen wird, werden auch im XML-Schema- **Explorer**angezeigt.

Der **XML-Schema-Explorer** ermöglicht Ihnen Folgendes:

- Abrufen einer kurzen Übersicht über das Schemaset.

- Durchsuchen und Navigieren in der Struktur.

- Durchführen von schlüsselwort- und schemaspezifischen Suchvorgängen. Weitere Informationen finden Sie unter durch [Suchen des Schema Satzes](../xml-tools/searching-the-schema-set.md).

- Hinzufügen der Suchergebnisse zur Diagramm Ansicht oder Inhalts Modell Ansicht

- Sortieren der Struktur nach Dokumentreihenfolge, Typ oder Namen. Weitere Informationen finden Sie unter [Sortieren, Filtern und Gruppieren](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

- Öffnen Sie den XML-Editor, und springen Sie zu den Code Positionen in der XSD-Datei. Weitere Informationen finden Sie unter [Integration in den XML-Editor](../xml-tools/integration-with-xml-editor.md).

- Generieren von Beispiel-XML für globale Elemente.

Der **XML-Schema-Explorer** stellt eine hierarchale Ansicht des Schemas bereit, das durch eine Strukturansicht festgelegt wurde. Der **XML-Schema-Explorer** bietet auch Such-, Filter-, Navigations-und Sortiervorgänge. Um auf den **XML-Schema-Explorer**zuzugreifen, führen Sie einen der folgenden Schritte aus:

- Wenn Sie sich in der [Start Ansicht](../xml-tools/start-view.md)befinden, klicken Sie auf den Link **XML-Schema-Explorer** .

- Wenn Sie sich in der [Diagramm Ansicht](../xml-tools/graph-view.md) oder in der [Inhalts Modell Ansicht](../xml-tools/content-model-view.md) befinden und über Knoten im Arbeitsbereich verfügen, wählen Sie im Kontextmenü (Rechtsklick) den **XML-Schema-Explorer**aus.

- Sie können auch den **XML-Schema-Explorer** im Menü **Ansicht** auswählen.

- Sie können auf den **XML-Schema-Explorer** aus einer *VB* -Datei zugreifen, die über ein Visual Basic XML-Literale verfügt, das einer *XSD* -Datei zugeordnet ist. Um das Schema im **XML-Schema-Explorer**anzuzeigen, klicken Sie mit der rechten Maustaste auf einen XML-Knoten in einem XML-Literaltyp oder auf einen XML-Namespace Import, und wählen Sie den Befehl **in Schema-Explorer** Weitere Informationen finden Sie unter [Integration von XML-Literalen in den XML-Schema-Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Strukturansicht
Der **XML-Schema-Explorer** zeigt vorkompilierte Schema Satz Informationen in einer Baumstruktur an. Die Struktur ist wie folgt aufgebaut:

- Auf oberster Ebene befindet sich der Schemasetknoten.

- Die zweite Ebene enthält die Namespaces.

- Die dritte Ebene enthält die Dateien.

- Die vierte Ebene enthält die globalen Knoten. Dazu können Elemente, Gruppen, komplexe Typen, einfache Typen, Attribute, Attributgruppen und `include`-, `import`- und `redefine`-Anweisungen gehören.

Im Folgenden Sie ein Beispiel für eine Struktur:

![XML-Schema-Explorer](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Auswahl und Aktivierung
Klicken Sie im Schema-Explorer einmal auf einen Knoten, um ihn hervorzuheben und auszuwählen.

Um einen Knoten zu aktivieren, doppelklicken Sie darauf, oder drücken Sie die **Eingabe** Taste, wenn der Knoten ausgewählt ist.

- Durch das Aktivieren eines Knotens wird die Datei, in der dieser Knoten definiert ist, geöffnet (wenn sie nicht bereits geöffnet ist), und der Knoten wird in der Datei ausgewählt.

- Durch das Aktivieren eines Dateiknotens wird die ausgewählte Datei geöffnet (wenn sie nicht bereits geöffnet ist), und der Knoten `<schema>` wird hervorgehoben.

- Beim Aktivieren eines Schemaset- oder Namespaceknotens geschieht nichts.

## <a name="drag-and-drop-nodes"></a>Knoten ziehen und ablegen
Sie können globale Knoten, Dateiknoten und Namespaceknoten per Drag &amp; Drop in einer XSD-Designer-Ansicht ablegen. Wenn es sich bei der aktuellen Ansicht um die [Start Ansicht](../xml-tools/start-view.md)handelt, wird die [Diagramm Ansicht](../xml-tools/graph-view.md)geöffnet, wenn Sie einen Knoten auf die Ansicht ziehen. Wenn es sich bei der aktuellen Ansicht um die [Inhalts Modell Ansicht](../xml-tools/content-model-view.md) oder die Diagramm Ansicht handelt, wird die Ansicht beim Ablegen eines Knotens nicht geändert.

Wenn Sie Dateien in der Ansicht ablegen, werden alle globalen Knoten in der Datei dem [Arbeitsbereich des XSD-Designers](../xml-tools/xml-schema-designer-workspace.md)hinzugefügt. Wenn Sie Namespaces in der Ansicht ablegen, werden dem Arbeitsbereich alle globalen Knoten im Namespace hinzugefügt. Der Arbeitsbereich wird für alle Ansichten verwendet.

 Lokale Knoten oder Importe können nicht per Drag &amp; Drop verschoben werden.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Hinzufügen von Knoten zum Arbeitsbereich aus dem XML-Schema-Explorer](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)