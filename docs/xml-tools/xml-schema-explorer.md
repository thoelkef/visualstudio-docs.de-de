---
title: XML-Schema-Explorer
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 110cad9883cbb129368dac4d481443a9f5d9813c
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751588"
---
# <a name="xml-schema-explorer"></a>XML-Schema-Explorer

Die **XML-Schema-Explorer** ist in Microsoft Visual Studio und der XML-Editor, damit Sie zur Bearbeitung des Schemas für XML Schema Definition Language (XSD) integriert. Wenn Sie eine XML-Schemadatei öffnen die **Schemaset** Knoten befindet sich der **XML-Schema-Explorer**. Alle enthaltenen, importierten oder neu definierten Schemas für die Zieldatei als auch alle Dateien, die über verwiesen werden ein `include` oder `import` -Anweisung auch angezeigt, der **XML-Schema-Explorer**.

 Die **XML-Schema-Explorer** können Sie die folgenden Schritte ausführen:

-   Abrufen einer kurzen Übersicht über das Schemaset.

-   Durchsuchen und Navigieren in der Struktur.

-   Durchführen von schlüsselwort- und schemaspezifischen Suchvorgängen. Weitere Informationen finden Sie unter [Durchsuchen des Schemasets](../xml-tools/searching-the-schema-set.md).

-   Hinzufügen der Suchergebnisse auf die Diagramm- oder Inhaltsmodellansicht

-   Sortieren der Struktur nach Dokumentreihenfolge, Typ oder Namen. Weitere Informationen finden Sie unter [sortieren, Filtern und Gruppieren von](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

-   Öffnen des XML-Editors und Springen zu Codepositionen in der XSD-Datei. Weitere Informationen finden Sie unter [Integration mit XML-Editor](../xml-tools/integration-with-xml-editor.md).

-   Generieren von Beispiel-XML für globale Elemente.

Die **XML-Schema-Explorer** bietet eine hierarchische Ansicht des Schemasets einer Strukturansicht an. Die **XML-Schema-Explorer** bietet auch die Suche, Filterung, Navigation und Sortierung. Für den Zugriff auf die **XML-Schema-Explorer**, führen Sie eine der folgenden:

-   Bei der [Ausgangsansicht](../xml-tools/start-view.md), klicken Sie auf die **XML-Schema-Explorer** Link.

-   Bei der [Diagrammansicht](../xml-tools/graph-view.md) oder [Inhaltsmodellansicht](../xml-tools/content-model-view.md) und Knoten in Ihrem Arbeitsbereich, verwenden Sie im Kontextmenü auf die **XML-Schema-Explorer**.

-   Sie können auch auswählen, die **XML-Schema-Explorer** aus der **Ansicht** Menü.

-   Sie erreichen die **XML-Schema-Explorer** aus einer *vb* -Datei, die ein Visual Basic-XML-Literal zugeordnet hat ein *XSD* Datei. Legen Sie das Schema angezeigt der **XML-Schema-Explorer**mit der rechten Maustaste auf einen XML-Knoten in ein XML-Literal oder einem XML-Namespaceimport, und wählen Sie die **im Schema-Explorer anzeigen** Befehl. Weitere Informationen finden Sie unter [Integration des XML-Literalen in XML-Schema-Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Strukturansicht
 Die **XML-Schema-Explorer** zeigt vorkompiliert Schemaset Informationen in einer Baumstruktur. Die Struktur ist wie folgt aufgebaut:

-   Auf oberster Ebene befindet sich der Schemasetknoten.

-   Die zweite Ebene enthält die Namespaces.

-   Die dritte Ebene enthält die Dateien.

-   Die vierte Ebene enthält die globalen Knoten. Dazu können Elemente, Gruppen, komplexe Typen, einfache Typen, Attribute, Attributgruppen und `include`-, `import`- und `redefine`-Anweisungen gehören.

Im Folgenden Sie ein Beispiel für eine Struktur:

![XML-Schema-Explorer](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Auswahl und Aktivierung
 Klicken Sie im Schema-Explorer einmal auf einen Knoten, um ihn hervorzuheben und auszuwählen.

 Um einen Knoten zu aktivieren, doppelklicken Sie darauf, oder drücken Sie **EINGABETASTE** Wenn der Knoten ausgewählt ist.

-   Durch das Aktivieren eines Knotens wird die Datei, in der dieser Knoten definiert ist, geöffnet (wenn sie nicht bereits geöffnet ist), und der Knoten wird in der Datei ausgewählt.

-   Durch das Aktivieren eines Dateiknotens wird die ausgewählte Datei geöffnet (wenn sie nicht bereits geöffnet ist), und der Knoten `<schema>` wird hervorgehoben.

-   Beim Aktivieren eines Schemaset- oder Namespaceknotens geschieht nichts.

## <a name="drag-and-drop-nodes"></a>Drag & drop von Knoten
 Sie können globale Knoten, Dateiknoten und Namespaceknoten per Drag & Drop in einer XSD-Designer-Ansicht ablegen. Wenn die aktuelle Ansicht der [Ausgangsansicht](../xml-tools/start-view.md), Ziehen eines Knotens die Ansicht wird geöffnet. die [Diagrammansicht](../xml-tools/graph-view.md). Wenn die aktuelle Ansicht der [Inhaltsmodellansicht](../xml-tools/content-model-view.md) oder Diagrammansicht, die Sicht wird nicht geändert werden, wenn Sie einen Knoten löschen.

 Ablegen von Dateien für die Sicht werden alle globalen Knoten in der Datei hinzufügen der [Arbeitsbereich des XSD-Designers](../xml-tools/xml-schema-designer-workspace.md). Wenn Sie Namespaces in der Ansicht ablegen, werden dem Arbeitsbereich alle globalen Knoten im Namespace hinzugefügt. Der Arbeitsbereich wird für alle Ansichten verwendet.

 Lokale Knoten oder Importe können nicht per Drag & Drop verschoben werden.

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Hinzufügen von Knoten im Arbeitsbereich "" aus der XML-Schema-Explorer](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)